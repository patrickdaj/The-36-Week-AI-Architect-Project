# 🤖 Block 9: Multi-Agent Systems

[← Block 8: Tool Use & ReAct](../08-tool-use-and-react/index.md) | [Block 10: SOC Analyst Agent →](../10-soc-analyst-agent/index.md)

> *"One agent is a tool. Multiple agents talking to each other is an architecture."*

**Quick Reference:** [→ Block 9 Quick Ref](quick-ref.md)

---

## Before You Start Block 9

- 📺 [DeepLearning.AI — Multi AI Agent Systems with crewAI](https://www.deeplearning.ai/short-courses/multi-ai-agent-systems-with-crewai/) — free, ~1 hour

**Setup:**
```bash
pip install crewai crewai-tools
```

---

### Session 36: Agent Communication Patterns

**Skill:** Understand how agents coordinate. Sequential handoff, parallel execution, supervisor/worker, debate.

**Build:** Create `05-agent-patterns.py`:
- Implement 3 communication patterns:
  1. **Sequential:** Agent A does research → passes findings to Agent B for analysis → Agent C writes the report
  2. **Parallel:** Three agents investigate different aspects simultaneously, results merged
  3. **Supervisor:** A manager agent breaks a task into subtasks, delegates to workers, assembles final output
- Use LangGraph for each pattern — compare code complexity and output quality

| Component | Task |
|-----------|------|
| Build | `05-agent-patterns.py` — 3 multi-agent patterns |
| Key | Sequential, parallel, supervisor architectures |

> 📖 **Read:** [LangGraph — Multi-Agent Architectures](https://langchain-ai.github.io/langgraph/concepts/multi_agent/)

---

### Session 37: CrewAI — Agents with Roles

**Skill:** Use CrewAI to define agents with specific roles, goals, and backstories. Higher-level abstraction than LangGraph.

**Build:** Create `06-security-crew.py`:
- Define a security review crew:
  - **Threat Analyst:** Researches and identifies threats in provided data
  - **Vulnerability Assessor:** Evaluates findings against known vulnerabilities
  - **Report Writer:** Synthesizes everything into an executive-ready document
- Input: a security scenario (e.g., "We detected unusual outbound traffic from our database server")
- Output: structured investigation report

| Component | Task |
|-----------|------|
| Build | `06-security-crew.py` — CrewAI security review team |
| Key | Agent roles, task delegation, output assembly |

> 📖 **Read:** [CrewAI — Getting Started](https://docs.crewai.com/) — the official docs

---

### Session 38: Agent Guardrails and Cost Control

**Skill:** Agents can loop, hallucinate actions, and burn through tokens. Build the safety nets.

**Build:** Create `07-agent-guardrails.py`:
- Implement guardrails layer:
  - **Token budget:** Hard cap per agent run (kill agent if exceeded)
  - **Iteration limit:** Maximum loops before forced termination
  - **Output validation:** Check agent outputs against allowed schemas
  - **Action allowlist:** Agents can only call approved tools
  - **Content filtering:** Detect and block hallucinated tool calls or unsafe operations
- Test: deliberately trigger each guardrail and verify it fires

| Component | Task |
|-----------|------|
| Build | `07-agent-guardrails.py` — safety and cost controls |
| Key | Budget enforcement, iteration limits, output validation |

---

### Session 39: Agent Observability

**Skill:** Trace and debug what agents are doing. When an agent gives a bad answer, you need to see every step.

**Build:** Create `08-agent-tracing.py`:
- Instrument your agents with structured logging:
  - Every thought, action, and observation logged with timestamps
  - Token usage per step
  - Tool call inputs and outputs
  - State transitions in the graph
- Visualize: generate a trace diagram showing the agent's path through a task
- Export: traces as JSON for analysis

| Component | Task |
|-----------|------|
| Build | `08-agent-tracing.py` — agent observability and tracing |
| Key | Structured logging, trace visualization, debugging |

> 📖 **Read:** [LangSmith Documentation](https://docs.smith.langchain.com/) — the ecosystem's observability tool (study the concepts, free tier or use your own logging)

---

### ⏰ Project 10: Live Agent Comparison

Run the same security investigation through your LangGraph agent and your CrewAI crew:
1. Same input scenario for both
2. Compare: quality of output, number of steps, token cost, time to complete
3. Which pattern won? Why?

→ `reports/agent-comparison-service.md`

---

[← Block 8: Tool Use & ReAct](../08-tool-use-and-react/index.md) | [Block 10: SOC Analyst Agent →](../10-soc-analyst-agent/index.md)
