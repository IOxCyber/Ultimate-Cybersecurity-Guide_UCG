# Scan Components: `Go to VM/VMDR > Scans > Scans > New > Scan`

## 1. Option Profile: `Scan settings` 
- `VMDR > Scans > Option Profiles`
- `Scan Settings`, Ports to scan (TCP/UDP), Perform 3-way handshaking, Vuln to detect/QIDs to include, Authentication, `Map Settings`, Overall performance, TCP/UDP Ports, `Additional Settings`, Host Discovery (Packet Options)
- Default Option Profile: `Initial Option(default)`
- ![image](https://github.com/user-attachments/assets/fca79fa0-9028-448d-91cb-229075ee1c18)
- ![image](https://github.com/user-attachments/assets/728ff07f-5725-4105-97e2-35ee3eb78b18)

### Note: For Authenticated Scans (set up Authentication Records `VM > Scans > Authentication > New record`)
- ![image](https://github.com/user-attachments/assets/31856f37-2718-4746-a42e-8c79a76c32b4)

## 2. Scanner Appliance: `Used to scan internal assets`
- `VMDR > Scans > Appliances > New >`
- A dedicated `device or virtual machine` deployed within the network.
- To conduct in-depth network-based scans, including authenticated and non-authenticated scans.
- `External Scanner: Included in Qualys Subs` to scan external public IPs
- `Virtual Scanner/Appliance: Need to set up`, To scan internal assets.

### Qualys Gateway Service (QGS): `Acts as a proxy between the internal network and the Qualys Cloud Platform`
- Routes scan data from internal scanners to the Qualys Cloud Platform over a secure, encrypted connection, eliminating the need to open inbound firewall ports or strict firewall rules.
- Typically, this involves allowing HTTPS (port 443).

## 3. Target Host Assets:
- Select the Assets option to specify the scan target using any combination of IP addresses, asset groups and FQDNs.
- Option 1: Net Blocks (`IP/IP range`)
- Option 2: `Asset Groups` (Any Host in subs can be added to the asset group)
- Option 3: `Asset Tags` (a way to manage assets in Dynamic/Automated Solution)
- ![image](https://github.com/user-attachments/assets/44c7df4d-c99c-4dad-a493-c4dde96e9866)

> FQDN(s) - Option Visible only when the DNS Tracking feature is enabled for your subscription.
### Note: `All = AND` & `ANY = OR`
