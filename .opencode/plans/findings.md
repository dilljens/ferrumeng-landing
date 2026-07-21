# Findings: Ferrum Engineering Landing — Pretty + Interactive

## Requirements
- Use `ferrum-logo.png` as the brand mark in nav and hero
- "Go all out" on interactivity (particle canvas, typing animation, 3D tilt, custom cursor, scroll reveals, mobile menu)
- No emoji on the site — use Unicode symbols or CSS-drawn alternatives
- Use `option7-neural.svg` as ambient hero background decoration
- Preserve single-file simplicity — no build step, no dependencies

## Pre-resolved Decisions
- **Architecture**: All additions go into `index.html` — inline CSS + JS
- **Logo**: `ferrum-logo.png` at 36px (nav) and 280px (hero decorative, 0.06 opacity)
- **Hero SVG**: `option7-neural.svg` inline, right-aligned, 400px, faint opacity, subtle pulse
- **Particle canvas**: Copper-toned node graph inspired by neural SVG, 12-18 nodes
- **Custom cursor**: 28px ring, 2px stroke, copper, ease-follow
- **Libraries**: None
- **Animations**: Gated by `prefers-reduced-motion`
- **Icons**: Unicode geometric shapes (◆ ▶ ◆) and CSS-styled elements instead of emoji

## Asset Audit
| Asset | Path | Purpose |
|---|---|---|
| `ferrum-logo.png` | `./ferrum-logo.png` | 1024x1024 RGBA, 216KB |
| `option7-neural.svg` | `./logos/option7-neural.svg` | 200x200, copper gradient nodes + connections |
| `favicon.svg` | `./favicon.svg` | Current: simple "F" in copper box |

## Current Architecture
- Single file: `index.html` (671 lines)
- Styles: inline in `<style>` block
- JS: none
- Sections: Nav, Hero, Services, About, Projects, Contact, Footer
- Palette: `#0c0c0e` background, `#d4d4d8` text, `#b45309` copper accent, `#fafafa` white headings
- Fonts: Inter (body), JetBrains Mono (code/labels)
- Deploy: Cloudflare Pages, zero build step

## Emoji Replacements
| Current | Replacement |
|---|---|
| ⚡ | CSS-styled lightning bolt or Unicode ⚡ |
| 🧠 | Unicode ◆ diamond or CSS icon |
| ⛓️ | Unicode chain or CSS icon |
| 🔌 | Unicode plug or CSS icon |
| ↗ | CSS arrow or Unicode ↗ (this is fine, it's a symbol) |
