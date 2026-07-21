# ☁️ Multi-Cloud Security Posture Management (AWS • Azure • Datadog)

## 📌 Project Overview

Designed and evaluated a unified Cloud Security Posture Management (CSPM) environment across Amazon Web Services (AWS) and Microsoft Azure using Datadog Cloud Security Management. The project centralises security visibility across multiple cloud providers, identifies infrastructure misconfigurations, correlates security risks across cloud environments, and validates remediation strategies to reduce the overall cloud attack surface.

---

## 🎯 Core Areas Covered

- Multi-Cloud Security Posture Management (CSPM)
- Cross-Cloud Asset Visibility
- Cloud Misconfiguration Detection
- Infrastructure Risk Prioritisation
- Multi-Cloud Attack Surface Reduction
- Cloud Security Hardening

---

## 🛠️ Technical Tasks & Functions Performed

### Multi-Cloud Environment Deployment

- Provisioned representative infrastructure across AWS and Azure.
- Configured secure cloud integrations with Datadog Cloud Security Management.
- Established least-privilege cloud identities for continuous posture assessment.
- Validated inventory visibility across compute, storage, networking, and identity resources.

### Infrastructure Security Assessment

- Assessed virtual machines, storage services, identity configurations, and networking components across both cloud providers.
- Evaluated publicly exposed resources, overly permissive security groups, excessive identity permissions, and storage configurations.
- Reviewed cloud resources against recognised security best practices.

### Cross-Cloud Risk Analysis

- Correlated security findings across AWS and Azure to identify high-risk attack paths.
- Prioritised remediation activities based on overall attack surface and potential business impact.
- Evaluated toxic security combinations involving identity, networking, compute, and storage resources.

### Security Hardening

- Remediated cloud misconfigurations across both environments.
- Reduced excessive permissions using least-privilege principles.
- Hardened network exposure through Security Groups and Network Security Groups (NSGs).
- Validated improvements through continuous posture reassessment.

---

## 🔐 Security Outcomes

- Established centralised visibility across AWS and Azure environments.
- Identified and remediated cloud infrastructure misconfigurations.
- Reduced multi-cloud attack surface through risk-based remediation.
- Validated secure cloud configurations using continuous posture monitoring.

---

## Architecture
```
```                           ┌──────────────────────────────┐
                           │          Datadog             │
                           │  Cloud Security Management   │
                           │                              │
                           │  • Asset inventory           │
                           │  • Misconfiguration findings │
                           │  • Posture dashboards        │
                           │  • Risk prioritisation       │
                           │  • Alerts                    │
                           └──────────────▲───────────────┘
                                          │
                     Cloud API integrations / read-only access
                                          │
                  ┌───────────────────────┴───────────────────────┐
                  │                                               │
                  │                                               │
        ┌─────────┴──────────┐                         ┌──────────┴─────────┐
        │      Microsoft      │                         │        AWS         │
        │       Azure         │                         │                    │
        └─────────▲──────────┘                         └──────────▲─────────┘
                  │                                               │
        Azure service principal                         AWS IAM integration
        with least-privilege                            role with read-only
        permissions                                     security permissions
                  │                                               │
      ┌───────────┼────────────┐                     ┌────────────┼───────────┐
      │           │            │                     │            │           │
      ▼           ▼            ▼                     ▼            ▼           ▼
 Resource      Azure VMs     Storage              EC2          S3 Bucket    IAM Roles
 Groups                     Account / Blob        Instances                 and Policies
      │           │            │                     │            │           │
      ▼           ▼            ▼                     ▼            ▼           ▼
   VNets       Windows VM   Public/private      Security      Public/private Excessive
   Subnets     Linux VM     containers          Groups        access settings permissions
   NSGs```
```

##Remediation Flow

```Datadog finding
      │
      ▼
Review affected cloud resource
      │
      ▼
Prioritise by severity and attack-path impact
      │
      ├── Restrict NSG / Security Group ingress
      ├── Remove public storage access
      ├── Reduce IAM / RBAC permissions
      └── Remove unnecessary public IP addresses
      │
      ▼
Datadog reassessment
      │
      ▼
Finding resolved / posture improved
```

## Artefacts

## 📚 Skills Demonstrated

- Multi-Cloud Security
- AWS Security
- Azure Security
- Datadog Cloud Security Management
- Cloud Security Posture Management (CSPM)
- Cloud Asset Inventory
- Infrastructure Risk Assessment
- Cloud Misconfiguration Analysis
- Identity & Access Security
- Network Security
- Least Privilege
- Cloud Security Hardening
