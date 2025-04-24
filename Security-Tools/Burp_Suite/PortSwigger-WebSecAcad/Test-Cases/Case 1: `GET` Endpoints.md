## **Case 1: `GET` Endpoints – Parameter in URL**

### **What It Is**  
- These endpoints send data via URL query parameters:
  ```
  https://example.com/search?q=shoes
  ```

### **Common Vulnerabilities**

| Vulnerability | What It Means | Example |
|---------------|----------------|---------|
| **Reflected XSS (CWE-79)** | Malicious scripts reflected in response | `q=<script>alert(1)</script>` |
| **Information Disclosure** | Sensitive info in URL (leaked via logs) | `?token=abcd1234` |
| **Open Redirect** | User redirected to malicious site | `?redirect=https://evil.com` |
| **SQL Injection (CWE-89)** | Query parameter used unsafely in SQL | `?id=1' OR '1'='1` |
| **IDOR (Insecure Direct Object Reference)** | Accessing data via predictable IDs | `?user_id=2` gives another user’s data |

---

### **Detailed Example – Reflected XSS via GET**

#### **Vulnerable Endpoint**
```html
GET /search?q=shoes
```

#### **Browser Output:**
```html
<h2>Search results for shoes</h2>
```

#### **Injection Payload:**
```url
/search?q=<script>alert('XSS')</script>
```

#### **Rendered Output:**
```html
<h2>Search results for <script>alert('XSS')</script></h2>
```

- Browser executes the script → XSS!

---

### **Where This is Seen?**

| Site Type | Example |
|-----------|---------|
| E-commerce | Search, product filters |
| Forums | Viewing topics/posts |
| Blogs | Comments preview |
| Social Media | Profile viewers via GET |

---

### **How to Test It**

1. **Tools**:
   - Burp Suite → Repeater to manipulate `GET` parameters.
   - curl:
     ```bash
     curl "http://example.com/search?q=<script>alert(1)</script>"
     ```

2. **Burp Scanner**: For automatic reflected XSS and SQLi checks.
3. **Manually**:
   - Check how query parameters are reflected.
   - Try breaking response with HTML/script tags.

---

### **Prevention**

- HTML Encode all user input before rendering.
- Use frameworks with built-in escaping (React, Django templates).
- Apply input validation & Content Security Policy (CSP).

