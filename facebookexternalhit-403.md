---
title: "facebookexternalhit gets 403 but the page loads for me"
---
# facebookexternalhit gets 403 but the page loads for me

The Sharing Debugger says "Bad Response Code 403", yet the page opens fine. Almost always: something in front of your origin treats the crawler as a bot (because it is one).

**Confirm:** `curl -s -o /dev/null -w "%{http_code}\n" -A "facebookexternalhit/1.1 (+http://www.facebook.com/externalhit_uatext.php)" https://your-site/page` — compare with a browser UA.

**Usual culprits and fixes**
- Cloudflare Bot Fight Mode / Super Bot Fight Mode: Bot Fight Mode can't be bypassed per-path on free plans; turn it off or use a WAF skip rule for verified bots (`cf.client.bot`) where your plan allows.
- Vercel/Netlify firewall or attack-challenge mode: add an allow rule for the social crawler user agents, or turn the challenge off for public pages.
- `robots.txt` disallowing `/` for `*`: Facebook honors robots for some fetches; allow `facebookexternalhit`, `Twitterbot`, `LinkedInBot`, `Slackbot`, `Discordbot`.
- Hotlink protection on the image host: the HTML may pass while the `og:image` URL 403s. Test the image URL too.

Then re-scrape in the Sharing Debugger.

---
*Disclosure: I build [SharePack](https://sharepack.adjudi.com/?utm_source=github-pages&utm_medium=article&utm_campaign=sharepack-intent-w2&utm_content=fb-403), a $29 one-time pack that shows exactly what each of five real crawlers gets back from your page and generates the fix. Its free check only offers the pack when it confirms the problem on your page. Everything above works without it.*
