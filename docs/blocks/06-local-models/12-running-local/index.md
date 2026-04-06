# 🏠 Block 12: Running Local

[← Block 11: Audit Swarm](../../05-agents/11-audit-swarm/index.md) | [Block 7: Fine-Tuning →](../13-fine-tuning/index.md)

> *"The moment you run a model on your own hardware, AI stops being a service and becomes infrastructure you control."*

**Quick Reference:** [→ Block 12 Quick Ref](quick-ref.md)

---

## Before You Start Block 12

- 📺 [Andrej Karpathy — Intro to Large Language Models](https://www.youtube.com/watch?v=zjkBMFhNj_g) — 1 hour, the best overview of what LLMs are
- 📺 [Andrej Karpathy — Let's build GPT from scratch](https://www.youtube.com/watch?v=kCc8FmEb1nY) — 2 hours, builds a transformer in Python. Watch it. You don't need to code along, but the intuition is invaluable.
- 📖 [Ollama Documentation](https://github.com/ollama/ollama/blob/main/README.md)

**Setup:**
```bash
# Install Ollama
curl -fsSL https://ollama.com/install.sh | sh
# Or on macOS: brew install ollama

# Pull your first models
ollama pull llama3.1:8b
ollama pull mistral
ollama pull phi3
```

---

### Session 44: Your First Local Model

**Skill:** Run LLMs on your own machine. Understand model sizes, quantization, and the tradeoffs of local vs. cloud.

**Build:** Create `01-local-chat.py`:
- Connect to Ollama's local API (OpenAI-compatible)
- Interactive chat with your local model
- Display: model name, tokens/second, memory usage
- Test: run the same prompt on llama3.1:8b, mistral, and phi3 — compare responses

| Component | Task |
|-----------|------|
| Build | `01-local-chat.py` — local model chat interface |
| Key | Ollama API, model switching, performance metrics |

> 📖 **Read:** [Ollama API Reference](https://github.com/ollama/ollama/blob/main/docs/api.md)

---

### Session 45: Benchmarking on Your Security Tasks

**Skill:** Systematically compare model quality on YOUR tasks. Generic benchmarks don't tell you which model is best for your domain.

**Build:** Create `02-benchmark.py`:
- Define 20 security-specific test prompts with expected outputs:
  - Config review accuracy
  - Incident analysis quality
  - CVE summary accuracy
  - Network troubleshooting advice
- Run each test across 3+ models
- Score: correctness (0-5), relevance, hallucination rate, response time
- Generate benchmark report with rankings

| Component | Task |
|-----------|------|
| Build | `02-benchmark.py` — security-focused model benchmark suite |
| Output | Benchmark report: which model wins for which tasks |

---

### Session 46: Swap Your Cloud Tools to Local

**Skill:** Make your Phase 2–5 tools work with local models. Measure the quality delta.

**Build:** Update your provider abstraction (Session 16) to support Ollama:
- Add `providers/ollama_provider.py`
- Run your network troubleshooter, advisory summarizer, and RAG system on local models
- Compare: quality delta vs. GPT-4/Claude, token speed, cost savings ($0 vs. $X)
- Document: which tools work fine locally, which need cloud models

| Component | Task |
|-----------|------|
| Build | `providers/ollama_provider.py` + integration tests |
| Report | Local vs. cloud quality comparison |

---

### Session 47: Model File Customization

**Skill:** Create custom Ollama modelfiles — set system prompts, parameters, and behavior at the model level.

**Build:** Create custom modelfiles for your tools:
```
# security-analyst.modelfile
FROM llama3.1:8b
SYSTEM "You are a senior security analyst..."
PARAMETER temperature 0
PARAMETER num_ctx 8192
```

Create 3+ modelfiles optimized for different tasks. Register them with Ollama.

| Component | Task |
|-----------|------|
| Build | 3+ custom Ollama modelfiles |
| Test | Compare custom vs. base model on target tasks |

---

### ⏰ Project 13: The Cloud-Free Challenge

Spend one full work session using ONLY local models (no ChatGPT, Claude, or Copilot cloud features):
1. Use your local tools for every AI task
2. Document: What worked? What was painfully slow? What was impossible locally?
3. Write your analysis

→ `reports/local-models-service.md`

---

[← Block 11: Audit Swarm](../../05-agents/11-audit-swarm/index.md) | [Block 7: Fine-Tuning →](../13-fine-tuning/index.md)
