---
title: "Gmail/Yahoo one-click unsubscribe: what the headers must look like (RFC 8058)"
---
# Gmail/Yahoo one-click unsubscribe: what the headers must look like (RFC 8058)

Since 2024 Gmail and Yahoo expect bulk senders to support one-click unsubscribe. A footer link is not enough; it's two headers, signed.

```
List-Unsubscribe: <https://example.com/u?token=...>, <mailto:unsub@example.com>
List-Unsubscribe-Post: List-Unsubscribe=One-Click
```
Requirements (RFC 8058):
- at least one **https** URI in `List-Unsubscribe` (mailto alone is not one-click);
- `List-Unsubscribe-Post: List-Unsubscribe=One-Click` exactly;
- your endpoint accepts a **POST** with that body and unsubscribes without a confirmation page or login;
- the DKIM signature's `h=` covers **both** headers.

Most ESPs (SendGrid, Mailgun, Postmark, SES) add these for marketing streams but not necessarily for transactional/raw sends you route as bulk. Check a real received message ("Show original").

Free: [oneclick-check](https://github.com/dimonch-byte/oneclick-check) — paste the raw headers, get pass/fail per requirement. Passing headers don't guarantee inbox placement.

---
*Disclosure: I build [Oneclickout](https://oneclickout.adjudi.com/?utm_source=github-pages&utm_medium=article&utm_campaign=oneclickout-intent-w2&utm_content=rfc8058), a $29 one-time pack that gives the exact per-ESP fix for your headers. Its free check only offers the pack when it confirms the problem on your page. Everything above works without it.*
