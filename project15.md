# Agentic AI Abuse & Privilege Escalation Lab (LLM Prompt Injection via Garak)

## 📌 Overview
This project demonstrates adversarial testing of an OpenAI LLM using **Garak**.  
The focus is on probing the model for **prompt injection, refusal bypass, and privilege escalation attempts**, while integrating with **Azure cloud services** for secure key management and logging.

---

## 🎯 Objectives
- Run Garak probes against an OpenAI LLM endpoint.  
- Store API keys securely in **Azure Key Vault**.  
- Log attack results into **Azure Table Storage** for analysis.  
- Showcase AI red teaming methodology in a cloud‑integrated environment.  

---

## 🔒 Security Considerations
- Keys are never hardcoded; always retrieved from **Azure Key Vault**.  
- Logs are stored in a controlled **Azure Table Storage** resource for auditability.  
- Attacks are run in a **lab environment only**, not against production systems.  

---

## 📊 Example Output
| Timestamp           | Probe Type       | Outcome                          |
|---------------------|------------------|----------------------------------|
| 2026-07-12 18:30    | Prompt Injection | Model bypassed refusal           |
| 2026-07-12 18:31    | Jailbreak        | Model resisted, returned refusal |

---

## 📂 Portfolio Positioning
This project highlights **AI red teaming** combined with **cloud security best practices**.  
It demonstrates the ability to:  
- Attack LLMs with Garak.  
- Securely manage secrets in Azure.  
- Log and analyze adversarial results in a structured way.  

