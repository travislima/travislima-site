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

A GitHub Pages workflow (`.github/workflows/deploy.yml`) deploys on push to `main`. Current setup: **github.io preview**.

One-time repo settings (done in the GitHub UI):

1. Rename the repo to `travislima.github.io` (Settings → General → Repository name), so the site serves at the root URL with no base-path changes.
2. Enable Pages: Settings → Pages → Build and deployment → Source: **GitHub Actions**.

After that, every push to `main` deploys to `https://travislima.github.io/`.

### Later: moving to travislima.com

1. In Settings → Pages, set **Custom domain** to `travislima.com` (or commit a `public/CNAME` file containing `travislima.com`).
2. At the domain registrar, point `travislima.com` A records to `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`, and add a `www` CNAME to `travislima.github.io`.
3. Set `site: 'https://travislima.com'` in `astro.config.mjs` and push.
4. Enable **Enforce HTTPS** in Pages settings once the certificate is issued.

The site also works as-is on Cloudflare Pages or Netlify (build command `npm run build`, output `dist/`).

## Still to do (deliberately not in v1)

- Real headshot/photos (photo slots use a monogram for now)
- Confirm the WordCamp Europe 2024 talk title on `/speaking/`
- DNS cutover of travislima.com; consolidate travislima.blog posts
- Newsletter signup, speaker kit PDF, testimonials
