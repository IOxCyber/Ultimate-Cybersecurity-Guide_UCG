## AWS Guard Duty: `Threat Detection Service`
- Monitor AWS Env. by analysing the CloudTrail logs, VPC flow logs, DNS logs queries, S3 Data Events, Malicious IP, Domain, File Hashes etc.

> Enable GuardDuty → Network Metadata auto-taps into VPC, CloudTrail, DNS telemetry → Analyzes → Alerts on suspicious activity.

```
Foundational Logs:
1. CloudTrail logs (API calls & user activity)
2. VPC Flow Logs (network traffic metadata)
3. DNS query logs
4. Threat intel feeds (malicious IPs, domains, file hashes)
```


## AWS GuardDuty – Data Sources & Visibility

| **Resource**          | **What GuardDuty Sees** |
|------------------------|--------------------------|
| **EC2 Instances**      | Network traffic patterns, API actions (e.g., unauthorized SSH, port scans) |
| **S3 Buckets**         | Unusual access (e.g., data exfiltration from public IPs, cross-region reads) |
| **VPCs / Subnets**     | Suspicious inbound/outbound traffic (botnets, crypto mining) |
| **IAM Users / Roles**  | Unusual API activity (e.g., logins from unknown geographies, privilege escalations) |
| **Lambda Functions**   | Suspicious invocations observed via CloudTrail logs |
| **EKS (Kubernetes)**   | Optional – EKS Audit Logs integration for cluster-level detections |
| **KMS (Key Management Service)** | Unusual key usage patterns (e.g., unexpected Decrypt, DisableKey, or ScheduleKeyDeletion API calls captured in CloudTrail) |


## Protection Plans for GuardDuty:
- Optional: S3 protection, EKS protection, Malware Protection, RDS protection, Lambda Protection
- Foundational (Required & can't be disabled) ie. Cloudtrail, VPC network flow, DNS Query logs

> AWS Detective (Root Cause Service), used to detect the threat/Malware/anomalies in the AWS resources i.e EBS volume, EC2, S3. Eg. backdoor, unauthorised access, crypto mineing, unauth Portscans etc

## How the Communication & Data Flow Happens

1. Every AWS resource interaction → API call
- EC2 start, S3 access, IAM login, etc.

2. CloudTrail logs those API calls.

3. VPC Flow Logs track network level communication between resources.

4. DNS Logs capture domain resolutions by EC2 or other workloads.

5. GuardDuty consumes copies of these logs internally.
> (no agents, no storage setup for GuardDuty deployment)

6. It analyzes them with machine learning & threat intel feeds, filter out with severity (Criteria, Medium, High, Low), finding type, Resource url

7. If anomalies or known threats are found → Findings generated → sent to Security Hub/EventBridge/SNS.

> A finding can be suppressed (hidden/archives from the detection)


## Usage:
- The total daily cost estimation of the usage of the Guard duty.