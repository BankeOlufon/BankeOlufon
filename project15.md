# 🤖 Agentic AI Abuse, Privilege Escalation & Sentinel SIEM Detection Lab (PyRIT)

## 📌 Project Overview
This lab demonstrates how an external attacker could manipulate an enterprise AI assistant to abuse backend privileges, and how defenders can detect and stop those attacks in real time.  

Using **Microsoft PyRIT (Python Risk Identification Tool)**, I scripted a blind attack scenario where the attacker only interacts through chat prompts. The workflow automatically probes the assistant for hidden tools, then runs a multi‑turn social engineering strategy to extract sensitive cloud database records.  

On the defense side, I configured runtime event logging into **Azure Log Analytics Workspace** and wrote custom **Kusto Query Language (KQL)** rules in **Microsoft Sentinel** to detect unauthorized tool execution and prompt injection attempts.

---

## 🎯 Technical Scope
- **Blind Attacker Simulation:** Modeling an external actor probing a chat interface for hidden functions.  
- **Excessive Agency Exploitation:** Forcing the AI to call backend APIs with elevated privileges.  
- **Multi‑Turn Prompt Injection:** Running iterative conversational attacks using PyRIT.  
- **Cloud Telemetry Logging:** Forwarding runtime events to Azure Monitor.  
- **SIEM Detection Engineering:** Writing Sentinel rules to alert on suspicious activity.  
- **MITRE ATLAS Mapping:** Aligning attack phases with a structured adversary matrix.  

---

## 🛠️ Implementation Breakdown

### 1. Target Setup (Prototype Backend + Azure OpenAI)
I **vibe‑coded a lightweight prototype backend** using Gemini to connect Azure OpenAI (GPT‑4o/GPT‑5 mini) with Azure Data Tables. This was a quick demo scaffold, not a production chatbot.  
* **Backend Functions:** Two functions were exposed — `query_public_stock()` (open inventory) and `query_internal_margins()` (sensitive supplier records).  
* **Security Flaw:** The backend relied on default cloud credentials with no role validation, meaning the AI assistant could access both tables if manipulated.  

### 2. External Attacker Pipeline (PyRIT)
I built a PyRIT script to simulate a realistic blind attack chain:  
* **Stage 1 (Reconnaissance):** Prompting the assistant to reveal available features and backend functions.  
* **Stage 2 (Exploitation):** Using behavioral manipulation to bypass system instructions and force execution of sensitive queries.  

### 3. Detection & SIEM Integration (Azure Sentinel)
I focused on the defense side by engineering detection rules:  
* **Log Aggregation:** Runtime events were shipped into Azure Log Analytics.  
* **Sentinel Analytics:** Custom KQL rules flagged when unauthenticated sessions triggered sensitive backend functions.  

---

## 🛡️ Mitigation Strategy

This vulnerability is classified as **Excessive Agency (OWASP LLM02)**. To secure the architecture, the following three controls must be implemented:

*   **User-Level Session Validation:** Never rely on the LLM's system prompt to restrict data access. The Python backend must extract the user's login token from the incoming web request and verify their specific role before executing any internal database function (such as `query_internal_margins`).
*   **Restricted Cloud Privileges:** The application's cloud identity (Managed Identity or Service Principal) must never hold global subscription rights like `Owner` or `Contributor`. In the Azure Portal, assign explicit, low-privilege RBAC roles (like `Storage Table Data Reader`) limited strictly to the required tables.
*   **API Endpoint Separation:** Split the chatbot into separate web tracks within your Python application code rather than giving one interface access to every tool. The public chatbot track (`/api/public-chat`) should only be compiled with the public tool schema, meaning the code for the internal margins tool is completely absent. The internal tool code should sit on a completely separate code endpoint (`/api/manager-chat`) that is locked behind a standard login screen.

 ---

## 🔐 Practical Security Insights
- **Prompt‑based security is unreliable:** If the server itself has backend access, attackers can inherit those privileges by manipulating the AI.  
- **Mitigation must be in code:** Backend logic should enforce user roles and tokens before executing database queries.
 
- **MITRE ATLAS Mapping:**  
  * **AML.T0015 (Reconnaissance):** Probing the LLM for tool schemas.  
  * **AML.T0051 (LLM Input Injection):** Multi‑turn adversarial prompt injections.  
  * **AML.T0055 (Excessive Agency):** Triggering high‑privilege queries via application identities.  

---

## 📚 Technical Skills Demonstrated
- **AI Security Testing:** Running automated adversarial attacks with PyRIT.  
- **Defensive Engineering:** Exporting runtime states to cloud logging.  
- **SIEM Rule Writing:** Building KQL detections in Sentinel.  
- **Vulnerability Analysis:** Identifying flaws where access control was missing from backend code.  

---

⚠️ **Note on scope:** I did not build chatbot logic or engineer a full backend system. The prototype was vibe‑coded with Gemini purely to connect Azure OpenAI with Azure Data Tables. My hands‑on work was in **attack simulation and defense engineering**.
