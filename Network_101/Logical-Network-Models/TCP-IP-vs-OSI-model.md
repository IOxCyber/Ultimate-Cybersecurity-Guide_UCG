## Basics:
-  Both models gives a `way of transmitting data over the internet.`
- was driven by the `need for standardization and a systematic approach to understanding and implementing network communication.`
-  `need for devices from different manufacturers to communicate`
- `breaking down the complex task of network communication into manageable parts`

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

| Layer Name         | Function                   | Protocols / Data Units                   | Devices Used                     | Common Attacks                        |
|--------------------|----------------------------|------------------------------------------|----------------------------------|----------------------------------------|
| **Physical (L1)**  | Transmit, Signals, Binary **Bits (0,1)**          | Cables, RF, Fiber, IEEE 802.11, 802.3    | Hubs, Repeaters, NIC             | Wiretapping, Signal Jamming, Sniffing |
| **Data Link (L2)** | Physical Addressing, Error Checking **Frame**         | Ethernet, ARP, PPP, MAC                  | Switches, NIC                    | MAC Spoofing, ARP Poisoning, STP Attacks |
| **Network (L3)**   | Logical Addressing **Path Determination**     | IP, ICMP, IGMP, ARP                      | Routers (L3)                    | IP Spoofing, MITM, Routing Attacks    |
| **Transport (L4)** | End-to-End Communication **Reliable Delivery** & TCP 3-way handshake     | TCP, UDP, SCTP                           | Gateways, Firewalls (L4-aware)  | SYN Flood, UDP Flood, Port Scanning   |
| **Session (L5)**   | **Session Control**        | NetBIOS, PPTP, SIP, RTP                  | Gateways, Proxies               | Session Hijacking, DoS                |
| **Presentation (L6)** | **Data Representation/Encryption**     | SSL/TLS, JPEG, MPEG, ASCII, Encryption   | None specific (Software layer)  | SSL Stripping, Malware in file formats |
| **Application (L7)** | **User Interface**       | HTTP, DNS, FTP, SMTP, SSH, POP3, SNMP    | Application Servers, Proxies    | XSS, SQLi, CSRF, Buffer Overflow       |
