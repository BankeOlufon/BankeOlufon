AEGIS IR
                         ATTACK GENERATION

┌────────────────────────────────────────────────────────────┐
│ Garak / Manual Attacker                                    │
│ Sends prompt injections, jailbreaks and encoded payloads   │
└────────────────────────────┬───────────────────────────────┘
                             │ HTTPS
                             ▼

                         APPLICATION

┌────────────────────────────────────────────────────────────┐
│ FastAPI                                                    │
│ Receives requests and writes structured security logs      │
└───────────────┬───────────────────────────┬────────────────┘
                │                           │
                │ prompt                    │ application logs
                ▼                           │
┌──────────────────────────────┐            │
│ L7-Aegis                     │            │
│ Scores suspicious requests   │            │
└───────────────┬──────────────┘            │
                │ detection log             │
                └──────────────┬────────────┘
                               │
                ┌──────────────▼─────────────┐
                │ Local LLM through Ollama   │
                │ Generates agent decisions  │
                └──────────────┬─────────────┘
                               │ tool request
                               ▼
                ┌────────────────────────────┐
                │ Agent Tool Layer           │
                │ Executes Python functions  │
                └──────────────┬─────────────┘
                               │ SQL
                               ▼

                         DATA LAYER

                ┌────────────────────────────┐
                │ PostgreSQL                 │
                │                            │
                │ • public_inventory         │
                │ • internal_wholesales      │
                │ • agent_actions            │
                │ • incident_audit           │
                └──────────────┬─────────────┘
                               │ database logs
                               ▼

                    MONITORING AND RESPONSE

  FastAPI logs ────────────────┐
  L7-Aegis logs ───────────────┤
  Agent tool logs ─────────────┤
  PostgreSQL logs ─────────────┤
  Linux logs ──────────────────┘
                │
                ▼
       ┌───────────────────────┐
       │ Wazuh Agent           │
       │ Collects local events │
       └───────────┬───────────┘
                   ▼
       ┌───────────────────────┐
       │ Wazuh Manager         │
       │ Decoders and rules    │
       └───────────┬───────────┘
                   ▼
       ┌───────────────────────┐
       │ Wazuh Dashboard       │
       │ Alerts and timeline   │
       └───────────┬───────────┘
                   ▼
       ┌───────────────────────┐
       │ Active Response       │
       │                       │
       │ • Block source IP     │
       │ • Revoke session      │
       │ • Disable tool        │
       │ • Preserve evidence   │
       └───────────────────────┘
