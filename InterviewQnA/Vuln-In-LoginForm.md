# Vulnerabilities in Web Login Pages

Web login pages, often the entry point for authentication, are prime targets for attackers. They can be tested using Burp Suite in **passive mode** (no interaction with the server, just observing requests/responses via the Proxy/Logger for info leaks or misconfigs) or **active mode** (using Scanner, Intruder, or Repeater to send modified payloads and probe responses).

## Unauthenticated Based:

1. Username Enumeration
Definition: Identify valid usernames by differing responses/timings — Testable on login page: Yes (Unauth).
Example Command: curl -i -X POST https://target/login -d "username=alice&password=wrong"


2. Weak Password Policy / Brute Force
Definition: Absence of rate-limiting or weak password rules allowing automated guessing — Testable on login page: Yes (Unauth).
Example Command: hydra -L users.txt -P passwords.txt target http-post-form "/login:username=^USER^&password=^PASS^:F=incorrect"


3. SQL Injection (Login Bypass)
Definition: Unsanitized login inputs allow SQL payloads to alter auth logic — Testable on login page: Yes (Unauth).
Example Command: curl -X POST https://target/login -d "username=admin' OR '1'='1'&password=x"


4. Information Disclosure / Verbose Errors
Definition: Error messages reveal DB/stack info that helps crafting exploits — Testable on login page: Yes (Unauth).
Example Command: curl -i -X POST https://target/login -d "username=' OR 1=1--&password=x" -v


5. Missing Security Headers / HTTPS Misconfig
Definition: Lack of HSTS/CSP/X-Frame-Options or TLS issues exposing creds — Testable on login page: Yes (Unauth).
Example Command: curl -I https://target/login


6. CAPTCHA Bypass or Absence
Definition: No or weak CAPTCHA allows automated submissions — Testable on login page: Yes (Unauth).
Example Command: burp intruder replay login requests ignoring captcha tokens


7. Insecure Credential Transmission
Definition: Credentials sent in cleartext or weakly encoded over HTTP — Testable on login page: Yes (Unauth).
Example Command: proxy intercept POST /login (inspect body for plaintext)


8. Clickjacking (Frameable Login Page)
Definition: Page can be framed due to missing X-Frame-Options allowing UI redress — Testable on login page: Yes (Unauth).
Example Command: curl -I https://target/login | grep -i X-Frame-Options


9. Forgot Password / Reset Token Weaknesses
Definition: Predictable or enumerable reset tokens or email enumeration via reset form — Testable on login page: Yes (Unauth via reset endpoint).
Example Command: curl -X POST https://target/reset -d "email=alice@example.com"


10. XSS in Login Fields (Reflected)
Definition: Unsanitized echoes in error messages allow injected scripts to run — Testable on login page: Yes (Unauth).
Example Command: curl -X POST https://target/login -d "username=<script>alert(1)</script>&password=x"


11. Session Fixation / PreSet Session ID
Definition: Session ID not regenerated on login allowing attacker-supplied session reuse — Testable on login page: Yes (Unauth→Auth flow).
Example Command: Set-Cookie: sessionid=attacker; then POST /login using same cookie


## Authentication Based:

12. Broken Authentication (Session Hijacking via flags/predictable IDs)
Definition: Cookies missing Secure/HttpOnly or predictable session IDs enable theft/guessing — Testable on login page: Yes (post-login cookie inspect).
Example Command: curl -I https://target/login | grep -i Set-Cookie


13. IDOR (Insecure Direct Object Ref) — post-login
Definition: Changing identifiers after auth returns other users' data — Testable on login page: Needs valid creds (With Credentials).
Example Command: GET /profile?id=100 then change id to 101


14. CSRF on Login-Dependent Actions
Definition: Absence of anti-CSRF tokens on state-changing actions performed when logged in — Testable on login page: Requires login to test protected actions (With Credentials).
Example Command: Replay POST /account/change-email without CSRF token


15. Autofill or Cached Credential Exposure
Definition: Browser autofill or cache headers cause creds to be stored on client or intermediary caches — Testable on login page: Yes (Unauth to inspect headers/HTML).
Example Command: curl -s https://target/login | grep -i cache-control


16. MFA Bypass or Weak Implementation
Definition: Flawed MFA flows or optional/skip-able MFA allowing bypass — Testable on login page: Requires valid creds & MFA flow (With Credentials).
Example Command: Attempt session reuse or bypass POST /mfa/verify with crafted requests


17. Logout Functionality Flaws
Definition: Logout not revoking session server-side leaving session valid — Testable on login page: Requires login (With Credentials).
Example Command: Login -> Logout -> re-use cookie to access protected page


18. Password Change Vulnerabilities
Definition: Weak change-password flows (no old password check, weak validation) enabling account takeover — Testable on login page: Requires login (With Credentials).
Example Command: POST /change-password with new_password=abc123 without providing old_password




---
