# How to Get the Most Out of This Program

> **The short version:** Build the project. Read the resource. Compare your approach. Write three sentences about what clicked. None of these are optional, and all of them compound.

---

## The Thing Most People Skip (Don't)

Every session has a **Read** — a linked article, doc page, or blog post that explains the *why* behind what you just built. These are not supplemental. They are half the curriculum.

When you build a tool without understanding why it works, you learn one pattern. When you read the resource alongside it, you learn a transferable principle that applies to a hundred systems you haven't built yet.

Anthropic's guide on [prompt engineering](https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering) isn't just about Claude. It explains how LLMs process instructions in a way that changes how you think about every API call, every system prompt, every time you're tempted to dump your entire codebase into the context window. That's the difference between using an API and understanding AI systems.

**The rule:** Before you close VS Code, open the article. Read it while the build is still in your memory.

---

## Compare Notes — The Video Component

Many sessions have a **Compare Notes** video or tutorial: a curated resource showing a professional building the same type of system or explaining the same concept.

This is not passive watching. The point is comparison:

- Did they structure their code the same way?
- What was different about their architecture?
- How did they handle the edge case you hit?
- What would you steal for next time?

Watch the video after you've built — not before. Watching before turns it into a tutorial you copy. Watching after turns it into a diagnostic.

---

## Before Every Block: Read Before You Code

Before starting a new block, open that block's `index.md` and skim the whole two weeks. It takes 15 minutes and catches problems that would otherwise surface mid-session:

- APIs that need free tier signup you didn't plan for
- Dependencies that need installing first
- Sessions that build on previous sessions' output
- Concepts you want to preview before the hands-on session

Each block's opening section ("Before You Start") has a short reading/setup list. Do at least the setup before you start coding.

---

## Two Files, Two Contexts

Each block has a **full guide** (`index.md`) and a **quick ref** (`quick-ref.md`). Use them differently:

| | Full Guide | Quick Ref |
|-|------------|-----------|
| **When** | Before the session | During the session |
| **What** | Read the skill explanation, context, and linked resources | Glance at the build task and API links |
| **Why** | The narrative connects the skill to everything else | You don't want to dig through prose while coding |

The full guide is where you understand the session. The quick ref is where you execute it.

---

## Sessions, Labs, and Projects

The curriculum has three types of hands-on work:

### 💻 Session
A focused skill + build. You learn one concept, build a small tool or component that uses it, read the resource, compare notes. Most of the curriculum is sessions.

### 🔬 Lab
A multi-session project that combines several skills into a larger build. Labs span 1–2 weeks and produce a substantial, portfolio-worthy tool. The SOC Analyst Agent and the Production Platform are labs.

### ⏰ Project
A deliverable. You deploy or demo what you've built under real-ish conditions. Show it to a colleague. Use it for actual work. Write up findings. The point is forcing your tools out of the "it works on my machine" bubble.

---

## The Weekly Rhythm

| Day | Activity | Time |
|-----|----------|------|
| **Weeknight 1** | Study: Read/watch assigned material | 1–2 hrs |
| **Weeknight 2** | Build: Code on current project | 1–2 hrs |
| **Weekend block** | Build: Focused project work + experimentation | 3–4 hrs |

You're targeting 5–8 hours per week. That's a realistic commitment for someone with a full-time job. The key is consistency — 6 hours every week beats 15 hours one week and zero the next.

---

## The Rules

1. **Build > Read.** If you're not coding, you're falling behind. Target 70% building / 30% studying.
2. **Ship weekly.** Commit something to your repo every week, even if it's small.
3. **Use your domain.** Every project uses security/networking data. Your 25 years of domain expertise is an unfair advantage — exploit it.
4. **Document as you go.** Architecture decisions, lessons learned, what broke. This IS the portfolio.
5. **No tutorial hell.** Read/watch once, then build. If stuck, use AI to help (you're literally learning AI — use it recursively).
6. **Compound your tools.** Each phase builds on the last. By Unit 7, you're combining everything into a production system.
7. **Own the failure modes.** When something breaks, document why. An architect who's been bitten by agent loops and token blowouts designs better systems than one who's only read about them.

---

## Your Unfair Advantages

You're not starting from zero. You're starting from 25 years of production engineering:

1. **Security mindset** — You already think about threat models, attack surfaces, trust boundaries. Most AI engineers don't. OWASP Top 10 for LLMs will feel like home.
2. **Infrastructure expertise** — Deployment, networking, monitoring, scaling — you've done this for decades. AI serving is just another service you already know how to run.
3. **CS degree** — Data structures, algorithms, systems thinking. The AI concepts click faster when you already understand the fundamentals underneath them.
4. **Domain expertise** — Security + AI is a white-hot intersection. The people who deeply understand BOTH are rare and extremely valuable.
5. **Engineering discipline** — You've shipped production systems for 25 years. Most AI demos never make it to production. You know how to get them there.

---

## Milestones

| Week | You Can... |
|------|------------|
| 2 | Write surgical prompts, explain token economics, manage context windows |
| 4 | Wrangle data in Python/Pandas, build CLI tools, work fluently in Jupyter |
| 8 | Build any LLM API app, handle streaming, manage costs, structure outputs |
| 13 | Design and build RAG systems, explain embeddings to your team |
| 20 | Build multi-agent systems with tool use and human-in-the-loop |
| 26 | Run and fine-tune models locally, evaluate model quality, serve local APIs |
| 32 | Design production AI architectures, secure AI systems, write ADRs |
| 36 | **Architect enterprise AI solutions, present and defend design decisions** |
