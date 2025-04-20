## Web vulnerabilities in HTTP methods used by APIs
- These vulnerabilities often arise from improper input validation, authentication issues, or lack of security controls.
- Below is a list of vulnerabilities associated with each HTTP method, along with examples of how they can be exploited and how to prevent them.

---

### `1. GET Vulnerability`
- `Vulnerability`: `Information Disclosure` and `IDOR (Insecure Direct Object References)`
  
#### `Example:`
```http
GET /api/user/123 HTTP/1.1
Host: example.com
```
- `Before Exploit`: An attacker can manipulate the user ID (`123`) in the URL to access data they shouldn't (e.g., another user's account).
- `Exploit`: Changing the ID in the URL to `GET /api/user/124` could grant access to another user's data if access controls are not implemented.
- `Impact`: The attacker retrieves unauthorized user information.

#### `Prevention`:
- Implement strong `access control` to ensure users can only access their data.
- Validate user input properly.
- Use URL encryption or tokens to hide sensitive information like user IDs.

---

### `2. POST Vulnerability`
- `Vulnerability`: `Cross-Site Request Forgery (CSRF)`

#### `Example:`
```http
POST /api/user/update HTTP/1.1
Host: example.com
Content-Type: application/json

{
  "name": "John Doe",
  "email": "attacker@example.com"
}
```
- `Before Exploit`: If CSRF protections aren't in place, an attacker can trick an authenticated user into submitting a POST request from another site.
- `Exploit`: The attacker can craft a malicious form on their website. When the victim (who is authenticated) visits the page, the form auto-submits and changes their account details without their knowledge.
- `Impact`: The attacker updates the victim's profile with attacker-controlled data.

#### `Prevention`:
- Use `anti-CSRF tokens` in sensitive forms.
- Implement `same-site cookies` to prevent cross-origin requests.
- Ensure `strong authentication` mechanisms.

---

### `3. PUT Vulnerability`
- `Vulnerability`: `Insecure Direct Object Reference (IDOR)`

#### `Example:`
```http
PUT /api/user/123 HTTP/1.1
Host: example.com
Content-Type: application/json

{
  "email": "attacker@example.com"
}
```
- `Before Exploit`: If a user can modify any account by changing the `123` in the URL, it could allow unauthorized modification of other users' data.
- `Exploit`: The attacker could change the `123` to another user's ID (e.g., `124`) and update the email of that account.
- `Impact`: The attacker modifies another user's profile.

#### `Prevention`:
- Use `authorization checks` to ensure users can only modify their data.
- Perform `input validation` on user IDs.
- Implement `role-based access control (RBAC)` to ensure only authorized users can update sensitive data.

---

### `4. DELETE Vulnerability`
- `Vulnerability`: `Broken Authentication` or `Missing Authorization`

#### `Example:`
```http
DELETE /api/user/123 HTTP/1.1
Host: example.com
```
- `Before Exploit`: If the server does not verify whether the user has permission to delete, an attacker could delete resources they shouldn't have access to.
- `Exploit`: The attacker could send a `DELETE` request to `/api/user/124`, deleting another user's account.
- `Impact`: The attacker deletes a resource (e.g., a user account, record, or file).

#### `Prevention`:
- Ensure `strong authorization` is in place to validate user permissions.
- Implement `rate-limiting` to avoid abuse.
- Require confirmation before deletion (e.g., soft deletes, confirmation prompts).

---

### `5. OPTIONS Vulnerability`
- `Vulnerability`: `Information Disclosure`

#### `Example:`
```http
OPTIONS /api/user HTTP/1.1
Host: example.com
```
- `Before Exploit`: An attacker can send an OPTIONS request to gather information about the allowed HTTP methods for a specific resource.
- `Exploit`: The server responds with:
```http
HTTP/1.1 200 OK
Allow: GET, POST, PUT, DELETE
```
- `Impact`: The attacker gains knowledge about the API's attack surface (e.g., allowed methods, potential entry points for exploitation).

#### `Prevention`:
- Limit the information returned in `OPTIONS` responses.
- Use `authentication` to restrict OPTIONS requests to trusted users.
- Implement `CORS` policies properly to avoid cross-origin attacks.

---

### `6. PATCH Vulnerability`
- `Vulnerability`: `Improper Data Validation`

#### `Example:`
```http
PATCH /api/user/123 HTTP/1.1
Host: example.com
Content-Type: application/json

{
  "email": "attacker@example.com"
}
```
- `Before Exploit`: If the API does not validate the input data or permissions correctly, an attacker can partially update a resource (e.g., changing email).
- `Exploit`: The attacker sends a PATCH request to modify sensitive fields (like email) on another user's account.
- `Impact`: The attacker alters another user's account data.

#### `Prevention`:
- Perform `input validation` on partial updates.
- Check `authorization` before applying PATCH changes.
- Ensure `proper validation rules` for each field being updated.

---

### `7. TRACE Vulnerability`
- `Vulnerability`: `Cross-Site Tracing (XST)`

#### `Example:`
```http
TRACE /api/user HTTP/1.1
Host: example.com
```
- `Before Exploit`: If TRACE is enabled, the attacker can exploit it to reflect malicious input back to the user, including session cookies.
- `Exploit`: The attacker sends a TRACE request that reflects user information (e.g., cookies) and then intercepts this data.
```http
HTTP/1.1 200 OK
Content-Type: message/http

TRACE /api/user HTTP/1.1
Cookie: session=xyz
Host: example.com
```
- `Impact`: The attacker retrieves sensitive information, including cookies, which can be used to hijack sessions.

#### `Prevention`:
- `Disable TRACE` on the server.
- Implement `strict security headers` like `X-Content-Type-Options` and `X-XSS-Protection`.

---
