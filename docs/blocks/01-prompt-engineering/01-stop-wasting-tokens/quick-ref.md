# ⚡ Block 1 Quick Reference — Stop Wasting Tokens

← [Back to Full Guide](index.md)

---

## Block 1 — Sessions 1–4

| Session | Build | Skill | Key Resource |
|---------|-------|-------|-------------|
| **Session 1** | `system-prompts/network-troubleshooter.md` | System prompts | [Anthropic — System Prompts](https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/system-prompts) |
| **Session 2** | `system-prompts/security-advisory-writer.md` | Few-shot prompting | [Prompting Guide — Few-Shot](https://www.promptingguide.ai/techniques/fewshot) |
| **Session 3** | `system-prompts/incident-analyzer.md` | Chain-of-thought | [Prompting Guide — CoT](https://www.promptingguide.ai/techniques/cot) |
| **Session 4** | `tools/token-counter.py` | Token counting & cost estimation | [OpenAI Tokenizer](https://platform.openai.com/tokenizer) |
| **Service 1** | `reports/prompt-audit-week-1.md` | Audit your real workflow | — |

---

## Block 2 — Sessions 5–8

| Session | Build | Skill | Key Resource |
|---------|-------|-------|-------------|
| **Session 5** | `tools/config-reviewer.py` | Structured output (JSON mode) | [OpenAI — Structured Outputs](https://platform.openai.com/docs/guides/structured-outputs) |
| **Session 6** | `tools/prompt-ab-tester.py` | Temperature, top-p, generation params | [Prompting Guide — Settings](https://www.promptingguide.ai/introduction/settings) |
| **Session 7** | `prompt-library/` (6 templates + renderer) | Prompt templates & variables | [LangChain — Prompt Templates](https://python.langchain.com/docs/concepts/prompt_templates/) |
| **Session 8** | `tools/injection-tester.py` | Prompt injection & defense | [OWASP — Prompt Injection](https://genai.owasp.org/llmrisk/llm01-prompt-injection/) |
| **Service 2** | Ship prompt library to GitHub | Package & document | — |

---

## Setup Checklist

```bash
# Create build repo (do this once for the whole curriculum)
mkdir -p ~/Development/ai-architect-builds/phase-0-prompts
cd ~/Development/ai-architect-builds
git init
python -m venv .venv
source .venv/bin/activate
pip install jupyter tiktoken
```

---

## Accounts Needed This Block

- None required — all tools run locally
- Optional: ChatGPT, Claude, or Gemini for testing prompts (free tiers)

---

## Files You'll Create

```
ai-architect-builds/phase-0-prompts/
├── system-prompts/
│   ├── network-troubleshooter.md
│   ├── security-advisory-writer.md
│   └── incident-analyzer.md
├── prompt-library/
│   ├── templates/
│   │   ├── incident-response.md
│   │   ├── config-review.md
│   │   ├── change-review.md
│   │   ├── vulnerability-assess.md
│   │   ├── runbook-generator.md
│   │   └── postmortem-writer.md
│   ├── render.py
│   └── README.md
├── tools/
│   ├── token-counter.py
│   ├── config-reviewer.py
│   ├── prompt-ab-tester.py
│   └── injection-tester.py
└── reports/
    └── prompt-audit-week-1.md
```
