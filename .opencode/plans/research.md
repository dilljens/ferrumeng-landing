# Research: Ferrum Engineering LLC Formation & Banking

## Wyoming SMLLC Formation — Sheridan, WY

### Step-by-Step
1. **Check name availability** at wyobiz.wy.gov (free)
2. **File Articles of Organization online** via WyoBiz wizard
   - Yourself as registered agent using your Sheridan street address
   - Member-Managed
   - Perpetual duration
   - $100 filing fee (+ ~2.4% CC fee)
   - Processing: instant to 3 business days
   - Expedited same-day: $50 extra
3. **Get EIN from IRS** at irs.gov/ein — free, 15 min, issued immediately
4. **Create Operating Agreement** (not filed with state, keep private)
5. **Open business bank account** with EIN + stamped Articles
6. **Annual report** due first day of anniversary month — $60 minimum/year

### Costs
| Item | Cost |
|------|------|
| SOS filing (online) | $100 |
| Annual report | $60/yr |
| State income tax | $0 (Wyoming) |
| Franchise tax | $0 |
| Registered agent | $0 (self — you live in Sheridan) |
| City business license | None (Sheridan doesn't require one) |

### Key Details
- Wyoming does NOT require member/manager names in the Articles — ownership is not public record
- SMLLC is a "disregarded entity" — report on Schedule C
- BOI Report (FinCEN): SMLLCs are exempt under Corporate Transparency Act
- No city business license needed in Sheridan

---

## Domain Name

**Chosen: ferrum-eng.com**

Rationale over alternatives:
- Keeps "Ferrum" as the brand
- ".com" credibility for a consulting firm
- "eng" is universally understood and relevant
- No hyphen confusion — easy to say "ferrum dash eng dot com"
- Available

Other candidates considered (but ferrum-eng.com is the pick):
- dilloneng.com (personal brand, weaker company identity)
- anvil.engineering (memorable but .engineering TLD less known)
- forgeferrum.com (long, punny)

---

## Bank Account Research

### Primary: Mercury (mercury.com)
- **$0/mo**, $0 minimum, free domestic wires, API for beancount
- Explicitly court Web3/blockchain companies (mercury.com/web3)
- API can pull transactions programmatically for beancount
- Freeze risk is real but lower for US-based consulting LLCs (not exchange, not MSB)
- Need: EIN, Articles of Organization, Operating Agreement
- App: iOS 5.0, Android 4.7

### Local Backup: Cowboy State Bank (Sheridan)
- **$0/mo**, $0 minimum, $100 opening deposit
- Physical branch in Sheridan (walk in)
- OFX/QFX download via Intuit Direct Connect — beancount-friendly
- Need: EIN, Articles of Organization, operating agreement
- Call 307.673.4456 to confirm crypto/blockchain consulting policy and Zelle availability

### Fallback: First Interstate Bank (Sheridan)
- $10/mo (waived with $500 balance)
- Has Zelle, better mobile app
- Sheridan branch on S Sheridan Ave

### Why not others
- **Novo**: No API, virtual reserves (not real sub-accounts), worse beancount story
- **Relay**: No API, CSV-only export, 20 real sub-accounts but manual imports
- **Slash**: Crypto-native with stablecoin support, but user doesn't want to worry about it right now
- **Custodia Bank**: Perfect mission alignment but Supreme Court case pending, not operational for payments yet
- **Kraken Financial**: WY SPDI but institutional only, not for single-member LLC
- **UniWyo CU**: No Sheridan branch

### Current Best Setup
1. **Mercury** — primary operating account (API for beancount, free wires, Web3-friendly)
2. **Cowboy State Bank** — local backup (walk-in branch, $0 fee, OFX/QFX download)

---

## SoloLedger Import System

### Import Methods (all feed into transactions.beancount)

| Method | CLI | Categorization | Best for |
|--------|-----|---------------|----------|
| Plaid auto-sync | `llc bank sync` | Config rules (simple substring) | Banks supporting Plaid |
| Bank CSV | `llc expense import file.csv` | Config rules | Any bank with CSV |
| OFX/QFX | (API only) | **Full 3-tier ML categorizer** | Banks with OFX download ← BEST |
| Receipt scan | `llc receipt scan` | Config rules | Physical receipts |
| Wave/QBO | (API) | Config rules | Wave/QBO exports |

Key insight: OFX/QFX import uses the full ML categorizer (exact → regex → embedding). Plaid and CSV use simple config-toml substring rules.

### What's Needed
- Plaid: env vars `PLAID_CLIENT_ID`, `PLAID_SECRET`, `PLAID_ACCESS_TOKEN`, `PLAID_ENV`
- Plaid disabled by default in config.toml (`plaid_enabled = false`)
- `llc init` wizard doesn't ask about bank connections — manual setup

---

## Sources

- https://sos.wyo.gov/Business/StartABusiness.aspx
- https://wyobiz.wy.gov/Business/Default.aspx
- https://www.irs.gov/ein
- https://mercury.com/web3
- https://cowboystatebank.com
- https://firstinterstatebank.com
- https://www.statebusinesscompliance.com/states/wyoming
- https://llcinsights.com/how-to-form-a-single-member-llc-in-wyoming/
