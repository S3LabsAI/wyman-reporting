# Wyman Reporting

Static hosting for the Kristin Wyman Agency campaign reports, deployed on Vercel.

## What's here

| Path | Description |
| --- | --- |
| `index.html` | Reports hub for Kristin Wyman Insurance Agency. Served at the site root, with one card per report. |
| `reports/home-campaign-performance-review.html` | Home Campaign Performance Review (Sept 15 – Oct 13, 2026), reviewed Nov 11, 2026. |
| `vercel.json` | Vercel config: static site, no build step, caching and security headers. |
| `.vercelignore` | Keeps repo metadata out of the deployment bundle. |

The report is fully self-contained: all images are inline base64 and the only
external requests are the Sora and Outfit webfonts from Google Fonts. It follows
the viewer's light/dark system setting and includes a theme toggle. There is no build
step, no framework, and no dependencies.

## Deploying

Import the repo at [vercel.com/new](https://vercel.com/new):

- **Framework Preset:** Other
- **Root Directory:** `./`
- **Build Command:** leave empty (overridden to none by `vercel.json`)
- **Output Directory:** leave empty — files are served straight from the repo root
- **Install Command:** leave empty

Every push to the default branch triggers a production deploy; pushes to other
branches get preview URLs.

## Adding another report

1. Drop the new HTML file in `reports/`, e.g. `reports/home-campaign-performance-review-2026-12.html`.
2. Add a card for it to the `.rgrid` in `index.html`, move the "Current" tag to the new card, and update the "Latest review" and "Reports" values in the strip.
3. Thanks to `cleanUrls`, it will be reachable at `/reports/<name>`.
4. Commit and push. Vercel redeploys automatically.

## Access

`X-Robots-Tag: noindex, nofollow` keeps these reports out of search engines,
but the URL is public to anyone who has it. For client-only access, turn on
Vercel Deployment Protection (password or SSO) in the project settings.
