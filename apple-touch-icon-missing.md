---
title: "Missing apple-touch-icon, manifest icons and favicon.ico: the minimal set"
---
# Missing apple-touch-icon, manifest icons and favicon.ico: the minimal set

In our scan of the top 1,500 Tranco domains, 43% of HTML homepages declared no `apple-touch-icon` and 69% had no web app manifest. Without them, iOS saves a screenshot to the home screen and Android shows a generic letter.

Minimal set that covers almost everything:
```html
<link rel="icon" href="/favicon.ico" sizes="32x32">
<link rel="icon" href="/icon.svg" type="image/svg+xml">
<link rel="apple-touch-icon" href="/apple-touch-icon.png"><!-- 180×180, no transparency -->
<link rel="manifest" href="/manifest.webmanifest"><!-- icons 192 and 512, plus a 512 maskable -->
```
Keep `/favicon.ico` at the root even if you declare others; some clients request it blindly. Start from a square source image of at least 512×512.

Free: [favicon-audit](https://github.com/dimonch-byte/favicon-audit) lists what your homepage declares and whether each loads.

---
*Disclosure: I build [Iconpack](https://iconpack.adjudi.com/?utm_source=github-pages&utm_medium=article&utm_campaign=iconpack-intent-w2&utm_content=apple-touch), a $19 one-time pack that generates the full icon set from your site. Its free check only offers the pack when it confirms the problem on your page. Everything above works without it.*
