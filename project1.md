# 🏢 Enterprise Cloud Infrastructure & Identity Lifecycle Engineering

## 📌 Project Overview
This project details the end-to-end design, deployment, and hardening of an enterprise-grade Azure tenant and identity perimeter. Moving away from vulnerable default cloud configurations, this infrastructure enforces strict least-privilege administrative boundaries, group-based identity lifecycles, single sign-on (SSO) integrations, and defensive network isolation—providing a secure corporate foundation before hosting organizational data.

---

## 🎯 Core Technical Objectives
- **Tenant Segmentation:** Organizing corporate assets into scoped resource groups based on departmental and logging boundaries.
- **Identity Lifecycle Management:** Building zero-trust group assignments and analyzing API disclosure vulnerabilities.
- **Access Control Engineering:** Deploying robust Conditional Access Matrices and hardening administrative portal visibility.
- **Log Pipeline Integration:** Linking native directory telemetry directly to centralized security analytics.

---

## 🛠️ Infrastructure Directory Topology

### 1. Resource Group & Asset Distribution
Assets are programmatically isolated into distinct resource groups to prevent cross-department blast radiuses and eliminate privilege creep:

| Resource Group | Deployed Assets & Infrastructure Components | Strategic Purpose |
| :--- | :--- | :--- |
| **`RG-Networks`** | `vnet-sfkek`, `nsg-dev-app`, `nsg-dev-db`, `nsg-dev-workstations`, `nsg-hr-app`, `nsg-hr-workstations` | Centralized virtual network topology and granular subnets protected by specific network security group ACLs. |
| **`NetworkWatcherRG`**| `nat-sfkek`, `nat-pip-sfkek`, `NetworkWatcher_uksouth` | Network diagnostic mechanics and NAT gateway routing for secure outbound internet traffic via static public IP. |
| **`RG-Dev`** | `devsect001` (Key Vault), `devstrg001` (Storage Account) | Sandboxed engineering resources and secure secret management for development lifecycles. |
| **`RG-HR`** | `hrkey001` (Key Vault), `strhr001` (Storage Account) | High-integrity storage and cryptographic secrets dedicated exclusively to human resources operations. |
| **`RG-LOGS`** | `loganalyticsdev-skefk`, `SecurityInsights(loganalyticsdev-skefk)` | Immutable centralized log engine hosting Microsoft Sentinel SIEM workspace data. |

### 2. Directory Identity Architecture
Directory objects are structured into functional roles to eliminate non-standard, direct user privilege assignments.

*   **Identities Deployed:**
    *   **Engineering/Dev:** `Ariya.dev`, `Sade.dev`
    *   **Security/SOC:** `Asake.security`, `hibiscus.sec`
    *   **Human Resources:** `usman.hr`
    *   **Administration:** `banke`, `emergency-admin` (Break-Glass Account)
    *   **Corporate Staff:** `employee1`, `employee2`, `employee3`, `powder`, `Solana`
*   **Security Group Design:**
    *   `Development` Group (Contains development-scoped identities)
    *   `HR` Group (Contains human resource-scoped identities)
    *   `Security` Group (Contains security and auditing identities)
    *   `Employees` Group (Baseline organizational membership directory)
    *   `Targeted Employee Group` (Explicitly includes all standard users, **excluding** Global Administrators and the `emergency-admin` break-glass account for Conditional Access enforcement).

---

## 🔒 Implemented Security Engineering Controls

### 1. Phishing-Resistant SSPR & Emergency Break-Glass Setup
- **Self-Service Password Reset (SSPR):** Enabled globally for the corporate directory, forcing registration via the Microsoft Authenticator App to protect user-driven credential rotation.
- **Break-Glass Strategy:** Built an offline emergency fallback account (`emergency-admin`). To avoid external authentication dependencies, this account is explicitly exempted from standard app-based MFA loops. Instead, it utilizes a static master recovery key/FIDO2 hardware mechanism and is completely excluded from restrictive Conditional Access targeting blocks to guarantee tenant access during an identity outage.

### 2. Enterprise Apps, Microsoft Graph API Triage, & SSO JIT
- **API Permission Hardening:** Audit of standard Azure App Registrations led to strict API baseline alignment. Allowed low-risk profile enumeration (`User.Read`) while explicitly blocking broad, high-risk data exposures such as `Mail.ReadWrite`.
- **SSO Just-In-Time (JIT) Provisioning:** Configured external federation using Single Sign-On (SSO) for the enterprise **Wrike App**. Tied directly to the `Security` group, enabling automated, on-the-fly provisioning to streamline identity lifecycle tracking.
- **App Creation Restrictons:** Hardened global tenant settings to fully disable standard self-service app registration and addition rights for non-admin license tiers, forcing all application requests through an authorized internal authorization workflow.

### 3. Conditional Access Matrix (Zero Trust Enforcement)
After disabling weak Azure Security Defaults, explicit, granular Microsoft-managed and custom Conditional Access templates were deployed.

> 🛡️ **PIM Architectural Review Note:** Deployed and evaluated Privileged Identity Management (PIM) with Eligible Assignments and Just-In-Time (JIT) self-activation on a trial global admin account. During security posture validation, determined that the risk profile introduced by potential JIT activation bypass vectors outweighed operational requirements for this tier. The trial account was offboarded and deleted, choosing to enforce hard-set daily admin segregation instead.

<img width="494" height="181" alt="image" src="https://github.com/user-attachments/assets/11783aa3-ab77-4567-914f-1ab551cf3b4b" />

- **Enforced MFA for All:** Out-of-the-box baseline rule mandating multi-factor challenge validation across all organizational endpoints.
- **Admin Portal Obfuscation:** Configured strict blocks preventing non-admin personnel from enumerating, viewing, or querying the Entra ID administration panel.

---

## 📊 Telemetry and Visibility Pipelines
To ensure complete monitoring across the identity lifecycle, the hardened environment's core notification streams were routed into the centralized logging infrastructure (Sentinel + Log Workspace):

- **Entra ID Sign-In Logs:** Pipeline captures authentication velocity, geolocation criteria, and multi-factor failure telemetry.
- **Entra ID Audit Logs:** Captures directory modifications, group alterations, and privilege elevation activities.
- **SIEM Core Integration:** Connected log pipelines directly to the `SecurityInsights` engine inside the `loganalyticsdev-skefk` workspace, ensuring that all identity lifecycle activities are indexed and ready for defensive hunting queries.

<img width="721" height="127" alt="image" src="https://github.com/user-attachments/assets/5307e067-7c5c-4e89-ae91-49784cb4ee0a" />
<img width="539" height="89" alt="image" src="https://github.com/user-attachments/assets/fdd04ac2-b4e6-4278-8479-81bd2a8fdaf6" />
<img width="533" height="263" alt="image" src="https://github.com/user-attachments/assets/1ef770ad-1815-4492-a79c-59196b089ff5" />
<img width="860" height="298" alt="image" src="https://github.com/user-attachments/assets/f32b6adb-04c7-4c0b-97bf-53ec6bd2fc8a" />

