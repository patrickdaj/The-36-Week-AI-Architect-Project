# 🤖 Unit 5 — AI Agents

<small>Weeks 14–20 · 4 blocks</small>

[→ Start Block 8](08-tool-use-and-react/index.md)

---

An agent is an LLM that can use tools, make decisions, and loop until a task is done. It's the difference between "AI that answers questions" and "AI that does work."

This unit takes you from tool calling to multi-agent swarms. You'll build a SOC analyst agent that queries threat intelligence, checks CVE databases, correlates findings, and writes incident summaries — with human-in-the-loop approval for anything high-severity. Then you'll build a multi-agent audit system where specialized agents collaborate.

**Your security brain matters here.** Agent guardrails are a trust boundary problem. Cost runaway is a resource exhaustion problem. Tool permissions are an access control problem. You already know how to think about these things.

---

## What You'll Build

- An **LLM with tools** — API calling, web search, database queries
- A **ReAct agent** that reasons, acts, and observes in a loop
- A **SOC analyst agent** with threat intel lookups, CVE correlation, and incident summarization
- A **multi-agent audit swarm** — network reviewer + compliance checker + report writer
- **Human-in-the-loop** approval workflows

---

## Blocks

| Block | Topic | Weeks |
|-------|-------|-------|
| [Block 8: Tool Use & ReAct](08-tool-use-and-react/index.md) | Function calling, tool definitions, ReAct pattern | 14–15 |
| [Block 9: Multi-Agent Systems](09-multi-agent-systems/index.md) | LangGraph, CrewAI, agent communication, state machines | 16–17 |
| [Block 10: SOC Analyst Agent](10-soc-analyst-agent/index.md) | 🔬 Lab — full SOC agent with threat intel and human-in-the-loop | 18–19 |
| [Block 11: Audit Swarm](11-audit-swarm/index.md) | 🔬 Lab — multi-agent infrastructure audit system | 20 |
