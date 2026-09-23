# icracontractor.com

Premium domain acquisition landing page for **[icracontractor.com](https://icracontractor.com)** — the exact-match `.com` brand for ICRA-specialized healthcare construction contractors.

## Stack

- [Astro](https://astro.build) 5 (static output) + Tailwind CSS
- Cloudflare Workers with static assets (`wrangler deploy`)

## SEO

- Optimized title (≤65 chars) and meta description (≤160 chars) with primary + commercial intent
- Canonical URL, `robots` meta, Open Graph, and Twitter Card markup
- JSON-LD structured data: `WebSite`, `WebPage`, `Product` + `Offer` (price matches visible content), `FAQPage`
- Sitemap: `/sitemap-index.xml` (via `@astrojs/sitemap`), declared in `robots.txt`
- 301 canonicalization handled in `src/worker.ts`:
  - `www` → apex, `http` → `https`
  - `/index.html` → `/`
  - extensionless paths → trailing slash
- `X-Robots-Tag: noindex` on `workers.dev` hosts and alternate URL variants (`/index.html`, `/404`)
- Security headers (HSTS, nosniff, frame options, referrer policy, permissions policy) applied in the Worker — required because `assets.run_worker_first = true` bypasses `_headers`/`_redirects`

## Conversion

- Above-the-fold "Secure This Domain" CTA + sticky mobile CTA
- Visible asking price aligned with `Offer` schema
- Inquiry form (FormSubmit → `sales@desertrich.com`) with honeypot spam trap and no-JS fallback
- Escrow / confidentiality / close-time trust signals
- FAQ section targeting long-tail ICRA and acquisition queries

## Develop

```bash
npm install
npm run dev      # local dev server
npm run build    # production build → dist/
npm run deploy   # wrangler deploy
```
