---

## ⚡ AWS CloudTrail – What It Monitors

- CloudTrail tracks API activity across all AWS services, focusing on who did what, when, and from where.
- Think of it as the “action logger” of AWS.

### Monitors:

- Management Events: API calls to manage resources (EC2 start/stop, IAM policy change, S3 bucket create/delete).

- Data Events: Access-level actions (GetObject, PutObject in S3; InvokeFunction in Lambda).

> CloudFormation, STS, IAM, KMS, ECR, GuardDuty, Config — basically every service that uses AWS APIs.

- Console + CLI + SDK activity (any user or role).


🧩 Analogy: Like Qualys or Sentinel audit logs — captures every “who touched what” action.


---

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