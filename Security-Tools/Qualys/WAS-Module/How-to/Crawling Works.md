### 🧠 You chose the crawl scope:

> **"Limit at or below URL hostname"**
>
> URL Structure: **scheme://subdomain.domain.tld:port/path?query#fragment**

---

### ✅ That means:

> Allow crawling anything that:

1. Belongs to the **same hostname** (like `shop.example.com`)
2. Uses **HTTP or HTTPS**
3. Uses **any port** (default or custom)

So with **start URL:**

```
https://shop.example.com/login
```

---

### 🔍 Breakdown of Each Crawled URL:

| URL                                             | Crawled? | Why?                                                                            |
| ----------------------------------------------- | -------- | ------------------------------------------------------------------------------- |
| `https://shop.example.com/login`                | ✅        | This is the **exact start URL**                                                 |
| `https://shop.example.com/admin/`               | ✅        | Same **hostname**, different **path**                                           |
| `https://shop.example.com/products/view?id=123` | ✅        | Same **hostname**, deeper **path**, still within scope                          |
| `http://shop.example.com:8080/api/`             | ✅        | Still the **same hostname**, only port & scheme changed (allowed by this scope) |

---

### 🔥 Key Point:

> “**Limit at or below URL hostname**” **≠** “Only this exact URL”
> It means:
> “**This domain** and **anything beneath it**, across all **URLs**, **paths**, **ports**, and **protocols**.”

---

### 📍 What It Will **NOT** Crawl:

| URL                              | Why Not?                      |
| -------------------------------- | ----------------------------- |
| `https://example.com/login`      | Different **hostname**        |
| `https://blog.shop.example.com/` | Different **subdomain**       |
| `https://cdn.example.net/`       | Entirely different **domain** |

---

### 🔓 Real-life Analogy:

> You're telling the scanner:
> "**Stay inside the `shop.example.com` building** — go into any room (path), basement (ports), or take any elevator (protocol), but don’t walk into another building like `example.com` or `blog.shop.example.com`.”

---
