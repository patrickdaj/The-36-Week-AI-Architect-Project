# 🏠 Block 35–36: Ship & Present

[← Block 33–34: Design & Build](../33-34-design-and-build/index.md) | [🏁 Back to Start](../../README.md)

> *"An architect doesn't just design buildings — they present them, defend them, and ship them. This is where you prove you can do all three."*

**Quick Reference:** [→ Block 35–36 Quick Ref](quick-ref.md)

---

## Before You Start Block 35

- Your capstone should be functional from Block 33–34
- 📖 [How to Write a Great README](https://www.makeareadme.com/) — your project's front door
- 📖 [Presentation Zen (summary)](https://www.garr.net/book-summary/presentation-zen-summary) — less is more

---

### Session 72: Polish and Harden

**Skill:** Go from "it works on my machine in a demo" to "someone else can clone this and run it."

**Build:** Polish your capstone:
- README.md: problem, solution, architecture diagram, setup, usage, examples
- `make setup` — one command to install everything
- `make demo` — one command to run the demo scenario
- Error handling: graceful failures with helpful messages
- Edge cases: empty input, huge input, malformed data, model timeout
- Configuration: all secrets in `.env`, all settings in `config.yaml`
- Clean code: remove debug prints, dead code, TODO comments

| Component | Task |
|-----------|------|
| Build | Production-grade README, Makefile, error handling |
| Test | Fresh clone → `make setup` → `make demo` works |

---

### Session 73: Portfolio Documentation

**Skill:** Document your project for a technical audience — hiring managers, peers, open source contributors.

**Build:** Create `capstone/docs/`:
- `DESIGN_DECISIONS.md` — why you chose each technology, tradeoffs considered
- `SECURITY.md` — threat model, guardrails, what's protected and what's not
- `EVALUATION.md` — test results, accuracy metrics, known limitations
- `COST_ANALYSIS.md` — what this costs to run (tokens/month, compute, storage)
- Update `ARCHITECTURE.md` with final state (things changed from the design)
- Blog post draft: 1,000-word writeup of what you built and what you learned

| Component | Task |
|-----------|------|
| Build | 5 documentation files + blog post draft |
| Key | Tell the story of what you built and why |

---

### Session 74: Record Your Demo

**Skill:** A good demo is worth 10,000 words of documentation. Practice and record.

**Build:**
- Write a demo script: exactly what you'll show, in what order, what you'll say
- Practice 3 times before recording
- Record a 5–7 minute video:
  1. The problem (30 seconds)
  2. Architecture overview (60 seconds)
  3. Live demo — happy path (2 minutes)
  4. Live demo — security scenario (1 minute)
  5. Live demo — failure/edge case handling (1 minute)
  6. Results and metrics (30 seconds)
  7. What you'd do differently (30 seconds)
- Tools: QuickTime (macOS), OBS, or Loom (free tier)

| Component | Task |
|-----------|------|
| Build | Demo script + 5-7 minute recorded walkthrough |
| Key | Practice before recording |

---

### Session 75: 36-Week Retrospective

**Skill:** Reflection is how learning becomes permanent. Look back and extract the signal.

**Build:** Create `RETROSPECTIVE.md` at the project root:
- **Skills inventory:** List every tool, technique, and concept you now know
- **Best builds:** Your top 3 favorite things you built and why
- **Hardest sessions:** What was most difficult and how you pushed through
- **What surprised you:** Things that were easier/harder than expected
- **Portfolio pieces:** Which projects are interview-ready?
- **Next 36 weeks:** If you kept going, what would Phase 2 look like?
  - Multimodal (vision + audio)?
  - Real-time streaming agents?
  - Custom pre-training?
  - Contributing to open source AI projects?

| Component | Task |
|-----------|------|
| Build | `RETROSPECTIVE.md` — the most important document you'll write |
| Key | Honest reflection, not a highlight reel |

---

### ⏰ Service 20: Final Presentation

This is it. Present your entire 36-week journey:

1. **Who you were** — network/security engineer blasting Copilot prompts (2 minutes)
2. **What you learned** — the progression from prompt engineering to platform architect (3 minutes)
3. **What you built** — live capstone demo (5 minutes)
4. **What's next** — where you're taking this (2 minutes)

Audience: present to at least one other person — a colleague, a friend, a meetup, or record it publicly.

→ `reports/final-presentation.md`

---

## 🏁 Congratulations

You started this curriculum knowing how to blast prompts at Copilot. You're finishing it having built:

- A prompt engineering toolkit
- Multiple RAG pipelines
- Autonomous AI agents
- A fine-tuned model
- A production AI platform with routing, caching, guardrails, and observability
- A full capstone project solving a real security problem

You're not an "AI enthusiast" anymore. You're an AI architect who happens to have a security background — and that combination is rare and valuable.

Now go build something that matters.

---

[← Block 33–34: Design & Build](../33-34-design-and-build/index.md) | [🏁 Back to Start](../../README.md)
