# Findings: Revenue Plan

## Requirements (from Discovery)

**Goal:** Start making money from ferrumeng portfolio. TalkEdit build is broken (downloads don't work). Other projects are partially working.

**Key question answered:** Which product to focus on first?

### Decision: SoloLedger First, TalkEdit Second

**Why SoloLedger first:**
1. **Already deployed** — sololedger.ferrumeng.com is live, Docker containers running on VPS
2. **Mature codebase** — 91/91 tests passing, CLI + API + SPA all functional
3. **Clear revenue model** — $15/mo cloud SaaS with unpaid self-hosted option
4. **Known market** — solo LLC consultants, freelancers struggling with QuickBooks
5. **Minimal remaining work** — just needs API keys configured and auth flow fixed
6. **Open source funnel** — GitHub repo drives organic discovery

**Why TalkEdit is second despite bigger potential:**
1. **Build is broken** — downloads don't work, need CI/CD fix first
2. **Higher complexity** — Tauri, Rust, Python backend, GPU dependencies
3. **Build iteration is slow** — self-hosted runners, long compile times
4. **Already has good setup** — landing page, Stripe, SEO, comparison pages all done

## Architecture Research

### SoloLedger Deploy Architecture
```
VPS (Docker Compose + Caddy)
├── sololedger-api (FastAPI, port 8100)
├── poolsplat (Node.js, port 3138)
└── caddy (reverse proxy, TLS termination)
```

SoloLedger repo is at `/home/dillon/_code/sololedger`. VPS at `40.160.241.74`.

### TalkEdit Build Architecture
```
Release Pipeline: tag push → GitHub Actions
├── Linux: self-hosted OVH runner → custom AppImage script
├── Windows: GitHub-hosted windows-latest → MSI + WiX
└── macOS: GitHub-hosted macos-latest → DMG
Upload: Cloudflare R2 bucket + updater manifest
```

### TalkEdit Download Status (as of July 24, 2026)

| Platform | R2 URL | Size | Status |
|----------|--------|------|--------|
| Windows x64 MSI | `TalkEdit_latest_x64_en-US.msi` | 204 MB | ✅ File exists (Jul 23) |
| macOS aarch64 DMG | `TalkEdit_latest_aarch64.dmg` | 21 MB | ✅ File exists but SUSPICIOUSLY SMALL |
| macOS x64 DMG | `TalkEdit_latest_x64.dmg` | — | ❌ 404 Not Found |
| Linux amd64 AppImage | `TalkEdit_latest_amd64.AppImage` | 148 MB | ✅ File exists (Jun 30 — stale) |
| updater.json | — | 1.8 KB | ✅ Updated Jul 23 |

The macOS DMG at 21 MB is likely missing the bundled Python backend, ffmpeg sidecar, and whisper.cpp — should be 150MB+. This is probably the main "build is wrong" complaint.

### TalkEdit Landing Page Status
- Domain: `talk-edit.com` (Cloudflare Pages)
- Content: Polished with hero, features, pricing ($49/$99), downloads, FAQ, SEO blog
- Comparison pages: vs Descript, vs MacWhisper (live)
- Blog: 6 SEO-optimized articles
- Stripe: Products created, checkout buttons wired
- Missing: Demo video (placeholder), email capture, analytics, testimonials

## Market Research

### SoloLedger Competitive Landscape
| Competitor | Pricing | SoloLedger Advantage |
|-----------|---------|---------------------|
| QuickBooks | $30-200/mo | Free self-hosted, no lock-in, privacy |
| FreshBooks | $19-50/mo | Open source, CLI-first, S-Corp tax engine |
| Bench (managed) | $299-399/mo | DIY option, transparent ledger files |
| GnuCash | Free | Modern UI, cloud sync, API access |
| Wave | Free (fees on payments) | No transaction fees, self-hosted data |

**Target persona:** Solo consultant, SMLLC or S-Corp, technical enough for CLI, hates QuickBooks, wants plain-text data ownership.

### TalkEdit Competitive Landscape
| Competitor | Pricing | TalkEdit Advantage |
|-----------|---------|-------------------|
| Descript | $24-40/mo | One-time $49, offline, no AI credits, Linux support |
| DaVinci Resolve | Free / $295 | Text-based editing (unique), simpler pricing |
| MacWhisper | €59 one-time | Cross-platform, video editing, not just transcription |
| Adobe Podcast | $55/mo | Desktop native, offline, one-time price |
| Kapwing/VEED | $16-50/mo | Desktop performance, no upload required |

**Target persona:** Podcasters and long-form content creators unhappy with Descript's new AI credit metering. Linux users (literally no competitor).

## Pre-resolved Decisions

1. **SoloLedger pricing:** Keep $15/mo cloud, $0 self-hosted. No change.
2. **TalkEdit pricing:** Keep $49/$99 one-time. Don't change during build fix.
3. **Marketing approach:** Community-first (HN, Reddit, GitHub). No paid ads.
4. **Project-Pulse:** Use for content generation, not as a revenue product.
5. **Build priority order for TalkEdit:** Linux → macOS → Windows (fix cheapest first).
6. **No new features in TalkEdit** — build fix only. Feature work is scope creep.

## Open Questions → Resolved

- Q: Why is macOS DMG only 21MB?
  → A: Probably built without ffmpeg/whisper/backend sidecars bundled. The build script might not be copying them to the right path. Need to verify.

- Q: Does SoloLedger actually work end-to-end for a paying customer?
  → A: The CLI works (91 tests pass). The cloud SPA shows sign-in page but Google auth isn't configured and Stripe webhook needs verification. The code path exists but hasn't been tested end-to-end.

- Q: Should we buy ads for any product?
  → A: No. Research shows organic-first works better for dev tools. Paid ads amplify, they don't create.

- Q: Should we launch TalkEdit on Product Hunt first or fix builds first?
  → A: Fix builds first. Launching a broken product on PH would burn the launch opportunity.
