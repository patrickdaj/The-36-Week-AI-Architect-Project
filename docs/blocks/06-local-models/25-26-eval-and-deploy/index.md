# 🏠 Block 25–26: Eval & Deploy

[← Block 23–24: Fine-Tuning](../23-24-fine-tuning/index.md) | [Block 27–28: Architecture Patterns →](../../07-production/27-28-architecture-patterns/index.md)

> *"If you can't measure it, you can't improve it. If you can't serve it, it doesn't exist."*

**Quick Reference:** [→ Block 25–26 Quick Ref](quick-ref.md)

---

## Before You Start Block 25

- 📺 [MLOps Zoomcamp — Model Deployment](https://github.com/DataTalksClub/mlops-zoomcamp) — free, practical
- 📖 [Hugging Face — Evaluate Library](https://huggingface.co/docs/evaluate/) — standardized evaluation
- 📖 [vLLM Documentation](https://docs.vllm.ai/) — high-throughput serving

---

### Session 52: Build an Evaluation Framework

**Skill:** Create a reusable evaluation harness that scores LLM outputs systematically instead of vibes-based "looks good."

**Build:** Create `eval/framework.py`:
- Define evaluation criteria: accuracy, relevance, completeness, format, safety
- Implement scoring methods:
  - **Exact match** — for structured output fields
  - **Semantic similarity** — embeddings cosine distance
  - **LLM-as-judge** — use a strong model to grade a weaker model's output
  - **Regex/schema validation** — for format compliance
- Test suite: 50+ golden examples with expected outputs
- Aggregate scoring: per-category and overall quality score
- Output: JSON report + human-readable summary

| Component | Task |
|-----------|------|
| Build | `eval/framework.py` — reusable evaluation harness |
| Key | Multiple scoring methods, golden test suite |

> 📖 **Read:** [Hamel Husain — Your AI Product Needs Evals](https://hamel.dev/blog/posts/evals/)
>
> 📖 **Read:** [OpenAI — Evals](https://github.com/openai/evals) — reference implementation

---

### Session 53: Model Serving with vLLM

**Skill:** Serve a local model behind an OpenAI-compatible API — the bridge between "running on my laptop" and "running in production."

**Build:** Create `serve/run_server.py` + configuration:
- Serve a model via vLLM (or llama.cpp server as fallback)
- OpenAI-compatible API: `/v1/chat/completions`, `/v1/completions`
- Configuration: max tokens, temperature, concurrent requests
- Test with your existing tools — swap the API endpoint, everything else works
- Load test: measure requests/second, latency p50/p95/p99

| Component | Task |
|-----------|------|
| Build | `serve/run_server.py` — model server with OpenAI-compatible API |
| Test | Swap your RAG or agent tool to hit local server |

> 📖 **Read:** [vLLM — Quick Start](https://docs.vllm.ai/en/latest/getting_started/quickstart.html)

---

### Session 54: Docker Packaging

**Skill:** Package your model + server into a Docker container. The model works on your machine; make it work on any machine.

**Build:** Create `serve/Dockerfile` + `docker-compose.yml`:
- Multi-stage build: base image + model weights + server
- Include: model, config, evaluation suite
- Environment variables for: model path, GPU layers, port, max workers
- Health check endpoint
- Docker Compose: model server + your RAG app + ChromaDB as a full stack
- Document: `serve/README.md` with build & run instructions

| Component | Task |
|-----------|------|
| Build | `serve/Dockerfile`, `docker-compose.yml` |
| Test | `docker compose up` — full stack running in containers |

---

### Session 55: CI/CD for AI — Eval on Every Push

**Skill:** Run your evaluation suite automatically when code changes. Catch regressions before they reach production.

**Build:** Create `.github/workflows/eval.yml`:
- Trigger: on push to `main`, on PR
- Steps: install deps → load test data → run eval suite → compare to baseline
- Pass/fail threshold: if accuracy drops below baseline, fail the build
- Artifact: evaluation report uploaded as build artifact
- Bonus: use a smaller/faster model for CI (Phi-3-mini) so it runs on CPU

| Component | Task |
|-----------|------|
| Build | `.github/workflows/eval.yml` + `eval/ci_runner.py` |
| Key | Automated eval, regression detection, baseline comparison |

---

### ⏰ Service 15: Full Deploy Demo

Deploy your complete stack and demonstrate:
1. User sends request to your API
2. API routes to local model (or cloud fallback)
3. RAG retrieves context from ChromaDB
4. Model generates response
5. Eval framework scores the response
6. All running in Docker containers

Record a 3-minute walkthrough → `reports/deploy-service.md`

---

[← Block 23–24: Fine-Tuning](../23-24-fine-tuning/index.md) | [Block 27–28: Architecture Patterns →](../../07-production/27-28-architecture-patterns/index.md)
