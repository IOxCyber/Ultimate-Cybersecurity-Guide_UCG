## 1. Fault injection vs. Manual:
### Fault injection: `Automated Testing (Fast)`
- Injecting "specially crafted" character strings into application form fields and examining the application's responses to detect vulnerabilities. 
- Crafted according to Web app vulnerability data and information provided by OWASP, Web Application Security Consortium (WASC), and Common Weakness Enumeration (CWE).

### Manual: Thru Burp Integration (To discover Design flaws)

## 2. Crawl Scope:
| Option Name                                               | What It Does                                                                                     | Use When                                                             | Example                                                                                                                                     |
| --------------------------------------------------------- | ------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- |
| **Limit at or below URL hostname**                        | Crawls all pages on the **same hostname**, regardless of path, **HTTP/HTTPS**, and **port**.     | You want to scan the full website (regardless of paths or ports).    | For `https://shop.example.com/login`, it will crawl: `https://shop.example.com/checkout`, `http://shop.example.com:8080/api`, etc.          |
| **Limit to content located at or below URL subdirectory** | Crawls **only within the given directory path** and below, regardless of hostname or subdomains. | You're testing only one **module or section** of the site.           | For `https://www.example.com/app/`, it crawls: `https://www.example.com/app/login`, `app/dashboard`, etc., but **not** `/about` or `/admin` |
| **Limit to URL hostname and specified sub-domain**        | Crawls only the hostname and **one additional subdomain** (you must specify it).                 | Your app interacts across the main domain + 1 subdomain (e.g., API). | Start URL: `https://example.com` with `api.example.com` as allowed → crawls only those two                                                  |
| **Limit to URL hostname and specified domains**           | Allows crawling the hostname and **specific domains you list** (multiple).                       | Needed when app spans across different domains (e.g., SSO, CDNs).    | Host: `example.com`, allow also `auth.partner.com`, `cdn.example.net`                                                                       |


## 4. Detection Scope:
| **Option**              | **Meaning (Concise)**                                                              |
| ----------------------- | ---------------------------------------------------------------------------------- |
| **Core**                | Scans for the most common modern web vulnerabilities; default & balanced.          |
| **Categories**          | Lets you choose specific vulnerability types (e.g., SQLi, Auth, etc.) to scan for. |
| **Custom Search Lists** | Gives fine-tuned control by including/excluding specific vulns via search lists.   |
| **XSS Power Mode**      | Deep XSS scan using both common and advanced payloads for harder-to-spot XSS.      |
| **Everything**          | Full scan — detects every vulnerability WAS is capable of identifying.             |



## 4. WAS Workflow:
- The workflow for analyzing a Web application involves five simple
- Steps: `1) Define Web Application, 2) Perform Discovery Scan—Crawl, 3) Perform Vulnerability Scan, 4) Create Reports, and 5) Fix Vulnerabilities`
```
Here is a detailed view of this workflow:
1. Define Web Application
• Identify the location (URL) of the Web App
• Define the “scope” of the Web App Crawl
• Choose from various scanning options—Option Profile:
• Select a scanner appliance
• Include “crawling hints” and/or header injection
• Use optional DNS Override
• Provide authentication credentials
- Form records
- Server records
• Identify areas to “white list” or “black list”
• Enable malware monitoring
2. Perform Discovery Scan (Crawl)
3. Perform Vulnerability Scan
4. Create reports to identify links crawled and vulnerabilities detected
5. Fix vulnerabilities
```
