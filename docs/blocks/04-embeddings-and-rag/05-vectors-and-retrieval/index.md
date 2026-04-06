# 🧠 Block 5: Vectors & Retrieval

[← Block 4: Structured Output](../../03-llm-apis/04-structured-output/index.md) | [Block 6: Advanced RAG →](../06-advanced-rag/index.md)

> *"An embedding is just a list of numbers that captures meaning. Similar meanings = nearby numbers. That's it."*

**Quick Reference:** [→ Block 5 Quick Ref](quick-ref.md)

---

## Before You Start Block 5

20 minutes of reading, plus an optional course:

- 📖 [Pinecone — What are Embeddings?](https://www.pinecone.io/learn/vector-embeddings/) — 10-minute read, the best intuition-first explainer for vectors and similarity
- 📺 [3Blue1Brown — But what is a GPT?](https://www.youtube.com/watch?v=wjZofJX0v4M) — skip to the embeddings visualization (~8 min mark), visual intuition for "meaning as coordinates"
- 📺 [DeepLearning.AI — LangChain: Chat with Your Data](https://www.deeplearning.ai/short-courses/langchain-chat-with-your-data/) — free, ~1 hour, optional but solid if you want the full RAG walkthrough before building

**Setup:**
```bash
mkdir -p ~/Development/ai-architect-builds/phase-3-rag
cd ~/Development/ai-architect-builds/phase-3-rag
pip install chromadb langchain langchain-community sentence-transformers
```

---

## Week 1 — Teach AI to Know Your Things

### Session 21: What Are Embeddings?

**Skill:** Understand embeddings — turning text into vectors (lists of numbers) where similar meanings are close together. No math beyond "these two arrows point the same direction."

**Build:** Create `01-embeddings-explorer.ipynb`:
- Use `sentence-transformers` to embed 20+ security-related phrases
- Embed pairs: ("firewall rule", "access control list"), ("DDoS attack", "denial of service"), ("SSH key", "public key authentication")
- Compute cosine similarity between all pairs
- Visualize: use t-SNE or UMAP to plot embeddings in 2D — do similar concepts cluster?
- Experiment: what happens when you embed a whole paragraph vs. a short phrase?

| Component | Task |
|-----------|------|
| Build | `01-embeddings-explorer.ipynb` — embedding similarity experiments |
| Key | sentence-transformers, cosine similarity, 2D visualization |

> 📖 **Read:** [Hugging Face — Sentence Transformers](https://huggingface.co/docs/sentence-transformers/) — the embedding models you'll use

---

### Session 22: ChromaDB and Vector Storage

**Skill:** Store embeddings in a vector database and retrieve the most similar ones for a query. This is the "retrieval" in RAG.

**Build:** Create `02-vector-store.py`:
- Create a ChromaDB collection
- Ingest 50+ text chunks from security documentation (use NIST CSF, CIS Benchmarks, or your own sanitized docs)
- Query: "How should we handle a compromised endpoint?" → get the 5 most relevant chunks
- Experiment with: number of results (k), distance metrics, metadata filtering
- Display: query → retrieved chunks → similarity scores

| Component | Task |
|-----------|------|
| Build | `02-vector-store.py` — ChromaDB ingestion and retrieval |
| Key | Collection creation, document ingestion, similarity search |

> 📖 **Read:** [ChromaDB — Getting Started](https://docs.trychroma.com/getting-started) — your local vector database

---

### Session 23: Your First RAG Pipeline

**Skill:** Connect retrieval to generation. Retrieve relevant context → inject into prompt → generate answer. This is RAG.

**Build:** Create `03-basic-rag.py`:
- Full pipeline: User question → embed → retrieve top-k chunks from ChromaDB → inject into LLM prompt → generate answer
- System prompt: "Answer the user's question using ONLY the provided context. If the context doesn't contain the answer, say so."
- Test with security policy questions:
  - "What's our password rotation policy?"
  - "How do we handle a phishing report?"
  - "What are the steps for onboarding a new firewall?"

| Component | Task |
|-----------|------|
| Build | `03-basic-rag.py` — complete RAG pipeline |
| Key | Embed query, retrieve context, inject into prompt, generate |

> 📖 **Read:** [LangChain — RAG Tutorial](https://python.langchain.com/docs/tutorials/rag/) — the canonical RAG walkthrough

---

### Session 24: Chunking Strategies

**Skill:** How you split documents into chunks determines RAG quality more than almost anything else. Learn the strategies and their tradeoffs.

**Build:** Create `04-chunking-lab.ipynb`:
- Take one long security document (NIST CSF, a vendor runbook, or synthesize one)
- Chunk it 4 different ways:
  1. Fixed size (500 tokens, 200 overlap)
  2. By paragraph/section headers
  3. Recursive character splitting (LangChain default)
  4. Semantic chunking (split on meaning shifts)
- For each: run the same 10 queries, compare retrieval quality
- Document: which chunking strategy gives the best results for security documentation?

| Component | Task |
|-----------|------|
| Build | `04-chunking-lab.ipynb` — chunking strategy comparison |
| Key | 4 strategies, same queries, retrieval quality comparison |

> 📖 **Read:** [Pinecone — Chunking Strategies](https://www.pinecone.io/learn/chunking-strategies/) — comprehensive overview

---

### ⏰ Project 6: RAG Demo for a Colleague

Load your RAG system with real (or realistic) security documentation. Demo it to a colleague or write it up as if you're presenting:
1. Show 5 questions and the RAG system's answers with source citations
2. Show 2 questions where the system correctly says "I don't have that information"
3. Show 1 question where it gets the wrong answer — explain why the retrieval failed

→ `reports/rag-demo-service.md`

---

[← Block 4: Structured Output](../../03-llm-apis/04-structured-output/index.md) | [Block 6: Advanced RAG →](../06-advanced-rag/index.md)
