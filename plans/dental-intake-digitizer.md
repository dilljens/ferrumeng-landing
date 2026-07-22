# Dental Intake Form Digitizer

**Product type:** Reusable SaaS (per-practice deployment)  
**Build time:** 3-4 days  
**Price:** $2,500 one-time  
**Target client:** Dental practices tired of paper clipboard intake

---

## The Problem

Every new patient fills out a paper clipboard form: name, address, insurance carrier, medical history, medications, reason for visit, HIPAA consent.

Then the front desk re-types all of it into the dental practice management system (Dentrix, Eaglesoft, OpenDental). For a practice with 20 new patients/month, that's **5-10 hours of re-typing per month.**

The paper also gets lost, is hard to read, and takes up filing space.

## What It Does

Two modes:

**Mode A — Text-to-Patient (before appointment):**
> Practice texts patient: "Please fill out your new patient forms here: [link]"
> Patient fills on phone in 3 minutes
> System generates a clean PDF summary
> Front desk prints and scans into PMS (or imports if API exists)

**Mode B — iPad Kiosk (in-office):**
> Patient arrives → signs in on an iPad → fills digital form
> Same result: clean PDF summary for the file

The key: **the output is a formatted PDF that matches their existing paper forms exactly.** No workflow change, just the input changes from paper to digital.

## The AI Feature

When a patient types free-text answers (e.g., "I take blood pressure meds and ibuprofen sometimes"), the AI extracts structured data:

| Question | Free-text answer | AI-extracted |
|----------|-----------------|-------------|
| Medications | "I take lisinopril and sometimes ibuprofen" | Lisinopril (daily), Ibuprofen (as needed) |
| Medical history | "Had my appendix out in 2010 and I'm allergic to penicillin" | Appendectomy (2010), Penicillin allergy |
| Reason for visit | "Tooth hurts on the right side when I chew" | Symptom: Pain on chewing, Location: Right side |

This saves the dentist time reading free-form text and ensures nothing is missed.

## Build Plan

| Component | Effort |
|-----------|--------|
| Web form builder (name, DOB, insurance, med history, etc. — standard fields) | 1 day |
| PDF generation (match practice's existing form layout) | 1 day |
| AI free-text extraction (Claude API) | 0.5 day |
| SMS/email link sending (Twilio + SendGrid) | 0.5 day |
| Dashboard (submissions, PDF download, patient history) | 1 day |

## Why It's Better Than the Alternatives

| Option | Cost | Friction |
|--------|------|----------|
| **YAPI / RevenueWell / PatientActivator** | $200–$500/mo | Must integrate with PMS, long setup, annual contracts |
| **Paper clipboards** | Free | 5-10 hrs/week re-typing, lost forms |
| **This tool** | $2,500 once | No integration needed. PDF matches their existing paper workflow |

## Sales Script

> *"Your staff re-types patient intake forms by hand. That's 5-10 hours a month of purely administrative work. I can set up a digital form in one day — patients fill it on their phone before they come in, and you get a clean PDF that matches your existing clipboard form exactly."*
