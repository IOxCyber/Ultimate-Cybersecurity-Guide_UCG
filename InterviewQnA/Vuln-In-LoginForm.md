# Vulnerabilities in Web Login Pages

Web login pages, often the entry point for authentication, are prime targets for attackers. They can be tested using Burp Suite in **passive mode** (no interaction with the server, just observing requests/responses via the Proxy/Logger for info leaks or misconfigs) or **active mode** (using Scanner, Intruder, or Repeater to send modified payloads and probe responses).


## Without Credentials (Unauthenticated Access - Focus on Public-Facing Login Form)

- Username Enumerate
- Brute Force/No Rate Limiting
- Login Bypass via Sqli
- XSS in Login
- 

These are testable by anyone intercepting or submitting to the login endpoint.

1. **Username Enumeration/Brute Force**  
   - **Description**: Server responses differ based on whether a username exists (e.g., "Invalid password" vs. "Invalid username"), allowing attackers to harvest valid usernames.  
   - **Burp Detection**: Passive - Observe response messages/timing in Proxy history for failed logins. Active - Use Intruder with username wordlists to compare responses (e.g., status codes, body length).  
   - **Impact**: Aids brute-force or targeted attacks.

2. **Weak Password Policy / Brute Force Vulnerability**  
   - **Description**: No rate limiting, allowing automated guessing of credentials; or acceptance of weak passwords (e.g., "123456").  
   - **Burp Detection**: Active - Intruder for brute-force attacks with payload lists (e.g., common passwords); check for no lockouts. Passive - N/A directly, but note absence of CAPTCHA in responses.  
   - **Impact**: Account takeover via automation.

3. **SQL Injection (in Login Fields)**  
   - **Description**: Unsanitized inputs (username/password) allow database manipulation (e.g., `' OR '1'='1` bypasses auth).  
   - **Burp Detection**: Active - Scanner auto-probes with injection payloads; or Repeater to test error messages (e.g., SQL errors). Passive - Look for database errors in responses.  
   - **Impact**: Unauthorized access or data dump.

4. **Information Disclosure / Verbose Error Messages**  
   - **Description**: Errors reveal tech stack (e.g., "MySQL syntax error") or internal details on invalid inputs.  
   - **Burp Detection**: Passive - Logger/Proxy captures response bodies for leaks (e.g., stack traces). Active - Scanner forces errors with malformed inputs.  
   - **Impact**: Helps attackers craft exploits.

5. **Missing Security Headers / HTTPS Misconfig**  
   - **Description**: Lack of HSTS, CSP, or X-Frame-Options; or HTTP instead of HTTPS exposing credentials in transit.  
   - **Burp Detection**: Passive - Target site map or HTTP history shows headers (or lack thereof). Active - N/A, but Scanner reports misconfigs.  
   - **Impact**: MITM attacks or clickjacking.

6. **CAPTCHA Bypass or Absence**  
   - **Description**: No protection against bots, or weak CAPTCHA easily solvable.  
   - **Burp Detection**: Active - Intruder to replay submissions ignoring CAPTCHA; test rate limits. Passive - Inspect HTML for CAPTCHA implementation flaws.  
   - **Impact**: Amplifies brute-force.

7. **Insecure Credential Transmission**  
   - **Description**: Passwords sent in plain text or weak encoding (e.g., Base64) over HTTP.  
   - **Burp Detection**: Passive - Proxy intercepts requests to see parameters (e.g., POST body). Active - N/A.  
   - **Impact**: Eavesdropping on credentials.

8. **Clickjacking (Frameable Login Page)**  
   - **Description**: Page can be iframed, tricking users into clicking hidden elements.  
   - **Burp Detection**: Passive - Check for X-Frame-Options header absence. Active - Scanner simulates framing.  
   - **Impact**: UI redressing attacks.

9. **Forgot Password / Reset Token Weaknesses**  
   - **Description**: Weak tokens (predictable) or rate-unlimited requests leaking user info.  
   - **Burp Detection**: Active - Scanner/Intruder tests token predictability or enumeration via email fields. Passive - Response differences on invalid emails.  
   - **Impact**: Account hijacking.

10. **XSS (Cross-Site Scripting) in Login Fields**  
    - **Description**: Reflected XSS via inputs echoed in errors (e.g., `<script>alert(1)</script>` in username).  
    - **Burp Detection**: Active - Scanner injects payloads; Repeater verifies execution. Passive - Rare, but spot unsanitized echoes.  
    - **Impact**: Session theft if it steals cookies.

## With Credentials (Authenticated Access - Post-Login Testing)

- Session Fixation (PreSet Session ID)
- Security Headers
- IDOR (Prev. Escalation)

These require valid logins (or bypassing auth via above vulns). Use Burp after authenticating: scope the session cookie, then scan authenticated areas. Active for probing; passive for session analysis.

1. **Session Fixation / Weak Session Management**  
   - **Description**: Pre-set session IDs aren't invalidated on login, allowing fixation attacks.  
   - **Burp Detection**: Passive - Compare pre/post-login cookies in Proxy. Active - Repeater to reuse old sessions post-login.  
   - **Impact**: Impersonation without credentials.

2. **Broken Authentication (e.g., Session Hijacking)**  
   - **Description**: Cookies lack HttpOnly/Secure flags, or predictable IDs.  
   - **Burp Detection**: Passive - Inspect Set-Cookie headers for flags/timing attacks. Active - Intruder guesses session IDs.  
   - **Impact**: Stolen sessions via XSS or MITM.

3. **IDOR (Insecure Direct Object References) Post-Login**  
   - **Description**: After login, accessing other users' data by tweaking IDs (e.g., `/profile?id=123` to 456).  
   - **Burp Detection**: Active - Scanner/Repeater modifies parameters with known IDs. Passive - N/A.  
   - **Impact**: Data leakage between accounts.

4. **CSRF (Cross-Site Request Forgery) on Login-Dependent Actions**  
   - **Description**: No anti-CSRF tokens, allowing forged requests post-login (e.g., change password).  
   - **Burp Detection**: Active - Scanner checks token absence; generate POC. Passive - HTML responses lack tokens.  
   - **Impact**: Unauthorized actions as logged-in user.

5. **Autofill or Cached Credential Exposure**  
   - **Description**: Browser autofill exposes creds, or pages cache sensitive data.  
   - **Burp Detection**: Passive - Responses with Cache-Control headers allowing storage. Active - N/A directly.  
   - **Impact**: Local theft on shared devices.

6. **MFA Bypass or Weak Implementation**  
   - **Description**: MFA not enforced, or codes sent insecurely (e.g., via URL params post-login).  
   - **Burp Detection**: Active - Intruder tests bypassing MFA flows. Passive - Observe MFA prompts/responses.  
   - **Impact**: Reduces auth strength.

7. **Logout Functionality Flaws**  
   - **Description**: Incomplete logout (sessions persist) or no revocation.  
   - **Burp Detection**: Active - Repeater reuses cookies after logout. Passive - Compare session behavior.  
   - **Impact**: Persistent access.

8. **Password Change Vulnerabilities**  
   - **Description**: No old password check, or weak hashing visible in responses.  
   - **Burp Detection**: Active - Scanner probes change endpoints. Passive - Leaks in error messages.  
   - **Impact**: Easy compromise escalation.

## Tips for Burp Suite Testing

- **Setup**: Use Burp Proxy to intercept traffic; authenticate once and extend session cookies to scope.
- **Passive Scan**: Enable in Proxy > Options > Passive Scanning for automatic header/input analysis—no risk of disruption.
- **Active Scan**: Right-click login request in site map > "Do active scan"; customize for auth by adding session cookies. Use cautiously on production!
- **Best Practices**: Always get permission (e.g., bug bounty scopes). Combine with manual testing for false positives. Reference OWASP Testing Guide (WSTG-ATHN) for checklists.


> Burp Extensions like "AuthMatrix" for auth testing or "Logger++" for better passive logs.