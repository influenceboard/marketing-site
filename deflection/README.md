# Vendor deflection guide: influenceboard.com/deflection

A setup guide for executives on Influence Board. It walks them through a one-time Microsoft Power Automate flow: drag a vendor email into an Outlook folder named Vendors Forward (the flow has the same name), and an automatic reply goes out from their own inbox pointing the vendor to Influence Board. The reply text is a template the executive adjusts as desired.

**Live:** https://influenceboard.com/deflection/ (unlisted, noindex)
**Shipped:** October 2026

## What's in this folder

| File | What it is |
|---|---|
| `index.html` | The full page file, with the WordPress fragment between the PASTE markers |
| `README.md` | This file |

## How it deploys

- One Custom HTML block on a new WordPress page with the slug `deflection`, Full-Width Content layout.
- Keeps the site header, nav and footer. Hides only the theme's page-title banner.
- Only the fragment between the PASTE-INTO-WORDPRESS markers goes into the CMS.
- Title, description, noindex setting and social share image live in the SEO plugin, not the HTML.

## Things that will bite you

- No ampersand pairs in the inline script. WordPress rewrites them and breaks the script.
- Don't zero `margin-top` on `.site-inner`. It keeps the content clear of the fixed theme header.
- Screenshots live in the WordPress Media Library (`/wp-content/uploads/2026/10/deflection-*.webp`), not in the code. If a screenshot changes, upload the new file and update its link in `index.html`.

## Build notes

- Sections: hero with a three-step flow, four setup steps with screenshots, a troubleshooting table.
- The reply template has a Copy text button that copies rich text (keeps the link) with a plain-text fallback.
- All styles are scoped to `.ibvr`.
- Screenshots are WebP, lazy loaded, with width and height set so the layout doesn't shift. The pasted fragment is about 16 KB.
- The how-it-works strip animates its arrows; it respects reduced-motion settings and stacks below 640px.
- Checked from 320px to 1280px wide with no horizontal scroll.

## Rolling back

Open `index.html` > History, copy the previous version's fragment, and paste it into the Custom HTML block. Update the page and clear the WP Engine cache.
