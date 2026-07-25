# 🛡️ Cloud Identity Attack Emulation & Security Controls Validation

## 📌 Project Overview

An offensive cloud security project focused on validating the resilience of Microsoft Entra ID identity controls under an assumed-breach methodology.

The project simulates common cloud identity attacks against an Azure enterprise environment to assess authentication and authorization controls. Security controls are then hardened to verify that the attacks are successfully mitigated.

---

# 🎯 Objectives

- Simulate Azure identity attacks
- Assess Microsoft Entra ID authentication controls
- Evaluate Azure RBAC permissions
- Identify excessive privilege assignments
- Validate Conditional Access and MFA protections
- Implement security hardening recommendations
- Verify that implemented controls mitigate the attacks

---

# 🏗️ Lab Architecture

```text
Attacker (Kali Linux)
        │
        ▼
Microsoft Entra ID
├── Enterprise Users
├── Security Groups
├── Azure RBAC
├── Conditional Access
└── Multi-Factor Authentication
        │
        ▼
Azure Resources
├── Resource Groups
├── Storage Accounts
├── Key Vault
└── Virtual Machines
```

---

# ⚔️ Attack Scenarios

## Password Spraying

**Objective**

Assess the effectiveness of Microsoft Entra ID authentication controls against password spraying attacks.

### Attack Workflow

```text
Attacker
        │
        ▼
Multiple Azure Accounts
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

Activities:

- Password spraying against enterprise accounts
- Validate Smart Lockout behaviour
- Validate account lockout behaviour
- Test MFA-protected accounts
- Assess Conditional Access effectiveness

---

## Azure RBAC Assessment

**Objective**

Identify excessive permissions and validate least-privilege implementation.

Activities:

- Enumerate Azure RBAC assignments
- Review role inheritance
- Identify excessive permissions
- Validate least-privilege implementation
- Attempt privilege escalation through misconfigured RBAC assignments

---

# 🛡️ Security Controls Validation

Validated:

- Microsoft Entra ID authentication
- Multi-Factor Authentication (MFA)
- Conditional Access
- Azure RBAC permissions
- Least-privilege implementation

---

# 🔧 Security Hardening

Following the assessment, the environment was hardened by:

- Removing excessive RBAC permissions
- Applying least-privilege principles
- Strengthening Conditional Access policies
- Enforcing MFA where appropriate
- Producing remediation recommendations

---

# 📂 Project Artefacts

- Azure RBAC role assignments
- Conditional Access policy configuration
- Microsoft Entra ID authentication screenshots
- Password spraying test results
- Security assessment notes
- Hardening recommendations
- Architecture diagrams

---

# 📚 Skills Demonstrated

- Microsoft Entra ID
- Azure RBAC
- Password Spraying
- Conditional Access
- Multi-Factor Authentication (MFA)
- Identity Security Assessment
- Privilege Analysis
- Security Controls Validation
- Cloud Security Hardening
