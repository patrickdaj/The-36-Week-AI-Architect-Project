# 🔬 Block 10: SOC Analyst Agent Lab

[← Block 9: Multi-Agent Systems](../09-multi-agent-systems/index.md) | [Block 11: Audit Swarm Capstone →](../11-audit-swarm/index.md)

> *"A SOC analyst's job is 80% correlation and 20% judgment. AI can do most of the 80%."*

**Quick Reference:** [→ Block 10 Quick Ref](quick-ref.md)

---

This is a two-week lab. You're building a complete SOC analyst agent that can triage alerts, investigate incidents, and write reports.

## Before You Start

- Sign up for: [VirusTotal API](https://www.virustotal.com/) (free, 4 req/min) and [AbuseIPDB](https://www.abuseipdb.com/) (free, 1000/day)
- Review your tool library from Session 33

---

## Architecture

```
[Alert Input] → SOC Agent receives alert data
     ↓
[Triage] → Classify severity, determine investigation plan
     ↓
[Investigate] → Query SIEM, threat intel, CVE databases
     ↓     ↓     ↓
[VirusTotal] [AbuseIPDB] [NVD] [Asset Inventory]
     ↓
[Correlate] → Cross-reference findings, build timeline
     ↓
[Human Approval] → High-severity: pause for analyst review
     ↓
[Report] → Structured incident summary with recommendations
```

### Week 1: Core Agent

**Session 40:** Build `soc-agent/tools/` — real API integrations:
- VirusTotal: IP/domain/hash reputation lookups
- AbuseIPDB: IP abuse reports and confidence scores
- NVD: CVE details for any mentioned vulnerabilities
- Mock SIEM: simulated log search returning realistic results
- Asset inventory: from your Phase 3 CVE analyzer

**Session 41:** Build `soc-agent/agent.py` — the LangGraph agent:
- State: alert data, investigation findings, timeline, severity assessment
- Tools wired up to the real APIs
- Investigation logic: the agent decides what to look up based on alert type
- Handles: IP-based alerts, hash-based alerts, domain-based alerts, vulnerability alerts

### Week 2: Production Features

**Session 42:** Build `soc-agent/hitl.py` — human-in-the-loop:
- Approval workflow for containment actions
- Risk scoring that determines approval requirements
- Timeout handling and escalation paths
- Decision audit trail

**Session 43:** Build `soc-agent/reporter.py` — incident reporting:
- Generates structured incident reports (markdown + JSON)
- Timeline reconstruction from investigation steps
- IOC extraction (IPs, domains, hashes, CVEs mentioned)
- Remediation recommendations with priority ranking
- Quality check: report completeness validation

---

### ⏰ Project 11: Simulated SOC Shift

Create 5 realistic alerts and run your SOC agent against each:
1. Malware hash detected on endpoint
2. Outbound connection to known C2 IP
3. Brute force SSH attempts against bastion host
4. Suspicious DNS queries (DGA-like domains)
5. Privilege escalation alert from EDR

Grade each: Was the triage correct? Was the investigation thorough? Was the report useful?

→ `reports/soc-agent-service.md`

---

[← Block 9: Multi-Agent Systems](../09-multi-agent-systems/index.md) | [Block 11: Audit Swarm Capstone →](../11-audit-swarm/index.md)
