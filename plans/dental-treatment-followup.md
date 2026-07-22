# Dental Treatment Plan Follow-Up System

**Product type:** Reusable SaaS (practice-specific deployment)  
**Build time:** 4-5 days  
**Price:** $5,000 one-time or $250/mo  
**Target client:** Dental practices with $50K+ in unscheduled treatment

---

## The Problem

A typical dental practice has **$50K–$200K in diagnosed but unscheduled treatment** at any time. Patients are told they need a crown ($1,500), implant ($4,500), or root canal ($1,200), but they leave without booking.

Common reasons:
- "I need to think about it"
- "Let me check my insurance"
- "I'll call next week" (they don't)
- "That's expensive — I need to save up"

Most practices **never follow up.** The patient forgets or goes elsewhere.

## What It Does

When a dentist marks a patient as "needs follow-up," the system sends a timed sequence of texts/emails designed to convert unscheduled treatment into booked appointments:

| Day | Message |
|-----|---------|
| **1** | Educational: "Here's a 2-minute video on why untreated cavities can lead to root canals" |
| **7** | Social proof: "9 out of 10 patients who needed a crown said the procedure was easier than they expected" |
| **14** | Financial: "We offer 0% financing through CareCredit. Most patients pay less than $50/month." |
| **30** | Urgency: "Dr. Smith wanted to personally check in. We have an opening this Thursday if you'd like to come in." |
| **60** | Final: "We haven't seen you since your diagnosis. Your dental health is important to us — please call to schedule." |

The dentist or front desk controls:
- Which patients get added to the sequence
- Which sequence they receive (crowns, implants, ortho, general)
- Pause/resume for individual patients
- Dashboard showing: patients in sequence, conversion rate, revenue recovered

## The Numbers

| Metric | Conservative Estimate |
|--------|---------------------|
| Unscheduled treatment per practice | $100K |
| Typical follow-up conversion rate | 20-35% |
| With automated follow-up | 35-55% |
| Additional treatment booked | $15K–$35K/year |
| System cost | $5K setup or $3K/yr |
| ROI | **3-7× in Year 1** |

## Build Plan

| Component | Effort |
|-----------|--------|
| Patient database + sequence configuration | 1 day |
| SMS/email sending engine (Twilio + SendGrid) | 1 day |
| Template sequences (crown, implant, root canal, perio, cosmetic) | 1 day |
| Dashboard (patients in sequence, conversions, revenue impact) | 1 day |
| Manual add + bulk import (paste patient list → queue them) | 1 day |

## Competition

| Alternative | Cost | Issue |
|------------|------|-------|
| **PatientActivator / Weave / RevenueWell** | $300-$800/mo | Expensive, long contracts, feature bloat, need PMS integration |
| **Manual call list** | Free (staff time) | Never gets done consistently |
| **This tool** | $5K once or $250/mo | Simple, no integration needed, focuses on ONE high-ROI use case |

## Sales Script

> *"You have $100K in treatment plans sitting in your files that patients never scheduled. I can build a system that texts them helpful reminders over 60 days. It converts 35-55% of those into booked appointments. At $100K in unscheduled treatment, that's $35K-$55K in extra revenue. The system costs $5,000. You decide if that math works."*
