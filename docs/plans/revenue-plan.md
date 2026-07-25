---
status: active
kind: plan
area: monetization
author: dillon
created: 2026-07-24
---

# Revenue Plan — Ferrum Engineering Portfolio Monetization

**Goal:** Ship revenue from SoloLedger and TalkEdit within 30 days, using Project-Pulse for marketing automation.

---

## Portfolio Readiness Matrix

| Product | Stage | Revenue Model | Monthly Potential | Effort to Ship | Priority |
|---------|-------|---------------|------------------|----------------|----------|
| **SoloLedger** | Mature, deployed | $15/mo cloud (SaaS) | $150-1,500 | 1-2 weeks | **🥇 #1** |
| **TalkEdit** | Commercial setup done | $49/$99 one-time | $200-2,000 | 2-4 weeks | **🥈 #2** |
| **Project-Pulse** | Functional | Marketing tool (enables others) | Indirect | 1 week | **🥉 #3** |
| **PoolSplat** | Early, blocked | TBD (early access) | $0 | 4-8 weeks | Deferred |
| **DagLock** | Pre-mainnet | TBD | $0 | Post-mainnet | Deferred |
| **Consulting** | Live | $18K-100K/project | Ongoing | Ongoing | Ongoing |

---

## Track A: SoloLedger — Go-to-Market `[ ]`
- **Description:** Turn the already-deployed, working app into a revenue-generating SaaS. Configure API keys, fix the sign-in flow, and launch marketing.
- 📏 Scope: ~8 files, ~200-400 lines changed
- **Tar get:** First paying customer within 2 weeks. $150 MRR within 30 days.

### Phase A1: Configure API Keys & Payment Flow `[ ]`
- 🏷 Priority: high
- 🔁 Max turns: 10
- [ ] Set `GOOGLE_CLIENT_ID` for Google OAuth sign-in
- [ ] Set `STRIPE_SECRET_KEY` for payment processing
- [ ] Set `PLAID_CLIENT_ID` + `PLAID_SECRET` for bank feeds (tier-2 feature)
- [ ] Set SMTP credentials for email notifications
- [ ] Test complete sign-in → payment flow on sololedger.ferrumeng.com
- [ ] Verify Stripe webhook processes subscription payments
- 📏 Scope: ~1 file (.env/config), ~50-80 lines
- ✅ Checkpoint: `curl -s https://sololedger.ferrumeng.com/health` returns 200 AND Google sign-in renders
- ⚙ Fallback: If Google OAuth isn't ready, enable email+password sign-in only as fallback
- Depends on: nothing

### Phase A2: Fix the Web SPA (Auth & Dashboard) `[ ]`
- 🏷 Priority: high
- 🔁 Max turns: 15
- [ ] Verify the sign-up flow works end-to-end
- [ ] Fix the Google sign-in button (currently shows "Google sign-in (configure GOOGLE_CLIENT_ID)" text)
- [ ] Ensure the web dashboard loads correctly after auth
- [ ] Test with a real Stripe Checkout → subscription activation
- [ ] Add Stripe webhook handler for subscription lifecycle
- 📏 Scope: ~3-5 files in `web/` and `app/api/`, ~150-250 lines
- ✅ Checkpoint: New user can sign up, see dashboard, and has active subscription
- ⚙ Fallback: If SPA auth is blocked, promote the CLI as primary UX and gate cloud features
- Depends on: A1 (API keys needed)

### Phase A3: Landing Page & First Marketing Push `[ ]`
- 🏷 Priority: high
- 🔁 Max turns: 10
- [ ] Add email waitlist capture to sololedger.ferrumeng.com landing
- [ ] Post "Show HN: SoloLedger — open-source accounting for consulting LLCs" to Hacker News
- [ ] Post to r/selfhosted, r/freelance, r/smallbusiness
- [ ] Create a 2-minute demo GIF showing CLI → web dashboard flow
- [ ] Add GitHub sponsor link to repo
- 📏 Scope: ~2-3 files, ~50-100 lines
- ✅ Checkpoint: At least 1 sign-up from non-self traffic
- ⚙ Fallback: If organic launch is quiet, do 10 direct DMs to solo consultants with the link
- Depends on: A2 (app must work before marketing)

---

## Track B: Fix TalkEdit Build `[ ]`
- **Description:** The landing page and payment setup look great, but the builds don't work when downloaded. Fix the CI/CD pipeline so downloads actually run, then push marketing.
- 📏 Scope: ~5-10 files, ~100-300 lines changed (CI/packaging only)
- **Target:** Fix builds within 2 weeks.

### Phase B1: Diagnose Build Failures `[ ]`
- 🏷 Priority: critical
- 🔁 Max turns: 5
- [ ] Build the AppImage locally (`bash scripts/build-appimage-locally.sh`) and test it
- [ ] Download the existing R2 AppImage and try running it — document the failure
- [ ] Check what's missing in the 21MB macOS DMG (should be 150MB+ with backend/ffmpeg)
- [ ] Identify top 3-5 bugs that prevent the app from working post-download
- [ ] List each specific fix needed
- 📏 Scope: 0 files changed (diagnosis only)
- ✅ Checkpoint: Document with specific error messages for each platform build
- ⚙ Fallback: If local build fails due to system deps, set up Docker-based build
- Depends on: nothing

### Phase B2: Fix Build Pipeline `[ ]`
- 🏷 Priority: critical
- 🔁 Max turns: 15
- [ ] Fix the AppImage build (corrupt squashfs, missing deps, runtime errors)
- [ ] Fix the MSI build (missing DLLs, Python backend bundling)
- [ ] Fix the DMG build (macOS aarch64 is only 21MB — missing ffmpeg/whisper/backend)
- [ ] Run `dry-run-release.yml` workflow to verify CI builds
- [ ] Smoke-test each platform build artifact
- 📏 Scope: ~3-8 files (build scripts, CI YAML, packaging config), ~100-300 lines
- ✅ Checkpoint: AppImage runs on clean Ubuntu 24.04 VM, MSI installs on Windows, DMG launches on macOS
- ⚙ Fallback: Fix one platform at a time — Linux first (cheapest to iterate), then macOS, then Windows
- Depends on: B1

### Phase B3: Rebuild & Relaunch `[ ]`
- 🏷 Priority: high
- 🔁 Max turns: 10
- [ ] Trigger a full release (`v0.2.61`) with all fixes
- [ ] Verify R2 artifacts are updated and downloadable
- [ ] Update the landing page download buttons if needed
- [ ] Re-enable any payment/checkout flows that were gated on broken builds
- [ ] Remove "demo video coming soon" placeholder — record and embed a 60s demo
- 📏 Scope: ~2-5 files, ~50-150 lines
- ✅ Checkpoint: `curl -I https://pub-1318c18d2a524a0a9cda209ceb60cdee.r2.dev/TalkEdit_latest_amd64.AppImage` returns 200 AND AppImage runs
- ⚙ Fallback: Ship a working Linux build first (biggest audience), macOS/Windows as follow-up
- Depends on: B2

---

## Track C: Project-Pulse — Marketing Automation `[ ]`
- **Description:** Set up Project-Pulse to automate marketing content generation. This powers distribution for BOTH SoloLedger and TalkEdit.
- 📏 Scope: ~3 files, ~50-100 lines changed
- **Target:** Running within 1 week.

### Phase C1: Configure Project-Pulse for Portfolio `[ ]`
- 🏷 Priority: medium
- 🔁 Max turns: 5
- [ ] Install and configure `~/.project-pulse/config.yaml` with all portfolio projects
- [ ] Set up LLM API key for content generation
- [ ] Configure channels: HN, Reddit, GitHub
- [ ] Run `pulse check --force` to generate initial content
- 💡 **Project-Pulse already has the marketing playbook built in** — use its social templates
- 📏 Scope: ~1-2 files (config + templates), ~30-60 lines
- ✅ Checkpoint: `pulse status --json` returns valid data for all projects
- ⚙ Fallback: If Project-Pulse has bugs, use its research docs as a manual playbook instead
- Depends on: nothing

### Phase C2: Generate & Approve Launch Content `[ ]`
- 🏷 Priority: medium
- 🔁 Max turns: 5
- [ ] Run `pulse web` and approve generated content
- [ ] Customize generated posts for authenticity (70% insight, 30% product)
- [ ] Schedule SoloLedger HN launch, Reddit posts, GitHub update
- [ ] Schedule TalkEdit fixes announcement
- 📏 Scope: 0 files changed (content review only)
- ✅ Checkpoint: Approved content queued for SoloLedger and TalkEdit
- ⚙ Fallback: Write posts manually using the marketing playbook templates
- Depends on: C1, A3 (align SoloLedger content with A3), B3 (TalkEdit content after build fix)

---

## Track D: PoolSplat — Unblock & Validate `[ ]`
- **Description:** PoolSplat has potential but is blocked (fal.ai balance exhausted) and too early for revenue. Quick unblock to validate market demand.
- 📏 Scope: ~2 files, ~20-40 lines changed
- **Target:** Working demo within 1 week.

### Phase D1: Top Up fal.ai & Test `[ ]`
- 🏷 Priority: low
- 🔁 Max turns: 3
- [ ] Top up fal.ai balance ($10-50 should be enough for testing)
- [ ] Verify the photo editing pipeline works end-to-end
- [ ] Test with a real user scenario (pool design from phone video)
- 📏 Scope: 0 code changes (just funding + testing)
- ✅ Checkpoint: Agnes API and at least one paid model (FLUX/Seedream) returns a result
- ⚙ Fallback: If fal.ai can't be topped up, the free Agnes API pipeline works for basic demo
- Depends on: nothing

### Phase D2: Build Waitlist Landing `[ ]`
- 🏷 Priority: low
- 🔁 Max turns: 5
- [ ] Update the poolsplat.ferrumeng.com viewer landing with a waitlist signup
- [ ] Add email capture to /poolsplat/ page on ferrumeng.com
- [ ] Post to r/pools, r/swimmingpools, r/homeimprovement to validate demand
- 📏 Scope: ~2 files, ~30-60 lines
- ✅ Checkpoint: Waitlist has 5+ emails from organic traffic
- ⚙ Fallback: Validate demand by DMing 10 pool contractors with a demo link
- Depends on: D1

---

## Summary: Where Money Comes From

| Stream | 30-Day Target | 90-Day Target | Effort |
|--------|--------------|---------------|--------|
| **SoloLedger Cloud** | $0 → $150 MRR | $500-1,500 MRR | 1-2 weeks setup |
| **TalkEdit Sales** | $0 → $500 | $2,000-5,000 | 2-4 weeks fix + launch |
| **Consulting** | Ongoing | $18K-100K/project | Existing pipeline |
| **PoolSplat** | $0 (validation) | TBD | Deferred |

**Total 30-day target:** ~$650+ from product revenue ($150 SoloLedger + $500 TalkEdit)
**Total 90-day target:** ~$2,500-6,500/mo + consulting

---

## Anti-Scope (What We're NOT Doing)

- ❌ Not building a mobile app for any product
- ❌ Not adding new features to TalkEdit — just fixing builds
- ❌ Not launching on Product Hunt yet (that's a phase 2 after builds work)
- ❌ Not monetizing ScriptureEngine, CoKicad, or Tau Viewer
- ❌ Not running paid ads (organic first)
- ❌ Not incorporating or worrying about legal structure (already done)
