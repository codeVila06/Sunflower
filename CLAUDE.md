# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Static HTML/CSS/JS marketing website for **Sunflower Parks & Gardens**, a real estate estate in Lagos, Nigeria. No build system, no dependencies, no framework — just open `frontend/index.html` in a browser.

## Running the Site

Open `frontend/index.html` directly in a browser. All asset paths are relative and CDN-based, so no local server is required (the embedded Google Map on `contact.html` needs internet access).

## Architecture

Five standalone HTML pages, each self-contained with a shared `<link>` to `css/style.css` and `<script>` to `js/slider.js`.

| Page | Purpose |
|---|---|
| `index.html` | Landing page — 8-slide hero carousel, about summary, FAQ |
| `about.html` | Company story, image collage, CEO message |
| `properties.html` | 6 property listing cards (₦15M–₦62M) |
| `iri.html` | ÌRÌ luxury sub-estate showcase with pricing/ROI |
| `contact.html` | Contact form, office info, embedded Google Map |

Navigation is repeated in every page's `<nav>` — changes must be applied to all five files.

## Design System

CSS custom properties defined in `:root` in `css/style.css`:

```css
--brand:      #FFD54A   /* primary yellow */
--brand-dark: #e6b83a   /* hover/active yellow */
--accent:     #0f1720   /* near-black for text/backgrounds */
--muted:      #6b6b6b   /* secondary text */
--glass:      rgba(255,255,255,0.7)  /* glassmorphism panels */
```

Max-width container is `1160px`. Responsive breakpoints: `980px`, `800px`, `600px`, `360px`.

External CDN: Google Fonts (Inter + Playfair Display), Font Awesome 6.4.0.

## JavaScript (`js/slider.js`)

Single file handles: hero carousel (6 s auto-advance, pauses on hover), mobile nav toggle, back-to-top button, and scroll-reveal animations via `IntersectionObserver`. No module system — all logic runs on `DOMContentLoaded`.