## SecurityHub: CSPM tool + Aggregate findings

- Performs Security best practices/complaince checks(PCIDSS, NIST, ISO 27K1 etc), aggregates findings, alerts & enables automated remediation action across all AWS accounts & environment.

> Ingest Finding from various AWS services like GuardDuty, Config, Inspector, AWS health, 3rd party Services SIEM, Firewall etc) & `normalised in AWS Security Findings Format(ASFF)` before injecting.

### Working: Findings > Injected to SecurityHub > Events > EventBridge > SNS, Alerts, ITSM tickets.

- <img width="1089" height="525" alt="1763558714997519974228996299474" src="https://github.com/user-attachments/assets/0657eea8-be91-4cc5-b7e8-cc92332ee525" />

## Modules:
- Summary: All findings with Security Score, Resource, Region
- Controls: 
- Security Standards: Compliance with industry standards, Control failed,passed, score etc
- Insights
- Findings
- Integration
- Automations
- Settings


- 