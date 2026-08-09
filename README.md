# Ferrum Engineering LLC

Wyoming-based consulting — enterprise AI systems, local business automation, bookkeeping.

## Site Structure

```
ferrumeng.com/              Cloudflare Pages (static)
├── index.html              Main landing page
├── dental/
│   └── index.html          Dental practice automation ($350/mo bundle)
├── sololedger/
│   └── index.html          SoloLedger — accounting for solo consulting LLCs
└── poolsplat/
    └── index.html          PoolSplat — 3D pool design from a phone video

sololedger.ferrumeng.com    VPS (Docker Compose)
                            FastAPI backend + SPA frontend
                            Serves SoloLedger web app + API
poolsplat.ferrumeng.com     VPS (Docker Compose)
                            Node.js server + 3D viewer
                            Serves PoolSplat 3D scenes + AI editing
```

## Service Lines

| Track | Location | Price | Market |
|-------|----------|-------|--------|
| Enterprise AI | Main site | $18K-$100K | Mid-size companies |
| Dental Automation | `/dental/` | $350/mo | Sheridan dental practices |
| SoloLedger | `/sololedger/` + `sololedger.ferrumeng.com` | $15/mo (cloud) / $0 (self-host) | Solo consultants, freelancers |
| PoolSplat | `/poolsplat/` | Early access | Homeowners, pool contractors |

## SoloLedger Strategy

SoloLedger is **MIT-licensed open-source** accounting software (CLI + API + SPA).
- Self-host: `pip install sololedger` and run locally (free)
- Cloud: hosted at `sololedger.ferrumeng.com` with bank feeds, receipt OCR, inline payments
- The open-source repo is the funnel — users find it on GitHub, some pay for the hosted version
- Deploy config for the VPS lives in `deploy/` of the main sololedger repo

## Deploy

### Main site (Cloudflare Pages)
Deploy manually from a local clone (the Pages project has no GitHub
integration wired up — pushes to GitHub do NOT auto-deploy):

```bash
ai-secret exec cloudflare_api -- sh -c \
  'export CLOUDFLARE_API_TOKEN="$CLOUDFLARE_API_KEY" CLOUDFLARE_ACCOUNT_ID="d9b6c3059be77c9f44b5ec7365fa50b8"; \
   wrangler pages deploy . --project-name ferrumeng-landing --branch main'
```

Static HTML only — zero build config.

### SoloLedger (VPS)
See `deploy/DEPLOY.md` in the [sololedger](https://github.com/dilljens/sololedger) repo.
