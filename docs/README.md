# The 36-Week AI Architect Project

**AI bootcamps cost $15,000 and teach you to copy tutorials. This costs nothing and teaches you to build.**

---

You already use AI. You prompt Copilot most days, actually. You're not bad at it. But you've hit the ceiling where blasting prompts gets you — you can get output, but you can't architect systems, you can't debug why the agent looped, and you can't explain to your CTO *why* RAG is the right pattern for that compliance problem. You just know it sounds right.

A bootcamp would fix some of that. It would also cost you five figures, require you to sit through lectures aimed at people who've never seen a terminal, and teach you to build toy demos that would never survive production.

This is the other option.

**36 weeks. 19 blocks. Every session builds something real.** You learn one professional AI skill per session, build a tool that uses it in your security/networking domain, study the resource that explains *why* it works, then compare your approach to how the pros do it. Skills compound. By the end you're not prompting — you're architecting.

---

## What a Tuesday Night Looks Like

You write a structured system prompt for a network troubleshooter CLI. You call the Gemini API with streaming, parse the response, and handle the error when your token count blows past the free tier. You read Anthropic's prompt engineering guide on why your few-shot examples aren't working, compare your approach to their cookbook, and commit your working tool. Done by 9.

That's it. That's the program. Repeat 140 times across prompt engineering, LLM APIs, RAG pipelines, agent systems, local models, fine-tuning, and production architecture.

---

## The Curriculum

### 🎯 [Unit 1 — Prompt Engineering](blocks/01-prompt-engineering/README.md) <small>Weeks 1–2</small>

Stop wasting tokens. Learn to write surgical prompts, manage context windows, and build reusable prompt templates for your daily security work.

| Block | Topic | Weeks | Guide | Quick Ref |
|-------|-------|-------|-------|-----------|
| 1 | Stop Wasting Tokens | 2 | [→](blocks/01-prompt-engineering/01-stop-wasting-tokens/index.md) | [→](blocks/01-prompt-engineering/01-stop-wasting-tokens/quick-ref.md) |

### 🐍 [Unit 2 — Python for AI](blocks/02-python-for-ai/README.md) <small>Weeks 3–4</small>

Get your Python muscle memory tuned for data and AI work. Pandas, Jupyter, and building CLI tools that process real security data.

| Block | Topic | Weeks | Guide | Quick Ref |
|-------|-------|-------|-------|-----------|
| 2 | Data & Tooling | 2 | [→](blocks/02-python-for-ai/02-data-and-tooling/index.md) | [→](blocks/02-python-for-ai/02-data-and-tooling/quick-ref.md) |

### 🔌 [Unit 3 — LLM APIs](blocks/03-llm-apis/README.md) <small>Weeks 5–8</small>

Call LLMs programmatically. Build real tools — a network troubleshooter, a CVE summarizer — not toy demos.

| Block | Topic | Weeks | Guide | Quick Ref |
|-------|-------|-------|-------|-----------|
| 3 | Your First AI Apps | 2 | [→](blocks/03-llm-apis/03-first-ai-apps/index.md) | [→](blocks/03-llm-apis/03-first-ai-apps/quick-ref.md) |
| 4 | Structured Output & Cost Control | 2 | [→](blocks/03-llm-apis/04-structured-output/index.md) | [→](blocks/03-llm-apis/04-structured-output/quick-ref.md) |

### 🧠 [Unit 4 — Embeddings & RAG](blocks/04-embeddings-and-rag/README.md) <small>Weeks 9–13</small>

Build systems that know YOUR things. Security knowledge bases, policy search, and a CVE impact analyzer that actually understands your infrastructure.

| Block | Topic | Weeks | Guide | Quick Ref |
|-------|-------|-------|-------|-----------|
| 5 | Vectors & Retrieval | 2 | [→](blocks/04-embeddings-and-rag/05-vectors-and-retrieval/index.md) | [→](blocks/04-embeddings-and-rag/05-vectors-and-retrieval/quick-ref.md) |
| 6 | Advanced RAG | 2 | [→](blocks/04-embeddings-and-rag/06-advanced-rag/index.md) | [→](blocks/04-embeddings-and-rag/06-advanced-rag/quick-ref.md) |
| 7 | 🔬 Lab: CVE Impact Analyzer | 1 | [→](blocks/04-embeddings-and-rag/07-cve-impact-analyzer/index.md) | [→](blocks/04-embeddings-and-rag/07-cve-impact-analyzer/quick-ref.md) |

### 🤖 [Unit 5 — AI Agents](blocks/05-agents/README.md) <small>Weeks 14–20</small>

Build AI that uses tools, makes decisions, and orchestrates workflows. SOC analyst agents, audit swarms, human-in-the-loop.

| Block | Topic | Weeks | Guide | Quick Ref |
|-------|-------|-------|-------|-----------|
| 8 | Tool Use & ReAct | 2 | [→](blocks/05-agents/08-tool-use-and-react/index.md) | [→](blocks/05-agents/08-tool-use-and-react/quick-ref.md) |
| 9 | Multi-Agent Systems | 2 | [→](blocks/05-agents/09-multi-agent-systems/index.md) | [→](blocks/05-agents/09-multi-agent-systems/quick-ref.md) |
| 10 | 🔬 Lab: SOC Analyst Agent | 2 | [→](blocks/05-agents/10-soc-analyst-agent/index.md) | [→](blocks/05-agents/10-soc-analyst-agent/quick-ref.md) |
| 11 | 🔬 Lab: Audit Swarm Capstone | 1 | [→](blocks/05-agents/11-audit-swarm/index.md) | [→](blocks/05-agents/11-audit-swarm/quick-ref.md) |

### 🏠 [Unit 6 — Local Models & Fine-Tuning](blocks/06-local-models/README.md) <small>Weeks 21–26</small>

Run models on your machine. Customize them for your domain. Understand what's under the hood without drowning in math.

| Block | Topic | Weeks | Guide | Quick Ref |
|-------|-------|-------|-------|-----------|
| 12 | Running Local | 2 | [→](blocks/06-local-models/12-running-local/index.md) | [→](blocks/06-local-models/12-running-local/quick-ref.md) |
| 13 | Fine-Tuning | 2 | [→](blocks/06-local-models/13-fine-tuning/index.md) | [→](blocks/06-local-models/13-fine-tuning/quick-ref.md) |
| 14 | Eval & Deploy | 2 | [→](blocks/06-local-models/14-eval-and-deploy/index.md) | [→](blocks/06-local-models/14-eval-and-deploy/quick-ref.md) |

### 🏗️ [Unit 7 — Production Architecture](blocks/07-production/README.md) <small>Weeks 27–32</small>

Think like an architect. Design AI systems for production — security, observability, cost, governance. This is where your 25 years of infrastructure experience becomes an unfair advantage.

| Block | Topic | Weeks | Guide | Quick Ref |
|-------|-------|-------|-------|-----------|
| 15 | Architecture Patterns | 2 | [→](blocks/07-production/15-architecture-patterns/index.md) | [→](blocks/07-production/15-architecture-patterns/quick-ref.md) |
| 16 | Security & Guardrails | 2 | [→](blocks/07-production/16-security-and-guardrails/index.md) | [→](blocks/07-production/16-security-and-guardrails/quick-ref.md) |
| 17 | 🔬 Lab: Platform Build | 2 | [→](blocks/07-production/17-platform-build/index.md) | [→](blocks/07-production/17-platform-build/quick-ref.md) |

### 🎓 [Unit 8 — Capstone](blocks/08-capstone/README.md) <small>Weeks 33–36</small>

Synthesize everything into an architect-level portfolio piece. Design, build, document, present.

| Block | Topic | Weeks | Guide | Quick Ref |
|-------|-------|-------|-------|-----------|
| 18 | Design & Build | 2 | [→](blocks/08-capstone/18-design-and-build/index.md) | [→](blocks/08-capstone/18-design-and-build/quick-ref.md) |
| 19 | Ship & Present | 2 | [→](blocks/08-capstone/19-ship-and-present/index.md) | [→](blocks/08-capstone/19-ship-and-present/quick-ref.md) |

---

## Start Here

1. **Read this first:** [How to Get the Most Out of This Program](how-to-use.md) — the mindset, the rhythm, and how sessions actually work
2. **Check your gear:** [Equipment Guide](equipment-guide.md) — you probably have most of it already
3. **Start building:** [Block 1: Stop Wasting Tokens](blocks/01-prompt-engineering/01-stop-wasting-tokens/index.md) — no shopping list needed, just your brain and a terminal

The pace is one block every two weeks. But life happens — each block is self-contained, so take a week off, double up, whatever. 36 weeks is the intent, not a deadline.

---

*Open source. Free forever. Built for the engineer who'd rather build an AI agent than sit through another webinar about "the future of AI."*
