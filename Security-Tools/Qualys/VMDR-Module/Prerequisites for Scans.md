# Prerequisites for Agent based, IP based & WAS Scanning:

---

## 1. AGENT-BASED (HOST-BASED) SCANNING
### Port Required
- Outbound 443 only (HTTPS to Qualys Cloud)

### Communication Flow
- Agent → Qualys Cloud (443 outbound)
> No scanner used

### Login Method
- No login, Agent runs locally with system-level access.

### Encryption
- Yes, TLS 1.2/1.3 end-to-end.

### Result Compiled By
- Agent locally → sent to Qualys Cloud

### Target Type
- Windows Servers/Workstations
- Linux Servers/Workstations
- Cloud VMs (AWS, Azure, GCP)
- Dynamic IP assets
- Remote laptops/Endpoints



---

## 2. IP-BASED (SCANNER-BASED) AUTHENTICATED SCANNING

### Ports Required
- Linux: 22 (SSH)

- Windows: 445 (SMBv2), 135 (RPC), dynamic RPC (49152–65535)

- Network Devices: 22 (SSH), 161 (SNMP), 23 (Telnet if used)

- Scanner → Qualys Cloud: outbound 443

### Communication Flow
- Scanner → Target (22/445/135/161)
- Scanner → Qualys Cloud (443 outbound)

### Login Method
- Linux: SSH username/password or SSH key + sudo
- Windows: Domain/Local service account (NTLMv2/Kerberos)
- Network Devices: SSH/SNMP credentials

### Encryption
- Target communication: SSH/SMB secure
- Scanner → Qualys Cloud: TLS 1.2/1.3
- Everything encrypted.

### Result Compiled By
- Scanner Appliance, then pushed to Qualys Cloud.

### Target Type
- Servers on LAN/VPN
- Network devices (firewalls, switches, routers)
- Appliances, printers, IOT devices
- Anything reachable via IP

---

## 3. WAS (WEB APPLICATION SCANNING)
### Ports Required
- 80 (HTTP) & 443 (HTTPS)
- Custom web ports (e.g., 8080, 8443)


### Communication Flow
- WAS Scanner Appliance → Web Application (80/443)
- WAS Scanner Appliance → Qualys Cloud (443)

> No special Scanner is required to run WAS scans, Same VM scanner compliance will work for WAS.

### Login Method
- Application login (form-based, header-based, cookie-based)

> Not OS login → no SSH/SMB required

### Encryption
- Web traffic: HTTP/HTTPS as per app
- Scanner → Qualys Cloud: TLS 1.2/1.3

### Result Compiled By
- WAS Scanner Engine → Qualys Cloud

### Target Type
- Public websites
- Internal web apps
- APIs
- Staging/pre-prod apps
- Any HTTP/HTTPS service

---


### SUPER-SIMPLE MEMORY MAP:
```
AGENT = No scanner, 443 only, inside-out view
IP-BASED = Scanner + SSH/SMB, outside-in view
WAS = Scanner + HTTP/HTTPS, web-layer view
```