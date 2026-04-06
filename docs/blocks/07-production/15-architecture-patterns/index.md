# 🏠 Block 15: Architecture Patterns

[← Block 14: Eval & Deploy](../../06-local-models/14-eval-and-deploy/index.md) | [Block 16: Security & Guardrails →](../16-security-and-guardrails/index.md)

> *"The difference between a demo and a product is architecture. Demos call one API. Products have routing, caching, fallbacks, and observability."*

**Quick Reference:** [→ Block 15 Quick Ref](quick-ref.md)

---

## Before You Start Block 15

30 minutes of reading + an optional course:

- 📖 [Chip Huyen — Building LLM Applications for Production](https://huyenchip.com/2023/04/11/llm-engineering.html) — 15-minute read, covers every pattern you'll implement this block (routing, caching, guardrails). Read this one fully.
- 📖 [LiteLLM — Getting Started](https://docs.litellm.ai/docs/) — 5-minute skim, one interface for 100+ model providers. You'll use this for the router.
- 📺 [DeepLearning.AI — Building Generative AI Applications with Gradio](https://www.deeplearning.ai/short-courses/building-generative-ai-applications-with-gradio/) — free, ~1 hour, optional — useful if you want a UI for your builds

---

### Session 56: Model Router

**Skill:** Route requests to the best model based on task complexity, cost, and latency requirements. This is the core of enterprise AI architecture.

**Build:** Create `platform/router.py`:
- Classification layer: analyze incoming request → simple / medium / complex
- Routing rules:
  - Simple (formatting, extraction) → local small model or cheapest API
  - Medium (analysis, Q&A) → mid-tier model (GPT-4o-mini, Claude Haiku)
  - Complex (multi-step reasoning, security analysis) → top-tier model
- LiteLLM integration: single interface for all providers
- Fallback chain: if primary fails, cascade to secondary → tertiary
- Request logging: model used, latency, tokens, cost estimate

| Component | Task |
|-----------|------|
| Build | `platform/router.py` — intelligent model routing |
| Key | Classification, routing rules, fallback chain |

> 📖 **Read:** [LiteLLM — Router](https://docs.litellm.ai/docs/routing) — production routing

---

### Session 57: Semantic Caching

**Skill:** If someone already asked a similar question, serve the cached answer. Cuts cost and latency dramatically.

**Build:** Create `platform/cache.py`:
- Embed incoming queries
- Compare against cache via cosine similarity (threshold: 0.95+)
- Cache hit: return stored response (with cache indicator)
- Cache miss: route to model, store response + embedding
- TTL: expire cache entries after configurable period
- Metrics: hit rate, average latency saved, cost saved

| Component | Task |
|-----------|------|
| Build | `platform/cache.py` — semantic similarity cache |
| Key | Embedding-based matching, TTL, hit rate metrics |

---

### Session 58: Streaming Gateway with FastAPI

**Skill:** Build an API gateway that ties together routing, caching, auth, and streaming — the foundation of your AI platform.

**Build:** Create `platform/gateway.py`:
- FastAPI application with:
  - `/v1/chat/completions` — OpenAI-compatible streaming endpoint
  - `/v1/models` — list available models and their capabilities
  - `/health` — health check for all downstream providers
  - `/metrics` — request counts, latencies, costs, cache stats
- Middleware pipeline: auth → rate limit → cache check → route → stream
- API key authentication (simple bearer token for now)
- Request/response logging with correlation IDs
- Server-Sent Events (SSE) streaming

| Component | Task |
|-----------|------|
| Build | `platform/gateway.py` — FastAPI AI gateway |
| Key | Streaming, middleware pipeline, structured logging |

> 📖 **Read:** [FastAPI — Streaming](https://fastapi.tiangolo.com/advanced/custom-response/#streamingresponse)

---

### Session 59: Observability Dashboard

**Skill:** You can't manage what you can't see. Build a dashboard that shows what your AI platform is doing in real-time.

**Build:** Create `platform/dashboard.py`:
- Gradio web UI (zero JavaScript needed)
- Panels:
  - Request timeline: recent requests with model, latency, tokens
  - Cost tracker: daily/weekly/monthly cost per model
  - Cache performance: hit rate over time
  - Error rates: failures by provider, by error type
  - Model comparison: same query across models (debug view)
- Data source: read from the request logs your gateway writes
- Auto-refresh every 30 seconds

| Component | Task |
|-----------|------|
| Build | `platform/dashboard.py` — Gradio monitoring UI |
| Key | Real-time metrics, cost tracking, model comparison |

> 📖 **Read:** [Gradio — Getting Started](https://www.gradio.app/guides/quickstart)

---

### ⏰ Project 16: Architecture Review

Demo your platform handling 3 different scenarios:
1. Simple query → routed to local model, cached
2. Complex security analysis → routed to top-tier model
3. Repeat similar query → served from cache

Walk through the dashboard showing routing decisions, cost, and cache hits.

→ `reports/architecture-service.md`

---

[← Block 14: Eval & Deploy](../../06-local-models/14-eval-and-deploy/index.md) | [Block 16: Security & Guardrails →](../16-security-and-guardrails/index.md)
