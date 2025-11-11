## AWS Encryption: `Cloud Data Protection`
- KMS (like Azure Key Vault service for key mgmt)
- Provides keys to encrypt the Data at rest(AES 256) and at Transit(TLS/SSL) flowing in or across AWS Services.

- Data At Rest (S3, EBS Elastic Block Service, RDS, DynamicDB)
- Data at Transit (Web, API, SSH for CLI)

- API Logs tracks via CloudTrail Service.

## AWS Guard Duty: `Threat Detection Service`
- Monitor AWS Env. by analysing the CloudTrail logs, VPC flow logs, DNS queries, Mal IP, Domain, File Hashes etc.

> Enable GuardDuty → N/w Metadata auto-taps into VPC, CloudTrail, DNS telemetry → Analyzes → Alerts on suspicious activity.

```
AWS GuardDuty is a managed threat detection service that continuously monitors your AWS environment by analyzing:

CloudTrail logs (API calls & user activity)

VPC Flow Logs (network traffic metadata)

DNS query logs

Threat intel feeds (malicious IPs, domains, file hashes)
```




