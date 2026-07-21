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

Windows Event Logs ─┐
                    │
Linux Syslog ───────┤
                    ▼
        Azure Monitor Agent (AMA)
                    ▼
      Log Analytics Workspace
                    ▼
      Microsoft Sentinel

---

<img width="847" height="152" alt="image" src="https://github.com/user-attachments/assets/0e2b9ec1-576c-4f05-822f-77d7e6b608b4" />
<img width="899" height="77" alt="image" src="https://github.com/user-attachments/assets/b037879e-00d5-400e-8914-cf867d177b3e" />
<img width="875" height="234" alt="image" src="https://github.com/user-attachments/assets/c7e3c2a5-e395-4a4a-867f-d0a9bfc4eb4c" />
<img width="623" height="116" alt="image" src="https://github.com/user-attachments/assets/02c86492-f245-401c-81d8-1cda31391eb8" />
<img width="613" height="230" alt="image" src="https://github.com/user-attachments/assets/3cbdd012-1f25-4cda-9aa6-154f3c3d61d9" />
<img width="596" height="254" alt="image" src="https://github.com/user-attachments/assets/050dc4f8-ee90-4ef5-9da8-5b896e84e5a8" />
<img width="661" height="483" alt="image" src="https://github.com/user-attachments/assets/558c442a-e31b-4d3e-9e5d-3c49f6990913" />
<img width="860" height="114" alt="image" src="https://github.com/user-attachments/assets/6db0f3c8-6a30-41d4-bf2f-b03ef3704acd" />
<img width="439" height="353" alt="image" src="https://github.com/user-attachments/assets/65cec526-5a50-4c3a-af76-d16d7669e182" />
<img width="650" height="452" alt="image" src="https://github.com/user-attachments/assets/fb02220d-fb48-4960-9e49-06e75b9a96c1" />
<img width="389" height="294" alt="image" src="https://github.com/user-attachments/assets/ce04017e-90c6-4797-841d-7c5bd5741012" />
<img width="882" height="586" alt="image" src="https://github.com/user-attachments/assets/e7b393df-b260-4856-b936-8bf86c82b3a1" />



## 🔗 Related Projects
- [Enterprise Cloud Infrastructure & Identity Lifecycle Engineering](#)  
- [Threat Detection Engineering & Distributed SIEM Operations](#)  
- [Assumed-Breach Emulation & Security Controls Validation](#)  
- [Zero Trust Remote Endpoint Architecture & Cloud XDR Integration](#)  
