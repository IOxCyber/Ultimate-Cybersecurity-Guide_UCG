## 1. Crawl Scope:
| Option Name                                               | What It Does                                                                                     | Use When                                                             | Example                                                                                                                                     |
| --------------------------------------------------------- | ------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- |
| **Limit at or below URL hostname**                        | Crawls all pages on the **same hostname**, regardless of path, **HTTP/HTTPS**, and **port**.     | You want to scan the full website (regardless of paths or ports).    | For `https://shop.example.com/login`, it will crawl: `https://shop.example.com/checkout`, `http://shop.example.com:8080/api`, etc.          |
| **Limit to content located at or below URL subdirectory** | Crawls **only within the given directory path** and below, regardless of hostname or subdomains. | You're testing only one **module or section** of the site.           | For `https://www.example.com/app/`, it crawls: `https://www.example.com/app/login`, `app/dashboard`, etc., but **not** `/about` or `/admin` |
| **Limit to URL hostname and specified sub-domain**        | Crawls only the hostname and **one additional subdomain** (you must specify it).                 | Your app interacts across the main domain + 1 subdomain (e.g., API). | Start URL: `https://example.com` with `api.example.com` as allowed → crawls only those two                                                  |
| **Limit to URL hostname and specified domains**           | Allows crawling the hostname and **specific domains you list** (multiple).                       | Needed when app spans across different domains (e.g., SSO, CDNs).    | Host: `example.com`, allow also `auth.example.com`, `cdn.example.net`                                                                       |


## 2. Detection Scope:
| **Option**              | **Meaning (Concise)**                                                              |
| ----------------------- | ---------------------------------------------------------------------------------- |
| **Core**                | Scans for the most common modern web vulnerabilities; default & balanced.          |
| **Categories**          | Lets you choose specific vulnerability types (e.g., SQLi, Auth, etc.) to scan for. |
| **Custom Search Lists** | Gives fine-tuned control by including/excluding specific vulns via search lists.   |
| **XSS Power Mode**      | Deep XSS scan using both common and advanced payloads for harder-to-spot XSS.      |
| **Everything**          | Full scan — detects every vulnerability WAS is capable of identifying.             |
