# proSapient partner page: influenceboard.com/prosapient

The page executives land on when proSapient invites them to join Influence Board. Its
job is to show, before anything else, how an Influence Board meeting differs from an
expert call: it's a vendor meeting the executive chooses to take, they're free to talk
about their company, and the vendor donates to a cause they choose.

**Live:** https://influenceboard.com/prosapient/
**Shipped:** October 8, 2026

---

## What's in this folder

| File | What it is |
|---|---|
| `index.html` | The canonical page. Full standalone document, with `PASTE-INTO-WORDPRESS` markers around the fragment that goes into the CMS. |
| `README.md` | This file. |

---

## How it deploys

A **new page** with the slug `prosapient`, Full-Width Content layout, and a **single
Custom HTML block**. No PHP, no plugin changes. Theme integration is CSS inside the file.
The page keeps the site header and nav and hides only the theme's page-title banner. It
isn't in the site menu; visitors reach it from proSapient's invitation messages.

Only the fragment **between the `PASTE-INTO-WORDPRESS` markers** goes into the CMS.

The page title, description and social share image live in the SEO plugin, not in this
file. The `<title>` and meta description in the file's `<head>` are for standalone
preview only.

### Three things that will bite you

Built on the Candidate Portal's shell, so it carries the same three rules:

**No ampersands in the inline scripts.** WordPress's content filter rewrites `&` inside
anything it reads as an HTML tag, and it reads a less-than comparison in a script as the
start of one. The scripts use `a ? b : c` or nested `if`s instead. Keep it that way.

**Keep the theme header's clearance.** Never zero `margin-top` on `.site-inner`. The
fixed header needs it.

**Clip, don't hide, the wrapper's sideways overflow.** The FAQ answer panel is
`position: sticky`, so the page wrapper uses `overflow-x: clip`, with `hidden` only as
the fallback for older browsers.

---

## Build notes

**Sections:** hero with video and a logo strip; how it compares to an expert call; who
set the rules, with a phone mockup of an executive's rules screen; how it works; FAQs;
the impact; peer sessions; close. Sections shared with the Candidate Portal use its
words, which come from the homepage.

**Hero.** A short eyebrow ("Invited by proSapient"), then the headline "This is
different from an expert call," then the community and the donation as the subhead.

**Comparison.** A white card on a light grey band, right under the hero. Each row is a
question. The expert call and Influence Board columns share one style; only the color
differs (neutral grey vs. sunflower), so both get a fair read and Influence Board stands
out. The highlight color is three CSS variables at the top of the block. At 640px and
below, each question sits above its two answers, still side by side. It's an ARIA table.

**FAQ.** Ten questions. Desktop: a question list, with the picked answer shown large in
a sticky navy panel. Phones: tap to open. Without JavaScript, every answer shows under
its question.

**Three inline scripts,** first-party, no dependencies: the phone-mockup sliders, the
stat count-up, and the FAQ. Click through the FAQ after every deploy.

---

## Rolling back

This is a new page with nothing to restore. To take it down, switch the page to Draft
in WordPress.
