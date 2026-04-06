# 🧠 Block 6: Advanced RAG

[← Block 5: Vectors & Retrieval](../05-vectors-and-retrieval/index.md) | [Block 7: CVE Impact Analyzer →](../07-cve-impact-analyzer/index.md)

> *"The difference between a RAG demo and a RAG system is handling the cases where retrieval fails gracefully."*

**Quick Reference:** [→ Block 6 Quick Ref](quick-ref.md)

---

## Before You Start Block 6

- 📺 [DeepLearning.AI — Building and Evaluating Advanced RAG](https://www.deeplearning.ai/short-courses/building-evaluating-advanced-rag/) — free, ~1 hour
- 📖 [LangChain — Advanced RAG Techniques](https://python.langchain.com/docs/tutorials/rag/) — query transformation, reranking

---

### Session 25: Hybrid Search — Keywords + Semantics

**Skill:** Combine keyword search (BM25) with semantic search (embeddings). Neither alone is sufficient — hybrid catches what the other misses.

**Build:** Create `05-hybrid-search.py`:
- Implement BM25 keyword search alongside ChromaDB semantic search
- Reciprocal Rank Fusion (RRF) to merge the two result sets
- Test: queries where keyword wins ("CVE-2024-1234"), where semantic wins ("how to handle compromised credentials"), and where hybrid beats both
- Compare retrieval quality across all three approaches on 10 test queries

| Component | Task |
|-----------|------|
| Build | `05-hybrid-search.py` — hybrid keyword + semantic search |
| Key | BM25, RRF, quality comparison |

> 📖 **Read:** [Pinecone — Hybrid Search](https://www.pinecone.io/learn/hybrid-search-intro/)

---

### Session 26: Source Citation and Provenance

**Skill:** Every RAG answer must show its sources. Build citation into the pipeline so users can verify and trust the output.

**Build:** Upgrade your RAG pipeline to `06-cited-rag.py`:
- Every answer includes numbered source citations: `[1] security-policy.md, section 3.2`
- Clickable references to the original document chunk
- Confidence scoring: how relevant was each retrieved chunk?
- "No relevant context found" handling — the system says "I don't know" when it should

| Component | Task |
|-----------|------|
| Build | `06-cited-rag.py` — RAG with source citations and confidence scores |
| Key | Source tracking through pipeline, citation formatting |

---

### Session 27: Evaluation — Is Your RAG Actually Good?

**Skill:** Systematically evaluate RAG quality. Without evaluation, you're just vibes-checking.

**Build:** Create `07-rag-eval.py`:
- Create an evaluation dataset: 20 questions with known correct answers and source documents
- Metrics:
  - **Retrieval quality:** Did the right chunks come back? (recall@k, precision@k)
  - **Answer quality:** Is the generated answer correct? (compare to ground truth)
  - **Faithfulness:** Does the answer stay within the retrieved context? (no hallucination)
- Run evaluation, generate a report with scores
- Identify: worst-performing questions and why retrieval failed

| Component | Task |
|-----------|------|
| Build | `07-rag-eval.py` — RAG evaluation framework |
| Key | Evaluation dataset, retrieval metrics, faithfulness checking |

> 📖 **Read:** [RAGAS Documentation](https://docs.ragas.io/) — the standard RAG evaluation framework

---

### Session 28: Document Ingestion Pipeline

**Skill:** Build a robust pipeline that ingests documents from multiple formats and keeps the vector store updated.

**Build:** Create `08-ingestion-pipeline.py`:
- Ingest from: Markdown, PDF, plain text, HTML
- Metadata extraction: document title, section, date, author, tags
- Deduplication: don't re-embed documents that haven't changed
- Incremental updates: add new docs without re-processing the whole corpus
- CLI interface: `python 08-ingestion-pipeline.py --source ./docs --collection security-kb`

| Component | Task |
|-----------|------|
| Build | `08-ingestion-pipeline.py` — multi-format document ingestion |
| Key | Format parsing, metadata, deduplication, incremental updates |

---

### ⏰ Project 7: Security Knowledge Base v1

Deploy your RAG system as a working security knowledge base:
1. Load 20+ real documents (sanitized policies, runbooks, vendor docs, or synthesized equivalents)
2. Query it with 10 realistic questions from your actual job
3. Grade each answer: correct, partially correct, wrong, correctly refused
4. Write architecture notes: what would you change for production?

→ `reports/security-kb-service.md`

---

[← Block 5: Vectors & Retrieval](../05-vectors-and-retrieval/index.md) | [Block 7: CVE Impact Analyzer →](../07-cve-impact-analyzer/index.md)
