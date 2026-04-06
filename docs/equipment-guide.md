# Equipment Guide

You probably have most of this already. If you don't, everything here is free or has a free tier.

---

## Your Machine

| Requirement | Minimum | Recommended |
|-------------|---------|-------------|
| **OS** | macOS, Linux, or Windows with WSL | macOS or Linux |
| **RAM** | 8 GB | 16+ GB (for running local models in Unit 6) |
| **Storage** | 20 GB free | 50+ GB (model files are large) |
| **GPU** | Not required until Unit 6 | Any NVIDIA GPU or Apple Silicon M-series chip |
| **Python** | 3.10+ | 3.11 or 3.12 |

> **Apple Silicon note:** If you're on an M1/M2/M3 Mac, you can run 7B–13B models directly in Ollama using the unified memory. No NVIDIA GPU needed. This is a genuine advantage.
>
> **No GPU at all?** Google Colab (free tier) gives you access to a T4 GPU for fine-tuning in Unit 6. You'll be fine.

---

## Software to Install Now

Install these before Block 1. Everything else gets installed per-block.

| Tool | What | Install |
|------|------|---------|
| **Python 3.11+** | Runtime | `brew install python@3.12` or [python.org](https://www.python.org/downloads/) |
| **Git** | Version control | `brew install git` or `xcode-select --install` |
| **VS Code** | Editor | [code.visualstudio.com](https://code.visualstudio.com/) |
| **GitHub Copilot** | Your AI pair programmer | [VS Code extension](https://marketplace.visualstudio.com/items?itemName=GitHub.copilot) — free for verified students/OSS, or use free tier |
| **uv** | Fast Python package manager | `curl -LsSf https://astral.sh/uv/install.sh \| sh` |
| **Jupyter** | Notebook environment | `uv pip install jupyterlab` (or use VS Code's built-in) |

---

## Accounts to Create (All Free)

Set these up before you need them. Creating accounts mid-session kills flow.

### Block 1 (Prompt Engineering)
- None needed — you're working locally

### Blocks 3–4 (LLM APIs)
- [ ] [Google AI Studio](https://aistudio.google.com/) — free Gemini API with generous limits
- [ ] [OpenAI Platform](https://platform.openai.com/) — free $5 credit for new accounts (verify current offer)
- [ ] [Anthropic Console](https://console.anthropic.com/) — free credits for new accounts (verify current offer)

### Blocks 5–7 (RAG)
- [ ] [Hugging Face](https://huggingface.co/) — free account for models and datasets
- [ ] [NVD API](https://nvd.nist.gov/developers/request-an-api-key) — free API key for CVE data

### Blocks 8–11 (Agents)
- [ ] [VirusTotal](https://www.virustotal.com/) — free API key (4 requests/min)
- [ ] [AbuseIPDB](https://www.abuseipdb.com/) — free API key (1000 checks/day)

### Blocks 12–14 (Local Models)
- [ ] [Ollama](https://ollama.com/) — installed locally, no account needed
- [ ] [Google Colab](https://colab.research.google.com/) — free tier with GPU access for fine-tuning

### Blocks 15–17 (Production)
- [ ] [Docker Desktop](https://www.docker.com/products/docker-desktop/) — free for personal use

---

## VS Code Extensions

| Extension | Why |
|-----------|-----|
| **Python** | Language support |
| **Jupyter** | Notebook support in VS Code |
| **GitHub Copilot** | AI pair programming |
| **REST Client** | Test API calls from VS Code |
| **Docker** | Container management |

---

## Install-Per-Block Tools

These get installed when you reach their respective blocks. Don't install everything now — you'll forget the setup by the time you need it.

| Block | Tool | Purpose |
|-------|------|---------|
| 3–4 | Pandas, NumPy, Matplotlib | Data analysis |
| 5–8 | google-genai, openai, anthropic | LLM API clients |
| 9–13 | chromadb, langchain | RAG pipeline |
| 14–20 | langgraph, crewai | Agent orchestration |
| 21–26 | ollama, unsloth, transformers | Local models and fine-tuning |
| 27–32 | fastapi, uvicorn, docker | Production serving |

---

## Cost Summary

| Item | Cost |
|------|------|
| Curriculum | Free |
| Python, Git, VS Code, Jupyter | Free |
| Google AI Studio (Gemini API) | Free tier |
| Ollama (local models) | Free |
| ChromaDB | Free |
| Hugging Face | Free |
| Google Colab (GPU) | Free tier |
| LangChain, LangGraph, CrewAI | Free / open source |
| Docker Desktop | Free for personal use |
| **Total** | **$0** |

> Some LLM APIs (OpenAI, Anthropic) offer limited free credits. After those run out, you can do everything with Google AI Studio's free Gemini tier and local Ollama models. The curriculum is designed to never require paid API access.
