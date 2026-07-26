# 🛡️ Cloud Identity Attack Emulation & Security Controls Validation

## 📌 Project Overview

This project simulates common cloud identity attacks against a Microsoft Entra ID tenant to evaluate the effectiveness of Azure identity security controls under an assumed-breach methodology.

The assessment focuses on authentication, authorization, and identity hardening by validating security controls such as Microsoft Entra Smart Lockout, Multi-Factor Authentication (MFA), Conditional Access, and Azure Role-Based Access Control (RBAC).

Following each assessment, security controls were reviewed, validated, and refined to verify that the implemented mitigations effectively reduced the attack surface.

> **📷 Screenshot:** Insert a high-level Azure tenant architecture diagram here.

---

# 🧰 Tools Used

- Microsoft Entra ID
- Azure Portal
- Kali Linux
- Spray365
- Microsoft Authenticator

---

# 🎯 Objectives

- Simulate common cloud identity attack techniques
- Assess Microsoft Entra ID authentication controls
- Evaluate Azure RBAC permissions
- Identify excessive privilege assignments
- Validate Microsoft Entra Smart Lockout
- Validate Multi-Factor Authentication (MFA)
- Validate Conditional Access policies
- Assess least-privilege implementation
- Produce security hardening recommendations
- Verify that implemented controls successfully mitigate identified attack paths

---

# 🏗️ Lab Architecture

```text
                     Kali Linux
                  (Attacker Machine)
                           │
                           ▼
                 Microsoft Entra ID
        ┌────────────────────────────────┐
        │ Enterprise Users               │
        │ Security Groups                │
        │ Conditional Access             │
        │ Smart Lockout                  │
        │ Multi-Factor Authentication    │
        │ Azure RBAC                     │
        └────────────────────────────────┘
                           │
                           ▼
                  Azure Resources
        ├── RG-Development
        ├── RG-HR
        ├── RG-Logs
        ├── Storage Accounts
        ├── Key Vault
        └── Virtual Machines
```

> **📷 Screenshot:** Insert the Azure architecture diagram here.

---

# ⚔️ Attack Scenarios

# Password Spraying Assessment

## Objective

Assess the resilience of Microsoft Entra ID authentication controls against password spraying attacks.

## Attack Workflow

```text
Attacker (Kali Linux)
        │
        ▼
Multiple Enterprise Accounts
        │
        ▼
Microsoft Entra ID
        │
        ▼
Authentication Controls
├── Smart Lockout
├── Conditional Access
└── Multi-Factor Authentication
```

## Activities

- Performed password spraying against multiple enterprise accounts
- Analysed Microsoft Entra authentication responses
- Investigated authentication failures using Microsoft Entra Sign-in Logs
- Validated Smart Lockout behaviour
- Validated MFA enforcement
- Assessed Conditional Access effectiveness

## Findings

- Successfully identified valid enterprise accounts during password spraying.
- Invalid passwords generated Microsoft Entra authentication failures and corresponding Sign-in Log events.
- Microsoft Entra Smart Lockout successfully mitigated repeated authentication attempts.
- MFA successfully protected privileged accounts from password-only authentication.
- Conditional Access policies were enforced as expected.

> **📷 Screenshot:** Password spraying execution output
> <img width="761" height="326" alt="image" src="https://github.com/user-attachments/assets/d0938215-98ab-4b4b-98c7-d6ec69fedd7f" />

> **📷 Screenshot:** Microsoft Entra Sign-in Logs
> <img width="603" height="314" alt="image" src="https://github.com/user-attachments/assets/76ab943a-d875-419c-bb65-fedebaf5f5b7" />


> **📷 Screenshot:** Smart Lockout configuration
> <img width="494" height="362" alt="image" src="https://github.com/user-attachments/assets/31450c54-834d-4ecf-8247-0203892cb390" />

> **📷 Screenshot:** Smart Lockout validation
> <img width="340" height="299" alt="image" src="https://github.com/user-attachments/assets/7fe9548b-0ded-4fa8-abb9-52295adabb49" />

> **📷 Screenshot:** MFA enforcement
> <img width="315" height="359" alt="image" src="https://github.com/user-attachments/assets/db516577-87ba-4f8c-9f92-729a91e1ea41" />

---

# Azure RBAC Security Assessment

## Objective

Assess Azure Role-Based Access Control implementation and validate least-privilege principles.

## Activities

- Enumerated Azure RBAC assignments
- Reviewed resource group role assignments
- Identified excessive permissions
- Validated least-privilege implementation
- Attempted privilege escalation through Azure RBAC permissions

## Azure RBAC Configuration

| Resource Group | Owner | Contributors | Readers |
|----------------|-------|--------------|----------|
| **RG-Development** | Admin | Development Group (2 members) | Security Group |
| **RG-HR** | Admin | HR Group (2 members) | Security Group |
| **RG-Logs** | Admin | Security Group (2 members) | None |

## Findings

- Azure resource groups followed role separation principles.
- Administrative permissions were restricted to the administrator account.
- Contributor access was limited to the appropriate resource groups.
- Security personnel received read-only access where appropriate.
- No successful Azure RBAC privilege escalation paths were identified.
- Least-privilege principles were successfully implemented across all resource groups.

> **📷 Screenshot:** Azure RBAC role assignments

> **📷 Screenshot:** IAM role assignments

---

# 🛡️ Security Controls Validation

The following Microsoft Entra ID security controls were successfully validated throughout the assessment:

- ✅ Microsoft Entra ID authentication
- ✅ Microsoft Entra Smart Lockout
- ✅ Multi-Factor Authentication (MFA)
- ✅ Conditional Access
- ✅ Azure RBAC
- ✅ Least-Privilege implementation

---

# 🔧 Security Hardening

Following the assessment, security improvements were implemented to strengthen the Azure identity environment.

## Improvements

- Reviewed Azure RBAC role assignments
- Removed unnecessary permissions where applicable
- Validated least-privilege implementation
- Strengthened Conditional Access policies
- Enforced Multi-Factor Authentication for privileged users
- Produced remediation recommendations

---

# 🚩 Security Finding

## Conditional Access Design Issue

The initial Conditional Access policy prevented all non-administrative users from accessing Azure administrative portals.

Although this reduced the attack surface, it unintentionally prevented Azure Contributors from managing Azure resources assigned through RBAC, creating an operational conflict between authorization and access control.

### Recommendation

Refine the Conditional Access policy by excluding authorised Azure administrative roles (such as Contributors where appropriate) or scope the policy only to high-privilege administrative roles (for example, Global Administrator, Privileged Role Administrator, or Owner). This preserves operational functionality while maintaining least-privilege principles.

> **📷 Screenshot:** Conditional Access policy configuration
> <img width="449" height="382" alt="image" src="https://github.com/user-attachments/assets/e19c319e-a717-46f8-b915-1eaac71a23a1" />

> **📷 Screenshot:** Conditional Access policy results
> <img width="317" height="239" alt="image" src="https://github.com/user-attachments/assets/e9d6355f-816b-4495-8a0b-864c6f0b7e25" />

---

# 📂 Project Artefacts

- Azure RBAC role assignments
- Microsoft Entra Sign-in Logs
- Microsoft Entra authentication responses
- Password spraying execution results
- Microsoft Entra Smart Lockout configuration
- Smart Lockout validation
- Conditional Access policy configuration
- Azure RBAC configuration
- Security assessment notes
- Security hardening recommendations
- Azure architecture diagrams

---

# 📚 Skills Demonstrated

- Microsoft Entra ID
- Azure RBAC
- Azure Identity Security
- Password Spraying
- Authentication Analysis
- Microsoft Entra Sign-in Logs
- Microsoft Entra Smart Lockout
- Conditional Access
- Multi-Factor Authentication (MFA)
- Least-Privilege Implementation
- Privilege Analysis
- Azure Security Hardening
- Cloud Identity Security Assessment

---

# ✅ Key Outcomes

- Successfully simulated password spraying attacks against a Microsoft Entra ID tenant.
- Validated Microsoft Entra Smart Lockout, Multi-Factor Authentication, Conditional Access, and Azure RBAC security controls.
- Confirmed that least-privilege principles were effectively implemented across Azure resource groups.
- Identified a Conditional Access policy design issue affecting Azure Contributors and documented an appropriate remediation.
- Demonstrated an end-to-end cloud identity security assessment aligned with an assumed-breach methodology.
