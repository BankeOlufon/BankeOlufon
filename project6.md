# 🔒 ARP Spoofing on a Wireless Network (Financial Institution Simulation)

## 📌 Project Overview
A network security lab simulating a **Man-in-the-Middle (MITM) attack** via ARP spoofing in a financial institution environment.  
The goal was to intercept and analyze live traffic while maintaining victim connectivity, demonstrating end-to-end MITM capability from discovery to packet analysis.

---

## 🎯 Core Areas Covered
- ARP Spoofing & MITM Attack Simulation  
- Network Discovery & Host Enumeration  
- Packet Capture & Traffic Analysis  
- Reverse DNS & ARP Table Inspection  

---

## 🛠️ Technical Tasks & Functions Performed

### MITM Workflow
- Performed **full-duplex ARP spoofing** against a target to position attacker host as MITM.  
- Enabled **IP forwarding** to ensure intercepted packets were routed correctly and victim retained access.  
- Used **Bettercap discovery modules** and reverse DNS lookup to enumerate devices on the LAN.  
- Ran **Bettercap net.sniff** to capture traffic and saved PCAP files for offline analysis in Wireshark.  
- Verified success by inspecting ARP tables on victim/gateway, viewing live ARP/HTTP packets, and analyzing TCP streams in Wireshark.  

### Tools & Techniques
- **Bettercap** – ARP spoofing, discovery, sniffing  
- **sysctl (ip_forward)** – IP forwarding configuration  
- **tcpdump / Wireshark** – Packet capture and analysis  
- **Reverse DNS & ARP inspection** – Host discovery and validation  

---

## 🔐 Security Outcomes
- Demonstrated end-to-end MITM capability: discovery → spoof → forward → capture → analyze.  
- Captured actionable packet evidence and documented the workflow.  
- Validated ability to intercept and analyze traffic without disrupting victim connectivity.  

---

## 📚 Skills Demonstrated
- ARP spoofing and MITM attack simulation  
- Network sniffing and packet analysis with Wireshark  
- Host discovery and reverse DNS lookups  
- Practical use of Bettercap for offensive security testing  

---

# 📷 Portfolio Artifacts
<img width="587" height="47" alt="a5" src="https://github.com/user-attachments/assets/3d788ba2-d0bf-4689-9a9c-05d905f2cff8" />
<img width="655" height="190" alt="a5" src= "https://github.com/user-attachments/assets/8a55ef61-1bd0-4b13-adbe-14d0a533e65d" />
<img width="587" height="47" alt="a5" src="https://github.com/user-attachments/assets/aac71231-5330-477f-8182-797851c4efa7" /> 

---

<!-- ## 📊 Phase Mapping Context
(Not applicable — standalone offensive security lab exercise)
-->

---

<!-- ## 📈 Why This Matters to Employers
Demonstrates practical offensive security skills in network MITM scenarios, including traffic interception, analysis, and validation of detection/mitigation strategies.
-->

---

## 🔗 Related Projects
- [Linux Web App Exploitation Lab (Initial Access)](#)  
- [Windows Privilege Escalation Lab (Local Takeover)](#)  
- [Active Directory Domain Pivot Lab (Network Conquest)](#)  
- [SaaS Security & Identity Pentesting (Okta Federation, SCIM, OAuth)](#)  
