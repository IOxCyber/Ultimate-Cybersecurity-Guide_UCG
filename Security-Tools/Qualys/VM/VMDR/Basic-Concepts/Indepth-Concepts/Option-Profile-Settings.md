
# Option Profile is the setting for scanning a host.

## Perimeter Scan: `Unauth scan for External facing IPs`
- `Full scan setting` for TCP/UDP (All 65535 Ports), non-authenticated for daily scans.
- `Load balancers` are meant to be invisible, can be added additionally. QID: 86189
- Qualys HTTP Header: To identify the Qualys traffic in networks.
- `No authentication should be used in perimeter scans.`
- Parallel Scaling Setting:
- ![image](https://github.com/user-attachments/assets/21358dee-f230-4dfd-a753-eff13482dfaa)


## On-Prem Scan: `Authenticated Scan of Internal Infrastructure`
- Std UPD/TCP ports
- `Full scan setting` for TCP/UDP (All 65535 Ports), non-authenticated for daily scans.
- `Load balancers` are meant to be invisible, can be added additionally. QID: 86189
- Additional Certificate Detection, adds more time to scan but detect the certificates.
- Enable `Parallel scaling` to boost the performance.
- Dissolve Agent: Build for specific registry keys, removed after scan complete for a highly secured assets.
- Can add MAX 50 internal scanners.
- Qualys HTTP Header: To identify the Qualys traffic in networks.
- Parallel Scaling Setting:
- ![image](https://github.com/user-attachments/assets/9ca2856c-c19e-49c3-98f9-d4451e5e71ef)


## Cloud Perimeter Scan: `To scan publically exposed EC2, Azure instances`
- Uses visibility data from Qualys Cloud Conectors.
- Connectors > Scans > Cloud Perimeter Scan's Config Settings > Save
- Connectors > Cloud > Select Cloud Type > Edit any EC2 instance >  Basic Details: AssetView (checked) > Tags and Activation >



