# Influence Board — Marketing Site

A home for Influence Board's marketing web pages: self-contained, brand-consistent pages that deploy onto the main site. Built and maintained by **Crystal Hatch** (VP of Platform, Influence Board).

## Pages

| Page | What it is | Live |
|------|-----------|------|
| [homepage](./homepage) | Executive-first homepage. Single Custom HTML block on page 582. | https://influenceboard.com/ |
| [vendor-redirect](./vendor-redirect) | Landing page for vendors redirected to Influence Board through the Cirrus Insight integration | https://influenceboard.com/new-model-for-executive-access/ |
| [candidate-portal](./candidate-portal) | Landing page for executives invited to join. Single Custom HTML block on page 5879. | https://influenceboard.com/candidate-portal/ |

## Conventions

- Each page lives in its own folder with an `index.html` and a short README.
- Shared brand system: **Aleo** (display) + **Barlow** (body); Prussian-navy palette with Celestial and Sunflower accents; uppercase button treatment.
- Pages are self-contained HTML, dropped into WordPress (Genesis on WP Engine) via a Custom HTML block. Styling handles full-width layout and clean integration with the host theme.
- Two integration modes: a page either **hides** the theme header (standalone landing pages) or **keeps** it (pages that sit inside the site's navigation). They need different CSS — a page that keeps the fixed header must preserve its top-margin clearance, or its first screen renders underneath it.
- An `index.html` stores the full standalone document. Where only part of it goes into the CMS, that fragment is marked with `PASTE-INTO-WORDPRESS` comments.

---

© Influence Board. Trademarks and brand assets belong to Influence Board.
