# 🔥 Basic Firewall Configuration Lab (Cisco Packet Tracer)

## 📌 Project Overview
This lab demonstrates how to configure a basic firewall in Cisco Packet Tracer. The objective was to set up a network topology, assign IP addresses, configure inbound firewall rules on a server, and verify the configuration by testing both blocked and allowed traffic.

---

## 📁 Project Files
- [📂 Basic Firewall Configuration Lab.pkt](Basic%20Firewall%20Configuration%20Lab.pkt) — Download and open in Cisco Packet Tracer
- Network topology diagram
- Firewall rule configuration screenshots
- Traffic testing screenshots

---

## 🛠️ Software & Equipment Used
- **Cisco Packet Tracer** — Network simulation software
- **1 Server** — Acts as the firewall
- **1 Switch** — Cisco 2960
- **3 PCs** — Simulate hosts on the network

---

## 🌐 Network Topology

<p align="center">
  <img src="Network%20Topology.png" width="700">
</p>

All devices are connected using **straight-through cables**:
- PC-1 (Temmy), PC-2 (Christiana), and PC-3 (David) connected to the Switch
- Server connected to the Switch

---

## 🌐 IP Addressing Table

| Device | Name | IP Address | Subnet Mask |
|--------|------|------------|-------------|
| Server | Firewall Server | 10.0.0.1 | 255.0.0.0 |
| PC-1 | Temmy | 10.0.0.2 | 255.0.0.0 |
| PC-2 | Christiana | 10.0.0.3 | 255.0.0.0 |
| PC-3 | David | 10.0.0.4 | 255.0.0.0 |

All devices are within the **Class A 10.0.0.0/8** network.

---

## ⚙️ Firewall Configuration

The firewall service was enabled on the Server and the following **Inbound Rules** were configured on **FastEthernet0**:

### 🔒 Rule 1 — Block ICMP Traffic
| Field | Value |
|-------|-------|
| Interface | FastEthernet0 |
| Action | **Deny** |
| Protocol | ICMP |
| Remote IP | 0.0.0.0 |
| Remote Wildcard Mask | 255.255.255.255 |

This rule blocks all **ping (ICMP)** traffic from any device trying to reach the server.

<p align="center">
  <img src="Block%20ICMP%20Traffic.png" width="700">
</p>

---

### ✅ Rule 2 — Allow IP Traffic
| Field | Value |
|-------|-------|
| Interface | FastEthernet0 |
| Action | **Allow** |
| Protocol | IP |
| Remote IP | 0.0.0.0 |
| Wildcard Mask | 255.255.255.255 |

This rule allows all other **IP traffic** (including HTTP) from any device to reach the server.

<p align="center">
  <img src="Allow%20IP%20Traffic.png" width="700">
</p>

---

## 🧪 Validation & Testing

### ❌ Test 1 — Block ICMP Traffic (Ping)

All three PCs attempted to ping the server at **10.0.0.1**. Due to Rule 1, all ping attempts resulted in **Request Timed Out** — confirming the ICMP block rule is working correctly.

<p align="center">
  <img src="Test%20Blocked%20ICMP%20Traffic.png" width="700">
</p>

> ✅ Result: No device can ping the server. Firewall rule working perfectly.

---

### ✅ Test 2 — Allow HTTP Traffic (Web Browser)

PC-3 (David) opened the **Web Browser** from the Desktop tab and navigated to **http://10.0.0.1** to attempt to reach the server via HTTP.

<p align="center">
  <img src="HTTP%20Traffic%20Allowed.png" width="700">
</p>

> ✅ Result: Server successfully reached via HTTP — confirming that IP traffic (including HTTP) is allowed while ICMP remains blocked.

---

## 🔐 Security Concepts Demonstrated

- **Firewall rule configuration** — defining inbound rules to control network traffic
- **Least Privilege Principle** — only necessary traffic (HTTP/IP) is allowed; unnecessary traffic (ICMP) is denied
- **Protocol-based filtering** — blocking specific protocols while permitting others
- **Traffic verification** — validating firewall rules through practical testing

---

## 🚀 Skills Demonstrated
- Cisco Packet Tracer network design
- IP addressing and subnetting (Class A)
- Server-based firewall configuration
- Inbound rule creation and management
- Network traffic testing and validation
- Technical documentation and findings reporting

---

## 📌 Author
**TemmyNetGuard**
Cybersecurity Student at **Altschool Africa** | ISC² Certified in Cybersecurity (CC)
Building secure systems one lab at a time. 🔐
