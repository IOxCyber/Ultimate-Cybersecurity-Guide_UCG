## Basics:
-  Both models gives a `way of transmitting data over the internet.`
- was driven by the `need for standardization and a systematic approach to understanding and implementing network communication.`
-  `need for devices from different manufacturers to communicate`
- `breaking down the complex task of network communication into manageable parts`

## TCP vs OSI: `Protocol vs Reference Model`
![image](https://github.com/IOxCyber/CyberEssentials/assets/40174034/daa490c9-983d-471d-9479-75d26d1f4237)


## 1. TCP/IP; `4 Layers`
- Practical model that addresses specific communication challenges and relies on standardized protocols.
- Widely implemented in the ARPANET, the precursor to the modern internet & designed and developed by the United States Department of Defense.

```
Link Layer (or Network Access Layer)
Internet Layer
Transport Layer
Application Layer
```


## 2. OSI serves: `7 Layers`
- a comprehensive, protocol-independent framework designed to encompass various network communication methods.
- It was introduced later as a conceptual framework in the late 1970s by the International Organization for Standardization (ISO).

| Layer Name         | Function (2 words)         | Protocols / Data Units                   | Devices Used                     | Common Attacks                        |
|--------------------|----------------------------|------------------------------------------|----------------------------------|----------------------------------------|
| **Physical (L1)**  | **Transmit Bits**          | Cables, RF, Fiber, IEEE 802.11, 802.3    | Hubs, Repeaters, NIC             | Wiretapping, Signal Jamming, Sniffing |
| **Data Link (L2)** | **Frame Handling**         | Ethernet, ARP, PPP, MAC                  | Switches, NIC                    | MAC Spoofing, ARP Poisoning, STP Attacks |
| **Network (L3)**   | **Path Determination**     | IP, ICMP, IGMP, ARP                      | Routers (L3)                    | IP Spoofing, MITM, Routing Attacks    |
| **Transport (L4)** | **Reliable Delivery**      | TCP, UDP, SCTP                           | Gateways, Firewalls (L4-aware)  | SYN Flood, UDP Flood, Port Scanning   |
| **Session (L5)**   | **Session Control**        | NetBIOS, PPTP, SIP, RTP                  | Gateways, Proxies               | Session Hijacking, DoS                |
| **Presentation (L6)** | **Data Formatting**     | SSL/TLS, JPEG, MPEG, ASCII, Encryption   | None specific (Software layer)  | SSL Stripping, Malware in file formats |
| **Application (L7)** | **User Interface**       | HTTP, DNS, FTP, SMTP, SSH, POP3, SNMP    | Application Servers, Proxies    | XSS, SQLi, CSRF, Buffer Overflow       |

---


---

### 🛠️ Real-Life Implementation
| Site/Service          | Layer-Related Examples                                        |
|-----------------------|---------------------------------------------------------------|
| **Wireshark**         | Captures traffic from L1–L7 (great for analyzing all layers)  |
| **BurpSuite**         | Focuses on L7 (Application Layer attacks)                     |
| **Cisco Routers**     | Operate primarily on L3 (Routing/IP-based decisions)          |
| **Firewalls (Palo Alto, CheckPoint)** | Inspect L3–L7 depending on NGFW capabilities   |
| **VoIP Services (Zoom, Skype)** | Use L5–L7: SIP, RTP, TLS                             |

---
