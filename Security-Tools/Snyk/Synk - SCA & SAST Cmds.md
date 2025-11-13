---

# 🧩 Snyk CLI — Complete Command Reference (SCA + SAST)

---

## 🔐 Authentication & Setup

| Purpose | Command | Notes |
|----------|----------|-------|
| Authenticate CLI with Snyk account | `snyk auth` | Opens browser for login; links CLI → account |
| Check CLI version | `snyk --version` | Ensures latest version |
| Display help | `snyk help` | Lists all available commands |

---

## 🧠 SAST (Snyk Code)

| Purpose | Command | Notes |
|----------|----------|-------|
| Scan source code for vulnerabilities | `snyk code test` | Static analysis of code files (.py, .js, .java, etc.) |
| Include specific directories/files | `snyk code test ./src` | Target custom code paths |
| Output as JSON | `snyk code test --json` | For automation/reporting |
| Save report to file | `snyk code test --json > snyk_code_report.json` | Useful for CI/CD reports |
| Set severity threshold | `snyk code test --severity-threshold=high` | Ignores lower severity issues |

---

## ⚙️ SCA (Snyk Open Source / Dependency Scanning)

| Purpose | Command | Notes |
|----------|----------|-------|
| Test dependencies for known CVEs | `snyk test` | Scans manifest files (requirements.txt, package.json, pom.xml, etc.) |
| Specify manifest file manually | `snyk test --file=requirements.txt` | Useful if multiple manifests exist |
| Upload project to Snyk dashboard | `snyk monitor` | Enables continuous monitoring in UI |
| Test all projects recursively | `snyk test --all-projects` | Scans app, Docker, and IaC together |
| Ignore specific issue temporarily | `snyk ignore --id=<VULN-ID>` | Example: `--id=SNYK-JS-LODASH-567746` |
| Unignore a previously ignored issue | `snyk ignore --remove --id=<VULN-ID>` | Re-enables detection for that vuln |
| Set severity threshold | `snyk test --severity-threshold=medium` | Filters results below threshold |
| JSON output for automation | `snyk test --json` | Machine-readable output |
| Save JSON output to file | `snyk test --json > snyk_sca_report.json` | Useful in pipelines |

---

## 🐳 Container / Docker Scanning

| Purpose | Command | Notes |
|----------|----------|-------|
| Scan Docker image | `snyk container test <image-name>` | Example: `snyk container test ubuntu:20.04` |
| Continuous monitoring | `snyk container monitor <image-name>` | Uploads scan result to dashboard |
| Include Dockerfile context | `snyk container test --file=Dockerfile <image>` | Detects base image CVEs and recommendations |
| Output as JSON | `snyk container test <image> --json` | Structured result for CI/CD |
| Test all projects | `snyk container test --all-projects` | Scans all container-related files |

---

## ☁️ Infrastructure-as-Code (IaC)

| Purpose | Command | Notes |
|----------|----------|-------|
| Scan Terraform, K8s, or Helm configs | `snyk iac test` | Detects misconfigurations |
| Target specific IaC file | `snyk iac test terraform/main.tf` | Focused scanning |
| Monitor IaC project | `snyk iac monitor` | Upload to dashboard for tracking |
| Output as JSON | `snyk iac test --json` | For integration/reporting |
| Save report | `snyk iac test --json > snyk_iac_report.json` | CI/CD-friendly |

---

## 🧩 General & Utility Commands

| Purpose | Command | Notes |
|----------|----------|-------|
| List all Snyk organizations | `snyk org list` | Useful for multi-org users |
| Set default organization | `snyk config set org=<ORG_ID>` | Required in multi-org setups |
| View current config | `snyk config` | Shows auth and org info |
| Logout / remove auth token | `snyk config unset api` | Clears authentication |
| Display all ignored issues | `snyk ignore --list` | Manage suppression rules |
| Display project details | `snyk project list` | Lists projects linked to account |

---

## 🚀 Pro-Level Integrations (CI/CD)

| Purpose | Command | Notes |
|----------|----------|-------|
| Run non-interactively in CI | `snyk test --api=<API_TOKEN>` | Token from dashboard → Org settings |
| Exit on severity threshold | `snyk test --severity-threshold=high` | Fails pipeline on high vulns |
| Auto-detect all modules | `snyk test --all-projects` | Great for mono-repos |
| Include Dev dependencies | `snyk test --dev` | Include non-production packages |
| Skip dev dependencies | `snyk test --prune-repeated-subdependencies` | Faster and cleaner scan |

---

## 🧾 Reporting Shortcuts

| Type | Command | Output |
|------|----------|---------|
| CLI Text Report | `snyk test` | Human-readable result |
| JSON Report | `snyk test --json > snyk_report.json` | Machine-readable |
| SARIF Report | `snyk test --sarif > snyk_report.sarif` | For GitHub Security tab |
| HTML Report (custom tool) | `snyk-to-html -i snyk_report.json -o report.html` | Needs `npm install -g snyk-to-html` |

---

## ⚡ Quick Reference Summary

| Use Case | Command |
|-----------|----------|
| Code (SAST) | `snyk code test` |
| Dependencies (SCA) | `snyk test` |
| Docker | `snyk container test <image>` |
| IaC | `snyk iac test` |
| Continuous Monitoring | `snyk monitor` |
| All in one | `snyk test --all-projects` |

---