# Tracking Methods: 
- Specifies how vulnerability findings will be tracked or indexed.

## 1. IP Address: Static IPs, Simplest way to add a host.
```
IPs may be entered in any of the following formats:
• List of single IPs 17.16.20.5, 17.16.20.21
• IP ranges 167.216.205.1-167.216.205.254
• CIDR 192.168.0.87/24      #/24 represents the Network Bits (Network-Host)
```

## 2. DNS Tracking: Dynamic IPs, Based on Asset DNS name. (Relying on DHCP to acquire Host's IP addresses)
- Uses the `Fully Qualified Domain Name (FQDN)`
- eg. `webserver.company.com`

## 3. NetBIOS: For Windows Assets, tracking by NetBIOS names.
- AKA Computer Name, `Cmd > nbtstat -n` OR `Right-click on 'This PC' > Check in Properties`

## 4. Qualys Agent Tracking: Assets tracked by Cloud Agent Installation (Qualys Host ID)
- The Qualys Host ID is universally unique (i.e., UUID) and is only available for “scannable” host assets when the “Agentless Tracking” feature is enabled.
- Unified View refers to a single record for the asset that includes both scan and agent data.

## 5. EC2 Instance ID: Based on Amazon EC2 instance ID
