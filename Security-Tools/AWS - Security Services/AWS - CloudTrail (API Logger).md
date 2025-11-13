---

# AWS CloudTrail Summary:
- Purpose: Tracks all API activity (Data & Management events) across AWS accounts for governance, compliance, and incident investigation.


---

## ✅ Key Points:

- Captures all API calls made within or outside AWS Console, SDKs, CLI, or Services.

> Records: who did what, from where (source IP), and when.

### Event Types:

1. Management Events: Actions on AWS resources (e.g., EC2 creation, S3 bucket deletion).

2. Data Events: Object-level operations (e.g., GetObject, PutObject in S3, Lambda Invoke).


> Agentless: Yes, collects events natively (no installation needed).

### Integrations:

- AWS GuardDuty: Uses CloudTrail logs to detect anomalies and threats.

- CloudWatch Logs / EventBridge: For alerting and automation.

- S3 / Athena: For long-term storage and querying.


> Log Encryption: Logs can be encrypted with KMS keys (Customer Managed Key optional).

### Multi-region: Can be configured to capture events across all regions.



---

### Example Use Case:
- Detect unauthorized API call to stop EC2 instances → GuardDuty triggers an alert using CloudTrail event logs.


---