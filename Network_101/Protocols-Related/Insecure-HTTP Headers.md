
### HTTP Security Headers:

HTTP headers are metadata sent by the server to the client (browser). Some of them enhance **security**, but when **missing or misconfigured**, they can lead to vulnerabilities.

---

### Common Insecure or Missing HTTP Headers

| **Header** | **Insecure or Missing Example** | **Why It Matters (Vulnerability)** | **Secure Value Example** |
|------------|-------------------------------|------------------------------------|---------------------------|
| `Strict-Transport-Security (HSTS)` | Not set | Downgrade attacks, MITM | `Strict-Transport-Security: max-age=63072000; includeSubDomains; preload` |
| `X-Content-Type-Options` | Not set | MIME-sniffing can cause XSS | `X-Content-Type-Options: nosniff` |
| `X-Frame-Options` | `ALLOWALL` or missing | Clickjacking | `X-Frame-Options: DENY` or `SAMEORIGIN` |
| `Content-Security-Policy (CSP)` | `default-src *` or missing | XSS, data injection | `Content-Security-Policy: default-src 'self';` |
| `X-XSS-Protection` | `0` or missing | XSS in older browsers | `X-XSS-Protection: 1; mode=block` *(deprecated in modern browsers)* |
| `Referrer-Policy` | Not set | URL leakage in Referer header | `Referrer-Policy: no-referrer` or `strict-origin-when-cross-origin` |
| `Permissions-Policy` | Not set | Access to sensitive features | `Permissions-Policy: camera=(), geolocation=(), microphone=()` |
| `Cross-Origin-Embedder-Policy` | Not set | Unsafe cross-origin loading | `Cross-Origin-Embedder-Policy: require-corp` |
| `Cross-Origin-Resource-Policy` | Not set | Cross-origin resource theft | `Cross-Origin-Resource-Policy: same-origin` |
| `Access-Control-Allow-Origin` | `*` (wildcard) | CORS abuse, data exfiltration | `Access-Control-Allow-Origin: https://yourdomain.com` |
| `Expect-CT` | Not set | Lack of cert transparency monitoring | `Expect-CT: max-age=86400, enforce, report-uri="https://yourdomain.com/report"` |
| `Cache-Control` | `public` or missing | Sensitive data stored in cache | `Cache-Control: no-store, no-cache, must-revalidate, private` |
| `Pragma` | Not set | May cache sensitive responses | `Pragma: no-cache` |
| `Expires` | Not set | Cached data may be reused | `Expires: 0` |
| `Server` | `Server: Apache/2.4.18 (Ubuntu)` | Server fingerprinting | Omit entirely or generalize: `Server: Secure` |
| `X-Powered-By` | `X-Powered-By: PHP/7.4.3` | Tech disclosure aids attackers | Remove or mask: `X-Powered-By: ` |
| `Set-Cookie` (flags) | Cookies without `HttpOnly`, `Secure` | Cookie theft (XSS), MITM | `Set-Cookie: sessionid=abc123; HttpOnly; Secure; SameSite=Strict` |
| `Feature-Policy` *(Deprecated)* | Not set | Modern browsers now use `Permissions-Policy` | Migrate to `Permissions-Policy` |

---

- **Minimal Must-Have Set**:
   - `Strict-Transport-Security`
   - `X-Content-Type-Options`
   - `X-Frame-Options`
   - `Content-Security-Policy`
   - `Set-Cookie` with all flags

### Real-World Risks When These Are Misconfigured:

1. **Clickjacking**: Without `X-Frame-Options`, your site can be embedded and trick users into clicking invisible buttons.
2. **XSS**: No `CSP` + bad input sanitization = open for JavaScript injection.
3. **MITM (Man-in-the-middle)**: Without `HSTS`, attackers downgrade HTTPS to HTTP and intercept traffic.
4. **Data Exposure**: `Referrer-Policy` missing? Internal paths might leak to 3rd-party sites.
5. **Browser Exploits**: `Permissions-Policy` not used? Attackers can exploit features like webcam/mic.

---

### 🧪 How to Check for These?
- **Burp Suite** → Look in **HTTP Response** headers.
- **curl**:  
  ```bash
  curl -I https://example.com
  ```


- Add these headers in **Web Server config (Apache/Nginx)**, **CDN settings**, or **Web Application firewall**.
- Example (Nginx):
  ```nginx
  add_header X-Frame-Options "DENY";
  add_header X-Content-Type-Options "nosniff";
  add_header X-XSS-Protection "1; mode=block";
  add_header Strict-Transport-Security "max-age=63072000; includeSubDomains; preload";
  add_header Content-Security-Policy "default-src 'self';";
  ```
