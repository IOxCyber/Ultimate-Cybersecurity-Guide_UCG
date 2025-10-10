## Below Options can be enabled when setting up an App for Scan.

# WAS > Web App > Authentication Record

1. Authentication Records — Store and replay login flows/credentials so the scanner can test authenticated fields. `USE NON-PRIVILEGE ACCOUNTS.`
- Using Records Methods:
1. Form Authentication:
    - HTTP Form-based Authentication (Standard login, Username & Password) - Same Domain
    - Custom Authentication (Non standard login field with additional fields like Tokens, 2FA or hidden fields)
    - Selenium Script (Complex Set Up, record the login process & upload it)

2. OAuth2 Authentication:
- Authentication Code (for server side app, Uses 3rd Party to login)
- Implicit(For client side Mobile or Web apps running in Browsers)
- Client Credentials (for apps where No User interaction required like HR portals)
- Resource Owner Password Credentials (When Creds exchanged for Tokens by the App)

3. Server Records:
- Basic (Encoded Creds)
- Digest (Hashed Creds)
- NTLM (Windows Integrated Enterprise Auth)

2. Header Injection:
- Configure custom HTTP headers to be added/overridden on requests made by the scanner.
- Useful to exercise header-based logic, test WAF rules, and check how app reacts to modified headers.

3. API Endpoint Definition:
- Explicitly `declare REST API endpoints (method, params, body, headers) Using Postman collection, Burp Proxy Capture, Swagger/OpenAPI File.` so the scanner can exercise APIs properly instead of only crawling HTML links.


4. Set Up Exclusion Lists
- Controls which URLs/parameters the scanner should skip (exclude) or only scan (allow list). 
- By Using regex or explicit URLs.

5. Default DNS Override:
- Make WAS resolve a host to a different IP than public DNS (overrides DNS resolution for the scan).

6. Redundant Links:
- Tell the crawler that certain URL patterns are duplicates or redundant so it avoids repeated crawling of similar pages that create noise and duplicate findings.
- Links can be specify as Regex to match a list of links.

eg. http://www.example.com/products/prod[1-99].html

7. Path Fuzzing Rules:
- Supply wordlists and rules to brute-force hidden files/directories and endpoints in {Url Rewriting} to perform fault injection tests (SQLi, XSS etc)

eg. http://www.abc/issue/{issue}/section/{section}/article/{article}
- Wordlist: admin, backup.zip, config.php, .git/, api/v1/login
- Template: /api/v1/{entity}/{id} where entity = users, orders and id = 1..100

8. Form Training:
- A process where `WAS learns how forms behave in your application & how to fill them, what hidden fields exist, how CSRF tokens are handled, how to submit multi-step forms` — so the scanner can exercise them properly.

9. Malware Monitoring:
- Detects the injected scripts, malware based on Behaviour & signatures on the web page and send Alerts via Emails.