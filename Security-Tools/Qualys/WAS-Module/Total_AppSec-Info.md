## AppSec Module:
- Use to assess Web Apps, API based on OWASP top 10 Security checks, web malware detection and PII exposure detection.
- Used in Asset Discovery, Risk Assessments, Remediation response etc.

## Challenges:
- No Centralized discovery of web apps & APIs in mukticloud env.
- Limited API security checks e.g missing compliance testing for OAS v3 (OpenAPI Specification)


## Knowledge Base: 
- `Qualys managed Repo containing Vuln signature`
- Reference to `OWASP top 10, WASC (Web AppSec Consortium) & CWE (Common Weakness Enumeration)
- eg. `vulnDef.category:"web application"`
- Information: Remote (No Auth Needed)

## Custom Signature:
- `Allow organizations to create their own detection rules`
- Required for Custom Signature: `Basic Info, Threat, Impact, Solution & enter a Valid Signature`
- Use to extend the detection logic.
- Custom Signature ID starts with `655`
- Web Application detection ID starts with `150`