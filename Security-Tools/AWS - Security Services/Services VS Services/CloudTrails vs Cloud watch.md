## CloudTrail — Monitors (corrected)

- **Management Events:** API calls that manage resources (e.g., `RunInstances`, `StopInstances`, `CreateBucket`, `PutBucketPolicy`, `CreateKey`, `DisableKey` for KMS).

- **Data Events:** Resource-data operations (e.g., `GetObject` / `PutObject` for S3, `Invoke` for Lambda). Note: data events are not enabled by default and may incur extra charges.

- **Services covered:** CloudTrail logs API activity for nearly every AWS service that uses APIs — e.g., **EC2, S3, VPC, IAM, STS, CloudFormation, ECR, KMS**, etc.

- **Sources:** Console, CLI, SDKs, and service-to-service API calls.

- **Integration:** GuardDuty consumes CloudTrail logs (including KMS events) for threat detection; logs can be archived to S3 or queried via Athena / CloudWatch for investigations.

🧩 Analogy: Like Qualys or Sentinel audit logs — captures every “who touched what” action.



## ⚙️ Amazon CloudWatch – What It Monitors

CloudWatch tracks performance, health, and logs across AWS resources — the “pulse monitor” of AWS.

### Monitors:

- Compute: EC2 (CPU, disk, memory), Lambda (invocations, duration, errors), ECS/EKS containers.

- Storage: EBS (I/O ops, throughput), S3 (requests, latency via CloudWatch metrics).

- Networking: VPC Flow Logs, NAT, ELB, API Gateway, Route 53 health checks.

- Applications: Custom metrics, app logs, and performance dashboards.

- Security: Metrics from GuardDuty, WAF, Config, and CloudTrail via metric filters.


🧩 Analogy: Like a mix of Dynatrace + Qualys EDR telemetry, showing system behavior rather than configuration risk.


---