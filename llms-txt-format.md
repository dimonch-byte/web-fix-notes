---
title: "llms.txt format: a minimal valid example"
---
# llms.txt format: a minimal valid example

`/llms.txt` (proposed at llmstxt.org) is a Markdown file describing your site for language-model tools.
```markdown
# Acme Docs
> One-sentence summary of what this site is.

## Docs
- [Quick start](https://acme.dev/start): install and first run
- [API](https://acme.dev/api): endpoints

## Optional
- [Changelog](https://acme.dev/changelog)
```
Common mistakes: serving your SPA's `index.html` at `/llms.txt` (status 200 but HTML), no H1, no link lines. Nobody can promise that an llms.txt gets you cited or ranked; it's a cheap, honest description of your site.

Free: [llms-txt-check](https://github.com/dimonch-byte/llms-txt-check) checks the shape.

---
*Disclosure: I build [Citekit](https://citekit.adjudi.com/?utm_source=github-pages&utm_medium=article&utm_campaign=citekit-intent-w2&utm_content=llms-format), a $19 one-time pack that generates llms.txt plus FAQ and Organization JSON-LD from your pages. Its free check only offers the pack when it confirms the problem on your page. Everything above works without it.*
