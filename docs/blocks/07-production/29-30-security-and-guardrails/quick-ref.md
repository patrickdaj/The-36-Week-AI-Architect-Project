# ⚡ Block 29–30 Quick Reference — Security & Guardrails

## Sessions at a Glance

| # | Session | You Build | Key Tools |
|---|---------|-----------|-----------|
| 60 | Prompt Injection Defense | `security/injection_defense.py` | Delimiters, classifiers, red team |
| 61 | Content Guardrails | `security/guardrails.py` | PII detection, hallucination check |
| 62 | AI Governance & Audit Logging | `security/audit.py` | Structured logs, compliance reports |
| 63 | Threat Model Your AI Platform | `security/threat-model.md` + `security_tests.py` | STRIDE, security regression |
| S17 | Security Audit Presentation | `reports/security-service.md` | Live attack demo |

## Setup Commands

```bash
pip install presidio-analyzer presidio-anonymizer  # PII detection
pip install spacy && python -m spacy download en_core_web_sm
# Already installed: fastapi, litellm, chromadb
```

## Key Files

```
security/
├── injection_defense.py    # Prompt injection multi-layer defense
├── guardrails.py           # Input/output content guardrails
├── audit.py                # Governance audit logging
├── threat-model.md         # STRIDE threat model
├── security_tests.py       # Automated security regression
└── red_team_suite.jsonl    # 50+ injection test cases

reports/
└── security-service.md
```

## OWASP LLM Top 10 Quick Reference

| # | Risk | Your Defense (Session) |
|---|------|----------------------|
| LLM01 | Prompt Injection | `injection_defense.py` (60) |
| LLM02 | Insecure Output Handling | `guardrails.py` output layer (61) |
| LLM03 | Training Data Poisoning | Dataset validation (48) |
| LLM04 | Model Denial of Service | Rate limiting (61), gateway (58) |
| LLM05 | Supply Chain Vulnerabilities | Model hash verification (44) |
| LLM06 | Sensitive Information Disclosure | PII detection (61), audit (62) |
| LLM07 | Insecure Plugin Design | Tool sandboxing (37) |
| LLM08 | Excessive Agency | Human-in-the-loop (40) |
| LLM09 | Overreliance | Confidence gating (61), evals (52) |
| LLM10 | Model Theft | Access controls, audit (62) |
