## AWS Security & Monitoring Services – Agent Requirement Summary

| **Service**        | **Agent Required?** | **Explanation** |
|--------------------|---------------------|-----------------|
| **CloudTrail**     | ❌ No | Native logging service that records all AWS API calls and management events automatically — no agent needed. |
| **CloudWatch**     | ⚙️ Optional | AWS services send logs/metrics automatically. For EC2, on-prem, or custom apps, CloudWatch Agent is needed for system-level metrics (CPU, memory, disk). |
| **GuardDuty**      | ❌ No | Threat detection service analyzing CloudTrail, VPC Flow, and DNS logs automatically — fully managed, no agent. |
| **Security Hub**   | ❌ No | Centralized dashboard aggregating findings from GuardDuty, Inspector, Config, etc. — no agent required. |
| **AWS Config**     | ❌ No | Tracks resource configurations and compliance via API calls — completely agentless. |
| **Inspector**      | ⚙️ Yes (Classic only) | Inspector Classic required EC2 agents. New **Inspector v2** is agentless and integrates via **AWS Systems Manager (SSM)**. |



### No agent hassle for most security services — AWS manages them natively. You only pay for:

1. CloudTrail → per event log stored (usually in S3).

2. CloudWatch → for metrics, dashboards, and custom logs.

3. GuardDuty → based on analyzed log volume (CloudTrail, DNS, VPC flow logs).

4. Config → per configuration item recorded.

5. Security Hub → per security check and active account.

6. Inspector → per EC2/ECR scan.


### Key takeaway:

> You just enable and configure, AWS does the collection internally — no agents, no maintenance.