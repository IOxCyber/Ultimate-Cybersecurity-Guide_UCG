## 1. Discovery Scan in Map
- Target Domain we set Domain Targets as

> example.application:[Ip Range] -- Explain it in details


## 2. Qualys VMDR, you can run scans using specific CVEs by first creating a Search List containing the CVEs and then attaching that list to your scan or report.


## 3. To configure Proxy:
Proxy Config:

RHEL:: /etc/sysconfig/qualys-cloud-agent

Ubuntu: /etc/default/qualys-cloud-agent

"https_proxy=http://<QGS Proxy>:Port


## 4. Zero Day Vulnerability: 
- vulnerabilities. vulnerability. cveIds: <Cve IDs> or [cve Ids, ....]


## 5. Cloud Agent Deployment via Scan: Prerequisites

Linux:
Port 22, SSH service running, Proxy or Not, correct scanner Location, Host be Alive

Windows:
WinRM, Auth Service, Host be Alive, SMB service running on Port 445


## 6. Auth Failing During Ip based scan(Windows): SMBv2 disabled, Qualys User Account is locked up (Login Error), Server is in domain, Changes made but not rebooted, WMI & RPC services are enabled, Ports 145/445 filtered at firewall or Host end




