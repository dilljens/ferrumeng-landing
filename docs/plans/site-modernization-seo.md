---
status: active
kind: plan
area: web
author: AI
created: 2026-07-25
---

# Site Modernization & SEO — Ferrum Engineering Landing

**Goal:** Modernize ferrumeng.com with updated content (Agentic AI OS, local dental strategy), fix SEO gaps, improve accessibility, and establish local search presence.

## Pre-resolved Decisions
- **No framework migration** — stay static HTML/CSS/JS, inline styles (current approach works well for a landing page)
- **No CMS** — keep it simple, one-person-editable
- **Google Fonts** — stay with Inter + JetBrains Mono, but add `font-display: swap`
- **Analytics** — Umami (self-hosted on VPS, free, unlimited sites)
- **Contact form** — Resend API (resend_key exists)
- **Client logos** — remove placeholder text badges from hero section

---

## Track A: Content & Messaging `[ ]`
*Update copy to reflect current business strategy — Agentic AI OS, two-track consulting model, local dental automation*

### Phase A1: Update Hero & Services Section `[ ]`
- [ ] Revise hero subtitle to emphasize AI + enterprise systems more prominently
- [ ] Update **AI Product Development** service card to explicitly mention **Agentic AI Systems** — unified chat interface, specialized AI agents, enterprise knowledge platforms
- [ ] Mention "Replace $300K+/yr in vendor tools with one unified system" as a capability
- [ ] Keep client logo area but consider replacing text logos with actual client brand marks (or remove placeholder names)
- **📏 Scope:** `index.html` — ~15 lines changed
- **✅ Checkpoint:** Hero mentions agentic/enterprise AI, services card includes unified platform language
- **⚙ Fallback:** Keep original text if wording doesn't land well

### Phase A2: Add Enterprise AI Project Card `[ ]`
- [ ] Add new project row in **Projects** section:
  > **Enterprise Agentic AI Platform** — "One AI interface that connects knowledge, compliance, support, and analytics. Replaces a $400K+ vendor stack."
  > Tag: `ai`
- [ ] No client name — keep it generic since Unicity isn't public
- **📏 Scope:** `index.html` — ~8 lines
- **✅ Checkpoint:** New project card visible in "Selected Work" section
- **⚙ Fallback:** Leave Unicity project off if you prefer not to hint at it

### Phase A3: Add Case Study / Results Section `[ ]`
- [ ] Add a **Results** section between Projects and Contact showing quantified outcomes:
  - "10+ years shipping production systems"
  - "4 engineering disciplines"
  - "Clients across firmware, AI, blockchain, EDA"
  - Maybe: "Replaced $400K/yr in vendor costs"
- [ ] Keep it factual, not hype
- **📏 Scope:** `index.html` — ~40 lines new section
- **✅ Checkpoint:** New section visible and responsive on mobile
- **⚙ Fallback:** Skip if it clutters the page; this can be a separate page later

### Phase A4: Contact Section Upgrade `[ ]`
- [ ] Add a simple contact form alongside the email link:
  - Name, email, message fields
  - Submit → POST to Resend API (resend_key already exists) or Formspree
  - `autocomplete` attributes for accessibility
- [ ] Add `aria-label` and proper labels on form fields
- [ ] Add submission feedback via `aria-live="polite"`
- **📏 Scope:** `index.html` — ~30 lines new form HTML + ~20 lines JS
- **✅ Checkpoint:** Form submits and sends email to dillon@ferrumeng.com
- **⚙ Fallback:** Stay with mailto-only if form handling is too complex

---

## Track B: SEO & Technical Foundation `[ ]`
*Fix all on-page SEO elements — schema, meta tags, performance, sitemap*

### Phase B1: Upgrade Structured Data (JSON-LD) `[ ]`
- [ ] Change `@type` from `Organization` to `["LocalBusiness", "ProfessionalService"]`
- [ ] Add: `telephone`, `priceRange`, `geo`, `openingHoursSpecification`, `areaServed` (Wyoming), `foundingDate` (2026), `numberOfEmployees`
- [ ] Add `hasOfferCatalog` listing the 4 service categories from the services section
- [ ] Add separate `WebSite` schema with `potentialAction` for SearchAction (site search)
- [ ] Add `Person` schema for Dillon Jensen (founder) with `affiliation` back to Organization
- **📏 Scope:** `index.html` — rewrite JSON-LD block (~60 lines)
- **✅ Checkpoint:** Google Rich Results Test passes for LocalBusiness + Organization
- **⚙ Fallback:** Keep current Organization schema as fallback

### Phase B2: Upgrade Subpage Schemas `[ ]`
- [ ] **dental/index.html** — Add `LocalBusiness` schema for service-area business (Sheridan, WY area)
- [ ] **sololedger/index.html** — Already has `SoftwareApplication`, verify it's complete
- [ ] **poolsplat/index.html** — Already has `SoftwareApplication`, verify it's complete
- **📏 Scope:** 3 files, ~30 lines each
- **✅ Checkpoint:** Each page has valid schema per Google Rich Results Test
- **⚙ Fallback:** Fix any validation errors found

### Phase B3: Improve Meta Tags & HTML Head `[ ]`
- [ ] Add `theme-color` meta tag: `<meta name="theme-color" content="#0c0c0e">`
- [ ] Add `author` meta tag
- [ ] Add `apple-touch-icon` link (180×180 PNG)
- [ ] Add `font-display: swap` to Google Fonts `@import`/link
- [ ] Ensure `<title>` on every page includes location (Sheridan, WY / Wyoming) for local SEO
  - Main page: append " | Sheridan, Wyoming" to title
  - Dental page: append " | Sheridan, WY" to title
- [ ] Update meta descriptions to be more compelling (include CTA, local keywords)
- **📏 Scope:** `index.html`, `dental/index.html`, `poolsplat/index.html`, `sololedger/index.html` — ~5 lines each
- **✅ Checkpoint:** All 4 pages have updated `<head>` with theme-color, apple-touch-icon, font-display: swap
- **⚙ Fallback:** N/A

### Phase B4: Sitemap & Robots.txt Refresh `[ ]`
- [ ] Update `sitemap.xml` to add `<lastmod>`, `<changefreq>`, `<image:image>` for logo
- [ ] Remove `Disallow: /accounting/` from `robots.txt` (no evidence this directory exists)
- [ ] Verify all 4 URLs in sitemap resolve correctly
- **📏 Scope:** `sitemap.xml`, `robots.txt`
- **✅ Checkpoint:** Sitemap validates at sitemaps.org
- **⚙ Fallback:** N/A

### Phase B5: Performance Optimization `[ ]`
- [ ] Add `loading="lazy"` to below-fold images (hero background logo, any other images)
- [ ] Minify HTML (remove excess whitespace/comments) or move to build step
- [ ] Verify HTTP headers at CDN level (Cloudflare Pages):
  - `Strict-Transport-Security`
  - `X-Content-Type-Options: nosniff`
  - Cache headers for static assets (already in `_headers`)
- [ ] Test with Google PageSpeed Insights
- **📏 Scope:** `index.html` + `_headers` review
- **✅ Checkpoint:** PageSpeed score ≥ 95 on mobile + desktop
- **⚙ Fallback:** Accept 85+ if lazy loading challenges arise

### Phase B6: Analytics Setup `[ ]`
- [ ] Choose: Plausible (self-host or cloud) vs Fathom vs GoatCounter
- [ ] Add tracking snippet (async, deferred)
- [ ] Verify events fire correctly
- **📏 Scope:** `index.html` — ~3 lines snippet
- **✅ Checkpoint:** Dashboard shows a visit after page load
- **⚙ Fallback:** Skip analytics entirely if privacy/performance concern

---

## Track C: Design, UX & Accessibility `[ ]`
*Modernize visual design, meet WCAG 2.1 AA, add PWA basics*

### Phase C1: Accessibility Pass (WCAG 2.1 AA) `[ ]`
- [ ] **Skip-to-content link**: `<a href="#main-content" class="skip-link">Skip to content</a>` as first element in `<body>`
- [ ] **Focus indicators**: Ensure `:focus-visible` styles are visible on all interactive elements (currently no visible focus ring)
- [ ] **Color contrast check**: Test all foreground/background pairs — especially the amber `#b45309` on dark `#111113` and `#0c0c0e`
- [ ] **Link text**: Ensure mailto link and all project links have descriptive visible text
- [ ] **Heading hierarchy**: Verify `h1` → `h2` → `h3` order with no gaps (hero h1, section h2s, card h3s — looks correct)
- [ ] **Alt text**: Add `alt=""` on decorative SVGs/icons; ensure nav logo alt is descriptive
- [ ] **Touch targets on mobile**: Ensure all interactive elements are ≥ 44×44px
- [ ] **Form validation** (when form is added in A4): proper error announcement
- **📏 Scope:** `index.html` — ~20 lines + focus style fixes
- **✅ Checkpoint:** Lighthouse Accessibility score ≥ 95
- **⚙ Fallback:** Achieve ≥ 90 as minimum pass

### Phase C2: PWA / Installability Basics `[ ]`
- [ ] Create `manifest.json`:
  ```json
  {
    "name": "Ferrum Engineering",
    "short_name": "FerrumEng",
    "icons": [{"src": "/ferrum-logo.png", "sizes": "512x512", "type": "image/png"}],
    "start_url": "/",
    "display": "standalone",
    "theme_color": "#0c0c0e",
    "background_color": "#0c0c0e"
  }
  ```
- [ ] Add `<link rel="manifest" href="/manifest.json">` to all pages
- [ ] (Optional) Add basic service worker for offline support
- **📏 Scope:** `manifest.json` (new file), all 4 HTML files (1 line each)
- **✅ Checkpoint:** Lighthouse PWA badge appears
- **⚙ Fallback:** Skip SW if too complex; just manifest is fine

### Phase C3: Visual Polish `[ ]`
- [ ] Replace text-based client logos ("Mechtro", "AMZ-G2", etc.) with actual client marks or remove the section if placeholder
- [ ] Add subtle testimonial card if you have any client quotes
- [ ] Improve mobile nav — current hamburger overlay is functional but could be smoother
- [ ] Add a subtle section divider between sections (gradient line or icon)
- **📏 Scope:** `index.html` — ~30 lines
- **✅ Checkpoint:** Visual consistency check on mobile + desktop passes
- **⚙ Fallback:** Keep current look

### Phase C4: 404 Page Modernization `[ ]`
- [ ] Add schema.org markup to 404 page
- [ ] Add theme-color meta tag for consistency
- [ ] Add proper heading hierarchy
- [ ] Ensure no broken links on the page
- **📏 Scope:** `404.html` — ~5 lines
- **✅ Checkpoint:** 404 page matches main site styling and has valid HTML
- **⚙ Fallback:** Keep current — it's already functional

---

## Track D: Local SEO & Google Business Profile `[ ]`
*Off-site: claim and optimize local search presence*

### Phase D1: Google Business Profile Setup `[ ]`
- [ ] Claim/verify Google Business Profile at google.com/business
- [ ] Primary category: "Engineering Consultant" or "Engineering Service"
- [ ] NAP consistency: `Ferrum Engineering LLC`, `Sheridan, WY`, `dillon@ferrumeng.com`
- [ ] Set service area: Sheridan, WY + statewide Wyoming
- [ ] Add 10+ photos (projects, logo, workspace)
- [ ] Write business description matching website copy
- [ ] Add service listings matching the 4 service categories
- **📏 Scope:** Off-site — Google Business dashboard
- **✅ Checkpoint:** Profile is verified and visible in Google Search
- **⚙ Fallback:** Not applicable — this is manual work

### Phase D2: Local Citations `[ ]`
- [ ] Add/claim listing on:
  - Bing Places for Business
  - Yelp Business
  - Sheridan Chamber of Commerce directory
  - WY Business Council directory (if applicable)
- [ ] Ensure NAP consistency across all listings
- **📏 Scope:** Off-site — manual submissions
- **✅ Checkpoint:** Business appears in at least 3 directory searches
- **⚙ Fallback:** Skip — focus on GBP first

### Phase D3: Link Building (Local) `[ ]`
- [ ] Get listed on Sheridan Chamber of Commerce member directory
- [ ] Contribute a column to Sheridan Press about local business tech
- [ ] Get backlinks from any client or partner websites
- **📏 Scope:** Ongoing
- **✅ Checkpoint:** At least 2 local backlinks point to ferrumeng.com
- **⚙ Fallback:** Accept zero for now; this is long-term

---

## Track E: Deployment & Verification `[ ]`
*Deploy changes, verify everything works*

### Phase E1: Deploy All Changes `[ ]`
- [ ] Push all HTML/CSS changes to Cloudflare Pages
- [ ] Verify all 4 pages render correctly
- [ ] Test contact form submission (if added)
- [ ] Verify DNS records still intact (MX, SPF, DKIM, DMARC)
- **📏 Scope:** Deployment
- **✅ Checkpoint:** ferrumeng.com loads with all changes
- **⚙ Fallback:** Roll back any broken changes

### Phase E2: Post-Launch Verification `[ ]`
- [ ] Google Rich Results Test — all 4 pages pass
- [ ] PageSpeed Insights — ≥ 95 on mobile + desktop
- [ ] W3C HTML validator — no errors on any page
- [ ] Lighthouse — ≥ 90 across all categories
- [ ] Manual keyboard navigation test
- [ ] Manual mobile responsive test (320px width)
- **📏 Scope:** Testing
- **✅ Checkpoint:** All tests pass
- **⚙ Fallback:** Address any failures in follow-up

---

## Acceptance Criteria
1. ✅ Site messaging reflects Agentic AI OS + local dental + enterprise consulting two-track model
2. ✅ All 4 pages have valid LocalBusiness/schema structured data
3. ✅ Shopify theme-color, apple-touch-icon, font-display: swap on all pages
4. ✅ Lighthouse ≥ 90 in all categories
5. ✅ WCAG 2.1 AA compliance (skip link, focus indicators, contrast, keyboard nav)
6. ✅ Contact form submits successfully (or mailto fallback)
7. ✅ Google Business Profile claimed and verified
8. ✅ Sitemap and robots.txt updated
9. ✅ Email forwarding still working after deployment
