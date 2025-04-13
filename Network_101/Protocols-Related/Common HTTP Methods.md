### **Common HTTP Methods**  
These methods define how a client (like a browser or tool) interacts with a server or web API.

| **Method** | **Definition (1-liner)** | **Purpose / Action** | **Payload** | **Idempotent?** | **Use in Pentesting / API Testing** |
|------------|--------------------------|----------------------|--------------|------------------|-------------------------------------|
| **GET**    | Retrieves data from server | Fetch resources (e.g., webpage, data) | No | Yes | Test for **info disclosure, query param tampering** |
| **POST**   | Sends data to server | Create/update a resource | Yes | No | Test for **XSS, SQLi, file upload vulnerabilities** |
| **PUT**    | Replaces a resource | Fully update an existing resource | Yes | Yes | Test for **overwriting resources**, insecure API calls |
| **PATCH**  | Modifies part of resource | Partially update data | Yes | No | Like PUT, but partial — **test for improper validation** |
| **DELETE** | Removes resource | Delete a resource from the server | Sometimes | Yes | Test for **access control** (can attacker delete?) |
| **HEAD**   | Retrieves headers only | Like GET, but no body returned | No | Yes | Used in **fingerprinting, testing presence of resources** |
| **OPTIONS**| Shows allowed methods | Discover what methods a server supports | No | Yes | Check for **method exposure**, **CORS misconfig** |
| **CONNECT**| Creates a tunnel | Used to establish **HTTPS over proxy** | Yes | No | Can be abused in **proxy bypass** attacks |
| **TRACE**  | Echoes request | Diagnostic tool for loop-back testing | No | Yes | Can be abused in **Cross-Site Tracing (XST)** |

---

### **Quick Notes to Remember**

- **GET** = Just get data (Read-only)
- **POST** = Send data (Create)
- **PUT** = Replace all (Update)
- **PATCH** = Replace some (Partial Update)
- **DELETE** = Remove stuff
- **OPTIONS** = Ask server “What can I do here?”
- **HEAD** = Check headers without downloading full content
- **CONNECT** = Tunnel to another host (e.g., HTTPS)
- **TRACE** = Bounce-back your request to test echo

---
