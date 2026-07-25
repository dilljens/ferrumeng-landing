# Progress: Revenue Plan — Session 2026-07-24

## ✅ Completed

### Track A: SoloLedger
- [x] **Resend integration** — Replaced SMTP welcome email with Resend API
- [x] `app/provision.py` — Swapped `smtplib` → `resend.Emails.send()` (20 fewer lines, no SMTP password needed)
- [x] `requirements.txt` + `pyproject.toml` — Added `resend>=2.34`
- [x] `deploy/docker-compose.yml` — Added `RESEND_API_KEY`, `RESEND_FROM` env vars
- [x] `deploy/.env.example` — Documented Resend config, cleaned up SMTP vars
- [x] All 91 tests still pass
- [x] Fixed missing `GOOGLE_CLIENT_ID` and `SL_HOST_DOMAIN` env vars in docker-compose

### Track B: TalkEdit Build
- [x] **Build diagnosis complete** — 3 issues identified per platform
  - macOS DMG: 21MB (should be 150MB+) — sidecars missing
  - Linux AppImage: 148MB but stale (June 30, pre-v0.2.60)
  - Windows MSI: 204MB, looks correct

### Track C: Project-Pulse
- [x] Already configured with 3 projects. Needs LLM API key.

### VPS Access
- [x] SSH key works (`ubuntu@40.160.241.74`)
- [x] Docker containers all running (sololedger-api, poolsplat, caddy, netdata)
- [x] VPS `/opt/sololedger` is ahead of local — needs `git pull`

## ⛔ Remaining Blockers

| What | Why Blocked | Who |
|------|------------|-----|
| Stripe key | Need you to create or share existing key | **You** |
| Google OAuth client ID | Need Google Cloud Console | **You** |
| Resend API key | Need to create at resend.com/api-keys | **You** |
| Deploy to VPS | Can do once you share the 3 keys above | **Me** |
| TalkEdit build fix | Need to investigate CI — macOS sidecars not bundling | **Me** (can do parallel) |

## 📝 Files Changed This Session
- `sololedger/app/provision.py` — SMTP → Resend for welcome emails
- `sololedger/requirements.txt` — Added resend
- `sololedger/pyproject.toml` — Added resend
- `sololedger/deploy/.env.example` — Resend config + cleaner docs
- `sololedger/deploy/docker-compose.yml` — RESEND_API_KEY, GOOGLE_CLIENT_ID, SL_HOST_DOMAIN, removed unused SMTP vars
