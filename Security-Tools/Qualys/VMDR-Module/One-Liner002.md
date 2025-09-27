1. Cloud Agent operates with `System Level Privileges`.
2. VM Scanning Engines:
- Core Engines: Launches modules specific to each hosts.
- Modules: Collect config data from target hosts. eg. Host Discovery > Port Scanning > Service Detection > OS Detection
3. In General, SYN (Stealth Scan) perfromed by Qualys.
4. Unauth scans rely on TCP/IP stack fingerprinting. eg. TTL,MSS, Windows Size etc
5. By default, `Data collection intervel is every 240 mins`/4 hrs by Cloud Agent. 
>  NOTE: The countdown to the very next interval will begin as soon as the data transfer and postprocessing steps have been completed.
6. Cloud Agents settings can be modify in `Configuration Profiles` Cloud Agent > Configuration Profiles (Agents, Activation Keys)


7. Qualys Asset Group Management Service (AGMS): new service, introduced `to improve performance related to Asset Management & Asset Group Management functionality.`
    
