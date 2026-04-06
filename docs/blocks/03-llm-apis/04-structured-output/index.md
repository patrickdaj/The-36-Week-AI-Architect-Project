# 🔌 Block 4: Structured Output & Cost Control

[← Block 3: First AI Apps](../03-first-ai-apps/index.md) | [Block 5: Vectors & Retrieval →](../../04-embeddings-and-rag/05-vectors-and-retrieval/index.md)

> *"If you can't parse the output programmatically, you haven't built a tool — you've built a chatbot."*

**Quick Reference:** [→ Block 4 Quick Ref](quick-ref.md)

---

## Before You Start Block 4

10 minutes — read whichever matches your API choice:

- 📖 [OpenAI — Structured Outputs](https://platform.openai.com/docs/guides/structured-outputs) — JSON mode and function calling, read the "Introduction" and "Examples" sections
- 📖 [Anthropic — Tool Use](https://docs.anthropic.com/en/docs/build-with-claude/tool-use) — Claude's approach to structured output via tool definitions

---

## Week 1 — Make AI Output Machine-Readable

### Session 17: JSON Mode and Schema Enforcement

**Skill:** Force LLMs to return valid JSON that matches a schema. This is how you build reliable pipelines, not prayer-based parsing.

**Build:** Create `04-advisory-summarizer.py`:
- Fetch latest CVEs from [NVD API](https://services.nvd.nist.gov/rest/json/cves/2.0)
- Send each to the LLM with JSON mode enabled
- Enforce output schema: `{ "cve_id", "summary", "severity", "affected_products[]", "remediation", "relevance_score" }`
- Handle: malformed JSON (retry with correction prompt), missing fields, schema validation
- Output structured JSON file of summarized advisories

| Component | Task |
|-----------|------|
| Build | `04-advisory-summarizer.py` — CVE summarizer with JSON output |
| Key | JSON mode, schema validation, NVD API integration |

> 📖 **Read:** [NVD API Documentation](https://nvd.nist.gov/developers/vulnerabilities) — the data source you'll use throughout the curriculum

---

### Session 18: Function Calling / Tool Use

**Skill:** Define functions the model can "call" — it decides when to use them based on the conversation. This is the foundation for agents in Unit 5.

**Build:** Create `05-smart-troubleshooter.py`:
- Upgrade your troubleshooter with tool definitions:
  - `lookup_cve(cve_id)` — fetches CVE details from NVD
  - `check_port_status(host, port)` — simulated port check
  - `lookup_ip_reputation(ip)` — simulated threat intel lookup
  - `search_knowledge_base(query)` — searches your prompt library
- The model decides which tools to call based on the conversation
- You execute the tool, return results, model continues reasoning

| Component | Task |
|-----------|------|
| Build | `05-smart-troubleshooter.py` — troubleshooter with tool use |
| Key | Tool definitions, tool execution loop, result injection |

> 📖 **Read:** [OpenAI — Function Calling](https://platform.openai.com/docs/guides/function-calling) — the standard pattern
>
> 📖 **Read:** [Anthropic — Tool Use](https://docs.anthropic.com/en/docs/build-with-claude/tool-use) — Claude's implementation

---

### Session 19: Cost Tracking and Budgeting

**Skill:** Track what your AI tools cost, set budgets, and optimize. In production, cost is a feature.

**Build:** Create `tools/cost-tracker.py`:
- Middleware that wraps all LLM API calls
- Logs: timestamp, model, input tokens, output tokens, cost, prompt hash
- Stores data in SQLite for querying
- Reports: daily/weekly costs, cost per tool, most expensive prompts
- Budget alerts: warn at 80%, hard stop at 100% of daily budget

Integrate into your troubleshooter and advisory summarizer.

| Component | Task |
|-----------|------|
| Build | `tools/cost-tracker.py` — API cost tracking middleware |
| Integrate | Add to troubleshooter and advisory summarizer |

> 📖 **Read:** [OpenAI — Pricing](https://openai.com/api/pricing/) — know what you're spending
>
> 📖 **Read:** [Google AI — Pricing](https://ai.google.dev/pricing) — compare against free tier limits

---

### Session 20: Daily Advisory Digest Pipeline

**Skill:** Combine everything into an automated pipeline. Fetch → Process → Summarize → Report.

**Build:** Create `06-daily-digest.py`:
- Scheduled pipeline that:
  1. Fetches new CVEs from NVD (last 24 hours)
  2. Filters by keywords relevant to your stack (e.g., "cisco", "palo alto", "ssh", "kubernetes")
  3. Summarizes each relevant CVE using your JSON schema
  4. Generates a markdown daily digest
  5. Tracks costs via your middleware
  6. Optionally sends to a Slack webhook or email (mock is fine)

| Component | Task |
|-----------|------|
| Build | `06-daily-digest.py` — automated CVE digest pipeline |
| Test | Run for last 7 days of CVEs, generate digest |

---

### ⏰ Project 5: Ship the Advisory Summarizer

Package your advisory summarizer as a documented, installable tool:
1. Add a `README.md` with usage examples
2. Add a `requirements.txt`
3. Run it for a real week and share the output with a colleague
4. Document: What was useful? What was noise? What would you change?

→ `reports/advisory-summarizer-service.md`

---

[← Block 3: First AI Apps](../03-first-ai-apps/index.md) | [Block 5: Vectors & Retrieval →](../../04-embeddings-and-rag/05-vectors-and-retrieval/index.md)
