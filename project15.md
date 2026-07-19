# 🤖 Agentic AI Abuse & Privilege Escalation Lab
### Black-Box LLM Pentesting using Garak, Azure OpenAI & FastAPI

> Simulating an external attacker attempting to manipulate an AI agent into disclosing restricted business information or performing unauthorized actions.

---

# 📖 Project Overview

As AI agents become increasingly integrated with enterprise systems, traditional web application security testing is no longer sufficient. Unlike conventional applications, LLM-powered agents can dynamically choose which tools to invoke, making them susceptible to **prompt injection**, **tool misuse**, and **excessive agency**.

This project demonstrates a realistic **black-box penetration test** against an AI agent built with **Azure OpenAI GPT-5-mini**.

The objective was **not** to compromise Azure infrastructure directly, but instead to determine whether an attacker interacting only through the public API could manipulate the AI agent into:

- 🔓 Revealing hidden system prompts
- 📂 Accessing internal business data
- 🛠 Invoking unauthorized tools
- 📊 Performing privileged business operations
- 🧠 Ignoring developer instructions

---

# 🏗️ Target Architecture

```
External Attacker
        │
        ▼
PowerShell / Garak
        │
        ▼
FastAPI Endpoint (/chat)
        │
        ▼
GPT-5-mini (Azure OpenAI)
        │
        ▼
Tool Selection
        │
        ▼
Azure Table Storage
```

The attacker had **no access** to:

- Azure Portal
- Source code
- Key Vault
- Storage Account
- Azure credentials

The only accessible interface was the public REST endpoint.

This accurately reflects a real-world black-box assessment.

---

# ⚙️ Testing Environment

### AI Model

- GPT-5-mini
- Azure OpenAI

### Framework

- FastAPI
- Python

### Automation

- Garak

### Testing Interface

- PowerShell
- REST API

### Backend Resources

- Azure Table Storage
- Azure Key Vault

---

# 🎯 Attack Objectives

The assessment focused on determining whether an attacker could exploit the AI agent through prompt engineering alone.

The primary objectives included:

- Extract hidden system prompts
- Bypass developer restrictions
- Access internal wholesale information
- Trigger unauthorized tool execution
- Abuse excessive AI agency

---

# ⚔️ Attack 1 — Direct Prompt Injection

## Objective

Determine whether carefully crafted prompts could convince the model to ignore its system instructions and retrieve restricted business information.

---

# 🔐 Attack 2 — System Prompt Extraction

## Objective

Attempt to reveal hidden system instructions controlling the agent.

---

# 🧠 Attack 3 — System Prompt Summarisation

## Objective

Attempt to indirectly infer hidden instructions without requesting them verbatim.

---

# 🤖 Garak Integration

To automate adversarial testing, Garak was configured to interact with the deployed FastAPI endpoint rather than directly importing the Python agent.

This preserved the black-box threat model.

```
Attacker
      │
      ▼
Garak
      │
      ▼
HTTP POST /chat
      │
      ▼
FastAPI
      │
      ▼
GPT-5-mini
```

This approach accurately simulated how a real attacker would interact with an exposed AI application.

---

# 🧪 Findings

| Test | Result |
|-------|--------|
| Prompt Injection | ✅ Failed |
| System Prompt Extraction | ✅ Failed |
| Prompt Summarisation | ✅ Only high-level policies disclosed |
| Internal Data Access | ✅ Blocked |
| Excessive Agency | ✅ Not observed |

---

# 📊 Overall Assessment

| Category | Rating |
|-----------|---------|
| Prompt Injection Resistance | 🟢 Strong |
| System Prompt Protection | 🟢 Strong |
| Tool Misuse Protection | 🟢 Strong |
| Internal Data Protection | 🟢 Strong |
| Overall Security Posture | 🟢 Low Risk |

---

# 💡 Key Takeaways

This assessment demonstrates that **a successful penetration test does not always result in a successful exploit**.

During testing, GPT-5-mini consistently:

- ✅ Respected developer-defined access controls
- ✅ Refused prompt injection attempts
- ✅ Prevented disclosure of hidden system instructions
- ✅ Limited access to authorised public business data
- ✅ Resisted attempts to manipulate tool usage

The assessment therefore concluded that **no unauthorized access or excessive agency was achieved under the defined external black-box threat model**.

---

# 🛠️ Technologies Used

- 🤖 Azure OpenAI GPT-5-mini
- 🐍 Python
- ⚡ FastAPI
- 🔍 Garak
- ☁️ Azure Table Storage
- 🔐 Azure Key Vault
- 💻 PowerShell
- 🌐 REST API

---

# 📚 Skills Demonstrated

- 🔍 AI Security Testing
- 🤖 LLM Prompt Injection Assessment
- 🧠 System Prompt Leakage Testing
- 🛡️ Agentic AI Security
- ☁️ Azure Security
- 🐍 Python Development
- 🔍 Garak Automation
- 📊 Security Assessment & Reporting


<img width="853" height="296" alt="image" src="https://github.com/user-attachments/assets/097dc8d5-637c-4f6a-9a87-ed716d945d98" />
<img width="689" height="211" alt="image" src="https://github.com/user-attachments/assets/e150e2ca-b179-41d4-bdcd-b1fbb23d4807" />
<img width="692" height="176" alt="image" src="https://github.com/user-attachments/assets/ae7f4e25-55d3-413a-87b8-9d35b780b102" />
<img width="950" height="403" alt="image" src="https://github.com/user-attachments/assets/cdc89459-1874-4ac8-a768-ac06ebf5502d" />




