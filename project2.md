# 🛡️ Threat Detection Engineering & Distributed SIEM Operations

## 📌 Project Overview
A security operations engineering project focused on building a centralized logging architecture and telemetry ingestion pipeline across an enterprise cloud footprint.  
This project showcases the end-to-end configuration of Microsoft Sentinel, onboarding diverse telemetry sources, and implementing custom detection analytics written in Kusto Query Language (KQL) to identify behavioral threat indicators.

---

## 🎯 Core Areas Covered
- Security Information & Event Management (SIEM) Architecture  
- Enterprise Logging & Telemetry Ingestion Pipelines  
- Detection Engineering & Behavioral Analytics (KQL)  
- Incident Triage, Correlation, & SOC Workflows  

---

## 🛠️ Technical Tasks & Functions Performed

### Logging Architecture & Pipeline Engineering
- Deployed a centralized Log Analytics Workspace with customized data retention, table schemas, and workspace-level access controls.  
- Onboarded cloud-native audit engines, establishing diagnostic streams for Directory Sign-in Logs, Audit Logs, and provisioning events.  
- Configured Data Collection Rules (DCRs) using the Azure Monitor Agent (AMA) to ship raw OS event logs into the repository.  

### SIEM Implementation & Detection Development
- Provisioned Microsoft Sentinel and linked ingestion pipelines to parse multi-source data feeds.  
- Developed custom Scheduled and Near Real-Time (NRT) detection rules using complex KQL queries.  
- Configured automated incident routing and analytic logic grouping to consolidate multi-stage threat events.  

### SOC Analyst Incident Lifecycle Workflows
- Built triage and investigation playbooks triggered by alerts.  
- Conducted deep-dive behavioral investigations across correlated telemetry tables (e.g., sign-in failures linked to key vault secret extraction attempts).  
- Mapped engineered alerts and hunting queries directly to tactics in the MITRE ATT&CK Cloud Matrix.  

---

<!-- ## 📊 Phase Mapping Context
- Phase 3: Monitoring Ingestion & Sentinel Foundation  
- Phase 6: Enterprise Activity Stream & Telemetry Generation  
- Phase 8: Cloud Detection Engineering & KQL Analytics  
- Phase 9: SOC Operations & Threat Inversion Tracking  
-->

---

## 🔐 Security Outcomes
- Centralized telemetry ingestion across cloud-native sources.  
- High-fidelity detection rules isolating anomalous behaviors.  
- Automated incident routing and unified case investigations.  
- SOC workflows mapped to adversary tactics.  

---

## 📚 Skills Demonstrated
- Microsoft Sentinel (KQL queries, playbooks)  
- Azure Monitor Agent (AMA) pipelines  
- Detection engineering & threat hunting  
- MITRE ATT&CK framework application  
- SOC workflow design  

---
<!--
## 📷 Portfolio Artifacts
[Placeholder: Sentinel dashboard screenshot]  
[Placeholder: KQL detection rule snippet]  

---

<!-- ## 📈 Why This Matters to Employers
Shows ability to design enterprise SIEM pipelines, engineer custom detections, and validate SOC workflows against adversary simulations — critical Tier 1/2 SOC analyst skills.
-->

---

## 🔗 Related Projects
- [Enterprise Cloud Infrastructure & Identity Lifecycle Engineering](#)  
- [Assumed-Breach Emulation & Security Controls Validation](#)  
- [Zero Trust Remote Endpoint Architecture & Cloud XDR Integration](#)  
- [Multi-Cloud Security Posture (AWS + Azure + Wiz/Trend Micro)](#)  
