---

# Qualys Scanner Deployment in AWS (VPC-wise)

## Scenario 1: Multiple VPCs (NOT Connected)
Each VPC is isolated → Needs its own Qualys Scanner.

Region: ap-south-1
└── VPC-1 (10.0.0.0/16)
    └── [Qualys Scanner #1]
        └── Scans EC2s inside VPC-1 only

Region: ap-south-1
└── VPC-2 (172.16.0.0/16)
    └── [Qualys Scanner #2]
        └── Scans EC2s inside VPC-2 only

Region: ap-south-1
└── VPC-3 (192.168.0.0/16)
    └── [Qualys Scanner #3]
        └── Scans EC2s inside VPC-3 only

**Reason:**  
VPCs are isolated → No routing → Scanner cannot reach other VPCs.

---

## Scenario 2: Multiple VPCs Connected via Peering / TGW
One Shared-VPC can host a single Qualys Scanner and scan all connected VPCs.

Region: ap-south-1
└── Shared Services VPC (10.0.0.0/16)
    └── [Qualys Scanner #1]
        └── Can scan across connections:
            ├── VPC Peering
            ├── Transit Gateway (TGW)
            └── Hub-and-Spoke Architecture

VPC-2 (172.16.0.0/16)
└── Connected → routed → scanned by same scanner

VPC-3 (192.168.0.0/16)
└── Connected → routed → scanned by same scanner

**Requirement:**  
- Route tables configured  
- SG/NACL allow traffic  
- Authentication ports open (22/445 etc.)

---

## Quick Comparison Table

| Architecture Type | VPCs Connected? | Scanner Needed | Reason |
|-------------------|-----------------|----------------|--------|
| Isolated VPCs     | No              | One per VPC    | No routing between VPCs |
| Peered VPCs       | Yes             | One shared     | Scanner can reach all subnets |
| TGW Hub-Spoke     | Yes             | One shared     | Central routing hub |
| Multi-Region      | N/A             | One per Region | Peering is regional only |

---

## Memory Rule
**Scanner = EC2**  
EC2 scans **only** what routing + firewall allows.  
If VPCs cannot talk → Scanner cannot scan.


---