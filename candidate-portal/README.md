# Candidate Portal: influenceboard.com/candidate-portal

The page executives land on when they're invited to join Influence Board. It explains
how the platform works from the executive's side: they set the rules, requests are
screened against them, and every meeting they accept funds a cause they choose.

**Live:** https://influenceboard.com/candidate-portal/
**Shipped:** September 24, 2026

---

## What's in this folder

| File | What it is |
|---|---|
| `index.html` | The canonical page. Full standalone document, with `PASTE-INTO-WORDPRESS` markers around the fragment that goes into the CMS. |
| `README.md` | This file. |

---

## How it deploys

Same method as the homepage: a **single Custom HTML block** on the existing page
(ID 5879), so the URL, SEO settings and inbound links stay put. No PHP, no plugin
changes. Theme integration is CSS inside the file. The page keeps the site header and
nav, and hides only the theme's page-title banner.

Only the fragment **between the `PASTE-INTO-WORDPRESS` markers** goes into the CMS.

The page title, description and social share image live in the SEO plugin (All in One
SEO), not in this file. The `<title>` and meta description in the file's `<head>` are for
standalone preview only.

### Three things that will bite you

**No ampersands in the inline scripts.** WordPress's content filter rewrites every `&`
inside anything it reads as an HTML tag, and it reads a less-than comparison in a script
(`i < items.length`) as the start of one, running to the next `>`. On the first deploy
that turned an `&&` in the FAQ script into `&#038;&#038;`. The script stopped, and the
FAQ fell back to its no-script layout. The code in the editor looked fine; only the
rendered page was broken. The scripts now use `a ? b : c` or nested `if`s instead. Keep
it that way.

**Keep the theme header's clearance.** Same as the homepage: never zero `margin-top` on
`.site-inner`. The fixed header needs it.

**Clip, don't hide, the wrapper's sideways overflow.** The FAQ answer panel is
`position: sticky`. `overflow-x: hidden` on the page wrapper turns it into a scroll
container and the panel stops following the page, so the wrapper uses
`overflow-x: clip`, with `hidden` as the fallback for older browsers.

---

## Build notes

**Sections:** hero with video and a logo strip; who set the rules, with a phone mockup of
an executive's rules screen; how Influence Board compares to a traditional board seat;
how it works; FAQs; the impact; peer sessions; close. Sections shared with the homepage
use the homepage's words.

**Three inline scripts,** first-party, no dependencies: the phone-mockup sliders, the stat
count-up, and the FAQ. The page still reads correctly if one fails, so click through the
FAQ after every deploy.

**FAQ.** Desktop: a question list, with the picked answer shown large in a sticky navy
panel. Phones: tap to open; answers stay open until tapped again. Without JavaScript,
every answer shows under its question. Each answer is written once and the panel copies
it, so edits happen in one place.

**Breakpoints.** Checked at 21 widths from 1920px down to 320px.

| Width | What changes |
|---|---|
| 1201px and up | Comparison strip runs as columns |
| 1121px and up | Peer cards four across (2 x 2 below) |
| 941px and up | How it works three across (two, plus one full width, below) |
| 861px and up | Hero in two columns; FAQ list with the answer panel |
| 720px and below | Impact stats: charity total full width, two below it |
| 640px and below | Comparison: topic above its two answers |
| 600px and below | Peer cards become a swipe row; How it works stacks; buttons 46px tall |
| 560px and below | Logo strip becomes a swipeable row that fades at the right edge |
| 480px and below | Impact stats stack |

**Accessibility.** Alt text on every logo, and the duplicated ticker pass is
`aria-hidden`. The comparison strip is an ARIA table. The FAQ uses real buttons with
`aria-expanded` and arrow-key navigation. Motion respects `prefers-reduced-motion`.

---

## Rolling back

The previous page is saved in WordPress as a draft titled "Candidate Portal (old)". Copy
its blocks back onto page 5879 to restore it.
