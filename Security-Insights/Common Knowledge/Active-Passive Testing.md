# Passive vs Active Testing (VAPT) — Quick Reference (BurpSuite)

| Testing Type     | What (Purpose)                                                                 | Why (Use of it)                                                     | Examples / Methods                                                                 | Extras (Alternatives & Notes)                                                                 |
|------------------|---------------------------------------------------------------------------------|----------------------------------------------------------------------|------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------|
| Passive Testing  | Understanding the application's behavior, structure and logic without altering it. | To collect intelligence safely for reconnaissance and planning.      | HTTP request/response observation, Missing Security Headers, Insecure Cookies (eg. missing httponly, Secure, Samesite), Information Disclosure (server banners), Unencrypted Login Forms. | Non-intrusive and silent; tools: Burp Proxy (passive), Wappalyzer, WhatWeb; doesn't change server state. |
| Active Testing   | Interacting directly with the app using crafted inputs to find vulnerabilities.     | To verify, exploit and confirm security weaknesses with proof-of-concept. | SQLi, XSS, CSRF testing, authentication/authorization/session checks, input validation tests, API fuzzing, weak passwords, Session Fixation | Noisy/verbose and may trigger alerts; tools: Burp Intruder, SQLMap, wfuzz, OWASP ZAP Active Scan. |

**Key note:** Always perform Passive reconnaissance before Active testing to target your tests and reduce unnecessary noise.
---

🧠 Key Insights (Keep it crisp & practical)

1. Passive = Observation mode → Like a spy listening to conversations. (No Payload Sent)


2. Active = Engagement mode → Like a hacker testing the locks. (With Payload Sent)


3. Passive gives intel, Active gives proof.


4. Use Passive before Active — it helps you plan precise attacks and avoid unnecessary noise.


---

Real-Life Implementation

Passive: While mapping Uber’s APIs, a tester observes traffic using Burp Proxy to note hidden endpoints and headers.

Active: Later, the tester fuzzes those endpoints to check for IDOR or injection flaws.