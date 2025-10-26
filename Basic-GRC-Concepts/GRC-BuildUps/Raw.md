## What Will You Assess? {Assets, People, Technology}

🔹 1. Assets (What to Inventory)

Servers, databases, applications (web, mobile, APIs)

Endpoints (staff devices, POS machines, medical devices)

Cloud platforms (AWS, Azure, etc.)

Third-party integrations (fintech APIs, lab partners, insurance)

Data types: cardholder data, SSNs, health records, logs


🔹 2. People (Who & What to Evaluate)

Roles with privileged access (admins, DBAs, doctors, cashiers)

Awareness levels (training, phishing readiness)

Onboarding/offboarding processes

Insider threat potential (intentional & unintentional)


🔹 3. Technology & Controls

Firewalls, antivirus, EDR/XDR

Patch/vulnerability management tools (like the ones you know!)

Encryption in transit & at rest

Logging/monitoring (SIEMs like Splunk, Dynatrace)

MFA, IAM, least privilege enforcement



---

## Baselines, Frameworks & Standards to Use

For Banks:

PCI-DSS (for payment data)

NIST CSF (core risk assessment framework)

FFIEC CAT Tool (cyber maturity for banks)

GLBA (privacy rule)


For Healthcare:

HIPAA Security Rule (Technical, Admin & Physical Safeguards)

NIST 800-66 (Risk Assessment & Safeguards Mapping)

NIST CSF (same as banking — widely adopted)



---

## Risk Assessment Flow (Explain This in Interview)

Step 1: Define Scope & Identify Assets

“We start by identifying critical assets — servers, apps, sensitive data, and integrations.”


Step 2: Identify Threats & Vulnerabilities

“We use threat intelligence (e.g., MITRE ATT&CK) and known vulnerability databases (e.g., CVEs).”


Step 3: Assess Controls

“We evaluate the effectiveness of existing security controls using CIS Top 18, NIST CSF, etc.”


Step 4: Analyze & Score Risk

“Using risk = Threat × Vulnerability × Impact, we rank the risks from critical to low.”


Step 5: Recommend Mitigations

“For each high-risk item, we propose control improvements or compensating controls.”


Step 6: Document & Report

“We produce a Risk Register, Gap Analysis, and a Remediation Plan.”



---

Real-World Example:

Bank: A misconfigured firewall exposes a legacy API used for customer fund transfers. Risk: External threat actor abuse → unauthorized transfers. Fix: Apply network segmentation + WAF + IAM tightening.

Healthcare: An outdated EMR server missing patches. Risk: Ransomware encrypts ePHI. Fix: Patch immediately + isolate + strengthen backups.


---