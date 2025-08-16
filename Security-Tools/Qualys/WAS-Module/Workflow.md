## 1. Fault injection vs. Manual:
### Fault injection: `Automated Testing (Fast)`
- Injecting "specially crafted" character strings into application form fields and examining the application's responses to detect vulnerabilities. 
- Crafted according to Web app vulnerability data and information provided by OWASP, Web Application Security Consortium (WASC), and Common Weakness Enumeration (CWE).

### Manual: Thru Burp Integration (To discover Design flaws)

## 2. WAS Workflow:
- The workflow for analyzing a Web application involves five simple
- Steps: `1) Define Web Application, 2) Perform Discovery Scan—Crawl, 3) Perform Vulnerability Scan, 4) Create Reports, and 5) Fix Vulnerabilities`
```
Here is a detailed view of this workflow:
1. Define Web Application
• Identify the location (URL) of the Web App
• Define the “scope” of the Web App Crawl
• Choose from various scanning options—Option Profile:
• Select a scanner appliance
• Include “crawling hints” and/or header injection
• Use optional DNS Override
• Provide authentication credentials
- Form records
- Server records
• Identify areas to “white list” or “black list”
• Enable malware monitoring
2. Perform Discovery Scan (Crawl)
3. Perform Vulnerability Scan
4. Create reports to identify links crawled and vulnerabilities detected
5. Fix vulnerabilities
```
