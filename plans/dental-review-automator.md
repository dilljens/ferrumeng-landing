# Dental Review Automator

**Product type:** Reusable SaaS (build once, sell to every practice)  
**Build time:** 1 day  
**Price:** $1,500 setup + $50/mo hosting  
**Target client:** Any dental practice in Sheridan (or anywhere)

---

## The Problem

Dental practices live and die by Google reviews. A practice with 50 five-star reviews gets 3-5x more new patient calls than one with 10 reviews. But front desk staff forgets to ask, and even when they remember, most patients walk out without leaving one.

## What It Does

After each appointment, the system auto-sends a text or email:

> *Day 1: "Thanks for visiting Dr. Smith! If you had a great experience, we'd love a Google review: [link]"*
> *Day 3 (if no review): "Just a reminder — your feedback helps us serve you better: [link]"*

The dentist gets a simple dashboard showing:
- Reviews submitted this week
- Review requests sent / opened / converted
- Average rating trend

## How It Works

```
Patient seen → Front desk clicks "Send Review Request" in a simple web app →
System sends SMS/email with review link → 
  ✓ If patient reviews: dashboard updates, auto-thank-you sent
  ✗ If no review after 3 days: one follow-up text
  ✗ If no review after 7 days: flag for front desk to mention next visit
```

## Tech Stack

| Component | What |
|-----------|------|
| **Frontend** | Single HTML page dashboard (like Ferrum landing page — no build step) |
| **Sending** | SMS via Twilio API, email via SendGrid or Resend |
| **Storage** | SQLite (one file, zero ops) |
| **Hosting** | $5/mo VPS or Railway/Render free tier |

## Why Dentists Buy It

A single extra 5-star review can bring in one new patient worth $1,500+ in treatment. The setup cost ($1,500) pays for itself with one new patient.

| Metric | Value |
|--------|-------|
| Practices in Sheridan | ~10 |
| Revenue at $1,500 each | $15,000 |
| Monthly recurring (10 × $50) | $500/mo |

## Sales Script

> *"Your front desk is busy and asking for reviews falls through the cracks. I built a system that sends a text after every appointment automatically. It takes me one hour to set up. You'll get more reviews without your staff doing anything."*
