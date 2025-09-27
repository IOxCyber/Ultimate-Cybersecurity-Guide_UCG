1. Asset Risk Score (ARS): AKA `TruRisk Score`, (Range: 0-1000) `token = riskScore`
2. Qualys Vulnerability Score (QVS) is a Qualys-assigned score for a vulnerability based on multiple factors eg. CVSS and external factors (active exploitation, likelihood of vulnerability being exploited in wild, sighting in the darkweb and social web, exploit code maturity, CISA known exploitable and many more.)
3. QDS: `Qualys Detection Score` (Score given to Vuln by Qualys) `Range 1-100` Low: 1-39, Medium: 40-69, High: 70-89, Critical: 90-100 `token = vulnerability.detectionScore`
4. QID: `Unique Qualys ID` given to Vulnerabilities.
5. Asset Criticality Score (ACS): (Range: 1-5) Determined by its assigned Asset Tags. `Default score: 2` `token = criticalityScore`
- The Asset Criticality Score that is based on Asset Groups cannot be changed in the Asset Tags section. Go to VMDR -> Assets -> Asset Groups and modify the Business Criticality for the Asset Group.

---
---

6. TruRisk: `Data-Driven Way To Prioritize Risks`, comprises of `(Qualys Detection Score (QDS) + Asset Criticality Score (ACS) + Asset Risk Score (ARS)`
> Both QDS and ARS are calculated values, while ACS is assigned to assets via Asset Tags.
- ![image](https://github.com/user-attachments/assets/8ed9a3b5-798b-45a3-a0c8-9bb2890d8d7f)
- ![image](https://github.com/user-attachments/assets/a8b2e1e7-d227-45bc-8d70-93a336a86500)
