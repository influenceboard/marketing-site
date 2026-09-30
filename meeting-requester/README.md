# Meeting Requester: influenceboard.com/meeting-requester

The page for companies that want a meeting with an executive on Influence Board. It
explains how requests work from the requester's side: executives set their rules for
access, Influence Board enforces them, and every meeting funds a cause the executive
chose. One call to action opens a short intake form.

**Live:** https://influenceboard.com/meeting-requester/
**Shipped:** September 30, 2026

---

## What's in this folder

| File | What it is |
|---|---|
| `index.html` | The canonical page. Full standalone document, with paste markers around the fragment that goes into the CMS. |
| `README.md` | This file. |

---

## How it deploys

Same method as the homepage and the candidate portal: a **single Custom HTML block** on
the existing page (ID 1629), so the URL, SEO settings and inbound links stay put. No PHP,
no plugin changes. Theme integration is CSS inside the file.

It shares its look with the vendor redirect page, but that page hides the theme header.
This one sits in the main site navigation, so it **keeps** the header and nav and hides
only the theme's page-title banner.

Only the fragment **between the `PASTE EVERYTHING BELOW` and `END PASTE` markers** goes
into the CMS.

The page title, description and social share image live in the SEO plugin (All in One
SEO), not in this file. The `<title>` in the file's `<head>` is for standalone preview only.

### Three things that will bite you

**No ampersands or less-than signs in the inline scripts.** WordPress's content filter
rewrites `&` inside anything it reads as an HTML tag, and it reads a less-than comparison
in a script as the start of one. The script then fails without an error. The scripts here
use `1 > p` and `a ? b : c` instead. Keep it that way.

**Keep the theme header's clearance, and leave the mobile menu alone.** Never zero
`margin-top` on `.site-inner`; the fixed header needs it. The mobile menu plugin is the
site nav on phones, so this page does not hide it (the vendor redirect page does, because
it hides the whole header).

**The intake triggers are buttons, not links.** Paperform's popup does not cancel a
link's click, so an `<a href>` would take the visitor off the page instead of opening the
form. If the Paperform script is blocked, the buttons open the form page directly.

---

## Build notes

**Sections:** hero; how it works (three steps, and step one's title also opens the form);
about Influence Board; every meeting funds a cause, with impact numbers that count up;
FAQs, the one light section on the page; close.

**Two inline scripts,** first-party, no dependencies: the impact count-up and the
Paperform loader with its fallback. The real numbers are in the HTML, so they still show
without JavaScript. The impact numbers are rounded-down totals shared with the homepage,
so they stay true as the totals grow.

**Intake:** the Paperform form `meeting-requester`. Each page gets its own form, named
after the page slug, so submissions arrive already separated by source.

**Breakpoints.** Checked at 21 widths from 1920px down to 320px.

| Width | What changes |
|---|---|
| 721px and up | How it works three across; About in two columns; FAQs in two columns; impact stats three across |
| 720px and below | Everything stacks to one column; impact stats show the charity total full width with two below it |
| 380px and below | Buttons get tighter side padding |

**Accessibility.** Real buttons with visible focus rings. Small text on navy uses a
slightly lighter celestial so it passes contrast. The count-up respects
`prefers-reduced-motion`. The decorative icon is `aria-hidden`.

---

## Rolling back

The previous page is saved in WordPress as a draft titled "Meeting Requester (old)". Copy
its blocks back onto page 1629 to restore it.
