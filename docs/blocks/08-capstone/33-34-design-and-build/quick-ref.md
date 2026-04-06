# ⚡ Block 33–34 Quick Reference — Design & Build (Capstone)

## Sessions at a Glance

| # | Session | You Build | Key Tools |
|---|---------|-----------|-----------|
| 68 | Architecture Design Document | `capstone/ARCHITECTURE.md` | Mermaid, design thinking |
| 69 | Core Pipeline | `capstone/src/` — data + LLM pipeline | RAG, embeddings, CLI |
| 70 | Agent Layer + Tools | `capstone/src/agents/` | Agents, tools, HITL |
| 71 | Security, Guardrails, Eval | `capstone/src/security/` + `capstone/tests/` | Guardrails, eval suite |
| S19 | Mid-Capstone Review | `capstone/PROGRESS.md` | Live demo + feedback |

## Capstone Structure

```
capstone/
├── ARCHITECTURE.md         # Design document
├── PROGRESS.md             # Status tracking
├── README.md               # Project overview + setup
├── src/
│   ├── main.py             # Entry point
│   ├── pipeline.py         # Core LLM + RAG pipeline
│   ├── ingest.py           # Data ingestion
│   ├── agents/
│   │   ├── orchestrator.py
│   │   └── tools/
│   └── security/
│       ├── guardrails.py
│       └── audit.py
├── tests/
│   ├── golden_tests.jsonl  # 30+ evaluation cases
│   └── test_pipeline.py
├── data/                   # Domain data for RAG
├── Dockerfile
├── docker-compose.yml
└── Makefile
```

## Decision Checklist

Before building, answer:
- [ ] What problem does this solve? (1 sentence)
- [ ] Who uses it? (specific role)
- [ ] What 3 capabilities does it combine?
- [ ] Local models, cloud models, or hybrid?
- [ ] What data does it need?
- [ ] What's the minimum viable demo?
