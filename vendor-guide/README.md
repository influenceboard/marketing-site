# Vendor guide: influenceboard.com/vendor-guide

A walkthrough for Meeting Requesters who already have an Influence Board login. It shows how to find executives, check fit, send a request, pay, and schedule, with a short video and a screenshot for each step. The page is unlisted: it is not in the site menus and is set to No Index, and it is shared by link.

**Live:** https://influenceboard.com/vendor-guide/
**Shipped:** October 2026

## What's in this folder

| File | What it is |
|---|---|
| `index.html` | The full page. Only the part between the PASTE-INTO-WORDPRESS markers goes into WordPress. |
| `README.md` | This file. |

## How it deploys

- One Custom HTML block on a top-level WordPress page, Full Width layout.
- Keeps the site header and nav; the page's own CSS hides the theme's page-title banner and zeroes the content padding.
- Only the fragment between the PASTE-INTO-WORDPRESS markers goes into the CMS.
- Screenshots load from the WordPress Media Library (WebP, 1280px wide). The video is a Vimeo embed.
- Title, description, and No Index live in All in One SEO, not in this file.

## Things that will bite you

- No ampersands in inline scripts (WordPress rewrites them). This page has no scripts; keep it that way or use WPCode.
- The slug `meeting-requesters` is taken by a 2023 media attachment, which is why this page uses `vendor-guide`.
- The Vimeo video must allow embedding on influenceboard.com, or the player shows a privacy error.
- Clear the WP Engine cache after every change.

## Build notes

- Sections: hero with video, steps 1 to 5, an "After you submit" band, steps 6 to 8, cost box, best-practice guide links, Concierge and Premium Services block, final call to action.
- Screenshots open full size on tap, which helps on phones.
- Checked at 360, 390, 430, 768, and 1280px wide: no horizontal scroll, all images load.

## Rolling back

Open `index.html` > History, pick the earlier version, and paste its fragment back into the WordPress block.
