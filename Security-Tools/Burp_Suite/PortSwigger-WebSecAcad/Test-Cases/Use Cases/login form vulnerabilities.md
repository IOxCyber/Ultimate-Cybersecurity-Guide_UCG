## 1. SQL Injection (CWE‑89)

- **What**: Malicious SQL in `username` or `password` fields.  
- **Why**: Bypass auth, dump the users table, pivot further.  
- **Example**:
  ```
  POST /login
  username=' OR '1'='1
  password=anything
  ```
  → Logs you in as first user.  
- **Seen At**: `/login`, `/api/authenticate`

---

## 2. Credential Stuffing & Brute‑Force

- **What**: Automated guessing of username/password pairs (often leaked from breaches).  
- **Why**: High success if users reuse credentials.  
- **Example**:
  ```bash
  hydra -l alice -P passwords.txt https://example.com http-post-form "/login:username=^USER^&password=^PASS^:Invalid"
  ```
- **Seen At**: `/login`, `/auth/submit`

---

## 3. Account Enumeration

- **What**: Login form reveals whether a username exists.  
- **Why**: Attackers gather valid accounts for targeted attacks.  
- **Example**:  
  - **Valid** user:  
    ```json
    {"success":false, "message":"Wrong password"}
    ```  
  - **Invalid** user:  
    ```json
    {"success":false, "message":"User not found"}
    ```
- **Seen At**: `/login`, `/api/authenticate`

---

## 4. Insecure Direct Object Reference (IDOR) via Session Fixation

- **What**: Attacker forces victim to use a known session ID.  
- **Why**: If session isn’t rotated on login, attacker can hijack.  
- **Example**:
  1. Attacker visits `/login?sessionId=ATTACKER_ID`  
  2. Victim logs in → same session ID used  
  3. Attacker sends requests with `Cookie: session=ATTACKER_ID` → now authenticated as victim  
- **Seen At**: `/login`, any endpoint that issues session cookies

---

## 5. Cross‑Site Request Forgery (CSRF)

- **What**: Login form can be tricked into logging a victim into attacker’s account (“login CSRF”).  
- **Why**: Once victim is logged into attacker’s account, attacker can track their actions or escalate further.  
- **Example**:  
  ```html
  <img src="https://bank.com/login?username=attacker&password=xxx" />
  ```
  Victim’s browser auto‑submits, logging them into attacker’s session.  
- **Seen At**: `/login`, `/authenticate`

---

## 6. Cleartext Credentials (Weak Transport)

- **What**: Login form uses HTTP or TLS 1.0, sends creds in clear.  
- **Why**: Sniffable over the network, immediately compromised.  
- **Example**:  
  ```http
  POST http://example.com/login
  username=alice&password=supersecret
  ```
- **Seen At**: Any unencrypted `/login` endpoint

---

## 7. Broken “Remember Me” Functionality

- **What**: Weak or predictable token stored in cookie.  
- **Why**: Attacker forges token to gain access without creds.  
- **Example**:  
  - `Set-Cookie: remember_me=USER1234`  
  - If predictable, attacker sets that cookie value and is authenticated.  
- **Seen At**: `/login`, `/session/remember`

---

## 8. Brute‑Forcing Multi‑Factor Bypass

- **What**: Login form sends MFA code in predictable way or uses same rate limits as password.  
- **Why**: Attacker brute‑forces the 2FA code.  
- **Example**:  
  - After password success, `/verify-otp` accepts any code without lockout.  
- **Seen At**: `/login`, `/verify-otp`

---

### 🔒 **Defenses**

- **Parameterized Queries / ORMs** for SQLi protection.  
- **Rate‑limit & account lockout** for brute‑force.  
- **Generic error messages** (`“Invalid credentials”` for both bad user & password).  
- **Rotate session IDs** on login (prevent fixation).  
- **CSRF tokens** on login forms (or use `SameSite` cookie flag).  
- **Enforce HTTPS** (TLS1.2+) and HSTS.  
- **Secure “Remember Me”** with signed, random tokens.  
- **MFA with throttling** and secure channels (SMS/Email).

---
