
### HTTP Security Headers:

HTTP headers are metadata sent by the server to the client (browser). Some of them enhance **security**, but when **missing or misconfigured**, they can lead to vulnerabilities.

---

### Common Insecure or Missing HTTP Headers

| **Header** | **Issue When Missing/Insecure** | **Why It Matters (Vulnerability)** | **Secure Value Example** |
|------------|----------------------------------|-------------------------------------|----------------------------|
| `Strict-Transport-Security (HSTS)` | Missing | Allows downgrade attacks (HTTPS → HTTP) | `Strict-Transport-Security: max-age=63072000; includeSubDomains; preload` |
| `X-Content-Type-Options` | Missing | MIME sniffing attacks | `X-Content-Type-Options: nosniff` |
| `X-Frame-Options` | Missing | Clickjacking | `X-Frame-Options: DENY` or `SAMEORIGIN` |
| `Content-Security-Policy (CSP)` | Missing or weak | XSS, data injection | `Content-Security-Policy: default-src 'self';` *(customize further)* |
| `X-XSS-Protection` | Not set or set to 0 | XSS attacks (older browsers) | `X-XSS-Protection: 1; mode=block` *(optional now)* |
| `Referrer-Policy` | Missing | Leaks internal URLs or sensitive info in referrer | `Referrer-Policy: no-referrer` or `strict-origin-when-cross-origin` |
| `Permissions-Policy` *(was Feature-Policy)* | Missing | Browser feature abuse (e.g., camera, mic) | `Permissions-Policy: camera=(), microphone=(), geolocation=()` |
| `Cross-Origin-Embedder-Policy` | Missing | Unsafe cross-origin resource loading | `Cross-Origin-Embedder-Policy: require-corp` |
| `Cross-Origin-Resource-Policy` | Missing | Can expose internal resources to 3rd-party sites | `Cross-Origin-Resource-Policy: same-origin` |
| `Access-Control-Allow-Origin` | Wildcard or unsafe | CORS misconfiguration (API abuse) | `Access-Control-Allow-Origin: https://yourdomain.com` |

---

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
