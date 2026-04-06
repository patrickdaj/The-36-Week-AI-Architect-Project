# 🎯 Block 1: Stop Wasting Tokens

[Block 2: Data & Tooling →](../../02-python-for-ai/02-data-and-tooling/index.md)

> *"The difference between a $0.002 prompt and a $0.20 prompt is knowing what to leave out."*

**Quick Reference:** [→ Block 1 Quick Ref](quick-ref.md)

---

## Before You Start Block 1

Skim these three — 30 minutes total, tops:

- 📖 [Anthropic — Prompt Engineering Best Practices](https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/overview) — 15-minute read, covers the full set of techniques (clarity, examples, CoT, role prompts). Read this one fully.
- 📖 [Prompt Engineering Guide — Basics of Prompting](https://www.promptingguide.ai/introduction/basics) — 5-minute read, model-agnostic overview of prompt elements and general tips
- 📺 [DeepLearning.AI — ChatGPT Prompt Engineering for Developers](https://www.deeplearning.ai/short-courses/chatgpt-prompt-engineering-for-developers/) — free, ~1 hour, code-along in Jupyter (do this one on Day 1 if you want a warm-up)

**Setup for the week:** Create your project repo and virtual environment:
```bash
mkdir -p ~/Development/ai-architect-builds/phase-0-prompts
cd ~/Development/ai-architect-builds
git init
python -m venv .venv
source .venv/bin/activate
pip install jupyter
```

**Rule for the block:** Every prompt you write this week goes in your prompt library. No throwaway prompts. If it's worth asking, it's worth saving.

---

## Week 1 — Your Prompts Are Expensive and Vague (Fix Both)

### Session 1: The System Prompt

**Skill:** Write a system prompt that constrains the model's behavior, output format, and domain expertise. Stop relying on the model to guess what you want.

**Build:** Create a file `system-prompts/network-troubleshooter.md` with a system prompt that turns an LLM into a senior network engineer. Include:
- Role definition ("You are a senior network engineer with 20+ years experience...")
- Output constraints (structured format: root cause, affected systems, remediation steps)
- Behavioral rules (always ask clarifying questions before diagnosing, cite protocols by RFC number)
- Limitations acknowledgment (tell user when you're unsure, never guess at IP addresses)

Test it in ChatGPT, Claude, or Copilot Chat. Compare the quality of response with vs. without the system prompt.

| Component | Task |
|-----------|------|
| Build | `system-prompts/network-troubleshooter.md` |
| Test | Same network problem with and without system prompt — screenshot both |

> 📖 **Read:** [Anthropic — Give Claude a Role](https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/give-claude-a-role) — how to define persona, expertise, and constraints — exactly what you're building
>
> 📖 **Read:** [Prompt Engineering Guide — General Tips for Designing Prompts](https://www.promptingguide.ai/introduction/tips) — concise list of do's and don'ts, model-agnostic

---

### Session 2: Few-Shot Prompting

**Skill:** Use examples to steer model output. Understand why "show, don't tell" works better than long instructions for formatting and style.

**Build:** Create `system-prompts/security-advisory-writer.md` — a prompt that takes raw CVE data and produces a structured advisory:
- Write 3 few-shot examples: give the model a raw CVE entry, show it the exact output format you want
- Include one negative example: "Here's what a BAD advisory looks like — don't do this"
- Test with 5 real CVEs from [NVD](https://nvd.nist.gov/) — compare one-shot vs. three-shot quality

| Component | Task |
|-----------|------|
| Build | `system-prompts/security-advisory-writer.md` with 3 few-shot examples |
| Test | Run against 5 real CVEs, save outputs |

> 📖 **Read:** [Prompt Engineering Guide — Few-Shot Prompting](https://www.promptingguide.ai/techniques/fewshot) — when to use it, how many examples, and failure modes
>
> 🎥 **Compare Notes:** [DeepLearning.AI — Iterative Prompt Development](https://learn.deeplearning.ai/chatgpt-prompt-eng/lesson/3/iterative) — watch how they refine prompts through iteration

---

### Session 3: Chain-of-Thought

**Skill:** Make the model think step-by-step. Understand why CoT works (it's not magic — it's forcing the model to use intermediate tokens as working memory).

**Build:** Create `system-prompts/incident-analyzer.md` — a prompt for security incident analysis:
- Include explicit chain-of-thought instructions: "First analyze the IOCs, then assess the kill chain stage, then determine blast radius, then recommend containment"
- Test: Give it a realistic incident (suspicious outbound traffic to known C2 IP, lateral movement indicators, unusual service account activity)
- Compare: Same incident with and without CoT instructions — is the CoT version more thorough?

| Component | Task |
|-----------|------|
| Build | `system-prompts/incident-analyzer.md` with CoT instructions |
| Test | Realistic incident scenario, compare CoT vs. direct |

> 📖 **Read:** [Prompt Engineering Guide — Chain-of-Thought](https://www.promptingguide.ai/techniques/cot) — the paper, the technique, and when it doesn't help
>
> 📖 **Read:** [Anthropic — Thinking / Extended Thinking](https://docs.anthropic.com/en/docs/build-with-claude/extended-thinking) — Claude's implementation of this pattern

---

### Session 4: Context Window Economics

**Skill:** Understand token counting, context window limits, and the cost implications of your prompts. Learn to calculate exactly what a prompt costs before you send it.

**Build:** Create `tools/token-counter.py`:
```python
# A CLI tool that:
# 1. Takes a prompt file as input
# 2. Counts tokens using tiktoken (OpenAI) or the model's tokenizer
# 3. Estimates cost at current API prices (GPT-4, Claude Sonnet, Gemini)
# 4. Warns if the prompt exceeds X% of the context window
# 5. Suggests which model tier to use based on prompt complexity
```

Run it against every prompt you've written so far. How much would each cost per call? Per 100 calls?

| Component | Task |
|-----------|------|
| Build | `tools/token-counter.py` — CLI token counter with cost estimation |
| Test | Run against all prompts from Sessions 1–3 |

> 📖 **Read:** [OpenAI — Tokenizer](https://platform.openai.com/tokenizer) — interactive tokenizer, see how text becomes tokens
>
> 📖 **Read:** [Anthropic — Token Counting](https://docs.anthropic.com/en/docs/build-with-claude/token-counting) — how different models count differently

---

### ⏰ Project 1: Prompt Audit of Your Real Workflow

This is your first "service" — take what you've learned and apply it to your actual work.

**The task:** Go through your last week of Copilot/ChatGPT/Claude usage. For each conversation:
1. Was there a system prompt? Could there have been?
2. How many tokens did you waste on vague instructions?
3. Rewrite the 3 worst prompts using your new techniques
4. Estimate the token/cost savings

Write up your findings in `reports/prompt-audit-week-1.md`.

---

## Week 2 — From Artisanal Prompts to Reusable Infrastructure

### Session 5: Structured Output (JSON Mode)

**Skill:** Force the model to return structured data you can parse programmatically. This is the bridge between "chatting with AI" and "building with AI."

**Build:** Create `tools/config-reviewer.py`:
- Takes a network/firewall config file as input
- Sends it to an LLM with a system prompt that returns JSON:
  ```json
  {
    "findings": [
      {
        "severity": "high",
        "rule": "SSH permits password auth",
        "line": 47,
        "recommendation": "Set PasswordAuthentication no",
        "cis_benchmark": "5.2.10"
      }
    ],
    "summary": "3 high, 2 medium, 1 low findings"
  }
  ```
- Parse the JSON response, generate a formatted report
- Handle the case where the model returns invalid JSON (it will — build the retry/fix logic)

| Component | Task |
|-----------|------|
| Build | `tools/config-reviewer.py` — config review with JSON output |
| Test | Run against a sample SSH config, firewall ruleset |

> 📖 **Read:** [OpenAI — JSON Mode](https://platform.openai.com/docs/guides/structured-outputs) — how to force structured output
>
> 📖 **Read:** [Anthropic — Tool Use](https://docs.anthropic.com/en/docs/build-with-claude/tool-use) — Claude's approach to structured output via tools

---

### Session 6: Temperature, Top-P, and Generation Parameters

**Skill:** Understand what the knobs do. Temperature isn't "creativity" — it's sampling distribution width. Learn when to set temp=0 (deterministic tasks) vs. temp=0.7 (creative tasks).

**Build:** Create `tools/prompt-ab-tester.py`:
- Takes a prompt and runs it N times at different temperature/top-p settings
- Records each response
- Compares: consistency (do you get the same answer?), quality (is the analysis better?), and diversity (for brainstorming tasks)
- Outputs a comparison table

Test it with:
1. Your incident analyzer prompt (should probably be temp=0)
2. A "generate 5 creative phishing email subject lines for security awareness training" prompt (higher temp)
3. Your config reviewer (definitely temp=0)

| Component | Task |
|-----------|------|
| Build | `tools/prompt-ab-tester.py` — A/B tester for generation parameters |
| Test | 3 different prompt types at varying temperatures |

> 📖 **Read:** [Prompt Engineering Guide — LLM Settings](https://www.promptingguide.ai/introduction/settings) — temperature, top-p, max tokens explained
>
> 📖 **Read:** [Cohere — Temperature](https://docs.cohere.com/docs/temperature) — another good explainer with visual intuition

---

### Session 7: Prompt Templates and Variable Injection

**Skill:** Turn one-off prompts into reusable templates with named variables. This is how prompt engineering becomes prompt infrastructure.

**Build:** Create `prompt-library/` directory with at least 6 reusable templates:

```
prompt-library/
├── templates/
│   ├── incident-response.md      # {incident_description}, {affected_systems}, {severity}
│   ├── config-review.md          # {config_type}, {config_content}, {compliance_standard}
│   ├── change-review.md          # {change_description}, {affected_systems}, {rollback_plan}
│   ├── vulnerability-assess.md   # {cve_id}, {asset_inventory}, {network_topology}
│   ├── runbook-generator.md      # {system_name}, {procedure_type}, {audience_level}
│   └── postmortem-writer.md      # {incident_summary}, {timeline}, {root_cause}
├── render.py                     # Loads template, injects variables, outputs final prompt
└── README.md                     # Documents each template's purpose and variables
```

Build `render.py` to load a template, substitute variables, and optionally count tokens before sending.

| Component | Task |
|-----------|------|
| Build | `prompt-library/` with 6 templates + renderer |
| Test | Render each template with realistic data |

> 📖 **Read:** [Python Docs — Template Strings](https://docs.python.org/3/library/string.html#template-strings) — the stdlib approach you'll use in `render.py`. Simple, no dependencies.

---

### Session 8: Prompt Injection and Defensive Prompting

**Skill:** Understand prompt injection — the SQL injection of the AI era. As a security engineer, this should terrify and fascinate you. Learn to write prompts that resist injection.

**Build:** Create `tools/injection-tester.py`:
- Takes a system prompt and tests it against common prompt injection attacks:
  - "Ignore all previous instructions and..."
  - Markdown/HTML injection in user input
  - Indirect injection via data (what if the log file you're analyzing contains injection?)
  - Encoding tricks (base64, Unicode)
- Records which attacks succeed and which are caught
- Suggests defensive improvements to the system prompt

Test it against every system prompt you've written in this block.

| Component | Task |
|-----------|------|
| Build | `tools/injection-tester.py` — prompt injection test suite |
| Test | Run against all system prompts from Block 1 |

> 📖 **Read:** [OWASP — Top 10 for LLM Applications — Prompt Injection](https://genai.owasp.org/llmrisk/llm01-prompt-injection/) — the canonical reference
>
> 📖 **Read:** [Simon Willison — Prompt Injection Attacks](https://simonwillison.net/2023/Apr/14/worst-that-can-happen/) — the best overview of the problem space
>
> 📖 **Read:** [Prompt Engineering Guide — Adversarial Prompting](https://www.promptingguide.ai/risks/adversarial) — injection, leaking, and jailbreaking techniques with examples

---

### ⏰ Project 2: Ship Your Prompt Library

**The task:** Package everything you've built into a clean, documented repo:

1. Organize all system prompts, templates, and tools into a coherent structure
2. Write a README that explains your prompt library to a colleague
3. Use your config-reviewer tool on a real (or realistic) config file and include the output
4. Run your injection tester against your best prompts and document the results
5. Commit everything. Push to GitHub.

This is your first portfolio piece. By Week 2, you should have:
- A documented prompt library with 6+ templates
- A token counter CLI
- A config reviewer tool
- A prompt A/B tester
- A prompt injection test suite
- A written prompt audit of your real workflow

---

## Optional: Go Deeper

### The Broader Concept: What LLMs Actually Are

You don't need math for this block, but building intuition about what's happening inside the model will pay dividends in every later unit:

- 📺 [3Blue1Brown — But what is a GPT?](https://www.youtube.com/watch?v=wjZofJX0v4M) — visual, math-light, 25 minutes. The best "what's happening in there" explainer.
- 📺 [Andrej Karpathy — Intro to Large Language Models](https://www.youtube.com/watch?v=zjkBMFhNj_g) — 1 hour overview from the former head of AI at Tesla. Surprisingly accessible.
- 📖 [Stephen Wolfram — What Is ChatGPT Doing?](https://writings.stephenwolfram.com/2023/02/what-is-chatgpt-doing-and-why-does-it-work/) — long but math-free. Best written overview.

### Model Comparison

If you have access to multiple models, try the same prompt on all of them:
- GPT-4 / GPT-4o (OpenAI)
- Claude 3.5 Sonnet / Claude 3 Opus (Anthropic)
- Gemini Pro (Google)
- Copilot (GitHub, backed by GPT-4)

Note the differences in style, depth, cost, and speed. This becomes critical in Unit 7 when you're building model routing.

---

[Block 2: Data & Tooling →](../../02-python-for-ai/02-data-and-tooling/index.md)
