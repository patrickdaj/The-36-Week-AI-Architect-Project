# 🏗️ Unit 7 — Production Architecture

<small>Weeks 27–32 · 3 blocks</small>

[→ Start Block 27–28](27-28-architecture-patterns/index.md)

---

This is where your 25 years of infrastructure experience becomes a superpower.

Most AI tutorials stop at "it works on my laptop." This unit is about everything that comes after: architecture patterns, security guardrails, observability, cost management, model routing, and the governance frameworks that make AI deployable in an enterprise. You've deployed production services for decades — AI serving is just another service with some new failure modes.

The OWASP Top 10 for LLM Applications will feel like coming home. Prompt injection is injection. Data exfiltration is data exfiltration. Insecure output handling is insecure output handling. The attack surface is new, but the security thinking is yours.

---

## What You'll Build

- A **production AI platform** combining your RAG, agents, and local models into a unified FastAPI service
- An **AI gateway/proxy** with model routing, failover, cost tracking, and audit logging
- **Security guardrails** — prompt injection detection, output sanitization, RBAC
- **Architecture Decision Records (ADRs)** for every major design choice
- A **threat model** for AI systems — your unique contribution

---

## Blocks

| Block | Topic | Weeks |
|-------|-------|-------|
| [27–28: Architecture Patterns](27-28-architecture-patterns/index.md) | LLM app patterns, model routing, caching, observability | 27–28 |
| [29–30: Security & Guardrails](29-30-security-and-guardrails/index.md) | OWASP LLM Top 10, prompt injection defense, AI governance | 29–30 |
| [31–32: Platform Build](31-32-platform-build/index.md) | 🔬 Lab — unified platform, AI gateway, Docker deployment | 31–32 |
