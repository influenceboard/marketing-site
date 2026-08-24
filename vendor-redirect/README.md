# Influence Board — Vendor Redirect Landing Page

A branded landing page that welcomes vendors who reach an Influence Board executive and are routed, through the Cirrus Insight integration, to Influence Board instead. The page acknowledges the redirect, explains what Influence Board is, and invites the visitor to request an introduction through a short intake form.

**Role:** Designed, built, and maintained by Crystal Hatch (VP of Platform, Influence Board).

## Overview

Influence Board runs an opt-in network where executives take vendor and partner meetings on their own terms, in support of a cause they choose. When a vendor's outreach is redirected, they land here. The page has one job: reassure, explain, and convert into an intake, all in the Influence Board brand.

The visitor sees a short "what just happened" flow, a plain explanation, and a single call to action that opens an intake form. Submissions are reviewed and followed up personally.

## Build

- **Single self-contained HTML page.** No build step, no dependencies beyond Google Fonts.
- **Brand system in CSS:** Aleo (display) and Barlow (body), a Prussian-navy palette with Celestial and Sunflower accents, and the brand's uppercase button treatment.
- **Scoped styling.** All page styles live under a single wrapper class so the page can be dropped into an existing themed site without affecting anything around it, with a small integration layer that lets it sit full-width and clean inside the host theme.
- **Accessible by intent:** readable type sizes, strong contrast on a dark background, reduced-motion support, and a fully responsive layout down to mobile.
- **Intake** is handled by an embedded form that opens as a popup, so the visitor never leaves the branded page.

## Deploy

Built for a WordPress site (Genesis framework on WP Engine). The page is added through a Custom HTML block; the styling handles full-width layout and clean integration with the host theme on its own. Versioned here so there's always a single source of truth for the live page.

---

© Influence Board.Trademarks and brand assets belong to Influence Board.
