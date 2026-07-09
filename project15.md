# 🤖 Agentic AI Abuse & Privilege Escalation Lab (PyRIT)

## 📌 Project Overview
Set up an automated red teaming pipeline using Microsoft PyRIT (Python Risk Identification Tool) to assess vulnerabilities in tool-enabled AI agents.  
This project demonstrates how adversaries can manipulate AI systems with excessive agency to execute unauthorized actions or leak sensitive data.

---

## 🎯 Core Areas Covered
- AI Agent Red Teaming & Adversarial Simulation  
- Prompt Injection & Excessive Agency Testing  
- Multi-Turn Attack Orchestration with PyRIT  
- MITRE ATLAS Mapping & Vulnerability Reporting  

---

## 🛠️ Technical Tasks & Functions Performed

### Target AI Agent Setup
- Configured a mock corporate AI assistant using Azure OpenAI / OpenAI API.  
- Provided the agent with mock “tools” (e.g., database read functions, marketing data search).  

### PyRIT Attack Orchestration
- Wrote Python scripts (~40 lines) to load PyRIT’s Crescendo and TAP attack strategies.  
- Automated multi-turn adversarial conversations to manipulate the AI agent.  
- Tested malicious objectives such as exfiltrating restricted HR salary lists.  

### Vulnerability Testing
- Simulated **Excessive Agency** by tricking the model into calling unauthorized tools.  
- Executed **Indirect Prompt Injection/Jailbreaking** to bypass system safety instructions.  

### Analytics & Reporting
- Collected conversational histories and evaluation scores in PyRIT’s SQLite database.  
- Used CoPyRIT GUI to visualize where guardrails failed.  
- Mapped exploits directly to MITRE ATLAS framework for structured reporting.  

---

<!-- ## 📊 Phase Mapping Context
(Not applicable — standalone AI red teaming case study)
-->

---

## 🔐 Security Outcomes
- Validated risks of excessive agency in AI agents.  
- Demonstrated prompt injection vulnerabilities in multi-turn conversations.  
- Produced structured vulnerability reports aligned with MITRE ATLAS.  

---

## 📚 Skills Demonstrated
- Python scripting with PyRIT framework  
- AI red teaming methodologies  
- Prompt injection and excessive agency testing  
- Vulnerability mapping to MITRE ATLAS  

---

<!-- ## 📷 Portfolio Artifacts
[Placeholder: PyRIT Crescendo attack script snippet]  
[Placeholder: CoPyRIT GUI showing failed guardrails]  
-->

---

<!-- ## 📈 Why This Matters to Employers
Shows ability to red team AI systems, identify excessive agency vulnerabilities, and produce structured reports aligned with industry frameworks.
-->

---

## 🔗 Related Projects
- [Enterprise Cloud Infrastructure & Identity Lifecycle Engineering](#)  
- [SaaS Security & Identity Pentesting (Okta Federation, SCIM, OAuth)](#)  
- [IoT Firmware Reverse Engineering & Vulnerability Research Lab](#)  
- [P5.js Game Development Project](#)  
