## Data Flow Diagram:

```
[ CloudTrail / VPC Flow / DNS Logs ]  
             │  
             ▼  
[ GuardDuty ] (Threat Detection)  
             │  
[ Inspector / Config / Macie ] (Vuln & Compliance)  
             │  
             ▼  
[ Security Hub ] (Aggregation + Correlation)  
               │  
     ┌───────┴─────────┐  
     ▼                    ▼  
[ EventBridge ]     [ Dashboard / Console ]  
              │  
              ▼  
┌───────────┬───────────┐  
│             │             │  
[SNS]      [Lambda]      [Step Functions via SSM]  
│             │             │  
▼             ▼             ▼  
(Email/SMS   (Automated   (Patching / Isolation  
Alerts)     Response)      /SG changes)
```