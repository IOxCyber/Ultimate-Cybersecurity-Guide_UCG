## 1. WAS KB: QIDs for Web App Starts with `150xx`

## 2. Web Application Security Consortium (WASC) Threat Classification:
- The WASC Threat Classification is a cooperative effort to clarify and organize the threats to the security of a website.

## 3. CWE (Common Weakness Enumeration) and CVE (Common Vulnerabilities and Exposures):
- CWE identifies types of software weaknesses, while CVE identifies specific instances of vulnerabilities.
- CWE is like common flaws, like "buffer overflow," while CVE describes a specific instance of a vulnerability, like "CVE-2023-23397".

## 4. Search List: `User-defined list of QIDs` for scan for custom QIDs
- WAS > Configuration
- Dynamic/Static

## 5. Robots.txt: A file that `tells search engines which pages or paths not to crawl` or index (e.g., Disallow: /admin/).

## 6. Sitemap.xml: An XML file that `lists all important URLs for a website, helping search engines crawl` and index them efficiently (e.g., https://example.com/sitemap.xml).

## 7. Scan Types:
- `Discovery Scan` after adding the App.
- `Vulnerability Scan` after adding the App.

## 8. Add Authentication Record for Auth-based scans.

## 9. URL Structure: `Scheme://Subdomain.Domain.TLD/dir1/subdir2/page.html`
- A directory is a segment right after the domain — like the main folder.
- A subdirectory is a nested folder inside a directory.
- eg. https://example.com/dir1/subdir2/page.html
```
| URL                                          | Dir      | Subdir                                   |
| -------------------------------------------- | -------- | ---------------------------------------- |
| `https://example.com/about`                  | `/about` | ❌ None                                  |
| `https://example.com/shop/products`          | `/shop`  | `/shop/products`                         |
| `https://example.com/blog/posts/2024/`       | `/blog`  | `/blog/posts/`, `/blog/posts/2024/`      |
| `https://site.org/app/user/profile/settings` | `/app`   | `/app/user/`, `/app/user/profile/`, etc. |
| `https://my.site.com/login`                  | `/login` | ❌ None                                  |
```


