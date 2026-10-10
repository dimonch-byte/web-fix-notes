---
title: "Block .env, .git and backup files on Apache and nginx"
---
# Block .env, .git and backup files on Apache and nginx

Deploys sometimes ship `.env`, `.git/`, `*.bak` or source maps into the web root. Check **your own** site, then deny them at the server.

**Apache (.htaccess)**
```apache
<FilesMatch "^\.(env|git|svn|hg|DS_Store)|\.(bak|old|orig|swp|sql|zip|tar|gz)$">
  Require all denied
</FilesMatch>
RedirectMatch 404 /\.git
```
**nginx**
```nginx
location ~ /\.(?!well-known) { deny all; return 404; }
location ~* \.(bak|old|orig|swp|sql)$ { deny all; return 404; }
```
Then: rotate any secret that was ever exposed (blocking doesn't un-leak it), and stop the files reaching the web root in the build.

Free: [leakdeny-check](https://github.com/dimonch-byte/leakdeny-check) checks your own origin by status only and never prints file contents. Only scan sites you own or are authorised to test.

---
*Disclosure: I build [Leakdeny](https://leakdeny.adjudi.com/?utm_source=github-pages&utm_medium=article&utm_campaign=leakdeny-intent-w2&utm_content=htaccess-nginx), a $29 one-time pack that detects which paths are exposed on your origin and gives exact Apache/nginx deny rules (plus Vercel/Netlify snippets; Caddy not supported). Its free check only offers the pack when it confirms the problem on your page. Everything above works without it.*
