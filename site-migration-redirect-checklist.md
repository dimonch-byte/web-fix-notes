---
title: "Site migration: find every old URL that will 404 before launch"
---
# Site migration: find every old URL that will 404 before launch

Most migration traffic losses are plain 404s on old URLs that had links. Before you switch DNS:

1. Export the **old** URL list: old sitemap, plus analytics' top landing pages, plus Search Console's linked pages (sitemaps miss things).
2. Export the **new** sitemap from staging.
3. Diff the paths. Every old path without an identical new one needs a 301 to its closest equivalent, not to the homepage.
4. Write rules in your host's format (Netlify `_redirects`, `vercel.json` redirects, nginx `return 301`, Cloudflare bulk redirects) and avoid chains.
5. After launch, request a sample of old URLs and confirm one hop to a 200.

Free: [redirect-diff](https://github.com/dimonch-byte/redirect-diff) does step 3 from two sitemaps or URL lists. Redirects keep links working; they're not a ranking guarantee.

---
*Disclosure: I build [Routepatch](https://routepatch.adjudi.com/?utm_source=github-pages&utm_medium=article&utm_campaign=routepatch-intent-w2&utm_content=migration-checklist), a $49 one-time pack that turns the gap into a host-ready redirect map. Its free check only offers the pack when it confirms the problem on your page. Everything above works without it.*
