# 🏢 Enterprise Cloud Infrastructure & Identity Lifecycle Engineering

## 📌 Project Overview
An enterprise-grade cloud engineering case study focusing on designing, deploying, and hardening a secure Azure infrastructure from scratch.  
This project demonstrates foundational mastery over identity boundaries, network isolation, directory role delegation, and programmatic resource isolation.  
The ultimate goal: build an identity and infrastructure foundation that natively aligns with the principle of least privilege before any corporate data or workloads are deployed.

---

## 🎯 Core Areas Covered
- Cloud Infrastructure Architecture & Network Isolation  
- Identity & Access Management (IAM) Governance  
- Granular Role-Based Access Control (RBAC) Mapping  
- Perimeter Hardening & Network Access Control Lists (ACLs)  

---

## 🛠️ Technical Tasks & Functions Performed

### Identity & Tenant Directory Setup
- Provisioned a dedicated corporate directory tenant and mapped root administrative subscription boundaries.  
- Established a scalable directory hierarchy separating user identities by operational type (Member vs. Guest) and origin (Cloud-only vs. External).  
- Designed a group-based administration framework to eliminate direct, non-standard user privileges.  

### Infrastructure Isolation & Network Hardening
- Designed and deployed isolated Virtual Networks (VNets) with distinct IP address spaces and custom subnets.  
- Hardened compute network perimeters using Network Security Groups (NSGs) with strict inbound/outbound ACLs.  
- Configured Private Endpoints and Service Endpoints to isolate production storage accounts and key vaults from public internet access.  

### Access Control & Directory Role Governance
- Implemented administrative segregation between Entra ID roles and Azure RBAC scopes.  
- Configured custom administrative permissions using least privilege principles.  
- Enforced Multi-Factor Authentication (MFA) and created a secure Break-Glass account recovery framework.  

<!--
---

## 📊 Phase Mapping Context
- Phase 1: Identity & Tenant Foundation  
- Phase 2: Resource Design & Directory Storage Architecture  
- Phase 4: Enterprise Identity Governance & Authentication Hardening  
- Phase 5: Virtual Networking & Compute Resource Deployment  
- Phase 11: Infrastructure Translation to Code (Terraform)  

---

## 🔐 Security Outcomes
- Enforced least privilege across directory and infrastructure roles.  
- Hardened perimeter with strict ACLs and NSGs.  
- Reduced risk of orphaned accounts with lifecycle governance.  
- Established recovery safeguards for privileged access.  

---

## 📷 Portfolio Artifacts
[Placeholder: Architecture diagram of Azure tenant hierarchy]  
[Placeholder: Screenshot of RBAC role assignments]  
[Placeholder: Terraform code snippet for VNet deployment]  

---

## 📈 Why This Matters to Employers
This project proves the ability to design secure cloud foundations before workloads are deployed. It demonstrates practical knowledge of IAM governance, network isolation, and infrastructure-as-code — all critical for enterprise cloud adoption.

-->

---


## 📚 Skills Demonstrated
- Azure AD & RBAC configuration  
- Network Security Groups & Private Endpoints  
- Identity lifecycle management  
- Terraform for Infrastructure as Code  

---

## 🔗 Related Projects
- [Threat Detection Engineering & Distributed SIEM Operations](#)  
- [Assumed-Breach Emulation & Security Controls Validation](#)  
- [Zero Trust Remote Endpoint Architecture & Cloud XDR Integration](#)  
- [Multi-Cloud Security Posture (AWS + Azure + Wiz/Trend Micro)](#)  
