## Understanding the Qualys Detection Score
- The Qualys Detection Score (QDS) is assigned to vulnerabilities detected by Qualys. QDS has a range from 1 to 100 and with four severity levels:

- Critical: 90-100

- High: 70-89

- Medium: 40-69

- Low: 1-39

## QDS is derived from the following factors:

a) Vulnerability technical details (CVSS score): The highest Qualys Vulnerability Score (QVS) for CVEs is associated with the QID.

b) Vulnerability temporal details: Monitors external threat intelligence details for a vulnerability and collect data like Exploit Code Maturity (ECM), malware, active threat actors, and if a threat is trending.

c) Vulnerability remediation details (CIDs): Applies mitigation controls to mitigate the risk from the vulnerability. Vulnerabilities that have applied mitigation controls via Qualys compliance modules will have reduced risk scores.
