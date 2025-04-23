## Must-Haves for Kickstart:
```
✅ Scope: www.*example.com, subdomains, APIs
✅ Roles/Accounts: Admin, User, Guest
✅ Source/Infra info: Tech stack, server, WAF
✅ Dev/Prod distinction: Know your testing ground
```

## Scope of the Testing:
1. What Domain, Subdomain, APIs, Endpoint to test
2. Application Walkthrough, working of the data flow etc.
3. URL (www.example.com / *example.com) where * is to test all subdomain (eg. blog.example.com, feedback.example.com etc)
4. Type of Testing (Black Box, White Box, Grey Box)
5. User Role Based - Credentials (White Box)
6. Source Code (White Box)

### In Detail:

| # | Category | Description |
|--|-----------|-------------|
| **1** | **Scope Definition** | Clearly define **target(s)**:<br>- Primary Domain(s): `www.example.com`<br>- Wildcard Subdomains: `*.example.com`<br>- APIs: `api.example.com/v1/*`<br>- Third-party integrations, static assets, CDN domains |
| **2** | **Application Walkthrough** | Detailed walkthrough with devs or product owners:<br>– Critical business functions<br>– Data flow: from input to DB<br>– Feature dependencies & conditions |
| **3** | **Test Approach** | Define testing type:<br>- 🔲 Black Box (no app insight)<br>- 🔲 Grey Box (limited creds)<br>- 🔲 White Box (full access, source code)<br><br>**Note**: For in-house, go *White/Grey Box* |
| **4** | **Credentials (RBAC)** | Provide **user roles**:<br>– Admin<br>– Moderator/Editor<br>– Standard User<br>– Guest / Limited Access<br><br>✔️ Needed for **Privilege Escalation**, **Horizontal/Vertical Access Control** tests |
| **5** | **Environment Access** | Confirm testing on:<br>– 🔲 Production<br>– 🔲 Staging/QA<br>– 🔲 Dev<br><br>🎯 Ensure: Isolation, safe test data, error visibility |
| **6** | **Source Code** | (For White Box)<br>– Provide full or partial access<br>– Tech stack info: PHP, Node.js, Django, etc.<br>– Dependencies: `package.json`, `composer.lock`, etc. |
| **7** | **Testing Duration & Schedule** | Fix timeline:<br>– Daily hours (if staging)<br>– Time-sensitive features<br>– Freeze windows (e.g. prod deploys) |
| **8** | **Target Surface Inventory** | Get or generate:<br>– URL Sitemap (crawlable pages)<br>– API Endpoints (Swagger/OpenAPI)<br>– JS files (LinkFinder, JSParser)<br>– Subdomains (Amass/Subfinder) |
| **9** | **Network & Infra Context** | Confirm:<br>– Load balancer (cloudflare, AWS ALB)<br>– Web Server type (Apache/Nginx)<br>– CDN, WAF (Cloudflare, Akamai, etc.)<br>– Rate limiting & IP banning |
| **10** | **Security Controls Enabled** | Know what's already in place:<br>– WAF (ModSecurity, Cloudflare)<br>– Input validation/sanitization<br>– Auth & Session controls<br>– Rate limiting (manual/automated tools) |
| **11** | **DevSecOps Pipelines** | Optional (White Box):<br>– CI/CD integration for auto-scanning<br>– Pre-commit hooks or SAST scans<br>– Deployment stages: dev → staging → prod |
| **12** | **In-Scope Vulnerability Categories** | Align with:<br>– OWASP Top 10 (Web + API)<br>– CWE/ CVSS scoring<br>– App-specific threats (e.g. payment fraud, business logic) |
| **13** | **Out-of-Scope Areas (if any)** | Clearly state:<br>– Payment gateways?<br>– 3rd-party libraries?<br>– Social logins / external auth?<br>– Email triggers / support tools? |
| **14** | **Point of Contact (PoC)** | Assign person(s):<br>– App Owner<br>– Developer<br>– Security POC<br><br>Needed for:<br>– Downtime handling<br>– Exploitation confirmation<br>– Remediation guidance |

---
