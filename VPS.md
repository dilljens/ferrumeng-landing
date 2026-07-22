# VPS Inventory — `40.160.241.74`

Hostname: `vps-65c892e3-vps-ovh-us`
OS: Ubuntu 26.04 LTS (Resolute Raccoon)
Kernel: 7.0.0-14-generic
CPU: AMD EPYC-Genoa, 4 cores
RAM: 7.7 GB total (~1.3 GB used)
Swap: 4 GB (2.4 GB used)
Disk: 72 GB (41 GB used — 57%)
Monitoring: Netdata (http://localhost:19999) + cron health check (every 5 min)

Tailscale: connected (100.73.157.121) — nodes: cachyos-x, iphone173

---

## Docker Containers (running)

### Ferrum Engineering (ours)

| Container | Image | Ports | RAM | Status |
|-----------|-------|-------|-----|--------|
| `sololedger-api` | deploy-sololedger-api | 8100 | 20 MB | Up |
| `poolsplat` | deploy-poolsplat | 3138 | 44 MB | Up |
| `ferrum-caddy` | caddy:2-alpine | 80, 443 | 18 MB | Up |

**Total: ~82 MB RAM, ~11 MB repo disk**

### Imposter (Supabase stack)

| Container | Image | Ports | RAM | Status |
|-----------|-------|-------|-----|--------|
| `imposter-backend-db-1` | postgres:17 | 127.0.0.1:5432 | 14 MB | Up (healthy) |
| `imposter-backend-rest-1` | postgrest/postgrest:v14.13 | 127.0.0.1:3000 | 8 MB | Up |
| `imposter-backend-realtime-1` | supabase/realtime:v2.111.4 | 127.0.0.1:4000 | 70 MB | Up |

Config: `/opt/imposter-backend/docker-compose.yml` — Supabase stack (PostgREST + Realtime + PostgreSQL) for [imposterirl](https://github.com/dilljens/imposterirl).

---

## Systemd Services (running)

| Service | Purpose | RAM | Notes |
|---------|---------|-----|-------|
| `scripture-api.service` | ScriptureEngine API | 179 MB | Python, port 8000 |
| `inklomancer-server.service` | Inklomancer Game Server | 21 MB | Node/tsx, port 3100 |
| `daglock-indexer.service` | DagLock indexer | — | Rust binary, port 8443 (127.0.0.1) |
| `daglock-bot.service` | DagLock trading bot | — | Node.js |
| `daglock-smtp-debug.service` | DagLock SMTP debug | — | — |
| `remote-recording.service` | TalkEdit Remote Recording | 4 MB | Python, port 8644 |
| `actions.runner.dilljens-TalkEdit.*` | GitHub Actions runner | **4.5 GB** | For TalkEdit repo CI |
| `tailscaled.service` | Tailscale VPN | — | Mesh VPN |
| `ssh.service` | SSH server | — | Port 22 |
| `docker.service` | Docker daemon | — | — |
| `cron.service` | Cron | — | Has daglock-indexer health check |
| `imposter-frontend.service` | Imposter IRL web frontend | — | Next.js, port 3001 |

---

## Repos in `/opt/`

| Repo | Origin | Type |
|------|--------|------|
| `sololedger/` | `github.com/dilljens/sololedger` | Python API + SPA |
| `poolsplat/` | Gitea `dillon_stuff/poolsplat` | Node.js MCP + 3D viewer |
| `imposter-frontend/` | `github.com/dilljens/imposterirl` | Next.js web app |
| `imposter-backend/` | (local) | Supabase docker-compose |
| `imposter-deploy/` | (local) | Deploy scripts |
| `daglock-bot/` | (local) | Node.js, trading bot |
| `daglock-indexer/` | (local) | Rust binary, blockchain indexer |
| `daglock-trade-bot/` | (local) | Python trading script |
| `actions-runner/` | GitHub Actions | CI runner for TalkEdit |
| `actions-runner-imposter/` | GitHub Actions | CI runner for Imposter |
| `kaspad/` | (local) | Kaspa node binary |
| `remote-recording/` | (local) | TalkEdit recording server |

---

## Port Map

| Port | Service | Binding |
|------|---------|---------|
| 22 | SSH | 0.0.0.0 |
| 53 | systemd-resolved | 127.0.0.53, 127.0.0.54 |
| 80 | Caddy (HTTP → HTTPS) | 0.0.0.0 |
| 443 | Caddy (HTTPS) | 0.0.0.0 |
| 1025 | Python (unidentified SMTP?) | 127.0.0.1 |
| 3000 | PostgREST (Imposter API) | 127.0.0.1 |
| 3001 | Next.js (Imposter frontend) | 0.0.0.0 |
| 3100 | Inklomancer game server | 0.0.0.0 |
| 4000 | Supabase Realtime | 127.0.0.1 |
| 5432 | PostgreSQL (Imposter) | 127.0.0.1 |
| 8000 | ScriptureEngine API | 127.0.0.1 |
| 8443 | DagLock indexer | 127.0.0.1 |
| 8644 | TalkEdit Remote Recording | 0.0.0.0 |
| 3138 | PoolSplat viewer | (container only) |
| 8100 | SoloLedger API | (container only) |

---

## Cron

Every 5 minutes: `/opt/daglock-indexer/health-check.sh` → logs to `/var/log/daglock-health.log`

---

---

## Monitoring

### Netdata (real-time dashboard + alarms)
Runs as Docker container — `netdata` in the `ferrumeng` compose stack.
- Dashboard: `http://localhost:19999` (host network, not exposed externally)
- Built-in alarms for CPU, memory, disk, network, and per-process metrics
- Email alerts: configure `NETDATA_EMAIL_SEND` SMTP settings in `.env`
- RAM overhead: ~50 MB

### Cron health check (belt-and-suspenders)
Script: `/opt/ferrum-health.sh` — runs every 5 min, logs to `/var/log/ferrum-health.log`

| Check | Threshold | Action |
|-------|-----------|--------|
| Memory usage | > 90% | Email alert to dillon@ferrumengineeringllc.com |
| Disk usage | > 85% | Email alert |
| Swap usage | > 80% | Email alert |

### What to watch
The GitHub Actions runner (`actions.runner.dilljens-TalkEdit.talkedit-ovh.service`) is the biggest RAM consumer — peaks at 5.8 GB during builds. This is normal but can push into swap. If you see sustained high swap in Netdata, consider:
- Staggering builds (avoid concurrent runs)
- Adding a `memory` limit to the runner's systemd service
- Or upgrading the VPS to one with more RAM

## Users

| User | Shell | Purpose |
|------|-------|---------|
| `root` | /bin/bash | Admin |
| `ubuntu` | /bin/bash | Primary user |
| `daglock` | /bin/false | Service account for DagLock |
| `gh-runner` | /bin/bash | GitHub Actions runner accounts |
