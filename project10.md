# 🔒 SaaS Security & Identity Pentesting (Okta Federation, SCIM, OAuth)

## 📌 Project Overview
A security assessment of a **cloud-native identity ecosystem** using an isolated Okta Developer Sandbox.  
This project simulates adversarial tradecraft targeting SCIM workflows, OAuth/OIDC federation, and administrative session configurations.

---

## 🎯 Core Areas Covered
- Identity Architecture Auditing  
- SCIM & Federation Exploitation Analysis  
- Token & Session Governance Testing  
- Telemetry & Detection Engineering  

---

## 🛠️ Technical Tasks & Functions Performed

### Tenant Provisioning & Directory Setup
- Established dedicated Okta Developer Tenant with synthetic enterprise objects.  
- Populated directory with nested groups, custom roles, and varied admin tiers.  

### SCIM Protocol Vulnerability Assessment
- Configured mock downstream SaaS app with unvalidated SCIM server.  
- Triggered sync execution to observe risks of attribute leakage.  

### Adversary Simulation
- Deployed Elastic Dorothy tool to simulate adversarial enumeration.  
- Tested MFA policies, password complexity, and group permissions.  

### Privilege Escalation & Persistence
- Simulated admin account takeover.  
- Introduced persistent backdoors via secondary API tokens and unauthorized OAuth authorizations.  

### Telemetry Analysis
- Extracted raw event streams from Okta System Log API.  
- Ingested logs into SIEM instance for normalization and adversary mapping.  

---

<!-- ## 📊 Phase Mapping Context
(Not applicable — SaaS identity pentesting case study)
-->

---

## 🔐 Security Outcomes
- Identified risks in SCIM attribute mapping.  
- Validated token governance and MFA enforcement gaps.  
- Produced remediation matrix for identity hardening.  

---

## 📚 Skills Demonstrated
- SaaS identity pentesting (Okta Federation, SCIM, OAuth)  
- Adversarial simulation with Elastic Dorothy  
- Token/session governance testing  
- SIEM telemetry analysis  

---

<!-- ## 📷 Portfolio Artifacts
[Placeholder: Okta tenant configuration screenshot]  
[Placeholder: Dorothy adversary simulation output]  
[Placeholder: SIEM log normalization evidence]  
-->

---

<!-- ## 📈 Why This Matters to Employers
Demonstrates ability to assess SaaS identity ecosystems, simulate adversarial tactics, and produce actionable remediation.
-->

---

## 🔗 Related Projects
- [Linux Web App Exploitation Lab (Initial Access)](#)  
- [Windows Privilege Escalation Lab (Local Takeover)](#)  
- [Active Directory Domain Pivot Lab (Network Conquest)](#)  
- [ARP Spoofing on a Wireless Network (Financial Institution Simulation)](#)  
