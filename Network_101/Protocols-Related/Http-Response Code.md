## HTTP response status code: [More](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status)
- <img width="500" alt="image" src="https://github.com/cybersome/Linux-octo/assets/40174034/2df5fede-4375-4e17-8dd3-dc660e39e6de">

## Useful Response:
### **1. 200 OK**
   - **Meaning**: The request was successful, and the server returned the requested resource.
   - **Why Useful**: Confirms that the requested action (like GET or POST) works as expected. During testing, this can indicate successful exploitation (e.g., sensitive data disclosure or improper access).

### **2. 301 Moved Permanently / 302 Found**
   - **Meaning**: The requested resource has been moved to a new URL (301 is permanent; 302 is temporary).
   - **Why Useful**: Can reveal potential open redirects or improper redirects, which could lead to phishing attacks or data leakage.

### **3. 401 Unauthorized**
   - **Meaning**: Authentication is required to access the requested resource.
   - **Why Useful**: Shows that the page is restricted. You can test for bypassing authentication mechanisms, weak credentials, or session management issues.

### **4. 403 Forbidden**
   - **Meaning**: The server understood the request but refuses to authorize it.
   - **Why Useful**: Indicates lack of access rights. Penetration testers can test for **access control weaknesses** by trying to bypass the 403 through IDOR (Insecure Direct Object References), role manipulation, or other techniques.

### **5. 404 Not Found**
   - **Meaning**: The requested resource could not be found.
   - **Why Useful**: Often used to confirm if sensitive resources, like backup files or admin pages, are exposed or properly hidden. Testing can uncover **unlinked or sensitive files**.

### **6. 405 Method Not Allowed**
   - **Meaning**: The request method is not supported for the resource.
   - **Why Useful**: Indicates method restrictions. Useful for testing **HTTP verb tampering**, where switching methods might reveal vulnerabilities (e.g., using GET instead of POST).

### **7. 500 Internal Server Error**
   - **Meaning**: The server encountered an error and could not complete the request.
   - **Why Useful**: Can indicate **misconfigurations**, **unhandled exceptions**, or **input validation failures**. Testing might reveal how the server responds to malformed inputs or unexpected requests, potentially leading to **SQL injection** or **remote code execution**.

### **8. 400 Bad Request**
   - **Meaning**: The server could not understand the request due to invalid syntax.
   - **Why Useful**: Can show input validation issues. Testing for **SQL injection**, **Cross-Site Scripting (XSS)**, or **malformed requests** might trigger this error.

### **9. 503 Service Unavailable**
   - **Meaning**: The server is temporarily unavailable, often due to maintenance or overload.
   - **Why Useful**: This can be useful for stress testing, as **Denial of Service (DoS)** attacks might cause this response when overloading the system.

### **10. 429 Too Many Requests**
   - **Meaning**: The user has sent too many requests in a given amount of time (rate limiting).
   - **Why Useful**: Useful for identifying **rate limiting** on sensitive functions (login attempts, password resets). Lack of rate limiting could lead to **brute-force attacks** or **credential stuffing**.

---

### **Common Exploits and How Response Codes Help:**

- **Authentication Bypass**: Testing for 401, 403 responses helps in verifying how authentication and authorization mechanisms can be bypassed.
- **Information Disclosure**: HTTP 200 responses, coupled with unexpected data leaks (like email addresses, user info), can highlight **data exposure**.
- **Insecure Direct Object References (IDOR)**: Look for 200 OK where restricted access should be enforced (403 expected).
- **Server Misconfigurations**: 500 responses during malformed input tests can hint at improper error handling, which might lead to deeper exploitation.

