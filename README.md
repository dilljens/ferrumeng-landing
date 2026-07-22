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
Push to GitHub — zero build config. Static HTML only.

### SoloLedger (VPS)
See `deploy/DEPLOY.md` in the [sololedger](https://github.com/dilljens/sololedger) repo.
