# 🧠 Unit 4 — Embeddings & RAG

<small>Weeks 9–13 · 3 blocks</small>

[→ Start Block 5](05-vectors-and-retrieval/index.md)

---

RAG — Retrieval-Augmented Generation — is why AI can "know" things it wasn't trained on. Your security policies, your network documentation, your incident runbooks — an LLM doesn't know any of it. RAG is how you teach it.

This unit takes you from "what's an embedding?" to building a production-grade RAG system over your security knowledge base. You'll understand the full pipeline — chunking, embedding, vector storage, retrieval, generation — and you'll build a CVE impact analyzer that checks your infrastructure inventory against the NVD.

**Intuition over math:** Embeddings are "meaning coordinates." Similar meanings = nearby points. Cosine similarity = "do these point the same direction?" That's all the math you need.

---

## What You'll Build

- A **security knowledge base** with full RAG pipeline (chunk → embed → store → retrieve → generate)
- **Hybrid search** combining keyword and semantic retrieval
- A **CVE impact analyzer** that cross-references NVD data against your asset inventory
- Source citation — every answer shows which document chunks informed it

---

## Blocks

| Block | Topic | Weeks |
|-------|-------|-------|
| [Block 5: Vectors & Retrieval](05-vectors-and-retrieval/index.md) | Embeddings, ChromaDB, basic RAG pipeline | 9–10 |
| [Block 6: Advanced RAG](06-advanced-rag/index.md) | Hybrid search, reranking, chunking strategies, source citation | 11–12 |
| [Block 7: CVE Impact Analyzer](07-cve-impact-analyzer/index.md) | 🔬 Lab — RAG over asset inventory + NVD data | 13 |
