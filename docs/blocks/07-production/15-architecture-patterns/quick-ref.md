# ⚡ Block 15 Quick Reference — Architecture Patterns

## Sessions at a Glance

| # | Session | You Build | Key Tools |
|---|---------|-----------|-----------|
| 56 | Model Router | `platform/router.py` | LiteLLM, classification |
| 57 | Semantic Caching | `platform/cache.py` | Embeddings, cosine similarity |
| 58 | Streaming Gateway | `platform/gateway.py` | FastAPI, SSE, middleware |
| 59 | Observability Dashboard | `platform/dashboard.py` | Gradio, metrics visualization |
| P16 | Architecture Review | `reports/architecture-service.md` | Live demo + walkthrough |

## Setup Commands

```bash
pip install litellm fastapi uvicorn gradio
pip install chromadb  # reuse for semantic cache embeddings
```

## Key Files

```
platform/
├── router.py              # Model routing + fallback
├── cache.py               # Semantic similarity cache
├── gateway.py             # FastAPI AI gateway
├── dashboard.py           # Gradio observability UI
├── config.yaml            # Model configs, routing rules
└── logs/                  # Request/response logs

reports/
└── architecture-service.md
```
