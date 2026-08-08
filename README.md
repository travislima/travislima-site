# travislima.com

Personal brand site for **Travis Lima**: ecommerce & customer success at WooCommerce, WordCamp speaker, and a decade in WordPress.

Built with [Astro](https://astro.build) + [Tailwind CSS v4](https://tailwindcss.com). No client-side JavaScript, fully static, dark-mode aware.

## Structure

| Page | Purpose |
|---|---|
| `/` | Positioning + proof points (Woo enterprise CS, WordCamp EU/US 2024, 10+ years in WordPress) |
| `/about/` | The story: welding inspector → WordPress 2013 → PMPro → WooCommerce, as a timeline |
| `/speaking/` | Talks (WCUS 2024, WCEU 2024, Do the Woo) + "invite me to speak" topics |
| `/writing/` | Markdown blog (`src/content/blog/`), with RSS at `/rss.xml` |
| `/contact/` | Email + social channels |

Global: per-page OG/meta tags, sitemap, and `Person` JSON-LD (`sameAs` linking GitHub / X / LinkedIn / WordPress.org profiles) so search engines connect the profiles.

## Development

```sh
npm install
npm run dev      # http://localhost:4321
npm run build    # static output in dist/
npm run preview
```

## Publishing a post

Add a Markdown file to `src/content/blog/`:

```md
---
title: 'Post title'
description: 'One-sentence summary used on cards, meta tags, and RSS.'
pubDate: 2026-08-01
tags: ['ecommerce']
draft: false
---

Post body…
```

The three seeded posts are **starter drafts written on Travis's behalf**. Edit freely before promoting the site.

## Deploying

A GitHub Pages workflow (`.github/workflows/deploy.yml`) deploys on push to `main` (enable **Settings → Pages → Source: GitHub Actions**). The site also works as-is on Cloudflare Pages or Netlify (build command `npm run build`, output `dist/`).

`astro.config.mjs` sets `site: 'https://travislima.com'`. Update it if deploying to a different domain first (e.g. a `*.github.io` preview needs `site` + `base` adjusted).

## Still to do (deliberately not in v1)

- Real headshot/photos (photo slots use a monogram for now)
- Confirm the WordCamp Europe 2024 talk title on `/speaking/`
- DNS cutover of travislima.com; consolidate travislima.blog posts
- Newsletter signup, speaker kit PDF, testimonials
