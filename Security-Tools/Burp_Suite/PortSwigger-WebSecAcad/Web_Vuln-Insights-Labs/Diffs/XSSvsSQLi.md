### 🔶 1. SQL Injection  `(Server-Side – DB Manipulation)`

#### 💬 Scenario:

A vulnerable login form where input is directly used in a SQL query.

```php
<?php
// Vulnerable PHP Code
$username = $_GET['user'];
$query = "SELECT * FROM users WHERE username = '$username'";
?>
```

#### 🧨 Injection Payload:

```
' OR '1'='1
```

#### 🔁 Final Query:

```sql
SELECT * FROM users WHERE username = '' OR '1'='1'
```

✅ Returns all users — **DB breached**.

---

### 🔷 2. Cross-Site Scripting (XSS) `(Client-Side – Browser Execution)`

#### 💬 Scenario:

A comment section that reflects user input without sanitization.

```php
<?php
// Vulnerable Code
echo "Comment: " . $_GET['comment'];
?>
```

#### 🧨 Injection Payload:

```html
<script>alert('XSS')</script>
```

#### 💥 Result in Browser:

Pops an alert box when the page is loaded.
✅ Code is executed in the **user's browser** — **Session can be hijacked**.

---

### 🧠 Final Difference:

| Feature             | SQL Injection                | Cross-Site Scripting (XSS)   |
| ------------------- | ---------------------------- | ---------------------------- |
| **Target**          | Database                     | Browser/User                 |
| **Scope**           | Backend (Server-Side)        | Frontend (Client-Side)       |
| **Goal**            | Data extraction/manipulation | Session hijack, cookie theft |
| **Injection Point** | SQL query                    | HTML/JS rendered to user     |

---
