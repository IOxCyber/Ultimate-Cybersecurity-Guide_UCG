### 🧩 QUALYS VM INTERVIEW REVISION SHEET

#	Topic	Key Points (Easy Recall)

1. Agent vs IP Scan:
• IP-based → static IPs, servers<br>• Agent-based → laptops, roaming endpoints<br>✅ IP = scheduled, Agent = continuous	
2. Scanner Setup	• Download OVA → Deploy (VMware/Hyper-V)<br>• Activate in Qualys UI → Verify via diagnostics	
3. QGS (Gateway Service)	• Proxy b/w agents & Qualys Cloud<br>• Caches, filters & encrypts traffic (port 443)<br>• Used in restricted networks	
4. Required Ports	Linux: 22 (SSH, sudo user)<br>Windows: 445 (SMBv2), 135 (WMI), NTLMv2<br>Both: 443 to Qualys Cloud	
5. Certificate Assessment	• Detect expired, weak, or self-signed certs<br>• Module: CertView / VMDR-CA<br>• Alerts on expiring SSL/TLS certs	
6. Asset Identification	• Manual inventory (CSV upload)<br>• Discovery scans, Qualys Agents, Cloud connectors<br>✅ Combo = full visibility	
7. External vs Internal Scanners	• Internal → LAN scans<br>• External → Internet-facing systems<br>✅ Use both for full coverage	
8. Prioritization	• Based on QDS, TruRisk, Severity, Exposure<br>• Critical + exploitable + internet = top priority	
9. Modules Used	• VMDR, SCA, Agent, WAS<br>• Optional: PC, CertView	
10. Use of QGS	• Secure proxy, cache, encrypt agent data<br>• Reduces direct cloud comms<br>• Helpful in air-gapped setups	
11. Handling Exceptions	• Use RTP/ARD → record justification<br>• Approved = excluded from reports<br>• Filter QIDs in reports	
12. Zero-Day	• Vendor unaware, no patch available<br>• VM team → monitor, apply WAF/IPS mitigations<br>• Eg: Log4Shell	
13. Agent Troubleshooting	• Check asset status, creds, port 443, agent service<br>• Review logs /var/log/qualys or C:\ProgramData\Qualys\Log	
14. Encryption (Agent ↔ Cloud)	• TLS 1.2+, Cert auth, AES-256 at rest<br>• Optional QGS encryption tunnel	
15. Auth vs Unauth Scans	• Auth = creds → deep accurate<br>• Unauth = no creds → surface only<br>✅ Auth = fewer false positives	
16. Agent vs IP Findings	• Agent = local + continuous<br>• IP = network snapshot<br>• Timing, access & scope cause differences	
17. False Pos/Neg	• FP = shown but not real<br>• FN = missed but real<br>• Fix: Auth scans + manual validation	



---

⚙️ Quick Interview:
🔹 Agent uses HTTPS (443) → Qualys Cloud.

🔹 QGS = Smart proxy + cache.

🔹 VMDR + TruRisk = prioritize smartly, not blindly by CVSS.

🔹 Authenticated scans = fewer FP, better compliance mapping.

🔹 Use ARD/RTP for exceptions & QID exclusion for clean reports.



---