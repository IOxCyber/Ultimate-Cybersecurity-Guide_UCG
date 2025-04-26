
# Firewall Evasion Techniques

Here are various firewall evasion techniques that can be used to bypass firewalls and IDS/IPS systems, along with examples of how they can be implemented.

## Firewall Evasion Techniques with Examples

| **Technique**                     | **What It Does**                                                              | **How to Perform Using Nmap/Tools**                                                                 |
|----------------------------------|-------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------|
| **Packet Fragmentation**         | Breaks payloads into smaller packets to avoid deep packet inspection.          | Nmap: `nmap -f` (this fragments the packets into smaller ones to bypass the firewall’s inspection).|
| **Source Port Manipulation**     | Uses ports that are typically trusted (like DNS, HTTPS, etc.) to sneak traffic through. | Nmap: `nmap --source-port 53 <target>` (using port 53, which is typically used for DNS).           |
| **Decoy Scanning**               | Sends packets from fake source IP addresses along with the attacker's IP to confuse detection systems. | Nmap: `nmap -D RND:10 <target>` (using 10 random decoys to confuse the IDS/IPS).                  |
| **Idle Scanning**                | Uses a "zombie" host to send packets to the target, keeping the attacker’s IP address hidden. | Nmap: `nmap -sI <zombie_ip> <target>` (using a third-party IP to do the scanning).                 |
| **Spoofed Source Address**       | Spoofs the source IP address to mislead the target or firewall about the origin. | Nmap: `nmap -S <spoofed_ip> <target>` (this fakes the source IP to avoid detection).                |
| **Tunneling**                    | Encapsulates malicious traffic inside permitted protocols (e.g., HTTP, DNS).   | Tools: `ssh -D` (can tunnel your traffic through a secure channel); `DNSCat2` for DNS tunneling.    |
| **Using Tor or Proxies**         | Routes traffic through an anonymous network like Tor or proxies to hide the attacker’s real IP address. | Tor: Use `torsocks nmap` (to route Nmap traffic over the Tor network).                            |
| **Timing (Slow Rate Scanning)**  | Sends packets slowly to avoid triggering rate-based detection systems (IDS/IPS). | Nmap: `nmap -T0` (the slowest scanning mode to avoid detection based on rate of packet transmission). |

## How These Techniques Help

- **Packet Fragmentation** and **Source Port Manipulation** help by breaking up traffic or using common ports to sneak through firewalls that are set to inspect traffic deeply.
- **Decoy Scanning** and **Idle Scanning** hide the origin of the scan, making it harder to trace back to the attacker.
- **Spoofed Source Address** can mislead IDS/IPS by hiding the real attacker's IP.
- **Tunneling** and **Tor/Proxies** make traffic look legitimate by using common, allowed protocols or anonymous networks.
- **Slow Rate Scanning** ensures that the traffic doesn’t trigger rate-based detection mechanisms like rate-limiting or threshold-based IDS/IPS.
