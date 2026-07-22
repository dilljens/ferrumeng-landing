# Plan: SoloLedger Restructure + Site Cleanup

Goal: Move `/accounting/` → `/sololedger/`, clean up the landing page, archive sololedger-app, prepare for VPS deploy.

## Requirements
- [x] Rename `/accounting/` → `/sololedger/` in the ferrumeng-landing repo
- [x] Update all cross-references (nav links, footer links, project links, README)
- [x] Clean up SoloLedger page — remove Dental/PoolSplat from nav (different audience), keep only main site link + GitHub + Sign In
- [x] Add email capture (waitlist/early access) to SoloLedger page since VPS isn't deployed yet
- [x] Copy deploy config from sololedger-app into main sololedger repo
- [x] Archive sololedger-app (add ARCHIVE.md, note it's deprecated)
- [x] Write the plan

## Pre-resolved Decisions
- Keep MIT license — trust is the product differentiator, OSS is marketing
- SoloLedger page lives at `/sololedger/` on ferrumeng.com (subdirectory, not subdomain for marketing)
- The app lives at `sololedger.ferrumeng.com` (VPS subdomain)
- No Dental/PoolSplat nav on SoloLedger page — different audience
- Email capture replaces dead "Get Started" CTA (VPS not deployed)

## Track A: Site Restructure `[ ]`
- Description: Move + rename accounting → sololedger, update all cross-refs
- 📏 Scope: 4 files, ~20 lines changed

### Phase A1: Rename directory `[ ]`
- 🏷 Priority: high
- [ ] `mv accounting sololedger`
- [ ] Update nav in `index.html`
- [ ] Update nav in `dental/index.html`
- [ ] Update nav in `poolsplat/index.html`
- [ ] Update project link in `index.html`
- [ ] Update `README.md`
- 📏 Scope: 5 files, ~15 lines
- ✅ Checkpoint: grep -c '/sololedger/' index.html dental/index.html poolsplat/index.html
- ⚙ Fallback: manual find-and-replace

### Phase A2: Clean up SoloLedger page `[ ]`
- [ ] Remove Dental/PoolSplat from nav (keep only Ferrum Engineering + Features + Pricing + GitHub + Sign In)
- [ ] Add email capture div (waitlist for when VPS is live)
- 📏 Scope: 1 file, ~30 lines
- ✅ Checkpoint: no "Dental" or "PoolSplat" in sololedger/index.html
- ⚙ Fallback: manual edit
- Depends on: A1

## Track B: Deploy Config Migration `[ ]`
- Description: Copy deploy files from sololedger-app into main sololedger repo, archive sololedger-app
- 📏 Scope: 2 repos, ~5 files

### Phase B1: Copy deploy to sololedger repo `[ ]`
- [ ] Copy `deploy/` from sololedger-app into sololedger repo
- [ ] Update paths in deploy files to reflect new home
- 📏 Scope: 4 files
- ✅ Checkpoint: ls /opt/sololedger/deploy/ (when deployed)
- ⚙ Fallback: manual copy
- Depends on: nothing

### Phase B2: Archive sololedger-app `[ ]`
- [ ] Add ARCHIVE.md explaining the repo is deprecated
- [ ] All deploy config now lives in main sololedger repo
- 📏 Scope: 1 file
- ✅ Checkpoint: ARCHIVE.md exists in sololedger-app
- ⚙ Fallback: manual write
- Depends on: B1
