### 🧩 QUALYS VM INTERVIEW REVISION SHEET

#	Topic	Key Points (Easy Recall)

1. Agent vs IP Scan:
- IP-based → static IPs, servers & scheduled.
- Agent-based → laptops, roaming endpoints & continuous.

2. Scanner Setup:
- Download OVA → Deploy (VMware/Hyper-V)<br>• Activate in Qualys UI → Verify via diagnostics	

3. QGS (Gateway Service):
- Proxy b/w agents & Qualys Cloud<br>• Caches, filters & encrypts traffic (port 443)<br>• Used in restricted networks	

4. Required Ports:
- Linux: 22 (SSH, sudo user)<br>Windows: 445 (SMBv2), 135 (WMI), NTLMv2<br>Both: 443 to Qualys Cloud	

5. Certificate Assessment:
- Detect expired, weak, or self-signed certs<br>• Module: CertView / VMDR-CA<br>• Alerts on expiring SSL/TLS certs	

6. Asset Identification:
- Manual inventory (CSV upload)<br>• Discovery scans, Qualys Agents, Cloud connectors<br>✅ Combo = full visibility	

7. External vs Internal Scanners:
- Internal → LAN scans<br>• External → Internet-facing systems<br>✅ Use both for full coverage	

8. Prioritization:
- Based on QDS, TruRisk, Severity, Exposure<br>• Critical + exploitable + internet = top priority	

9. Modules Used:
- VMDR, SCA, Agent, WAS<br>• Optional: PC, CertView	

10. Use of QGS:
- Secure proxy, cache, encrypt agent data<br>• Reduces direct cloud comms<br>• Helpful in air-gapped setups	

11. Handling Exceptions:
- Use RTP/ARD → record justification<br>• Approved = excluded from reports<br>• Filter QIDs in reports	

12. Zero-Day:
- Vendor unaware, no patch available<br>• VM team → monitor, apply WAF/IPS mitigations<br>• Eg: Log4Shell	

13. Agent Troubleshooting:
- Check asset status, creds, port 443, agent service<br>• Review logs /var/log/qualys or C:\ProgramData\Qualys\Log	

14. Encryption (Agent ↔ Cloud):
- TLS 1.2+, Cert auth, AES-256 at rest<br>• Optional QGS encryption tunnel	

15. Auth vs Unauth Scans:
- Auth = creds → deep accurate<br>• Unauth = no creds → surface only<br>✅ Auth = fewer false positives	

16. Agent vs IP Findings:
- Agent = local + continuous<br>• IP = network snapshot<br>• Timing, access & scope cause differences	

17. False Pos/Neg:
- FP = shown but not real<br>• FN = missed but real<br>• Fix: Auth scans + manual validation	

18. Scanner = For IP-based scans → Uses its OWN TLS tunnel.

19. QGS = For Agent-based scans → Provides a tunnel FOR agents.

---

⚙️ Quick Interview:
🔹 Agent uses HTTPS (443) → Qualys Cloud.

🔹 QGS = Smart proxy + cache.

🔹 VMDR + TruRisk = prioritize smartly, not blindly by CVSS.

🔹 Authenticated scans = fewer FP, better compliance mapping.

🔹 Use ARD/RTP for exceptions & QID exclusion for clean reports.



🧩 Hotfix vs Patching in Vulnerability Management

Term	What (Purpose)	Why (Use Case)	Example	Extras / Relation

Hotfix	A temporary, quick fix for a specific issue or security bug	Immediate mitigation without full testing cycle	Microsoft releases KB5015807 to fix a specific Windows kernel vuln	- Emergency fix<br>- Often manually applied<br>- May be replaced by later cumulative patch
Patch	A permanent, tested update addressing one or more vulnerabilities	Regular, structured fix included in vendor patch cycle	Monthly “Patch Tuesday” updates from Microsoft	- Includes bug fixes, enhancements<br>- Tested & versioned before release



---
⚙️ VM (Vulnerability Management) Context
Aspect	Explanation::
Detection	Qualys identifies missing hotfixes/patches using QIDs (e.g., QID 105314: Microsoft KB missing)
Prioritization	High-risk vulnerabilities (e.g., exploited in wild) may trigger hotfix deployment first
Lifecycle	Hotfix → tested → merged into next patch → deployed via WSUS/SCCM or config management tool
Tracking	VM teams verify closure by rescanning — if QID still appears → patch/hotfix didn’t apply correctly.
