# Plan: Register ferrum-eng.com + Wyoming LLC

## Sheet Anchor
- Domain: **ferrum-eng.com**
- LLC name: **Ferrum Engineering LLC** (check availability at wyobiz.wy.gov)
- Entity type: Wyoming Single-Member LLC (SMLLC)
- Owner: Dillon
- Location: Sheridan, WY
- Registered agent: Self (Dillon's Sheridan street address)
- Bank accounts: Mercury (primary) + Cowboy State Bank (local backup)

---

## Phase 1: Domain + LLC Filing (Day 1)

### Step 1 — Register ferrum-eng.com
- [ ] Register at Cloudflare Registrar (or Namecheap, whichever you use)
- [ ] Owner: Ferrum Engineering LLC (use owner name if LLC not yet formed)
- [ ] Nameservers: Cloudflare (if using Cloudflare for DNS/SSL)
- [ ] Annual cost: ~$10-15/yr

### Step 2 — Check LLC name availability
- [ ] Go to wyobiz.wy.gov
- [ ] Use the Entity Name Search
- [ ] Verify "Ferrum Engineering" is distinguishable from existing names
- [ ] If taken, decide on alternative (Ferrum Eng LLC, Ferrum Engineering Solutions LLC, etc.)

### Step 3 — File Articles of Organization (online, WyoBiz)
- [ ] Go to wyobiz.wy.gov → New Business Entity Wizard
- [ ] Entity type: Domestic Limited Liability Company
- [ ] LLC Name: Ferrum Engineering LLC (or checked variant)
- [ ] Registered Agent: Dillon [Your Full Name]
- [ ] Reg Agent Street Address: [Your Sheridan street address] (NOT a PO box)
- [ ] Reg Agent Mailing Address: [Your Sheridan address or PO box]
- [ ] Principal Office Address: [Your Sheridan address]
- [ ] Mailing Address: [Your Sheridan address]
- [ ] Management: Member-Managed
- [ ] Organizer Name: Dillon [Your Full Name]
- [ ] Organizer Address: [Your Sheridan address]
- [ ] Effective Date: Immediate (date of filing)
- [ ] Duration: Perpetual
- [ ] Pay $100 (+ CC convenience fee ~$2.40)
- [ ] Download/save stamped Articles of Organization (PDF)

### What you get back
- Stamped Articles of Organization (proof of LLC existence)
- SOS File Number (you'll need this for bank accounts)
- Usually available for download same-day or within 3 business days

---

## Phase 2: EIN + Operating Agreement (Day 1-2)

### Step 4 — Get EIN from IRS
- [ ] Go to irs.gov/ein (online assistant)
- [ ] Legal structure: "Single Member LLC" (or "LLC" → "Single Member")
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

### Step 6 — Open Cowboy State Bank account (local, same-day)
- [ ] Call first: 307.673.4456
  - Confirm they accept blockchain/software consulting LLCs
  - Confirm what documents they need
  - Ask about Zelle availability for business accounts
- [ ] Visit Sheridan branch with:
  - Stamped Articles of Organization
  - EIN confirmation (CP 575)
  - Operating Agreement
  - Photo ID
  - $100 opening deposit
- [ ] Open Small Business Checking ($0/mo, $0 minimum)
- [ ] Set up online banking
- [ ] Download/confirm OFX/QFX export works (for beancount)
- [ ] Get debit card
- [ ] Ask about Zelle setup

### Step 7 — Open Mercury account (online)
- [ ] Go to mercury.com
- [ ] Apply for business checking
- [ ] Need: EIN, Articles of Organization, Operating Agreement, ID
- [ ] Company type: Software / Technology Consulting (not "Crypto Business")
- [ ] Describe: "Engineering consulting firm specializing in embedded systems, AI product development, and blockchain protocol development"
- [ ] Link your Cowboy State Bank account for initial funding
- [ ] Set up API access (for beancount automation)
- [ ] Request debit card

---

## Phase 4: Website + Email (Day 2-7)

### Step 8 — Point ferrum-eng.com to the landing page
- [ ] Update DNS for ferrum-eng.com to point to Cloudflare Pages (where current index.html lives)
- [ ] Verify SSL works
- [ ] Set up email forwarding (e.g., dillon@ferrum-eng.com → your personal email)
  - Cloudflare Email Routing (free) or
  - iCloud+ Custom Email Domain or
  - Fastmail / MX Route

### Step 9 — Deploy the prettified landing page to ferrum-eng.com
- [ ] Update CNAME record for the new domain
- [ ] Or deploy a fresh copy to ferrum-eng.com
- [ ] Add email address to the Contact section

---

## Phase 5: Configure SoloLedger (Day 2-7)

### Step 10 — Run `llc init`
- [ ] `llc init` with your new LLC details
- [ ] Business name: Ferrum Engineering LLC
- [ ] State: WY
- [ ] EIN: [your new EIN]
- [ ] Address: [your Sheridan address]

### Step 11 — Connect bank accounts
- [ ] Set up Plaid (if Mercury supports Plaid for the sync tool)
  - Set `PLAID_CLIENT_ID`, `PLAID_SECRET`, `PLAID_ACCESS_TOKEN`, `PLAID_ENV`
  - Set `plaid_enabled = true` in config.toml
- [ ] Or set up manual CSV/OFX import from Cowboy State Bank
- [ ] Create expense rules in config.toml for common categories
- [ ] Initial import: pull last 90 days of transactions

---

## Phase 6: Annual Maintenance

### Ongoing
- [ ] File annual report with WY SOS each year (anniversary month) — $60
- [ ] No state income tax filing needed (WY has none)
- [ ] File Schedule C with personal 1040 (SMLLC is a disregarded entity)
- [ ] Keep Cowboy State Bank account active with occasional use (to avoid dormancy)
- [ ] Monitor Mercury account for any verification requests (respond within deadline)
- [ ] Pay estimated quarterly federal taxes (1040-ES)

---

## Cost Summary

| Item | One-time | Annual |
|------|----------|--------|
| ferrum-eng.com domain | $10-15 | $10-15 |
| WY SOS filing | $100 | — |
| WY annual report | — | $60 |
| Registered agent | $0 | $0 |
| Mercury bank | $0 | $0 |
| Cowboy State Bank | $100 deposit (refundable) | $0 |
| EIN | $0 | — |
| Cloudflare Pages | $0 | $0 |
| **Total** | **~$210** | **~$70-75** |
