# Web App Scanning Testing Techniques:
- WAS performed Testing using below 2 techniques i.e Fault Injection (covers 80-85% vulns), Manual Testing (Burp Integration)

## 1. Fault injection: `Automated Testing (Fast)`
- An automated feature of WAS module, which is a dynamic application security testing (DAST) solution.
- The `scanner automatically performs fault injection during a vulnerability scan after it has finished crawling your web application.`
- Injecting "specially crafted" character strings into application form fields to detect vulnerabilities. 
- Character Strings are Crafted according to Web app vulnerability data and information provided by OWASP, Web Application Security Consortium (WASC), and Common Weakness Enumeration (CWE).
- Discovers 80-85% of Web App Vulnerabilities.

### Once the scan begins, Qualys performs a two-phase process:
## 1. Crawling (Discovery phase): 
- The scanner first crawls your web application to map its pages, links, forms, and other components. 
- This provides the engine with a complete inventory of potential injection points.

## 2. Vulnerability Testing (Fault Injection phase): 
- After crawling, the scanner inserts specially crafted "faults"—or malicious payloads—into the discovered input fields, forms, and parameters. 
- The scanner then observes and analyzes the application's response to identify vulnerabilities. 

### The types of fault injection tests include fuzzing to test for various vulnerabilities: 
SQL injection, Cross-Site Scripting (XSS), API Injection, Input Validation. 

## 2. Manual: Thru Burp Integration
- To discover Design flaws by Human Interaction.
