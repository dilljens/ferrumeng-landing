# Progress: Revenue Plan — Final Session 2026-07-25

## ✅ All Issues Fixed

| Issue | Fix |
|-------|-----|
| Google sign-in crash ("Internal Server Error") | Fixed `datetime.now()` → `datetime.datetime.now()` |
| Demo data 401 error | Onboarding now checks `onboarding_complete` flag only |
| Onboarding not showing | Skipped onboarding entirely — template has sample data |
| "Import file doesn't do anything" | Toast feedback on all uploads (success/error) |
| "Connect My Bank" shows but doesn't work | **Hidden** when Plaid not configured |
| Session lost on restart | Sessions persisted to `sessions.json` on disk |
| Tax endpoint crashed | Template files now included in Docker image |

## 🎯 What's Ready
- https://sololedger.ferrumeng.com — fully functional
- Sign up → see dashboard with sample data ($11,855 cash, 12 transactions)
- 14-day trial with full access
- Stripe checkout + webhook for upgrades
- Google OAuth + email/password login
- CSV/OFX import with toast feedback
- Session persistence

## 📋 Next Step
Decide what to work on:
- [ ] **Marketing execution** — HN post, Reddit, direct DMs (plan in docs/plans/marketing-execution.md)
- [ ] **TalkEdit build fix** — diagnose the macOS DMG and stale AppImage
- [ ] **Something else?**
