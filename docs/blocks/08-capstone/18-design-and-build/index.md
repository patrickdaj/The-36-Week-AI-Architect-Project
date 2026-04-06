# 🏠 Block 18: Design & Build (Capstone)

[← Block 17: Platform Build](../../07-production/17-platform-build/index.md) | [Block 19: Ship & Present →](../19-ship-and-present/index.md)

> *"This is your thesis. Pick a real problem from your security work, design an AI solution, and build it from scratch."*

**Quick Reference:** [→ Block 18 Quick Ref](quick-ref.md)

---

## Before You Start Block 18

- Review everything you've built in Blocks 1–32
- Pick your capstone project (see ideas below)
- 📖 [Google — People + AI Guidebook](https://pair.withgoogle.com/) — designing AI products for humans

---

## Capstone Project Selection

Pick ONE project that solves a real problem from your network/security work. It should combine at least 3 of these capabilities:

| Capability | You Built It In |
|-----------|----------------|
| RAG | Blocks 9–12 |
| Agents / Tool Use | Blocks 14–20 |
| Local Models | Blocks 21–24 |
| Model Routing | Block 15 |
| Security / Guardrails | Block 16 |
| Evaluation | Block 14 |

### Project Ideas (pick one or propose your own)

1. **Incident Response Copilot** — Ingests SIEM alerts, correlates with threat intel (RAG), triages automatically (agent), escalates to human when uncertain (HITL), runs locally for sensitive data.

2. **Security Policy Auditor** — Feeds in corporate security policies (RAG), reviews infrastructure configs (agent), maps to compliance frameworks (CIS, NIST), generates remediation playbooks.

3. **Network Anomaly Explainer** — Takes NetFlow/PCAP data, identifies anomalies, uses AI to explain what the traffic pattern means, suggests investigation steps, auto-generates tickets.

4. **Vulnerability Management Platform** — Ingests scan results from multiple tools, prioritizes by business context (RAG on asset inventory), generates remediation guidance, tracks SLA compliance.

5. **Your Own Idea** — The best capstone is the one that solves a problem that annoys you at work every day.

---

### Session 68: Architecture Design Document

**Skill:** Design before you build. Create a proper architecture document that you'd present to a team.

**Build:** Create `capstone/ARCHITECTURE.md`:
- **Problem statement** — what pain point does this solve? Who's the user?
- **Architecture diagram** — components, data flow, integration points (Mermaid diagram)
- **Component inventory:**
  - Models: which models, local vs. cloud, routing strategy
  - Data: what gets ingested, how it's chunked, where it's stored
  - Agents: what agents, what tools, what guardrails
  - Security: threat model for your specific application
  - Evaluation: how you'll measure if it's working
- **Tech stack** — exact libraries, versions, why each was chosen
- **Milestone plan** — what you'll build in Sessions 69–72

| Component | Task |
|-----------|------|
| Build | `capstone/ARCHITECTURE.md` |
| Key | Thoughtful design, not just code |

---

### Session 69: Core Pipeline

**Skill:** Build the data ingestion and core AI pipeline first. Get the foundation working before adding features.

**Build:** Depends on your project, but generally:
- Data ingestion: load your domain data → chunk → embed → store
- Core LLM pipeline: system prompt + RAG retrieval + model call
- Basic CLI interface to test the pipeline
- Verify: send 10 representative queries, confirm reasonable outputs

| Component | Task |
|-----------|------|
| Build | `capstone/src/` — core pipeline |
| Test | 10 representative queries with reasonable outputs |

---

### Session 70: Agent Layer + Tools

**Skill:** Add the intelligent automation layer that makes your capstone more than a chatbot.

**Build:**
- Define agent(s) with specific roles
- Build domain-specific tools (API calls, file operations, calculations)
- Wire up: user request → agent → tools → RAG → response
- Human-in-the-loop for high-risk operations
- Error handling: what happens when a tool fails?

| Component | Task |
|-----------|------|
| Build | `capstone/src/agents/` — agent layer + tools |
| Test | End-to-end agent flow with tool calls |

---

### Session 71: Security, Guardrails, and Evaluation

**Skill:** Harden your capstone with the security patterns you learned and build proper evaluation.

**Build:**
- Input/output guardrails tuned for your domain
- Audit logging for every interaction
- Evaluation suite: 30+ golden test cases specific to your project
- Run eval: measure accuracy, safety, latency
- Fix the worst failures

| Component | Task |
|-----------|------|
| Build | `capstone/src/security/` + `capstone/tests/` |
| Test | Pass rate on golden test suite |

---

### ⏰ Project 19: Mid-Capstone Review

Demo your capstone in its current state:
1. Architecture walkthrough
2. Live demo of core pipeline
3. Show 3 things working, 2 things that need improvement
4. Get feedback from a peer/friend/AI code reviewer

→ `capstone/PROGRESS.md`

---

[← Block 17: Platform Build](../../07-production/17-platform-build/index.md) | [Block 19: Ship & Present →](../19-ship-and-present/index.md)
