# CinCin Marketing Website

Standalone static marketing site for **playcincin.com**.

Completely separate from the CinCin PWA (which lives at **app.playcincin.com**).

## Files

```
cincin_www/
├── public/                 ← Published as the site; nothing outside it is served
│   ├── index.html          ← The entire site (HTML + CSS + JS, zero dependencies)
│   ├── brand/              ← Logo SVGs (stacked, horizontal, mark, wordmark; -dark = for cream backgrounds)
│   ├── favicon.svg         ← Glasses mark on espresso
│   ├── apple-touch-icon.png
│   ├── og-image.png        ← 1200×630 social share image
│   ├── robots.txt          ← Search engine crawl rules
│   ├── sitemap.xml         ← For Google/Bing indexing
│   └── _redirects          ← Sevalla redirect rules: www.playcincin.com → playcincin.com (301)
├── docs/                   ← Agent docs
├── CLAUDE.md               ← Agent instructions
├── .gitignore
└── README.md
```

Put every new page or asset in `public/`; everything outside it stays private.

## Deployment

Hosted on **Sevalla** as a static site: repo `miczagami/cincin_www`, branch `main`, no build command, publish directory `public`. Pushing to `main` deploys.

**Before merging the move into `public/`** (the site is leaving Vercel for Sevalla):
1. Disconnect the `cincin_www` Vercel project from Git (Vercel → Project → Settings → Git → Disconnect). Otherwise the merge redeploys Vercel, which may still publish the repo root and would then 404.
2. If the Sevalla static site already exists, set its publish directory to `public` and clear its Error file.

Until the DNS switch, the live domains keep serving Vercel's last deployment, so merged changes don't go live there yet.

`public/_redirects` permanently redirects every path on `www.playcincin.com` to the same path on `playcincin.com`. It only takes effect once both domains are added to the static site.

Full setup for all three CinCin services (this site, the app and the API) is in `cincin_backend/documentation/DEPLOYMENT-SEVALLA.md`.

## DNS Setup (Cloudflare, DNS only)

| Domain | Points to |
|--------|-----------|
| `playcincin.com`, `www.playcincin.com` | This static marketing site (Sevalla static site; www redirects to the apex) |
| `app.playcincin.com` | The CinCin PWA (Sevalla static site) |
| `api.playcincin.com` | The CinCin API (Sevalla application) |

## Links to the App

All CTAs point to `https://app.playcincin.com/auth/signup` or `https://app.playcincin.com/auth/login`. Update these URLs if your PWA subdomain changes.

## Brand

Styled to the **CinCin Brand Guidelines v1**: Espresso `#241C18`/`#2E2420`, Merlot `#63192B`, Gold `#CBA135`, Cream `#F0E6D2`, set in Poppins. The colour tokens are CSS variables at the top of `public/index.html`. Buttons are pills: gold primary, merlot secondary, cream outline, gold text link.

The logo files in `public/brand/` were extracted from the guideline PDF as vectors, and the same files ship in the app (`cincin_frontend/public/brand/`). Don't redraw or recolour them. Use the `-dark` versions on cream or gold backgrounds.

## Customisation

- **Stat numbers**: Edit the `data-count` attributes in the stats section (currently placeholder values)
- **Testimonials**: Replace with real beta tester quotes before launch (current ones are placeholders)
- **Pricing**: Monthly $12.99, annual $9.99/mo — matches the PWA SubscriptionPage
- **Footer links**: `/privacy` and `/terms` pages need to be created (separate HTML files)
