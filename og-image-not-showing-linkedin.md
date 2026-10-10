---
title: "og:image not showing on LinkedIn, Slack or Facebook: the 6 usual causes"
---
# og:image not showing on LinkedIn, Slack or Facebook: the 6 usual causes

Your page looks fine in a browser but the link preview is blank. Crawlers don't run your JavaScript and don't share your cookies, so check what *they* get.

1. **Relative `og:image`.** `content="/og.png"` works in some places and fails in others. Use an absolute `https://` URL. (In our homepage scan of the top 1,500 Tranco domains, 3.1% of HTML homepages used a relative og:image path.)
2. **No `og:image` at all** in the server-rendered HTML. If a client-side router injects tags after load, crawlers never see them. 36% of the HTML homepages we scanned had none.
3. **Bot blocked.** WAF/"bot fight" rules return 403 to `facebookexternalhit`, `LinkedInBot` or `Twitterbot` while humans get 200. Test: `curl -A "LinkedInBot/1.0" -I https://your-site/page`.
4. **Image URL returns HTML** (a login wall or SPA 404) instead of `image/png`/`image/jpeg`. `curl -I` the image URL with a bot UA and check `content-type`.
5. **Size/format.** Use 1200×630 PNG/JPEG under ~5 MB; some crawlers ignore SVG and are inconsistent with WebP. Add `og:image:width`/`height` so the first share renders (only 20.5% of scanned homepages did).
6. **Stale cache.** Re-scrape with the Facebook Sharing Debugger and LinkedIn Post Inspector after fixing.

Free tools: paste your `<head>` into [og-lint](https://dimonch-byte.github.io/og-lint/), or fail PRs with [og-lint-action](https://github.com/dimonch-byte/og-lint-action).

---
*Disclosure: I build [SharePack](https://sharepack.adjudi.com/?utm_source=github-pages&utm_medium=article&utm_campaign=sharepack-intent-w2&utm_content=og-not-showing), a $29 one-time pack that fetches your live page as Facebook, X, LinkedIn, Slack and Discord crawlers and generates the tags plus a correctly sized image set. Its free check only offers the pack when it confirms the problem on your page. Everything above works without it.*
