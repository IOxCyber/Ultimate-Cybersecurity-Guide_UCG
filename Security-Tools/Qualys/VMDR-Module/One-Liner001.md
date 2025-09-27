1. CVE: Common Vulnerability & Exposure (`DB of all publically known Vuln`)
2. CVSS: Common Vulnerability Scoring System `Low (0.1 - 3.9) < Medium (4.0 - 6.9) < High (7.0 - 8.9) < Critical (9.0-10)`
3. CVSS Types: Base (Actual), Temporal (Varies with times & Events), Environmental (Specific to Organization)
4. Vuln Levels: `Red (Confirmed) > Yellow (Potential) > Blue (Information Gathered)`
5. DNS: Domain Name System eg. `Scheme://SubDomain.Domain.Top-Level-Domain:Port/Query?` https://www.example.com:443/Search?


---
---

6. PoC: `Proof of Concept` (How a vuln can be exploited)
7. False Positive: Eg. Misidentification of Unpatched s/w versions, Default Config detection, Open Ports/SSL Misconfig.
8. False Negative: Eg. Unpatch Vuln, Misconfig firewall Rules, WebApp Vuln (SQLi)
9. EDR: Endpoint Detection & Response (`For individual Endpoints, Monitoring & Responding to threats`) eg. MS Defender, SentinelOne
10. XDR: Extended Detection & Response (`Integrates & correlates data from multiple security tools`) eg. MS 365 Defender, Palo Alto Cortex XDR

---
---

11. Log Location {`Linux: var/log/qualus`}, Windows {`C/programData/qualys`}: Hidden
12. Zero Day Vuln: `Vuln discovered & exploiting in the wild, unknown to the vendor & no patch available` eg. XSS, SQLi, Remote Code Execution (Log4j, SMBv1) etc
13. Maps: Network/Asset Discovery & Visualization tool
14. To check listening Ports: `Win > netstat -an | find "Listen"` `Linux > netstat -tuln (Self)`
15. To check specific Port status: `nmap -p 443 -sn Ip_addr`, nc -vz IP_Addr 80
16. To check/Test Creds:
  - Win: `RDP (Enter IP/hostname > Username/Pwd)`
  - Linux: `ssh username@IpAddress` or Using Putty on win `Add hostname/Ip in "Hostname"` or Check from UI when adding the Cred Record: Test
