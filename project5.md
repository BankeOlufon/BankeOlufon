# 🌐 Multi-Cloud Security Posture Management (AWS + Azure + Prowler / Data Dog)

## 📌 Project Overview
This project details the architectural deployment and evaluation of a Multi-Cloud Security Posture Management (CSPM) evaluation across heterogeneous cloud ecosystems. Using **Prowler Open Source**, this lab establishes a centralized, command-line-driven compliance auditing framework across concurrent AWS and Azure infrastructure deployments. 

By programmatically linking both environments to a single Prowler auditing node via secure API configurations, this lab simulates real-world environmental misconfigurations, maps dangerous attack paths, and isolates "Toxic Combinations" to prioritize remediation across the entire multi-cloud footprint.

---

## 🎯 Strategic Focus Areas
- **Multi-Cloud Perimeter Auditing:** Cross-tenant security mapping spanning both Amazon Web Services (AWS) and Microsoft Azure.
- **Automated Baseline Compliance:** Auditing infrastructure states against industry-standard frameworks (CIS Benchmarks, NIST, ISO 27001).
- **Toxic Combination Discovery:** Correlating overlapping security flaws (e.g., exposed storage + over-privileged identity) into single attack paths.
- **Risk-Prioritized Remediation:** Executing localized operational fixes to sever attack chains without disrupting baseline cloud operations.

---

## 🛠️ Technical Tasks & Functions Performed

### 1. Multi-Cloud Inventory & Audit Node Deployment
- **Dual-Provider Infrastructure Setup:** Provisioned sample test infrastructure across both cloud segments:
  - **AWS Space:** Amazon EC2 compute instances, Identity and Access Management (IAM) role boundaries, and Amazon S3 storage buckets.
  - **Azure Space:** Virtual Machines (VMs), Azure Resource Groups, and Entra ID storage blobs.
- **Auditing Node Execution:** Deployed an isolated Linux orchestration node, installing Prowler via Python’s package manager (`pip install prowler`) with zero custom coding dependencies.
- **Cross-Cloud Identity Mapping:** Configured an Azure Service Principal with read-only directory/subscription-level permissions and linked an AWS IAM cross-account auditing role to allow Prowler to securely query raw asset configurations via native APIs (`az cli` and `aws cli`).

### 2. Simulated Infrastructure Vulnerabilities
To challenge Prowler’s detection engine and evaluate absolute environmental posture, specific security mistakes were intentionally introduced across both providers:
- **Exposed Data Assets:** Modified access control lists (ACLs) to expose a private AWS S3 bucket and an Azure Blob Container directly to the public internet.
- **Permissive Firewalls:** Configured open ingress rules (0.0.0.0/0) on AWS Security Groups and Azure Network Security Groups (NSGs) for highly targeted management ports (SSH port 22 / RDP port 3389).
- **Identity Excess:** Attached an over-privileged service account key containing administrative write permissions to a standard, non-administrative asset.

### 3. Toxic Combination Analysis & Attack Path Remediation
- **Scanning Automation:** Triggered comprehensive multi-cloud scans using single-line terminal execution paths, pulling configuration data simultaneously from both providers.
- **Attack Chain Visualizations:** Used Prowler’s automatically generated HTML dashboards to correlate independent vulnerabilities into toxic, operational attack paths:

  [ Open Ingress Port 22 ] ──> [ Unpatched Compute VM ] ──> [ Over-Privileged Identity Key ] ──> [ Public Storage Leak ]

  - **Remediation Execution:** Prioritized fix ordering based on risk severity scores. Closed the root firewall rule on the perimeter network layer, breaking the attack chain at the initial access vector and neutralizing the downstream risk to underlying cloud data storage.

---

## 📊 Implemented Command-Line Architecture

The auditing environment is updated and run directly from the deployment node terminal using standard CLI mechanics:

```bash
# Step 1: Install the open-source posture engine
pip install prowler

# Step 2: Authenticate to both cloud providers using baseline command-line tools
aws configure
az login

# Step 3: Execute the automated multi-cloud assessment matrix
# Run comprehensive audit across AWS infrastructure assets
prowler aws

# Run explicit Azure tenant audit and generate a clean, local HTML dashboard report
prowler azure --az-cli-auth -M html


```
---
📷 Portfolio Artifacts & Posture Dashboard
Artifact 1: Consolidated Prowler HTML Assessment Dashboard
[Screenshot Placeholder: Local Prowler HTML Dashboard output showing multi-cloud security compliance scores and pass/fail distribution metrics]

The centralized multi-cloud security assessment dashboard generated natively by Prowler.
Artifact 2: Target Audit Log Summary
| Provider | Target Resource Affected | Vulnerability Identified | Severity Category | Remediation Action Deployed |
| :--- | :--- | :--- | :--- | :--- |
| AWS | s3://corp-financial-vault | Public Read Access Enabled | Critical | Restricted ACL boundaries to Private IAM Access Only. |
| Azure | nsg-dev-workstations | Open Ingress RDP (Port 3389) | High | Blocked 0.0.0.0/0 and limited access to specific corporate IP space. |
| AWS | iam-app-executor-key | Excessive Admin Privileges | High | Rolled key credentials and attached stripped, read-only policy. |

---
<!--
📈 Why This Matters to Enterprise Employers
True Multi-Cloud Visibility: Proves capability to handle concurrent cloud architectures (AWS + Azure) without relying on restricted, corporate enterprise licenses or complex coding environments.

Command-Line Engineering Efficiency: Demonstrates that I can deploy open-source testing solutions via terminal frameworks, manage API integrations safely, and parse configuration data into actionable remediation summaries.

Framework and Governance Readiness: The evaluation methods align explicitly with CIS Foundations Benchmarks for AWS and Azure, proving the capability to maintain corporate audit preparedness.

-->
