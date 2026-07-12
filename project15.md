# 🤖 Agentic AI Abuse, Privilege Escalation & Sentinel SIEM Detection Lab (PyRIT)

## 📌 Project Overview
This project simulates an end-to-end attack lifecycle where an external threat actor targets an enterprise AI storefront assistant to exploit **Excessive Agency (OWASP LLM02)** and **Sensitive Information Disclosure (OWASP LLM06)** vulnerabilities. 

Using **Microsoft PyRIT (Python Risk Identification Tool)**, I built an attack script to model a blind external attacker who lacks access to backend source code. The attack workflow automatically conducts reconnaissance to find available tools via chat prompts and then executes a multi-turn social engineering strategy to extract backend cloud database records.

To defend against this, the application's runtime events were piped into an **Azure Log Analytics Workspace**. I then wrote custom **Kusto Query Language (KQL)** rules inside **Microsoft Sentinel** to detect unauthenticated tool execution and prompt injection attempts in real time.

---

## 🎯 Technical Scope
- **Blind Attacker Simulation:** Modeling an external threat actor probing a chat interface for hidden functions.
- **Excessive Agency Exploitation:** Bypassing soft system prompts to force an LLM to call high-privilege backend APIs.
- **Automated Multi-Turn Prompt Injection:** Orchestrating iterative conversational attacks using PyRIT.
- **Cloud Telemetry Logging:** Shipping application event runtime states to Azure Monitor.
- **SIEM Detection Engineering:** Writing production-ready Sentinel rules to alert on security events within an AI runtime.
- **MITRE ATLAS Mapping:** Mapping AI exploitation phases directly to a structured matrix.

---

## 🛠️ Implementation Breakdown

### 1. The Vulnerable Target Architecture (Python & Azure OpenAI)
I rapidly prototyped a Python application integrated with **Azure OpenAI (GPT-4o/GPT-5 mini)** to serve as a corporate AI assistant. 
* **Backend Functions:** The application utilizes the `azure-data-tables` SDK to expose two functions to the LLM: `query_public_stock()` (for open inventory) and `query_internal_margins()` (for sensitive business records and supplier PII).
* **The Security Flaw:** The Python backend relies on local OS tokens (`DefaultAzureCredential`) to communicate with Azure Storage, giving the app server permission to read both tables. However, the code contains **no user-role validation** before executing the database functions. It relies entirely on the LLM's system prompt to enforce data permissions.

### 2. The External Attacker Pipeline (PyRIT)
Because an external attacker cannot view the underlying Python variables, I configured a PyRIT script to execute a realistic, blind attack chain in two stages:
* **Stage 1 (Reconnaissance):** The script prompts the AI assistant to list its available features, plugins, and backend capabilities, mapping out exposed functions.
* **Stage 2 (Exploitation):** Once the tool names are discovered, the script initiates a multi-turn conversation strategy. It uses behavioral manipulation to bypass the LLM's system instructions, forcing the backend to fetch confidential supplier rows without administrative authorization.

### 3. Detection & SIEM Integration (Azure Log Analytics & Microsoft Sentinel)
To monitor and catch these injections, I configured the application's runtime engine to generate structured JSON event logs every time a backend tool is triggered.
* **Log Aggregation:** Telemetry is forwarded directly into an Azure Log Analytics Workspace.
* **Sentinel Analytics:** I deployed custom KQL rules inside Microsoft Sentinel. These rules match incoming chat actions against user authentication tables, alerting defenders the moment a public session successfully triggers a sensitive, internal data function.

---

## 🔐 Practical Security Insights

* **The Fallacy of Prompt-Based Security:** This lab demonstrates that system prompts are not a valid security boundary for data authorization. If an app server has access to a database via cloud identity tokens, an attacker who manipulates the LLM effectively inherits the server's backend privileges.
* **Mitigation Strategy:** Security must be enforced in the backend code. The Python application must parse the user's JSON Web Token (JWT) or session role before passing execution variables to the `azure-data-tables` SDK, ensuring the request is dropped regardless of what the LLM instructs the app to do.
* **MITRE ATLAS Mapping:**
  * **AML.T0015 (Reconnaissance):** Probing the LLM to map out underlying tool schemas.
  * **AML.T0051 (LLM Input Injection):** Executing multi-turn adversarial prompt injections.
  * **AML.T0055 (Excessive Agency):** Forcing backend scripts to run high-privilege queries using application identities.

---

## 📚 Technical Skills Demonstrated

* **AI Security Testing:** Orchestrating automated multi-turn adversarial attacks using Microsoft PyRIT.
* **Defensive Engineering:** Exporting application runtime states to cloud logging environments.
* **SIEM Rule Engineering:** Writing functional KQL detection scripts to isolate prompt injection exploits within Microsoft Sentinel.
* **Vulnerability Analysis:** Auditing structural code flaws where data access controls are decoupled from user sessions.
