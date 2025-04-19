# Common API Vulnerability:

### **1. Broken Object Level Authorization (BOLA)**

- **Explanation:** 
  BOLA happens when an API does not properly check if the user has access to an object (such as user data or resources) before providing it. This allows attackers to access data they shouldn’t have access to by manipulating object references.
  
- **Example (Exploit):**
  - **Before Exploit:** 
    ```
    GET https://api.app.com/orders/12345  (user A can view their own order)
    ```
    User A changes the ID in the URL to:
    ```
    GET https://api.app.com/orders/12346  (user A accesses another user’s order)
    ```

  - **After Exploit:** User A views/edits another user's order by changing the `order ID` in the request.

- **Mitigation:**
  - Implement proper authorization checks for every object.
  - Ensure each user can only access resources they are authorized to access.

- **OWASP Category:** [API1:2019 - Broken Object Level Authorization](https://owasp.org/www-project-api-security/)

---

### **2. Broken Authentication**

- **Explanation:** 
  This happens when authentication mechanisms are weak, allowing attackers to impersonate legitimate users. It can occur due to weak passwords, lack of two-factor authentication, or using tokens insecurely.

- **Example (Exploit):**
  - **Before Exploit:**
    The API allows users to authenticate using weak credentials.
    ```
    POST /login
    {
      "username": "john",
      "password": "password123"
    }
    ```

  - **After Exploit:** Attackers can easily brute-force weak passwords and access user accounts.

- **Mitigation:**
  - Use strong passwords and enforce password policies.
  - Implement multi-factor authentication (MFA).
  - Secure authentication tokens and session IDs.

- **OWASP Category:** [API2:2019 - Broken Authentication](https://owasp.org/www-project-api-security/)

---

### **3. Excessive Data Exposure**

- **Explanation:** 
  APIs often expose more data than necessary, relying on the client to filter what should be shown. Attackers can manipulate API requests to retrieve sensitive information that should be hidden.

- **Example (Exploit):**
  - **Before Exploit:**
    API responds with more data than needed:
    ```json
    GET /user/12345
    {
      "user_id": 12345,
      "username": "john",
      "password_hash": "abc123",
      "credit_card_info": "4111-1111-1111-1111"
    }
    ```

  - **After Exploit:** Attackers can view sensitive data like `password_hash` and `credit_card_info` by inspecting the API response.

- **Mitigation:**
  - Only expose the minimum required data in API responses.
  - Use server-side filtering to prevent sensitive data from being exposed.

- **OWASP Category:** [API3:2019 - Excessive Data Exposure](https://owasp.org/www-project-api-security/)

---

### **4. Lack of Resources & Rate Limiting**

- **Explanation:** 
  This vulnerability occurs when the API doesn’t limit the number of requests a client can make. This can lead to resource exhaustion (Denial of Service, or DoS) or abuse of the API’s functionality.

- **Example (Exploit):**
  - **Before Exploit:**
    An attacker sends a large number of requests to the API, causing it to crash or slow down.
    ```
    GET /api/user/12345 (thousands of times in a short period)
    ```

  - **After Exploit:** The API becomes unavailable to legitimate users due to excessive requests.

- **Mitigation:**
  - Implement rate limiting (e.g., allow only a certain number of requests per minute).
  - Use caching to minimize server load for repeated requests.
  - Introduce mechanisms like throttling or quotas.

- **OWASP Category:** [API4:2019 - Lack of Resources & Rate Limiting](https://owasp.org/www-project-api-security/)

---

### **5. Mass Assignment**

- **Explanation:** 
  Mass Assignment occurs when an API automatically binds user input to object attributes. Attackers can manipulate input to update fields they shouldn’t be able to access, like admin privileges or sensitive settings.

- **Example (Exploit):**
  - **Before Exploit:**
    The API allows users to update their profile by passing parameters:
    ```json
    PATCH /user/12345
    {
      "username": "john",
      "role": "admin"
    }
    ```

  - **After Exploit:** The user modifies their role to "admin" by directly changing it in the request.

- **Mitigation:**
  - Implement strict input validation and only allow authorized fields to be updated.
  - Use whitelisting to limit which attributes users can modify.

- **OWASP Category:** [API6:2019 - Mass Assignment](https://owasp.org/www-project-api-security/)

---

### **6. Security Misconfigurations**

- **Explanation:** 
  APIs are often vulnerable due to security misconfigurations like open ports, insecure default settings, or missing security headers.

- **Example (Exploit):**
  - **Before Exploit:**
    The API does not use secure headers like `X-Frame-Options` or `Content-Security-Policy`.
  
  - **After Exploit:** Attackers could exploit these misconfigurations to perform **Clickjacking** or **XSS attacks**.

- **Mitigation:**
  - Ensure security best practices are followed during deployment.
  - Regularly audit and fix misconfigurations in APIs.
  - Use tools like **OWASP ZAP** or **Burp Suite** to check for security misconfigurations.

- **OWASP Category:** [API7:2019 - Security Misconfiguration](https://owasp.org/www-project-api-security/)

---

### **7. Injection Attacks**

- **Explanation:** 
  Injection vulnerabilities occur when user input is passed directly to a database or another interpreter without proper validation or sanitization, allowing attackers to execute malicious code or queries.

- **Example (Exploit):**
  - **Before Exploit:**
    The API allows direct user input in SQL queries:
    ```
    GET /api/user?name=john' OR 1=1 -- 
    ```

  - **After Exploit:** The attacker gains access to the entire user database due to an **SQL Injection**.

- **Mitigation:**
  - Use parameterized queries or prepared statements.
  - Validate and sanitize all user inputs.
  - Use security libraries like **ORMs** to prevent direct interaction with databases.

- **OWASP Category:** [API8:2019 - Injection](https://owasp.org/www-project-api-security/)

---

### **8. Improper Assets Management**

- **Explanation:** 
  APIs often have exposed old versions that are no longer maintained, which attackers can target. This occurs due to improper management of deprecated or unpatched APIs.

- **Example (Exploit):**
  - **Before Exploit:**
    An attacker discovers that an older API version with known vulnerabilities is still accessible.
    ```
    GET /v1/user/12345 (using an outdated version of the API)
    ```

  - **After Exploit:** The attacker exploits vulnerabilities in the old API version, bypassing newer security mechanisms.

- **Mitigation:**
  - Decommission and remove outdated or unused API versions.
  - Keep API documentation up to date and manage versioning securely.

- **OWASP Category:** [API9:2019 - Improper Assets Management](https://owasp.org/www-project-api-security/)

---

### **9. Insufficient Logging & Monitoring**

- **Explanation:** 
  This happens when the API does not properly log and monitor user activities, making it difficult to detect attacks or breaches in real time.

- **Example (Exploit):**
  - **Before Exploit:** 
    An attacker brute-forces multiple user accounts, but the API lacks logging for failed login attempts, so administrators are unaware of the attack.
  
  - **After Exploit:** The attacker compromises several accounts without triggering alerts.

- **Mitigation:**
  - Implement logging and monitoring for critical events like authentication failures.
  - Set up alerts for suspicious activities.
  - Use tools like **SIEM (Security Information and Event Management)** to detect real-time threats.

- **OWASP Category:** [API10:2019 - Insufficient Logging & Monitoring](https://owasp.org/www-project-api-security/)

---

### **Summary of Common API Vulnerabilities**

---

| **Vulnerability**                       | **OWASP Category**                  | **Explanation**                                                       | **Mitigation**                                                       |
|-----------------------------------------|------------------------------------|-----------------------------------------------------------------------|----------------------------------------------------------------------|
| **Broken Object Level Authorization**   | API1: BOLA                         | Unauthorized access to objects by manipulating object references.     | Implement strict object-level authorization checks.                  |
| **Broken Authentication**               | API2: Broken Authentication        | Weak or insecure authentication mechanisms.                           | Use strong passwords, MFA, and secure token management.              |
| **Excessive Data Exposure**             | API3: Excessive Data Exposure      | API returns more data than necessary.                                 | Limit the data exposed in API responses.                             |
| **Lack of Resources & Rate Limiting**   | API4: Rate Limiting                | No limit on the number of requests leading to DoS attacks.            | Implement rate limiting and quotas.                                  |
| **Mass Assignment**                     | API6: Mass Assignment              | Automatically binding user input to object attributes.                | Use whitelisting for allowed attributes.                             |
| **Security Misconfiguration**           | API7: Security Misconfiguration    | Exposed APIs due to insecure settings or misconfigurations.            | Follow security best practices and regularly audit configurations.   |
| **Injection Attacks**                   | API8: Injection                    | Unvalidated input leads to SQL/NoSQL/Command injection.               | Use parameterized queries and validate input.                        |
| **Improper Assets Management**          | API9: Assets Management            | Old or deprecated API versions still accessible.                      | Decommission outdated API versions and manage versioning properly.   |
| **Insufficient Logging & Monitoring**   | API10: Logging & Monitoring        | Lack of monitoring allows attacks to go unnoticed.                    | Implement logging for critical events and real-time threat detection.|

---
