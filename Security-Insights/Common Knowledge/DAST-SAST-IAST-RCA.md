## Quick Definitions:

| Acronym | Full Form                         | What it Does                                                                 |
|---------|----------------------------------|------------------------------------------------------------------------------|
| **DAST** | Dynamic App Security Testing     | Black-box testing of **running apps** (no source code needed).              |
| **IAST** | Interactive App Security Testing | Real-time analysis during app runtime with insight from the inside.         |
| **SAST** | Static App Security Testing      | White-box testing – inspects **source code** or binaries.                   |
| **RCA**  | Root Cause Analysis              | Pinpoints **why/how** a vuln occurred, helps fix it at the source.          |

---

## Tool Mapping to DAST, IAST, SAST, and RCA:

| Tool / Skill                  | DAST ✅ | IAST 🔍 | SAST 🔬 | RCA 🧠 | Notes                                                                 |
|------------------------------|---------|--------|---------|--------|-----------------------------------------------------------------------|
| **Burp Suite**               | ✅ Yes  | 🚫 No  | 🚫 No   | 🧠 Limited | Excellent DAST (manual+automated); great for discovering vulns.       |
| **WebInspect**               | ✅ Yes  | 🚫 No  | 🚫 No   | 🧠 Limited | Enterprise DAST tool; scan dynamic apps for OWASP Top 10.             |
| **SQLMap**                   | ✅ Yes  | 🚫 No  | 🚫 No   | ✅ Yes   | Auto SQLi exploitation; outputs where the injection happens.          |
| **Nmap / Zenmap**            | ⚠️ Indirect | 🚫 No  | 🚫 No   | ✅ Partial| Not a DAST tool, but helps fingerprint services, ports, vulns.        |
| **Wireshark**                | ⚠️ Indirect | 🚫 No  | 🚫 No   | ✅ Yes   | Traffic analysis helps identify causes & misconfigurations (RCA).     |
| **Qualys VM / Nessus**       | ✅ Partial | 🚫 No  | 🚫 No   | ✅ Yes   | Primarily vuln scanners; limited DAST on exposed services.            |
| **Splunk Enterprise**        | 🚫 No   | 🚫 No  | 🚫 No   | ✅ Yes   | RCA powerhouse – logs, alerts, patterns, anomalies, audit trails.     |
| **Python, SQL, JavaScript**  | 🚫 No   | 🚫 No  | ✅ Yes  | ✅ Yes   | Coding knowledge = write SAST rules, analyze source-level issues.     |
| **Linux/Windows OS**         | 🚫 No   | 🚫 No  | 🚫 No   | ✅ Yes   | Knowing OS internals helps in debugging and RCA.                      |
| **ServiceNow**               | 🚫 No   | 🚫 No  | 🚫 No   | ✅ Yes   | Incident response and tracking RCA workflows.                         |
| **VirtualBox**               | 🚫 No   | 🚫 No  | 🚫 No   | ✅ Yes   | Sandbox vulns, replay issues to analyze root cause.                   |
| **Networking & Cloud Basics**| 🚫 No   | 🚫 No  | 🚫 No   | ✅ Yes   | Critical for RCA in distributed systems and cloud architectures.       |

---
---

## Recommendations:

| Area          | Tool to Learn Next      | Why? |
|---------------|--------------------------|------|
| **SAST**       | `Semgrep`, `SonarQube`   | Lightweight, great for dev/pentest crossover. |
| **IAST**       | `Contrast Security`      | Industry-relevant; deep insight during runtime. |
| **DAST++**     | `OWASP ZAP` (automated)  | Open-source, scriptable, CI-friendly. |
| **Automation** | Python + `AutoSploit`    | Build your own scanning pipelines. |
