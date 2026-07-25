# 🛡️ Threat Detection Engineering & SIEM Operations

## 📌 Project Overview
This security operations engineering project focuses on building a centralized Azure logging and monitoring environment using **Microsoft Sentinel**, **Log Analytics Workspace**, **Azure Monitor Agent (AMA)**, **Virtual Network Flow Logs**, **Traffic Analytics**, **Defender for Cloud**, **Automation Rules**, and **Azure Logic Apps**.

The primary detection scenario identifies malicious external port scanning against Azure virtual machines by detecting external source IPs attempting connections to more than **15 unique destination ports within a one-hour window**.

---

## 🎯 Objectives
- **Centralized Logging**: Build a unified logging architecture to aggregate Azure identity, endpoint, infrastructure, and network telemetry into a single Log Analytics Workspace.  
- **Agent Deployment**: Configure Azure Monitor Agent (AMA) and Data Collection Rules (DCR) for OS-level log collection on Windows and Linux endpoints.  
- **SIEM Integration**: Connect Microsoft Sentinel to the centralized workspace to establish detection, alerting, investigation, and response capabilities.  
- **KQL Development**: Develop KQL queries for network flow validation, source IP scoping, threat hunting, detection, host investigation, and post-remediation validation.  
- **Custom Detection Rule**: Create a Microsoft Sentinel Scheduled Analytics Rule designed to identify external port-scanning activity.  
- **Entity & Framework Mapping**: Map alerts and incidents to Sentinel entities (IP Address, Host) and align detections with the MITRE ATT&CK framework.  
- **SOAR Automation**: Configure Automation Rules and an Azure Logic App playbook to orchestrate response workflows.  
- **Threat Intelligence Enrichment**: Query the AbuseIPDB API to enrich suspected attacker IP addresses with real-time reputation scores.  
- **Automated Notifications**: Deliver rich email notifications to security analysts containing alert context and threat intelligence data.  
- **Incident Investigation**: Establish structured investigation workflows using KQL to evaluate reconnaissance severity and scope.  
- **Targeted Remediation**: Define manual remediation workflows to block malicious source IPs via Azure Network Security Group (NSG) deny rules.  

---

## 🏗️ Security Monitoring Architecture

### Telemetry Pipeline

```
Microsoft Entra ID
├── Sign-in Logs
├── Audit Logs
└── Provisioning Logs

Azure Control Plane
└── Azure Activity Logs

Windows VM
├── Azure Monitor Agent
├── Windows Security Events
├── Windows Event Logs
└── Heartbeat

Linux VM
├── Azure Monitor Agent
├── Syslog
└── Heartbeat

Azure Virtual Network
└── Virtual Network Flow Logs
↓
Traffic Analytics
↓
Log Analytics Workspace
↓
Microsoft Sentinel
├── Hunting Queries
├── Analytics Rules
├── Alerts
├── Incidents
├── Automation Rules
└── Logic App Playbook
├── AbuseIPDB Enrichment
└── Email Notification 
```


---

## 📊 Centralized Telemetry Map

| **Data Source** | **Scope** | **What it records** |
|-----------------|-----------|----------------------|
| SigninLogs | Microsoft Entra ID (Identity) | User sign-ins, MFA, Conditional Access, failed logins |
| AuditLogs | Microsoft Entra ID (Identity) | User/group changes, password resets, app registrations, role assignments |
| AzureActivity | Azure Control Plane (Subscription) | Resource creation, deletion, RBAC changes, policy changes |
| AzureDiagnostics | Azure Resources | Diagnostic logs from Azure services (Key Vault, Storage, App Gateway, etc.) |
| Event | Windows Endpoints | Windows Application, System and other Event Logs |
| Heartbeat | Azure Arc / AMA-managed Endpoints | Agent health and connectivity |
| Microsoft Defender for Cloud | Azure Resources | Security posture, recommendations, attack paths, cloud security alerts |
| Virtual Network Flow Logs | Azure VNets | Network flows (source/destination IP, ports, protocol, allow/deny, bytes) |
| Storage Logs | Azure Storage Accounts | Blob, file, queue and table access |
| Key Vault Logs | Azure Key Vault | Secret, key and certificate access |

---

## 🔧 Azure Monitor Agent & Log Collection Setup
The **Azure Monitor Agent (AMA)** was deployed across target virtual machines and linked to **Data Collection Rules (DCR)** to specify which operational events to collect and forward to the central Log Analytics Workspace.

### Collected Telemetry Scope
- **Windows VM Telemetry**:
  - Successful (Event ID 4624) and failed (Event ID 4625) RDP logins  
  - Windows Security Events & Audit Logs  
  - Administrative PowerShell execution events  
  - System file creation and modification activity  
  - System & Application event logs  
  - Periodic agent Heartbeat signals  

---

## 🔎 Detection Scenario: External Malicious Port Scanning

**Detection Goal**  
Detect external network reconnaissance targeting Azure virtual machines by isolating external source IP addresses attempting to connect to >15 distinct destination ports within 1 hour.

**Core Detection Criteria**:
- Direction: Inbound network flows (`FlowDirection == "Inbound"`)  
- Origin: External IP addresses (excluding RFC 1918 private IP ranges)  
- Status: Denied connection attempts (`FlowStatus == "Denied"`, `DeniedInFlows > 0`, or `FlowStatus == "Malicious"`)  
- Threshold: `dcount(DestPort) > 15`  
- Grouping: Grouped by Attacker IP, Target IP, and Target Machine  
- Time Window: Rolling 1-hour window  

---

## 🧪 KQL Queries

### External Port-Scanning Detection Rule
```kql
NTANetAnalytics
| where TimeGenerated > ago(1h)
| where SubType == "FlowLog" and FlowDirection == "Inbound"
| where SrcIp !startswith "10."
    and SrcIp !startswith "192.168."
    and SrcIp !startswith "172."
| where FlowStatus == "Denied"
    or DeniedInFlows > 0
    or FlowStatus == "Malicious"
| summarize
    DistinctPortsScanned = dcount(DestPort)
    by SrcIp, DestIp, DestVm
| where DistinctPortsScanned > 15
| project
    AttackerIP = SrcIp,
    TargetMachine = DestVm,
    DistinctPortsScanned
```
### ⚙️ Automation Rule & Logic App Orchestration

```
Analytics Rule Detects Port Scan
        ↓
Sentinel Generates Alert
        ↓
Automation Rule Evaluates Conditions
        ↓
Matching Alert Context Confirmed
        ↓
Logic App Playbook Initiated

```
### 🔄 Logic App Playbook & Threat Intelligence Integration

```
Microsoft Sentinel Alert Trigger
        ↓
Receive Alert Payload
        ↓
Extract Entities (Attacker IP, Target Host)
        ↓
HTTP GET Request to AbuseIPDB
        ↓
Parse IP Reputation Data
        ↓
Format HTML Alert Summary
        ↓
Send Office 365 Outlook Email

```

## 🔍 Investigation & Remediation Workflow
Triage & Investigation Steps:

Analyst receives automated email and opens Sentinel Incident.

Review mapped AttackerIP and TargetMachine entities.

Inspect AbuseIPDB confidence score and threat report history.

### Remediation Process:

```
Sentinel Alert Triggered
        ↓
Analyst Conducts Network Evidence Review
        ↓
AbuseIPDB Threat Intelligence Verified
        ↓
Malicious Intent Confirmed
        ↓
Inbound Deny Rule Created in Azure NSG
        ↓
Subsequent Traffic Dropped & Validated

```

## 🔐 Security Outcomes & Project Achievements
Centralized Security Infrastructure: Unified logs across Entra ID, Control Plane, VM OS logs, and Network Flow logs into Sentinel.

Custom Detection Coverage: Operationalized a KQL detection rule targeting active reconnaissance.

Framework Standardized: Aligned alerting with MITRE ATT&CK T1595 (Active Scanning).

Automated SOAR Capabilities: Reduced MTTR

---
<img width="791" height="328" alt="image" src="https://github.com/user-attachments/assets/dedea3b3-4a56-4275-934f-0c646d0451a1" />
<img width="317" height="415" alt="image" src="https://github.com/user-attachments/assets/4479d0ac-e382-4c78-9cf3-34baaffbb710" />
<img width="587" height="398" alt="image" src="https://github.com/user-attachments/assets/1e2bc4b9-1336-475d-957a-dcc2a34cf99a" />
<img width="428" height="374" alt="image" src="https://github.com/user-attachments/assets/ae9a0ff2-35ed-4e5d-89e5-6ec89b5967e2" />
<img width="755" height="312" alt="image" src="https://github.com/user-attachments/assets/21265eb2-7fe9-4267-b64b-c960595b2e0d" />
<img width="562" height="244" alt="image" src="https://github.com/user-attachments/assets/52bf361f-1b9d-4840-aba3-fd88241b73c5" />
<img width="272" height="398" alt="image" src="https://github.com/user-attachments/assets/77b598e0-dda0-4fb4-9b41-287bae3d65bf" />
<img width="264" height="55" alt="image" src="https://github.com/user-attachments/assets/c6947803-ab84-42b6-9941-ac77eefacb56" />


