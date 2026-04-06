# ⚡ Block 12 Quick Reference — Running Local

← [Back to Full Guide](index.md)

---

| Session | Build | Skill | Key Resource |
|---------|-------|-------|-------------|
| **Session 44** | `01-local-chat.py` | Ollama local chat | [Ollama Docs](https://github.com/ollama/ollama/blob/main/README.md) |
| **Session 45** | `02-benchmark.py` | Security-focused benchmarking | — |
| **Session 46** | `providers/ollama_provider.py` | Cloud → local swap | — |
| **Session 47** | 3 custom modelfiles | Model customization | — |
| **Service 13** | `reports/local-models-service.md` | Cloud-free challenge | — |

## Setup
```bash
brew install ollama   # or curl install
ollama pull llama3.1:8b && ollama pull mistral && ollama pull phi3
```
