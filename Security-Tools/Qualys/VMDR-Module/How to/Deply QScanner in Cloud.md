# Qualys Scanner Deployment Guide (AWS + Azure)


---

1. Deploying Qualys Scanner in AWS (Marketplace Method)

Prerequisites

Qualys subscription (VM/PC/WAS)

Qualys Scanner Activation Code

IAM permissions to launch EC2

A subnet with Internet access (NAT/IGW)

Security Group allowing outbound 443



---

Step-by-Step

Step 1 — Open AWS Marketplace

AWS Console → AWS Marketplace → Search "Qualys Virtual Scanner Appliance"

Step 2 — Select the Scanner Image

Product → Qualys Virtual Scanner Appliance → Continue to Subscribe

Step 3 — Configure the EC2

Choose Instance Type:

t2.medium or t3.medium (recommended)

Select VPC & Subnet where scanning is required

Attach a Security Group:


Security Group Rules

Outbound:
  - HTTPS (443) → 0.0.0.0/0

Inbound:
  - None required (scanner initiates all traffic outbound)

Step 4 — Launch the Instance

Launch EC2 → Wait for instance to boot (~2 min)

Step 5 — Activate the Scanner

Open EC2 Console → Get Public IP / Private IP
Connect to console (EC2 serial console recommended)

Enter:

Qualys Activation Code
Qualys Platform URL (example: https://qualysguard.qg3.apps.qualys.com)

Step 6 — Verify Registration

Qualys Console → Scans → Appliances → Scanner shows as Active


---

2. Deploying Qualys Scanner in Azure (Marketplace Method)

Prerequisites

Qualys subscription

Scanner Activation Code

Azure permissions to deploy VM

Subnet with Internet outbound

NSG permitting outbound 443



---

Step-by-Step

Step 1 — Open Azure Marketplace

Azure Portal → Marketplace → Search "Qualys Virtual Scanner"

Step 2 — Create the VM

Create → Choose Subscription + Resource Group

Recommended VM Size:

Standard B2ms / D2s_v3

Step 3 — Configure Networking

Select:

VNet

Subnet

Public IP (optional)

NSG rules:


NSG Rules

Outbound:
  - HTTPS (443) → Internet

Inbound:
  - None required

Step 4 — Launch the VM

Review + Create → Deploy

Step 5 — Activate

Open VM Serial Console → enter:

Activation Code
Qualys Platform URL

Step 6 — Verify

Qualys Console → Scans → Appliances → Status: Connected


---

3. Important Notes

Do I need multiple scanners?

Scenario	Scanner Needed?	Why

Multiple VPCs / VNets NOT connected	Yes (1 per network)	No routing
Peered VPCs / VNets	Optional	Scanner can route across
Transit Gateway setup	Optional	Central scanner works
Only Agent-based scanning	No scanner required	Agents send data directly



---

4. Ports & Communication Requirements

Module	Scanner Needed	Ports Required	Direction

VM (IP-based Scan)	Yes	22, 135, 445, 161, etc.	Scanner → Target
PC (Compliance)	Yes	Same as above	Scanner → Target
WAS	Yes	80, 443	Scanner → Web App
Agent-based VM	No	443 only	Agent → Qualys Cloud



---

5. Quick Memory Trick

Scanner → Needs to reach targets
Agent → Needs only outbound 443
WAS → Uses Scanner for crawling + attacks


---