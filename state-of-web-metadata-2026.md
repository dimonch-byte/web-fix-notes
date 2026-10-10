---
title: "State of share cards, icons and security headers (Oct 2026)"
---
# State of share cards, icons and security headers (Oct 2026)
**Method.** On 2026-10-10 we requested the homepage (one GET of `https://domain/`) of the first 1,500 domains in the Tranco top-1M list. 835 returned an HTML 200; the rest are CDNs, APIs or redirects/blocks. We parsed `<meta>`/`<link>` tags and response headers. No other paths were requested, nothing was probed, and no per-site results are published or kept. Homepages of very large sites are not typical of small sites; treat these as a floor.

| Signal | % of HTML homepages |
|---|---|
| has og:image | 64.0 |
| og:image is a relative URL (of all pages) | 3.1 |
| og:image width/height declared | 20.5 |
| has twitter:card | 54.4 |
| declares any icon | 86.7 |
| has apple-touch-icon | 56.6 |
| has web app manifest | 30.8 |
| Strict-Transport-Security | 67.2 |
| X-Content-Type-Options | 52.3 |
| Referrer-Policy | 29.1 |
| Content-Security-Policy (enforced) | 46.7 |
| CSP Report-Only | 7.1 |
| Permissions-Policy | 15.2 |

**Takeaways.** A third of the most-visited homepages ship no og:image, four in five omit image dimensions, nearly half have no apple-touch-icon, and most don't send Referrer-Policy or Permissions-Policy. If the biggest sites miss these, small sites almost certainly do.

Check your own: [og-lint](https://dimonch-byte.github.io/og-lint/) · [favicon-audit](https://github.com/dimonch-byte/favicon-audit) · [headers-baseline](https://github.com/dimonch-byte/headers-baseline). Raw aggregate: [aggregate.json](aggregate.json).

*Disclosure: I build paid fix packs for some of these ([SharePack](https://sharepack.adjudi.com/?utm_source=github-pages&utm_medium=article&utm_campaign=sharepack-intent-w2&utm_content=state-report), IconPack, HeaderKit). The data above is not a ranking or a compliance measure.*
