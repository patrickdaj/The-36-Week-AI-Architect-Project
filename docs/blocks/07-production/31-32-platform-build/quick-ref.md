# ⚡ Block 31–32 Quick Reference — Platform Build

## Sessions at a Glance

| # | Session | You Build | Key Tools |
|---|---------|-----------|-----------|
| 64 | Unified Platform Assembly | `platform/app.py` | FastAPI, middleware chain |
| 65 | Agent Integration Layer | `platform/agents.py` | Agent registry, async API |
| 66 | Docker Compose Full Stack | `docker-compose.yml`, `Makefile` | Docker Compose, health checks |
| 67 | Integration Testing | `tests/integration/` (5 files) | pytest, end-to-end tests |
| S18 | Platform Demo | `reports/platform-service.md` | Full stack demo |

## Setup Commands

```bash
# Everything should already be installed from previous blocks
# Verify Docker is running:
docker compose version

# New dependencies for testing:
pip install pytest httpx pytest-asyncio
```

## Key Files

```
platform/
├── app.py                 # Unified entry point
├── agents.py              # Agent API layer
├── router.py              # Model routing (from Block 27)
├── cache.py               # Semantic cache (from Block 27)
├── gateway.py             # Streaming gateway (from Block 27)
├── dashboard.py           # Monitoring UI (from Block 27)
└── config.yaml            # All platform configuration

security/                   # From Block 29-30

docker-compose.yml          # Full stack definition
Makefile                    # make up, make down, make test
.env                        # API keys, model selection

tests/integration/
├── test_chat.py
├── test_cache.py
├── test_guardrails.py
├── test_agents.py
└── test_fallback.py
```

## Makefile Targets

```makefile
up:      docker compose up -d
down:    docker compose down
logs:    docker compose logs -f
test:    pytest tests/integration/ -v
build:   docker compose build --no-cache
```
