# 🔐 Azure Advanced Security Hardening Project
## Project Overview
Implemented advanced security controls across Azure networking, compute, and data services to close critical gaps in platform protection, workload hardening, and storage/database security. This project demonstrates end‑to‑end defense strategies aligned with AZ‑500 exam objectives.

## 🎯 Core Areas Covered
- Platform Protection (Firewall, WAF, DDoS, Private Endpoints)
- Compute Security (VM disk encryption, patch management, AKS/ACR, Functions/App Service)
- Storage & Database Security (SAS tokens, encryption, SQL security)

---

## 🛠️ Technical Tasks & Functions Performed

### Platform Protection
- Deployed **Azure Firewall** in a hub‑and‑spoke topology with rule collections for inbound/outbound traffic.
- Configured **Firewall Manager** for centralized policy enforcement across VNets.
- Implemented **Application Gateway with WAF** to protect a sample web app against OWASP Top 10 threats.
- Integrated **Azure Front Door** for global traffic distribution and TLS termination.
- Enabled **DDoS Protection Standard** on the main VNet.
- Created **Private Endpoints** for Storage and Key Vault, blocking public access.
- Configured **Service Endpoints** for SQL Database to restrict traffic to trusted VNets.
- Applied **resource firewall rules** to Storage Accounts, SQL Databases, and Key Vault.

### Compute Security
- Enabled **Azure Disk Encryption** on Windows and Linux VMs using Key Vault.
- Configured **Update Management** for VM patching via Azure Automation.
- Implemented **Just‑In‑Time VM access** to reduce exposure of RDP/SSH ports.
- Deployed **Azure Kubernetes Service (AKS)** with role‑based access control and network policies.
- Secured **Azure Container Registry (ACR)** with private endpoints and managed identities.
- Hardened **Azure Functions** and **App Service** with managed identities and restricted network access.

### Storage & Database Security
- Configured **Storage Account firewalls** to allow only trusted VNets and IP ranges.
- Implemented **Shared Access Signatures (SAS)** with limited permissions and expiry times.
- Enabled **encryption at rest** with Microsoft‑managed keys and validated **TLS in transit**.
- Deployed **SQL Database auditing** to Log Analytics Workspace for continuous monitoring.
- Enabled **SQL Advanced Threat Protection** for anomaly detection.
- Configured **SQL firewall rules** to restrict access to specific IP ranges.
- Integrated **Managed Identities** for applications accessing Storage and SQL without credentials.

---

## 🔐 Security Outcomes
- Centralized firewall and WAF protection for applications and VNets.
- Reduced exposure to volumetric and application‑layer attacks with DDoS + WAF.
- Hardened compute workloads with encryption, patching, and JIT access.
- Secured container and serverless workloads with RBAC and private endpoints.
- Fine‑grained access control for storage data using SAS tokens.
- Continuous monitoring and threat detection for SQL Database activity.
- Encrypted data at rest and in transit for compliance.
- Eliminated credential sprawl with managed identities.

---

## 📊 Architecture Diagram

```Internet
│
┌────▼─────┐
│ Azure    │
│ FrontDoor│
└────▲─────┘
│
┌────▼─────┐
│ App GW + │
│ WAF      │
└────▲─────┘
│
┌────▼─────┐
│ Azure    │
│ Firewall │
└────▲─────┘
│
VNet Hub
│
┌────▼─────┐
│ Spoke VNets│───Private Endpoints (Storage, SQL, Key Vault, ACR)
└───────────┘
│
▼
┌───────────────┐
│ Compute Layer │───VMs (Disk Encryption, JIT, Patch Mgmt)
│               │───AKS (RBAC, Network Policies)
│               │───Functions/App Service (Managed Identity)
└───────────────┘
│
▼
┌───────────────┐
│ Data Layer    │───Storage (SAS, Firewall, Encryption)
│               │───SQL Database (Auditing, Threat Detection, Firewall Rules)
└───────────────┘```

