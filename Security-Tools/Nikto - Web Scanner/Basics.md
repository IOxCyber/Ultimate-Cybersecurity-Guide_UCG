# Nikto Web Scanner: 
- An `open-source web server scanner` that performs comprehensive tests against web servers for dangerous files, outdated versions, and security issues.

---

## Usages (in Short)
- Scan web servers for common vulnerabilities.
- Detect outdated software, misconfigurations, and exposed scripts.
- Useful for quick recon during pentests or red teaming.

---

## Examples

### 1. Basic Web Scan
```bash
-h (specify /host)
nikto -h http://192.168.56.101
```

### 2. Scan Specific Port
```bash
nikto -h http://192.168.56.101:8080
```

- Multiple Sites at once: `nikto -h targets.txt`
- Follow Redirects: `nikto -h http://target.com -followredirects 1`
## Use Tuning Option (Specific Test Type):
```
Tuning Value	Test Type
1	Interesting File/CGI
2	Misconfigurations
3	Information Disclosure
4	Injection (XSS/Command)
5	Remote File Retrieval
6	Denial of Service
7	Remote Execution
8	SQL Injection
9	Authentication Bypass

You can combine like: -Tuning 12389

eg. nikto -h http://192.168.56.101 -Tuning 123
```

### 3. Save Output: csv, txt, XML, HTML

![image](https://github.com/user-attachments/assets/df1d5cc4-3292-4a1e-8e11-d16b2eb5e18e)

```bash
nikto -h http://192.168.56.101 -o output.txt -Format txt
```

### 4. Use with Proxy (e.g., BurpSuite)
```bash
nikto -h http://192.168.56.101 -useproxy http://127.0.0.1:8080
```

### 5. Verbose Output
```bash
nikto -h http://192.168.56.101 -Display V
```

---

## What Nikto Can Test

| Type                  | Description                                           |
|-----------------------|-------------------------------------------------------|
| ✅ Outdated Servers    | Apache, Nginx, Tomcat, IIS, etc.                      |
| ✅ Default Files       | `/phpinfo.php`, `/test/`, `/admin/`, backup files    |
| ✅ Misconfigurations   | Directory indexing, no SSL, improper headers         |
| ✅ Insecure Scripts    | Old PHP, CGI, Perl scripts with known vulns          |
| ✅ WebDAV Issues       | Checks for insecure HTTP methods (PUT, DELETE)       |
| ✅ Vulnerability Checks| XSS, Open Redirects, Error Disclosures               |

---

## ⚠️ Limitations

| Limitation                          | Explanation                                       |
|------------------------------------|---------------------------------------------------|
| ❌ No stealth mode                 | Easily detectable by IDS/IPS                      |
| ❌ Not updated frequently          | May miss latest zero-days                         |
| ❌ Web App logic blind             | Can't handle JS-heavy or dynamic pages            |
| ❌ No authentication testing       | Doesn't test post-login functionalities           |
| ❌ Basic scan only (no deep crawling) | Shallow scans, doesn’t fuzz parameters          |

---

## Alternatives

| Tool         | Purpose                                             |
|--------------|-----------------------------------------------------|
| **OWASP ZAP**| Full-featured web app scanner (GUI + automation)    |
| **Burp Suite** | Manual + automated scanning, great for deep testing |
| **Wfuzz**     | Fuzzing tool for parameters & files                 |
| **Dirb/Dirbuster** | Brute-force directory/file discovery           |
| **Nessus/Qualys WAS**     | Enterprise-grade vuln scanner, includes web checks|
| **Acunetix**   | Commercial tool with deep web vuln coverage        |

