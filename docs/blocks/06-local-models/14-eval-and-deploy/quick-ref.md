# ⚡ Block 14 Quick Reference — Eval & Deploy

## Sessions at a Glance

| # | Session | You Build | Key Tools |
|---|---------|-----------|-----------|
| 52 | Build an Evaluation Framework | `eval/framework.py` | Embeddings, LLM-as-judge |
| 53 | Model Serving with vLLM | `serve/run_server.py` | vLLM, OpenAI-compatible API |
| 54 | Docker Packaging | `serve/Dockerfile` + `docker-compose.yml` | Docker, multi-stage builds |
| 55 | CI/CD for AI | `.github/workflows/eval.yml` | GitHub Actions, eval regression |
| P15 | Full Deploy Demo | `reports/deploy-service.md` | End-to-end walkthrough |

## Setup Commands

```bash
# vLLM (requires NVIDIA GPU)
pip install vllm

# Alternative: llama.cpp server (CPU-friendly)
# Already installed via Ollama — use `ollama serve`

# Docker
brew install docker docker-compose

# Evaluation tools
pip install rouge-score nltk scikit-learn
```

## Key Files

```
eval/
├── framework.py          # Evaluation harness
├── golden_tests.jsonl     # Test cases with expected outputs
├── ci_runner.py           # CI-compatible eval runner
└── baseline.json          # Passing scores threshold

serve/
├── run_server.py          # vLLM/llama.cpp server wrapper
├── Dockerfile             # Container definition
├── docker-compose.yml     # Full stack: model + RAG + DB
└── README.md              # Build & run instructions

.github/workflows/
└── eval.yml               # CI pipeline
```
