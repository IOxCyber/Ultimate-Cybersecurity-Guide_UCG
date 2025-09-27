# Scan Types in Qualys:

## 1. `Authenticated Scans`
- `Definition`: Authenticated scans require credentials to log into the system.
    - These scans provide more accurate and comprehensive results by interacting directly with Windows's registry settings, configuration files, and In Linux by executing commands.
    - Perform `in-depth analysis and obtain detailed` information about the system.

### `Examples of Scans`:
  - `Compliance Scans`: Assess adherence to policies and standards (e.g., PCI-DSS, HIPAA).
  - `Vulnerability Assessment`: Identifies vulnerabilities with higher accuracy.
  - `Configuration Assessment`: Checks for misconfigurations and policy compliance.
### `Advantages`:
  - More accurate and comprehensive results.
  - Can interact with the system's internals configurations.
  - Fewer false positives compared to non-authenticated scans.

## 2. `Non-Authenticated Scans`
- Non-authenticated scans do not require credentials and do not log into the system.
- They are also known as agentless scans.
- These scans rely on network-exposed services and ports to produce results and are more prone to false positives.
- To quickly identify visible vulnerabilities and assets without needing system credentials.

 ### `Examples of Scans`:
  - `Basic Network Scan`: Identifies open ports and services.
  - `Host Discovery`: Detects active hosts on the network.
  - `Map Feature in Qualys`: Maps the network to identify live hosts and services.

### `Advantages`:
  - Easier to set up since no credentials are needed.
  - Useful for initial assessments and discovering network exposure.

### `Disadvantages`:
  - Higher likelihood of false positives.
  - Limited depth of analysis compared to authenticated scans.
  - Can be blocked or limited by network defenses like IDS/IPS.

## 3. `Agent-Based Scans`
- Agent-based scans use lightweight agents installed on the systems to perform assessments.
- These scans produce accurate results by leveraging system-level privileges and reduce network overhead.
- To scan remote devices, dynamic assets, and systems that are not always connected to the network.

### `Examples of Scans`:
  - `Continuous Monitoring`: Provides ongoing assessment and alerts for new vulnerabilities.
  - `Dynamic Asset Scanning`: Scans devices that frequently change locations or network environments.
  - `Remote Device Scanning`: Assesses devices which are not constantly connected to the corporate network.

### `Advantages`:
  - More accurate and comprehensive due to direct system access.
  - Reduced network overhead.
  - Effective for scanning remote and dynamic assets.
### `Disadvantages`:
  - Requires installation and management of agents on all target systems.

## Additional Scan Types in Qualys
- `Web Application Scanning`: Specifically targets web applications to identify vulnerabilities like SQL injection, cross-site scripting (XSS), and others.
- `Patch Management Scanning`: Assesses the status of patches on systems and helps in identifying missing patches.
- `Cloud Assessment Scanning`: Scans cloud infrastructure for vulnerabilities and misconfigurations.
- Perimeter Scan: Without authentication, it is for public DNS or public-facing IPs.



