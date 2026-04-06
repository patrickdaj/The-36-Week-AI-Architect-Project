# 🔌 Block 5–6: Your First AI Apps

[← Block 3–4: Data & Tooling](../../02-python-for-ai/03-04-data-and-tooling/index.md) | [Block 7–8: Structured Output →](../07-08-structured-output/index.md)

> *"Most AI apps are API wrappers with good prompts. That's not an insult — it's a superpower if you do it right."*

**Quick Reference:** [→ Block 5–6 Quick Ref](quick-ref.md)

---

## Before You Start Block 5

- 📺 [DeepLearning.AI — Building Systems with the ChatGPT API](https://www.deeplearning.ai/short-courses/building-systems-with-chatgpt-api/) — free, ~1 hour
- 📖 [Google AI Studio — Quickstart](https://ai.google.dev/gemini-api/docs/quickstart) — set up your free Gemini API access
- 📖 [OpenAI — API Quickstart](https://platform.openai.com/docs/quickstart) — if using OpenAI credits

**Setup:**
```bash
mkdir -p ~/Development/ai-architect-builds/phase-2-ai-apps
cd ~/Development/ai-architect-builds/phase-2-ai-apps
pip install google-genai openai anthropic httpx rich
```

**Accounts needed:** At least one of: Google AI Studio (free, recommended), OpenAI (free credits), Anthropic (free credits).

---

## Block 5 — Make the API Do Real Work

### Session 13: Your First API Call

**Skill:** Call an LLM API from Python. Handle authentication, basic request/response, and error handling.

**Build:** Create `01-first-call.py`:
- Call Google Gemini (or OpenAI) with a simple prompt
- Print the response, the token usage, and the estimated cost
- Add: retry on rate limit (429), timeout handling, API key from environment variable
- Use your network-troubleshooter system prompt from Block 1 — see it work programmatically

| Component | Task |
|-----------|------|
| Build | `01-first-call.py` — basic LLM API call with error handling |
| Key | API auth from env vars, retry logic, token counting |

> 📖 **Read:** [Google — Gemini API Reference](https://ai.google.dev/gemini-api/docs) — your primary free API
>
> 📖 **Read:** [OpenAI — API Reference](https://platform.openai.com/docs/api-reference) — the industry standard

---

### Session 14: Streaming Responses

**Skill:** Stream responses token-by-token instead of waiting for the full response. Critical for CLI tools and user-facing apps.

**Build:** Create `02-streaming.py`:
- Same troubleshooter prompt but with streaming output
- Print tokens as they arrive (like ChatGPT's typing effect)
- Collect the full response while streaming for logging
- Measure: time-to-first-token vs. time-to-completion
- Add: Rich library for pretty terminal output with spinners and markdown rendering

| Component | Task |
|-----------|------|
| Build | `02-streaming.py` — streaming response with rich terminal output |
| Key | Stream iteration, time-to-first-token, Rich formatting |

> 📖 **Read:** [Anthropic — Streaming](https://docs.anthropic.com/en/api/streaming) — how streaming works under the hood  

---

### Session 15: Conversation Memory

**Skill:** Maintain conversation context across multiple turns. Understand how messages arrays work and why context windows have limits.

**Build:** Create `03-network-troubleshooter.py` — your first real tool:
- Interactive CLI: user describes a problem, AI responds, user can follow up
- Maintains conversation history in the messages array
- Tracks cumulative token usage across turns
- Warns when approaching context window limits (80% threshold)
- Saves conversation history to a JSON file for later review
- Uses your system prompt from Block 1

| Component | Task |
|-----------|------|
| Build | `03-network-troubleshooter.py` — interactive CLI with memory |
| Key | Messages array, turn tracking, context window management |

> 📖 **Read:** [OpenAI — Chat Completions](https://platform.openai.com/docs/guides/chat-completions) — the messages format all providers use

---

### Session 16: Multi-Provider Abstraction

**Skill:** Write code that works across multiple LLM providers. Don't lock yourself into one API.

**Build:** Create `providers/` module:
```python
# providers/
# ├── __init__.py
# ├── base.py          # Abstract base class
# ├── gemini.py        # Google Gemini implementation
# ├── openai_provider.py  # OpenAI implementation
# └── anthropic_provider.py  # Anthropic implementation
#
# Interface: send(messages, model, temperature, stream) -> Response
```

Update `03-network-troubleshooter.py` to use the provider abstraction. Swap providers with a flag: `--provider gemini`.

| Component | Task |
|-----------|------|
| Build | `providers/` — multi-provider abstraction module |
| Refactor | Update troubleshooter to use providers |

> 📖 **Read:** [LiteLLM](https://docs.litellm.ai/) — how the ecosystem handles this (study the pattern, you don't need the library)

---

### ⏰ Service 4: Dog-Food Your Troubleshooter

Use your network troubleshooter CLI on a real network problem you've dealt with this week. If nothing comes up, use one of these scenarios:
- Intermittent DNS resolution failures in a multi-VPC environment
- BGP flapping between two peers after a firmware upgrade
- Asymmetric routing causing stateful firewall drops

Write up: Did the AI give useful advice? Where did it hallucinate? What would make it better? → `reports/troubleshooter-service.md`

---

[← Block 3–4: Data & Tooling](../../02-python-for-ai/03-04-data-and-tooling/index.md) | [Block 7–8: Structured Output →](../07-08-structured-output/index.md)
