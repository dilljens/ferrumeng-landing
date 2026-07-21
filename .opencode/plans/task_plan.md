# Project: Ferrum Engineering Landing — Pretty + Interactive

Goal: Transform the single-file landing page from a static text-based layout into a polished, animated experience with the `ferrum-logo.png` as the brand mark and rich interactivity throughout. No emoji anywhere.

## Requirements
- [ ] R1: Replace text logo `ferrum<em>//</em>eng` with `ferrum-logo.png` in the nav bar
- [ ] R2: Display `ferrum-logo.png` as a decorative visual in the hero section
- [ ] R3: Use `option7-neural.svg` as an ambient decorative background element in the hero
- [ ] R4: Add mobile hamburger menu (nav links are invisible on mobile currently)
- [ ] R5: Add scroll-reveal animations for sections (IntersectionObserver, fade+slide-up)
- [ ] R6: Active nav link highlighting based on scroll position
- [ ] R7: Animated canvas particle network background in hero (neural-inspired)
- [ ] R8: Hero typing animation on the tagline
- [ ] R9: Mouse-follow copper glow in the hero
- [ ] R10: 3D tilt interaction on service cards
- [ ] R11: Custom copper cursor ring
- [ ] R12: Back-to-top button
- [ ] R13: Stat counter animation (add a stats row with count-up)
- [ ] R14: Performance safeguards (prefers-reduced-motion, canvas throttle)
- [ ] R15: No emoji anywhere in the HTML

## Pre-resolved Decisions
- Architecture: All additions go into the single `index.html` file — inline CSS + inline JS (no build step, no dependencies)
- Logo treatment: `ferrum-logo.png` (1024x1024 RGBA) used at 36px in nav, 280px as hero decorative element with opacity
- SVG treatment: `logos/option7-neural.svg` embedded as an inline SVG in the hero, used as a subtle background graphic (400px, low opacity, positioned off-center right)
- Particle canvas: Draws an animated node graph with copper-colored nodes and connection lines, inspired by option7-neural styling
- Custom cursor: Copper ring (28px diameter, 2px stroke, follows mouse with 100ms ease delay), hides native cursor on interactive elements
- No external libraries — all zero-dependency vanilla JS
- Icons: use Unicode symbols or CSS-drawn elements instead of emoji

## Track A: Visual & Interactive Overhaul `[ ]`
- Description: Single track covering the entire landing page transformation
- Scope: 1 file (`index.html`), ~700-900 new lines

### Phase A1: Logo & Hero Background Visuals `[ ]`
- [ ] Replace text logo with the PNG in the nav
- [ ] Add ferrum-logo.png as decorative element in hero (large, centered behind text, low opacity)
- [ ] Inline option7-neural.svg as hero background graphic (positioned right, ~400px, ~0.15 opacity, subtle CSS pulse)
- [ ] Replace emoji service icons with Unicode/CSS alternatives
- Scope: 1 file, ~50 lines changed
- Checkpoint: `grep -c 'ferrum-logo.png' index.html` returns 2 (nav + hero)

### Phase A2: CSS Foundation for Interactivity `[ ]`
- [ ] Add CSS custom properties for copper tones
- [ ] Add scroll-reveal animation keyframes
- [ ] Add intro page-load animation
- [ ] Add mobile hamburger styles
- [ ] Add nav shrink styles
- [ ] Add custom cursor styles
- [ ] Add back-to-top button styles
- [ ] Add 3D card tilt perspective styles
- [ ] Add stat counter row styles
- Scope: 1 file, ~150 lines in style

### Phase A3: Core JS — Navigation & Scroll `[ ]`
- [ ] Mobile hamburger toggle
- [ ] Active nav link tracking via IntersectionObserver
- [ ] Nav shrink on scroll
- [ ] Back-to-top button
- [ ] Scroll-reveal via IntersectionObserver
- Scope: 1 file, ~120 lines in script

### Phase A4: JS — Canvas Particle Network `[ ]`
- [ ] Full-bleed canvas behind hero content
- [ ] 12-18 copper nodes with F-like distribution
- [ ] Connection lines between nearby nodes
- [ ] Slow drift animation, connection pulsing
- [ ] Mouse interaction (attraction, brighter connections)
- [ ] Copper color scheme
- Scope: 1 file, ~150 lines in script

### Phase A5: JS — Typing Animation & Mouse Effects `[ ]`
- [ ] Character-by-character typing of hero h1
- [ ] Mouse-follow copper radial glow in hero
- [ ] Custom copper cursor ring
- [ ] Cursor enlarges on hover over interactive elements
- Scope: 1 file, ~120 lines in script + CSS

### Phase A6: JS — 3D Card Tilt & Micro-interactions `[ ]`
- [ ] 3D tilt on service cards (max +/-8 deg rotation)
- [ ] Project row hover glow
- [ ] Contact email subtle glow
- Scope: 1 file, ~60 lines in script

### Phase A7: JS — Stat Counter & Polish `[ ]`
- [ ] Stats row: Projects, Domains, Languages, Clients
- [ ] Count-up animation on scroll reveal
- [ ] prefers-reduced-motion gate
- [ ] Canvas scroll throttle
- Scope: 1 file, ~80 lines

### Phase A8: Final QA & Responsiveness `[ ]`
- [ ] Test mobile/tablet/desktop
- [ ] Verify no console errors
- [ ] Test prefers-reduced-motion
- [ ] Confirm retina-quality logo
- Scope: 1 file, ~20 lines tweaks
