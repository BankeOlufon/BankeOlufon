# 🌐 Azure Infrastructure & Network Security Lab

## 📌 Project Overview
A security assessment of **Azure networking and infrastructure configurations**, focusing on how misconfigurations can expose cloud environments.  
This project simulates adversarial tradecraft targeting NSG rules, public VM exposure, lateral movement, and private endpoint bypass scenarios.

---

## 🎯 Core Areas Covered
- Virtual Network & Subnet Architecture  
- NSG & ASG Rule Testing  
- Public vs. Private Endpoint Exposure  
- Lateral Movement Simulation  
- Infrastructure Logging & Sentinel Integration  

---

## 🛠️ Technical Tasks & Functions Performed

### Virtual Network & Subnet Setup
- Created VNets, address spaces, and subnets with NAT configuration.  
- Assigned public vs. private IPs to validate exposure risks.  

### Network Security Group (NSG) Testing
- Configured inbound/outbound NSG rules.  
- Simulated misconfigurations to observe unintended access paths.  
- Applied Application Security Groups (ASGs) for segmentation.  

### VM Deployment & Exposure
- Deployed Windows and Linux VMs with varied sizes and managed disks.  
- Tested secure access via Bastion and Just‑In‑Time (JIT) VM access.  
- Simulated public VM exposure and lateral movement from compromised hosts.  

### Endpoint Security
- Configured service endpoints and private endpoints.  
- Tested bypass scenarios to validate segmentation enforcement.  
- Reviewed DNS basics in Azure for secure resolution.  

### Defender for Cloud & Logging
- Enabled Microsoft Defender for Cloud with secure score and recommendations.  
- Collected NSG flow logs, Windows Event Logs, and Linux Syslog.  
- Verified ingestion into Log Analytics and Sentinel for detection.  

---

## 🔐 Security Outcomes
- Identified risks in NSG misconfigurations and public VM exposure.  
- Validated segmentation controls with ASGs and private endpoints.  
- Demonstrated lateral movement detection through infrastructure logging.  
- Strengthened monitoring with Defender for Cloud secure score and alerts.  

---

## 📚 Skills Demonstrated
- Azure network segmentation and NSG rule testing  
- VM deployment, Bastion/JIT access, and exposure analysis  
- Endpoint security (service vs. private endpoints)  
- Infrastructure logging and Sentinel integration  
- Microsoft Defender for Cloud monitoring  

---

<img width="847" height="152" alt="image" src="https://github.com/user-attachments/assets/0e2b9ec1-576c-4f05-822f-77d7e6b608b4" />


## 🔗 Related Projects
- [Enterprise Cloud Infrastructure & Identity Lifecycle Engineering](#)  
- [Threat Detection Engineering & Distributed SIEM Operations](#)  
- [Assumed-Breach Emulation & Security Controls Validation](#)  
- [Zero Trust Remote Endpoint Architecture & Cloud XDR Integration](#)  
