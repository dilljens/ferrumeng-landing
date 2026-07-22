# Dental Insurance Claim Assistant

**Product type:** Reusable SaaS (customizable per practice's note format)  
**Build time:** 2-3 days  
**Price:** $3,000 one-time or $150/mo  
**Target client:** Dental practices processing 50+ claims/week

---

## The Problem

The single biggest time drain in a dental office is insurance claims. The workflow:

```
Dentist sees patient → Dictates/scribbles clinical notes → 
Front desk reads the note → Manually enters CDT codes, tooth numbers,
procedure descriptions, diagnosis codes into insurance portal →
Submits claim (15 minutes per claim)
```

For a practice seeing 15 patients/day with insurance, that's **3+ hours of claim processing daily.** At $18/hr for a front desk staffer, that's $270/week in labor — plus the delays mean slower reimbursement.

## What It Does

A simple web tool: **paste the clinical note → get a pre-filled claim summary.**

Front desk workflow becomes:

```
Dentist sees patient → Writes note as usual → Front desk pastes note
into the tool → AI extracts CDT codes, tooth numbers, diagnosis → 
Staff reviews (30 seconds) → Copies formatted claim into insurance portal
```

Total time per claim: **3 minutes instead of 15.**

## The AI Piece

A clinical note might say:

> *"Tooth #14 — MOD amalgam. Caries removed, cavity prep completed, 
> amalgam placed and carved. Occlusion checked. Pt tolerated well."*

The AI extracts:

| Field | Value |
|-------|-------|
| CDT Code | D2160 (amalgam — three surfaces, permanent) |
| Tooth # | 14 |
| Arch | Maxillary |
| Material | Amalgam |
| Surfaces | Mesial, Occlusal, Distal |
| Diagnosis | Dental caries |

CDT codes are standardized (ADA maintains ~750 codes). The AI maps the clinical description to the correct code. Staff reviews and corrects if needed — this is the key: **the AI assists, it doesn't replace the human.**

## Build Plan

```
Day 1: Build CDT code database (750 codes with descriptions and rules)
       → This is just a structured JSON file. The ADA publishes 
         the CDT codebook — the codes are standard, no licensing needed.
       
Day 2: Build Claude API integration for note parsing
       → Prompt engineering: "Extract CDT code, tooth number, surfaces,
         diagnosis from this dental note. Return JSON."
       → Test on 20 sample notes from public dental resources
       
Day 3: Build web UI
       → Text area: paste note
       → Result: editable claim summary
       → Buttons: Copy to clipboard, Clear, History
       → Bonus: practice-specific presets (common codes they use)
```

## Why It's Defensible

| Concern | Answer |
|---------|--------|
| **What if the AI gets the code wrong?** | Staff reviews every extraction. The tool is an assist, not automation. |
| **Can't they just buy Dentrix's AI add-on?** | They can, but it's $500/mo and requires switching workflows. This is $3K once or $150/mo and works with anything. |
| **Does it integrate with their PMS?** | No. Copy-paste is the integration. It's dumb but it works and takes zero IT. |

## Sales Script

> *"Your front desk spends 15 minutes per insurance claim. I can get that down to 3 minutes. You paste the dentist's note, the system pre-fills the claim, and your staff just reviews and submits. $3,000 one-time. It'll pay for itself in 3 months."*
