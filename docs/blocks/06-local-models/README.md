# 🏠 Unit 6 — Local Models & Fine-Tuning

<small>Weeks 21–26 · 3 blocks</small>

[→ Start Block 12](12-running-local/index.md)

---

Every tool you've built so far sends data to someone else's servers. That's fine for many use cases — but for sensitive security data, classified infrastructure details, or air-gapped environments, you need models that run on your hardware.

This unit takes you from "download a model" to "fine-tune a domain-specific model and serve it via API." You'll run Llama, Mistral, and Phi locally through Ollama, benchmark them on your security tasks, then fine-tune a 7B model with your own security Q&A data using QLoRA on free Colab GPUs.

**Intuition over math:** Transformers = "which words should pay attention to which." Fine-tuning = "teaching it your specialty without rewriting the brain." LoRA = "adding a small adapter instead of changing every weight." That's the mental model.

---

## What You'll Build

- A **local model stack** with Ollama running multiple models
- **Benchmarks** comparing local models on your security tasks
- **API compatibility layer** — swap your earlier tools from cloud to local models
- A **fine-tuned security model** trained on your domain data
- An **evaluation pipeline** comparing fine-tuned vs. base model quality

---

## Blocks

| Block | Topic | Weeks |
|-------|-------|-------|
| [21–22: Running Local](12-running-local/index.md) | Ollama setup, model comparison, API compatibility | 21–22 |
| [23–24: Fine-Tuning](13-fine-tuning/index.md) | Dataset creation, QLoRA with Unsloth, training on Colab | 23–24 |
| [25–26: Eval & Deploy](14-eval-and-deploy/index.md) | Evaluation metrics, model serving, local API deployment | 25–26 |
