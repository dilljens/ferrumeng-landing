---
status: active
kind: plan
area: infrastructure
author: dillon
created: 2026-07-25
---

# Deferred Tasks — Dev Environment & Plaid

---

## Track A: Dev Environment

### Phase A1: Local Dev Workflow (1 hour)
**Problem:** Every code change goes straight to production. Can't test before deploy.

**Solution:** Run SoloLedger locally with hot-reload.

```bash
cd /home/dillon/_code/sololedger
.venv/bin/uvicorn app.api:app --reload --host 0.0.0.0 --port 8100
# → http://localhost:8100/app/
```

Changes to `app/` or `web/` files auto-reload. Test everything here before pushing.

**Also needed:** Reset script to wipe test data:
```bash
docker exec sololedger-api sh -c "rm -f /app/users.json /app/tenants.json && rm -rf /app/ledgers/*"
```

### Phase A2: Staging Subdomain (2 hours, optional)
**When:** When you have 10+ users and can't risk breaking production

**Setup:**
1. Add DNS A record: `staging.sololedger.ferrumeng.com` → VPS IP
2. Copy production docker-compose.yml, change port + container name
3. Add to Caddyfile → routes to second container
4. Use a separate `.env` with test Stripe keys

**Files to create:**
- `/opt/sololedger/deploy/docker-compose.staging.yml`
- `/opt/sololedger/deploy/.env.staging`

### Phase A3: Git Workflow (30 min)
**Simple rule:**
1. Make changes locally, test with `uvicorn --reload`
2. Commit + push
3. SSH into VPS → `git pull → docker compose up -d --build`
4. Run a quick smoke test: sign up, check tax, check import

---

## Track B: Plaid Bank Connect

### Phase B1: Get Plaid Keys (15 min)
1. Go to https://dashboard.plaid.com/signup
2. Sign up (use existing account if you have one)
3. Go to https://dashboard.plaid.com/team/keys
4. Copy `PLAID_CLIENT_ID` and `Sandbox Secret`

### Phase B2: Deploy to VPS (5 min)
```bash
ai-secret set plaid_client_id    # paste client id
ai-secret set plaid_secret       # paste sandbox_secret_...

# Then deploy:
ssh ubuntu@40.160.241.74
echo "PLAID_CLIENT_ID=..." >> /opt/sololedger/deploy/.env
echo "PLAID_SECRET=..." >> /opt/sololedger/deploy/.env
echo "PLAID_ENV=sandbox" >> /opt/sololedger/deploy/.env
cd /opt/sololedger/deploy && docker compose up -d --build sololedger-api
```

### Phase B3: Verify (5 min)
- Go to https://sololedger.ferrumeng.com/app/
- Sign in, go to Import page
- Click "Connect Your Bank"
- Sandbox environment shows a test bank (username: `user_good`, password: `pass_good`)
- Should show "Bank connected successfully" toast

### Phase B4: Production (when ready)
1. Submit Plaid app review (takes 1-3 days)
2. Get production API keys
3. Update `.env` with production keys
4. Users can connect their real bank accounts

### When to Enable Plaid
**Criteria:**
- [ ] 5+ users ask for bank sync
- [ ] At least 1 paying Professional subscriber
- [ ] Revenue covers Plaid's $0.50/user/mo cost

**Until then:** CSV/OFX file import works fine for the free tier.
