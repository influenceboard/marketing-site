# Homepage — influenceboard.com

The Influence Board homepage. Executive-first: the page speaks to the business
leaders who set the terms, not to the vendors requesting meetings.

**Live:** https://influenceboard.com/
**Shipped:** September 8, 2026

---

## What's in this folder

| File | What it is |
|---|---|
| `index.html` | The canonical page. Full standalone document, with `PASTE-INTO-WORDPRESS` markers around the fragment that goes into the CMS. |
| `homepage-pre-v5-snapshot.txt` | The previous homepage's block markup, captured immediately before this version replaced it. Rollback source of record. |
| `README.md` | This file. |

---

## How it deploys

WordPress on the Genesis framework with the Altitude Pro theme. The page ships as a
**single Custom HTML block** on the existing homepage — no PHP, no plugin changes, no
new page. Theme integration is handled by CSS inside the file itself, which means the
page carries everything it needs and nothing else on the site has to change.

Only the fragment **between the `PASTE-INTO-WORDPRESS` markers** goes into the CMS. The
surrounding `<html>`/`<head>`/`<body>` exists so this file renders standalone for preview
and produces readable diffs.

### Two things that will bite you

**Keep the theme header's clearance.** The site header is `position: fixed`, roughly 91px
tall. The theme's `.site-inner { margin-top: 100px }` is the only thing holding content
clear of it. The usual theme-integration CSS zeroes that margin — correct on a page that
*hides* the header, wrong here. Zero it and the top of the hero disappears behind an
opaque bar. It looks fine in local preview and breaks the moment it's live.

**Guard against bare-element styles.** Scoping every rule to `.ibhome` is not enough. The
theme also styles bare `button`, `input`, `blockquote` and `li`, and those rules reach
inside any wrapper. Left unguarded they produce a hairline on the range sliders, wrapped
button labels, doubled quote marks, and stray list markers. The guard block near the
bottom of the stylesheet neutralises all of it — and it needs `!important` on the list
rules specifically, because a theme selector like `.entry-content ul li` outscores a
plain `.ibhome li`.

---

## Build notes

**Self-contained, with images on the CDN.** All CSS and JS are inline. Images are served
from the WordPress media library rather than embedded as data URIs — an earlier build
inlined them and came to 1.08 MB, against 55 KB now. Base64 images can't be cached or
lazy-loaded, which is a poor trade on the most-visited page on the site.

**Three inline scripts,** all first-party, no dependencies: a meeting-value calculator, the
phone-mockup sliders, and the stat count-up. If a CMS block strips inline `<script>`, all
three fail *silently* — the page still looks correct. Always click through them after
deploying.

**Accessibility.** All images carry alt text; the duplicated logo-ticker pass is
`aria-hidden` so screen readers announce each company once per cycle rather than twice.
The count-up respects `prefers-reduced-motion`. Tap targets are 46px on phones. Body copy
meets WCAG AA against its backgrounds.

**Mobile.** The logo ticker swaps from an animated marquee to a scrollable row under
560px. The peer-session cards become a scroll-snap carousel under 600px, with the next
card deliberately peeking past the edge — that peek is the affordance. The hero animation
is desktop-only, hidden under 861px.

---

## Rolling back

`homepage-pre-v5-snapshot.txt` holds the complete previous block markup. Restoring it
needs more than the markup — see the dependency list in that file's header comment
(synced patterns, sliders, plugins, and the theme's page-specific CSS).
