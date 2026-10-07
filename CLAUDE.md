# Holistic Fire Safety — Website Guide for Claude

Read this first. It tells you everything about how this site works so you can help the owner make changes through conversation alone. The person you are working with is **non-technical** — never ask them to run commands, edit code, or use technical tools. You do the work through their browser; they only handle sign-ins.

## What this is

The live website for **Holistic Fire Safety Ltd** (holisticfire.com) — a passive fire protection company in Barton-Upon-Humber, UK. It is a fully static site: plain HTML and CSS, no build step, no frameworks, no JavaScript beyond a tiny mobile menu toggle.

## How publishing works

1. **This GitHub repo is the master copy.** Every file here is served as-is.
2. **Netlify auto-deploys from the `main` branch.** Any commit to main is live at https://holisticfire.com within ~60 seconds. There is nothing to configure or trigger — committing IS publishing.
3. **To make a change:** edit the file(s) via the GitHub website in the user's browser (web editor for text edits, "Upload files" to add or replace whole files — uploading a file with an existing name overwrites it).
4. **To verify a change is live:** fetch `https://holisticfire.com/<path>?cb=<timestamp>` and check for your change, or load the page in the browser. Allow a minute for deploy. GitHub's "raw" CDN caches for ~5 minutes, so prefer checking the live site.

Netlify site name: **holisticfire** (holisticfire.netlify.app) on Jonny's Netlify account (sign-in: Google). DNS is at GoDaddy: A @ → 75.2.60.5, CNAME www → holisticfire.netlify.app. Email (MX/Outlook records at GoDaddy) is separate from the website — never touch DNS records other than A @ and CNAME www.

## Hard rules

- **Mirror real copy, never invent it.** All service descriptions, case studies, news articles and contact details were taken verbatim from the company's materials. Do not rewrite, embellish or invent company claims, stats, testimonials or legal text. New content must come from the company (documents, their Google Drive, or text pasted in chat).
- **Confirmed contact details:** Unit 10B, Humber Bridge Ind Est, Harrier Road, Barton-Upon-Humber, DN18 5RP · 01652 317316 · customer@holisticfire.com
- **Nav and footer are duplicated in every HTML file.** A change to either must be applied to all ~25 pages (script it, don't hand-edit).
- The contact form uses **Netlify Forms** (`data-netlify="true"`) — submissions appear in the Netlify dashboard.

## Site structure

```
index.html                 Homepage (hero, What We Do plates, partnership, accreditations, testimonials)
about.html                 About + team grid (photos in assets/img/team-*.jpg)
contact.html               Contact details + Netlify form
testimonials.html          Testimonials
services/                  index + 7 service pages
case-studies/              index + 7 case-study pages
news/                      index + 4 article pages (mirrored from old site)
css/style.css              THE single stylesheet for everything
assets/logo-colour.svg     Colour logo (nav), logo-white.svg (footer/dark)
assets/img/                All images (optimised)
assets/docs/               data-privacy-policy.pdf, cookies.pdf (footer links)
```

## Design system (match it exactly when adding anything)

- **Fonts:** Barlow Condensed (headings, uppercase, bold 600/700) + IBM Plex Sans (body), loaded from Google Fonts.
- **Palette (CSS custom properties in style.css):** `--ink:#171B20` (near-black), `--paper:#F5F4F1` (warm off-white), `--peach:#E9EDF1` (light steel wash), `--apricot:#EFC9AA`, `--red:#E07840` (brand orange, sampled from the logo), `--red-dark:#BE5F2E`, `--rust:#A65B2A`, `--steel:#5A6672`, `--line:#D9DAD7`.
- **Signature motifs:** "plate" cards with a 4px orange top border; eyebrow labels (small caps, letter-spaced, short orange dash before); dark ink sections for outcomes/CTAs; page-hero banners with photo + gradient overlay. Homepage hero uses gradient `linear-gradient(100deg, rgba(23,27,32,.92) 0%, rgba(23,27,32,.72) 45%, rgba(190,95,46,.55) 100%)` over home-banner.jpg.
- **Mobile (≤620px):** card grids become horizontal swipe rows (scroll-snap); nav collapses behind a Menu button. Test changes at 390px width.
- **Case study pages** share a template: page-hero → cs-stats plates → cs-grid (cs-content article + cs-aside with photo and "At a Glance" facts) → dark cs-outcome → cs-close quote → cs-next card (they cycle in a loop) → CTA band.
- New pages: copy an existing page of the same type and edit — never write from scratch.

## Common tasks

- **Edit text:** find it with GitHub search or in the local file, edit that file via the GitHub web editor, commit to main.
- **Add a case study / news article:** duplicate the closest existing page, replace content (verbatim from source material), add a card to the section's index page, update the cs-next loop (case studies only).
- **Add/replace an image:** optimise first (resize to ~1100-1600px wide, JPEG quality ~72), upload to assets/img/ via GitHub "Add file → Upload files".
- **Anything site-wide (nav, footer):** apply to every HTML file.

## History / context

- Rebuilt from the old Squarespace site (July–Oct 2026) by Jonny Teeling (jonnyteeling on GitHub) working with Claude. Went live on holisticfire.com on 6 Oct 2026.
- The old Squarespace site still exists (subscription active) as a rollback; GoDaddy DNS backup from before the switch is in the repo owner's records.
- Known open items: higher-res accreditations image wanted (Aug 2025 version); README.md is outdated (describes an early version — this file is authoritative).
