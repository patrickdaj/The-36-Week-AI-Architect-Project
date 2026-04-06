# 🏠 Block 17: Platform Build (Lab)

[← Block 16: Security & Guardrails](../16-security-and-guardrails/index.md) | [Block 18: Design & Build →](../../08-capstone/18-design-and-build/index.md)

> *"This is the lab where everything you've built plugs together into one platform. Router, cache, guardrails, agents, RAG — one unified system."*

**Quick Reference:** [→ Block 17 Quick Ref](quick-ref.md)

---

## Before You Start Block 17

- Review your work from Blocks 27–30 — you're assembling those pieces
- 📖 [The Twelve-Factor App](https://12factor.net/) — production app principles
- 📖 [FastAPI — Beyond the Basics](https://fastapi.tiangolo.com/tutorial/) — middleware, dependencies, testing

---

### Session 64: Unified Platform Assembly

**Skill:** Take your gateway, router, cache, guardrails, and agent systems and wire them into a single cohesive platform.

**Build:** Create `platform/app.py` — the unified entry point:
- FastAPI application combining:
  - Model router (Session 56)
  - Semantic cache (Session 57)
  - Streaming gateway (Session 58)
  - Input/output guardrails (Session 61)
  - Audit logging (Session 62)
- Request lifecycle:
  1. Authenticate → 2. Log request → 3. Input guardrails → 4. Cache check → 5. Route to model → 6. Output guardrails → 7. Log response → 8. Return
- Configuration via YAML: models, routing rules, guardrail settings, cache TTL
- Clean separation: each component is a middleware or dependency injection

| Component | Task |
|-----------|------|
| Build | `platform/app.py` — unified platform entry point |
| Key | Middleware chain, dependency injection, config-driven |

---

### Session 65: Agent Integration Layer

**Skill:** Your platform serves chat completions. Now add agent capabilities — tools, RAG, multi-step reasoning — accessible via API.

**Build:** Create `platform/agents.py`:
- API endpoint: `/v1/agents/{agent_id}/run`
- Register agents: SOC Analyst (from Block 18-19), CVE Analyzer (from Block 7), Audit Swarm (from Block 11)
- Each agent gets: its own system prompt, tool set, guardrails, model routing preferences
- Async execution with status polling: start agent run → poll for completion
- Include your RAG pipeline as a tool available to all agents

| Component | Task |
|-----------|------|
| Build | `platform/agents.py` — agent API layer |
| Key | Agent registry, async execution, per-agent config |

---

### Session 66: Docker Compose Full Stack

**Skill:** Package the entire platform into a Docker Compose stack that anyone can run with one command.

**Build:** Update `docker-compose.yml`:
- Projects:
  - `gateway` — your FastAPI platform (session 64-65)
  - `chromadb` — vector database for RAG + cache
  - `ollama` — local model serving
  - `dashboard` — Gradio monitoring UI (session 59)
- Shared volumes for: logs, model weights, vector data
- Environment-based config: `.env` file for API keys, model selection
- Health checks: each service reports readiness
- `Makefile` with common commands: `make up`, `make down`, `make logs`, `make test`

| Component | Task |
|-----------|------|
| Build | `docker-compose.yml`, `Makefile` |
| Test | `make up` → entire platform running |

---

### Session 67: Integration Testing

**Skill:** Write tests that verify your platform works end-to-end, not just unit tests for individual components.

**Build:** Create `tests/integration/`:
- `test_chat.py` — send chat request, verify response, check audit log
- `test_cache.py` — send same request twice, verify cache hit
- `test_guardrails.py` — send injection attempts, verify blocked
- `test_agents.py` — trigger agent run, verify tool calls, verify output
- `test_fallback.py` — kill primary model, verify fallback works
- All tests run against Docker Compose stack
- `make test` runs the full suite

| Component | Task |
|-----------|------|
| Build | `tests/integration/` — 5 test files |
| Key | End-to-end tests against running platform |

---

### ⏰ Project 18: Platform Demo

This is the Unit 7 capstone moment. Demo the full platform:
1. Start with `make up` — everything launches
2. Show the dashboard — all services green
3. Send a simple query → routed to local model, cached
4. Send a security analysis request → routed to top-tier model
5. Attempt prompt injection → blocked by guardrails
6. Trigger SOC Analyst agent → watch tool calls in logs
7. Show audit trail for the entire demo session

→ `reports/platform-service.md`

---

[← Block 16: Security & Guardrails](../16-security-and-guardrails/index.md) | [Block 18: Design & Build →](../../08-capstone/18-design-and-build/index.md)
