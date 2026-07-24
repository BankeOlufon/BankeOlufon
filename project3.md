# 🛡️ Cloud Identity Attack Emulation & Security Controls Validation

## 📌 Project Overview

An offensive security project focused on validating the resilience of enterprise Azure identity and cloud access controls under an assumed-breach methodology. This project simulates adversarial identity techniques, privilege escalation paths, and cloud resource abuse to evaluate authentication, authorization, and access management controls while identifying opportunities for defensive hardening.

---

## 🎯 Core Areas Covered

- Cloud Identity Attack Simulation
- Microsoft Entra ID Security Assessment
- Privilege Escalation & Access Control Validation
- Azure Resource Abuse
- Security Controls Validation

---

## 🛠️ Technical Tasks & Functions Performed

### Identity Attack Emulation

- Conducted password spraying and credential stuffing simulations against enterprise identities.
- Emulated OAuth consent phishing and malicious application authorization.
- Simulated access token theft, refresh token abuse, and session hijacking scenarios.
- Evaluated authentication controls including Conditional Access and Multi-Factor Authentication (MFA).

### Privilege Escalation & Cloud Resource Abuse

- Enumerated Azure Storage resources for exposed blobs and overly permissive access.
- Assessed Azure Key Vault access controls and secret exposure risks.
- Evaluated Managed Identity configurations for privilege escalation opportunities.
- Tested Azure RBAC assignments for excessive permissions and privilege inheritance.
- Assessed Service Principals and application permissions for potential abuse paths.

### Security Controls Validation

- Validated the effectiveness of Conditional Access policies against simulated identity attacks.
- Assessed RBAC implementations using least-privilege principles.
- Tested identity security controls against persistence and privilege escalation techniques.
- Produced remediation guidance to strengthen identity governance and cloud access security.

---

## 🔐 Security Outcomes

- Identified identity misconfigurations and excessive privilege assignments.
- Validated Azure authentication and authorization controls against common cloud attack techniques.
- Evaluated cloud resource access controls for privilege escalation opportunities.
- Produced actionable hardening recommendations for Microsoft Entra ID and Azure resource security.

---

## 📚 Skills Demonstrated

- Microsoft Entra ID Security
- Cloud Identity Penetration Testing
- Password Spraying & Credential Attacks
- OAuth & Consent Phishing
- Access Token & Session Abuse
- Azure RBAC Security Assessment
- Managed Identity Security
- Service Principal Security
- Azure Storage & Key Vault Security Assessment
- Privilege Escalation Analysis
- Security Controls Validation
- Cloud Security Hardening

---

## Random Section:

port scans + wireshark + network watcher investigation phase 7

External Reconnaissance Investigation (Port 21 Anomaly)

Problem

Nmap reported TCP/21 as open (ftp), despite no FTP service being intentionally deployed.

Investigation

✅ Verified no local listener using Get-NetTCPConnection.
✅ Attempted manual FTP connection; no banner was returned and the connection eventually timed out.
✅ Verified Azure NSG using IP Flow Verify; inbound traffic was denied by the DenyAllInBound rule.
✅ Captured traffic with Wireshark (tcp.port == 21); no packets reached the Windows VM.

Conclusion

The reported service could not be validated from the operating system.
Evidence suggests the observed result was not an exposed FTP service on the VM.
Reconnaissance tools should always be validated with host- and network-level evidence before drawing conclusions.

<img width="256" height="74" alt="image" src="https://github.com/user-attachments/assets/1e1e3eea-7e9b-4dd1-b5ac-d6995e74bf15" />
<img width="263" height="47" alt="image" src="https://github.com/user-attachments/assets/6eea0a35-af97-4c04-9fba-58d6da1bdedc" />
<img width="547" height="176" alt="image" src="https://github.com/user-attachments/assets/a047b1b2-5ee8-4a28-882f-62743797fb05" />

---

## 🔗 Related Projects

- [Enterprise Cloud Infrastructure & Identity Lifecycle Engineering](#)
- [Azure Infrastructure & Network Security Lab](#)
- [Threat Detection Engineering & Distributed SIEM Operations](#)
- [Zero Trust Remote Endpoint Architecture & Cloud XDR Integration](#)
- [Multi-Cloud Security Posture (AWS + Azure + Datadog)](#)
