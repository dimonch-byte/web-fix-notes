---
title: "Security headers on Vercel and Netlify: a safe baseline"
---
# Security headers on Vercel and Netlify: a safe baseline

In our homepage scan of the top 1,500 Tranco domains, 67.2% sent HSTS, 52.3% nosniff, 29.1% Referrer-Policy and 15.2% Permissions-Policy. Static hosts send few of these by default.

**Vercel** (`vercel.json`):
```json
{"headers":[{"source":"/(.*)","headers":[
 {"key":"Strict-Transport-Security","value":"max-age=31536000; includeSubDomains"},
 {"key":"X-Content-Type-Options","value":"nosniff"},
 {"key":"Referrer-Policy","value":"strict-origin-when-cross-origin"},
 {"key":"Permissions-Policy","value":"camera=(), microphone=(), geolocation=()"},
 {"key":"X-Frame-Options","value":"SAMEORIGIN"}]}]}
```
**Netlify** (`_headers`):
```
/*
  Strict-Transport-Security: max-age=31536000; includeSubDomains
  X-Content-Type-Options: nosniff
  Referrer-Policy: strict-origin-when-cross-origin
  Permissions-Policy: camera=(), microphone=(), geolocation=()
  X-Frame-Options: SAMEORIGIN
```
CSP: start with `Content-Security-Policy-Report-Only` built from what your pages actually load; enforcing a guessed CSP breaks sites. Headers are one layer, not a security audit.

Free: [headers-baseline](https://github.com/dimonch-byte/headers-baseline) shows which of these your site sends.

---
*Disclosure: I build [Headerkit](https://headerkit.adjudi.com/?utm_source=github-pages&utm_medium=article&utm_campaign=headerkit-intent-w2&utm_content=vercel-netlify-headers), a $29 one-time pack that writes host-specific baselines from a crawl of your site. Its free check only offers the pack when it confirms the problem on your page. Everything above works without it.*
