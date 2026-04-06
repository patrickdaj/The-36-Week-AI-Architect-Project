# 🤖 Block 8: Tool Use & ReAct

[← Block 7: CVE Impact Analyzer](../../04-embeddings-and-rag/07-cve-impact-analyzer/index.md) | [Block 9: Multi-Agent Systems →](../09-multi-agent-systems/index.md)

> *"An agent is an LLM in a loop: think, act, observe, repeat. The magic is in knowing when to stop."*

**Quick Reference:** [→ Block 8 Quick Ref](quick-ref.md)

---

## Before You Start Block 8

- 📖 [Anthropic — Building Effective Agents](https://docs.anthropic.com/en/docs/build-with-claude/agent-overview) — the best overview of agent patterns
- 📖 [Lilian Weng — LLM Powered Autonomous Agents](https://lilianweng.github.io/posts/2023-06-23-agent/) — the seminal blog post
- 📺 [DeepLearning.AI — AI Agents in LangGraph](https://www.deeplearning.ai/short-courses/ai-agents-in-langgraph/) — free, ~1 hour

**Setup:**
```bash
mkdir -p ~/Development/ai-architect-builds/phase-4-agents
cd ~/Development/ai-architect-builds/phase-4-agents
pip install langgraph langchain langchain-community
```

---

### Session 32: ReAct from Scratch

**Skill:** Implement the ReAct (Reason + Act) pattern manually — no frameworks. Understand the loop before you use a library to abstract it.

**Build:** Create `01-react-from-scratch.py`:
- Implement a simple agent loop:
  1. **Thought:** LLM reasons about what to do next
  2. **Action:** LLM picks a tool and provides arguments
  3. **Observation:** You execute the tool, return results
  4. **Repeat** until the LLM says "Final Answer"
- Tools: `search_web(query)`, `calculate(expression)`, `lookup_ip(ip_address)`
- Parse the LLM's output format manually (regex or structured output)
- Add: maximum iteration limit (prevent infinite loops), cost tracking per iteration

| Component | Task |
|-----------|------|
| Build | `01-react-from-scratch.py` — ReAct agent without frameworks |
| Key | The loop, tool dispatch, iteration limits |

> 📖 **Read:** [ReAct Paper (Yao et al., 2022)](https://arxiv.org/abs/2210.03629) — the original paper, read the abstract and examples

---

### Session 33: Tool Definitions Done Right

**Skill:** Design tools that models can actually use well. Bad tool descriptions = bad tool selection = broken agents.

**Build:** Create `02-tool-library.py`:
- Define 6+ tools relevant to security operations:
  - `query_siem(query, time_range)` — search SIEM logs (mock with local data)
  - `lookup_threat_intel(indicator, type)` — check IP/domain/hash against threat feeds
  - `get_asset_info(hostname)` — retrieve asset details from inventory
  - `check_vulnerability(cve_id)` — look up CVE from NVD
  - `run_nmap_scan(target, ports)` — simulated port scan (NEVER run real nmap without permission)
  - `create_ticket(title, severity, description)` — create an incident ticket (mock)
- Each tool: clear description, typed parameters, example usage, error handling
- Test: give the agent different scenarios and verify it picks the right tools

| Component | Task |
|-----------|------|
| Build | `02-tool-library.py` — security-focused tool library |
| Key | Clear descriptions, typed params, testable |

> 📖 **Read:** [OpenAI — Function Calling Best Practices](https://platform.openai.com/docs/guides/function-calling) — tool design guidance

---

### Session 34: LangGraph Basics

**Skill:** Use LangGraph to build stateful agents with proper state management, conditional routing, and persistence.

**Build:** Create `03-langgraph-agent.py`:
- Rebuild your ReAct agent using LangGraph
- Define: state schema, tool nodes, router (conditional edges), end condition
- Add: state persistence (save/resume agent runs)
- Add: streaming of agent actions (show each thought/action as it happens)
- Compare: how much cleaner is LangGraph vs. your manual loop?

| Component | Task |
|-----------|------|
| Build | `03-langgraph-agent.py` — LangGraph-based agent |
| Key | State graph, conditional edges, persistence |

> 📖 **Read:** [LangGraph — Quick Start](https://langchain-ai.github.io/langgraph/tutorials/introduction/) — the official tutorial

---

### Session 35: Human-in-the-Loop

**Skill:** Build agents that pause and ask for approval before taking high-impact actions. This is critical for security tools.

**Build:** Create `04-human-in-the-loop.py`:
- Extend your LangGraph agent with approval gates:
  - **Low risk** (read-only queries): execute automatically
  - **Medium risk** (creating tickets, sending alerts): notify human, auto-approve after timeout
  - **High risk** (blocking IPs, isolating hosts): require explicit human approval
- Implement: CLI-based approval (input prompt), approval timeout, rejection handling
- Log all decisions: what was proposed, what was approved/rejected, by whom

| Component | Task |
|-----------|------|
| Build | `04-human-in-the-loop.py` — agent with approval workflows |
| Key | Risk classification, approval gates, decision logging |

> 📖 **Read:** [LangGraph — Human-in-the-Loop](https://langchain-ai.github.io/langgraph/concepts/human_in_the_loop/) — built-in support for breakpoints

---

### ⏰ Project 9: Agent Failure Post-Mortem

Build an agent that deliberately encounters problems:
1. Run it on a scenario where it should loop (conflicting information)
2. Run it on a scenario where it picks the wrong tool
3. Run it on a scenario where a tool returns an error
4. Document every failure mode and how you'd fix it

→ `reports/agent-failures-service.md`

---

[← Block 7: CVE Impact Analyzer](../../04-embeddings-and-rag/07-cve-impact-analyzer/index.md) | [Block 9: Multi-Agent Systems →](../09-multi-agent-systems/index.md)
