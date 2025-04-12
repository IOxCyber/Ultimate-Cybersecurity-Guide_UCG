### **Wireshark Cheat Sheet: Filters, Layers:

---

## **1. Wireshark Display Filter Cheat Sheet**

Use these filters to quickly isolate traffic:

| **Use Case**                        | **Filter**                                        |
|------------------------------------|--------------------------------------------------|
| Traffic from/to IP                 | `ip.addr == 192.168.56.101`                      |
| Traffic between 2 IPs              | `ip.src == 192.168.56.101 && ip.dst == 192.168.56.102` |
| Filter by port                     | `tcp.port == 80` (or `udp.port == 53`)           |
| HTTP traffic only                  | `http`                                           |
| DNS traffic                        | `dns`                                            |
| Only TCP traffic                   | `tcp`                                            |
| Only UDP traffic                   | `udp`                                            |
| TCP 3-way handshake                | `tcp.flags.syn == 1`                             |
| Failed connections (RST)           | `tcp.flags.reset == 1`                           |
| Contains string in payload         | `frame contains "admin"`                         |
| Traffic from a MAC address         | `eth.addr == aa:bb:cc:dd:ee:ff`                  |
| Filter by protocol                 | `icmp`, `smtp`, `ftp`, `telnet`, etc.            |
| Filter by TCP stream               | `tcp.stream eq 0`                                |

---

## **2. Are We Capturing Frames or Packets?**
- In Wireshark, you're capturing **frames** — the entire **Layer 2 Ethernet frame**, which contains:
  - **Ethernet header**
  - **Payload (IP packet)**

---

##  **3. What Layer Are We Capturing in Wireshark**
- Wireshark captures traffic starting from **Layer 2 (Data Link)**:
  - Ethernet Frames: `Destination MAC`, `Source MAC`, `Type`
  - IP Packets inside (Layer 3)
  - TCP/UDP segments (Layer 4)
  - And application data (Layer 5–7)

So it's effectively **Layer 2 and up**.

---

### **Visual Breakdown:**

| **Layer** | **Captured?** | **Example in Wireshark** |
|-----------|---------------|---------------------------|
| 2 - Data Link | ✅ Yes | Ethernet II details |
| 3 - Network | ✅ Yes | IP source/destination |
| 4 - Transport | ✅ Yes | TCP/UDP ports |
| 5–7 - Application | ✅ Yes | HTTP, FTP, DNS, etc. |
| 1 - Physical | ❌ No | Electrical signals are not captured |

---

## ✅ Pro Tips:
- Use Follow TCP Stream: `Right Click on Packet > follow > TCP Stream` to view full sessions (like HTTP login).
- Use `Statistics > Protocol Hierarchy` to get a breakdown of protocol usage.
```
