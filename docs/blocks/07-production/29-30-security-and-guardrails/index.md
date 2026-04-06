# 🏠 Block 29–30: Security & Guardrails

[← Block 27–28: Architecture Patterns](../27-28-architecture-patterns/index.md) | [Block 31–32: Platform Build →](../31-32-platform-build/index.md)

> *"You already know how attackers think. Now apply that to the one system where the attack surface is a text box."*

**Quick Reference:** [→ Block 29–30 Quick Ref](quick-ref.md)

---

## Before You Start Block 29

- 📖 [OWASP Top 10 for LLM Applications](https://owasp.org/www-project-top-10-for-large-language-model-applications/) — the definitive list
- 📺 [Simon Willison — Prompt Injection Explained](https://simonwillison.net/2023/Apr/14/worst-that-can-happen/) — blog + talks
- 📖 [NIST AI Risk Management Framework](https://www.nist.gov/artificial-intelligence/executive-order-safe-secure-and-trustworthy-artificial-intelligence) — governance reference

---

### Session 60: Prompt Injection Defense

**Skill:** You built prompt injection attacks in Session 8. Now build the defenses. This is your security background paying off.

**Build:** Create `security/injection_defense.py`:
- Input sanitization: detect and neutralize injection patterns
- Techniques:
  - **Delimiter isolation** — wrap user input in clear delimiters the model respects
  - **Instruction hierarchy** — system prompt reinforcement
  - **Input classification** — pre-screen inputs with a fast model (is this an attack?)
  - **Output validation** — does the response violate expected boundaries?
- Red team test suite: 50+ injection attempts from your Session 8 work
- Defense scorecard: which techniques block which attacks?

| Component | Task |
|-----------|------|
| Build | `security/injection_defense.py` — multi-layer defense |
| Test | Red team suite: 50+ attacks, measure block rate |

> 📖 **Read:** [Rebuff — Prompt Injection Detection](https://github.com/protectai/rebuff) — reference implementation

---

### Session 61: Content Guardrails

**Skill:** Control what goes in and what comes out. PII detection, topic boundaries, hallucination detection.

**Build:** Create `security/guardrails.py`:
- **Input guardrails:**
  - PII detection: regex + NER for emails, SSNs, API keys, IPs
  - Topic boundaries: reject off-topic requests (with explanation)
  - Rate limiting per user/session
- **Output guardrails:**
  - PII scrubbing: catch any PII that leaks into responses
  - Hallucination detection: check claims against retrieved sources
  - Toxicity filter: basic content safety check
  - Confidence gating: if model uncertainty is high, flag for human review
- Integrate with your gateway middleware pipeline from Session 58

| Component | Task |
|-----------|------|
| Build | `security/guardrails.py` — input/output guardrails |
| Key | PII detection, hallucination checks, confidence gating |

> 📖 **Read:** [Guardrails AI](https://www.guardrailsai.com/docs) — framework reference
>
> 📖 **Read:** [NeMo Guardrails](https://github.com/NVIDIA/NeMo-Guardrails) — NVIDIA's approach

---

### Session 62: AI Governance & Audit Logging

**Skill:** Enterprise AI needs audit trails. Who asked what, which model answered, what guardrails fired, and what data was accessed.

**Build:** Create `security/audit.py`:
- Structured audit log for every AI interaction:
  - Timestamp, user ID, session ID
  - Input (with PII redacted), output (with PII redacted)
  - Model used, tokens consumed, cost
  - Guardrails triggered (which ones, pass/fail)
  - Data sources accessed (RAG chunks retrieved)
  - Response time, cache hit/miss
- Log storage: append-only JSON lines (tamper-evident)
- Search/filter: query logs by user, time range, guardrail triggers
- Compliance report generator: summarize AI usage for a time period

| Component | Task |
|-----------|------|
| Build | `security/audit.py` — governance audit system |
| Key | Structured logging, PII redaction, compliance reports |

---

### Session 63: Threat Model Your AI Platform

**Skill:** Apply your security engineering skills to create a formal threat model for your entire AI platform.

**Build:** Create `security/threat-model.md`:
- STRIDE analysis for your AI gateway:
  - **Spoofing** — API key theft, model impersonation
  - **Tampering** — prompt injection, training data poisoning
  - **Repudiation** — user denies actions (your audit log handles this)
  - **Information Disclosure** — PII leaks, model extraction, RAG data exposure
  - **Denial of Service** — token exhaustion, model overload
  - **Elevation of Privilege** — jailbreaking, bypassing guardrails
- For each threat: likelihood, impact, existing controls, gaps, mitigations
- Create `security/security_tests.py`: automated security regression tests

| Component | Task |
|-----------|------|
| Build | `security/threat-model.md` + `security/security_tests.py` |
| Key | STRIDE analysis, automated security testing |

---

### ⏰ Service 17: Security Audit Presentation

Present your AI platform security posture:
1. Live demo: attempt 5 prompt injection attacks → show defenses catching them
2. Show PII detection in action (use synthetic data)
3. Walk through audit logs for a session
4. Present threat model and remaining gaps

→ `reports/security-service.md`

---

[← Block 27–28: Architecture Patterns](../27-28-architecture-patterns/index.md) | [Block 31–32: Platform Build →](../31-32-platform-build/index.md)
