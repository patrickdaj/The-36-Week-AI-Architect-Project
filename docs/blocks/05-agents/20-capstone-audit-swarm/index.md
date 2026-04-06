# 🔬 Block 20: Infrastructure Audit Swarm Capstone

[← Block 18–19: SOC Analyst Agent](../18-19-soc-analyst-agent/index.md) | [Block 21–22: Running Local →](../../06-local-models/21-22-running-local/index.md)

> *"Three agents reviewing a network config catch things one agent misses. That's the whole point."*

**Quick Reference:** [→ Block 20 Quick Ref](quick-ref.md)

---

One-week capstone for Unit 5. Build a multi-agent system that audits network infrastructure.

## The Build: Audit Swarm

### Agent Definitions

**Agent 1: Network Config Reviewer**
- Role: Analyze network device configurations for misconfigurations
- Tools: Config parser, CIS benchmark reference, best practice database
- Output: List of findings with severity and CIS benchmark reference

**Agent 2: Security Policy Compliance Checker**
- Role: Compare configurations against organizational security policies
- Tools: Policy database (RAG from Unit 4), compliance rule engine
- Output: Compliance status per policy requirement, gaps identified

**Agent 3: Report Synthesizer**
- Role: Combine findings from both agents into an executive audit report
- Tools: Report template, severity calculator, remediation recommender
- Output: Executive summary + detailed findings + prioritized remediation plan

### Architecture

Build with LangGraph or CrewAI (your choice based on Block 16–17 comparison):
- Sequential pipeline: Reviewer → Compliance → Synthesizer
- Each agent gets the output of the previous agent plus the original configs
- Final output: comprehensive audit report in markdown

### Input

Use sample network configs (SSH, firewall rules, SNMP, NTP, etc.) — generate realistic samples or use sanitized versions of real configs.

---

### ⏰ Service 12: Audit Report Delivery

Run the full swarm against 3+ different configuration sets. Present the audit reports as if delivering to management:
1. Are the findings accurate?
2. Are the severity ratings appropriate?
3. Would you trust this output in a real audit?

→ `reports/audit-swarm-service.md` plus the generated audit reports

---

[← Block 18–19: SOC Analyst Agent](../18-19-soc-analyst-agent/index.md) | [Block 21–22: Running Local →](../../06-local-models/21-22-running-local/index.md)
