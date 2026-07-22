# Plan: Register ferrumeng.com + Wyoming LLC

## Sheet Anchor
- Domain: **ferrumeng.com** ✅ registered
- LLC name: **Ferrum Engineering LLC** ✅ (available, filing submitted)
- Entity type: Wyoming Single-Member LLC (SMLLC)
- Owner: Dillon Jensen
- Location: Sheridan, WY
- Registered agent: Self (Sheridan address)
- Bank accounts: Mercury (primary) + First Interstate Bank (local backup)

---

## Phase 1: Domain + LLC Filing (Day 1) ✅ Done

### Step 1 — Register ferrumeng.com
- [x] Registered at Cloudflare/Namecheap — **ferrumeng.com** (~$10-15/yr)

### Step 2 — Check LLC name availability
- [x] Checked on wyobiz.wy.gov — "Ferrum Engineering" is available

### Step 3 — File Articles of Organization (online, WyoBiz)
- [x] Filed: Domestic LLC, Member-Managed, Perpetual
- [x] Registered Agent: Self (Sheridan address)
- [x] Organizer: Dillon Jensen
- [x] Paid $100 (+ CC fee)
- [ ] Download/save stamped Articles of Organization (PDF)

---

## Phase 2: EIN + Operating Agreement (Day 1-2)

### Step 4 — Get EIN from IRS
- [ ] Go to irs.gov/ein (online assistant)
- [ ] Legal structure: "Single Member LLC"
- [ ] Reason: "Started a new business"
- [ ] LLC name: Ferrum Engineering LLC
- [ ] Your SSN (as responsible party)
- [ ] Your Sheridan address
- [ ] Takes ~15 minutes, issued immediately
- [ ] Save the CP 575 Notice (PDF)

### Step 5 — Draft Operating Agreement
- [ ] Create a one-page Operating Agreement covering:
  - LLC name and purpose (engineering consulting)
  - Owner (Dillon — 100% membership interest)
  - Member-Managed
  - Capital contributions (initial deposit)
  - Distribution of profits (all to member)
  - Dissolution provisions
- [ ] Sign and date (keep with LLC records, not filed with state)

---

## Phase 3: Banking (Day 1-3)

### Step 6 — Open Mercury (online)
- [ ] Apply at mercury.com as "Software / Technology Consulting"
- [ ] Need: EIN, stamped Articles, Operating Agreement, ID
- [ ] Set up API access for beancount
- [ ] Request debit card + IO credit card (1.5% cashback)

### Step 7 — Open First Interstate Bank (walk-in, Sheridan)
- [ ] Visit Sheridan branch with: EIN, stamped Articles, OA, ID, $100 deposit
- [ ] Open Classic Business Checking ($10/mo, waived at $500 balance)
- [ ] Ask about Web Connect / QFX export for beancount
- [ ] Set up online banking, ask about Zelle
- [ ] Get instant-issue debit card

---

## Phase 4: Website + Email (Day 2-7)

### Step 8 — Point ferrumeng.com to the landing page
- [ ] Deploy index.html to Cloudflare Pages
- [ ] Point ferrumeng.com DNS to Cloudflare Pages
- [ ] Set up email forwarding (dillon@ferrumeng.com → personal email)
- [ ] Update Contact section with new email

---

## Phase 5: Configure SoloLedger

### Step 9 — Run `llc init`
- [ ] `llc init` with LLC details
- [ ] Business name: Ferrum Engineering LLC
- [ ] State: WY
- [ ] EIN: [your new EIN]
- [ ] Address: Sheridan, WY

### Step 10 — Connect bank accounts
- [ ] Mercury: Set up API (Plaid client ID, secret, access token)
- [ ] First Interstate: Set up QFX/OFX import path
- [ ] Create expense rules in config.toml
- [ ] Initial import: pull last 90 days of transactions

---

## Phase 6: Annual Maintenance

### Ongoing
- [ ] File annual report with WY SOS each year (anniversary month) — $60
- [ ] No state income tax filing needed (WY has none)
- [ ] File Schedule C with personal 1040 (SMLLC is a disregarded entity)
- [ ] Pay estimated quarterly federal taxes (1040-ES)

---

## Cost Summary

| Item | One-time | Annual |
|------|----------|--------|
| ferrumeng.com domain | ~$10-15 | ~$10-15 |
| WY SOS filing | $100 | — |
| WY annual report | — | $60 |
| Registered agent | $0 | $0 |
| Mercury | $0 | $0 |
| First Interstate ($500 min to waive fee) | $100 deposit | $0 |
| EIN | $0 | — |
| Cloudflare Pages | $0 | $0 |
| **Total** | **~$210** | **~$70-75** |
