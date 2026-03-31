# CinCin Marketing Website

Standalone static marketing site for **playcincin.com**.

Completely separate from the CinCin PWA (which lives at **app.playcincin.com**).

## Files

```
cincin-website/
├── index.html      ← The entire site (HTML + CSS + JS, zero dependencies)
├── favicon.svg     ← CinCin "C" favicon
├── robots.txt      ← Search engine crawl rules
├── sitemap.xml     ← For Google/Bing indexing
├── og-image.png    ← TODO: Create 1200×630 OG image (see below)
└── README.md
```

## Deployment

This is a static site — deploy to any static host:

**Vercel:**
```bash
cd cincin-website
vercel --prod
```

**Netlify:** Drag the folder into Netlify dashboard, or connect the repo.

**AWS S3 + CloudFront:** Upload all files to an S3 bucket, front with CloudFront, point playcincin.com DNS.

**GitHub Pages:** Push to a repo, enable Pages on the main branch.

## DNS Setup

| Domain | Points to |
|--------|-----------|
| `playcincin.com` | This static marketing site |
| `app.playcincin.com` | The CinCin PWA (Vite/React app) |

## Links to the App

All CTAs point to `https://app.playcincin.com/auth/signup` or `https://app.playcincin.com/auth/login`. Update these URLs if your PWA subdomain changes.

## OG Image

Create a 1200×630 image for social sharing. Suggested design:
- Background: #0A0A0A
- Radial cyan glow at center
- "CinCin" in white, 96px bold
- "AI · TASTING · GAME" in #22D3EE, small caps
- "Scan. Taste. Compete." in #CCCCCC

Save as `og-image.png` in this directory.

## Customisation

- **Stat numbers**: Edit the `data-count` attributes in the stats section (currently placeholder values)
- **Testimonials**: Replace with real beta tester quotes before launch
- **Pricing**: Monthly $12.99, annual $9.99/mo — matches the PWA SubscriptionPage
- **Footer links**: `/privacy` and `/terms` pages need to be created (separate HTML files)
