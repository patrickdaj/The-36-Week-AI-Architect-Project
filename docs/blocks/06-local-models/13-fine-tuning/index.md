# 🏠 Block 7: Fine-Tuning

[← Block 12: Running Local](../12-running-local/index.md) | [Block 14: Eval & Deploy →](../14-eval-and-deploy/index.md)

> *"Fine-tuning isn't teaching the model new facts — it's teaching it your voice, your format, and your judgment."*

**Quick Reference:** [→ Block 7 Quick Ref](quick-ref.md)

---

## Before You Start Block 13

~1 hour of video + skim the docs:

- 📺 [DeepLearning.AI — Finetuning Large Language Models](https://www.deeplearning.ai/short-courses/finetuning-large-language-models/) — free, ~1 hour, covers when to fine-tune vs. prompt vs. RAG
- 📖 [Hugging Face — Fine-tune a pretrained model](https://huggingface.co/docs/transformers/training) — single focused page, the mechanics of fine-tuning with Transformers
- 📖 [Unsloth Documentation](https://docs.unsloth.ai/) — skim the quickstart, you'll use this for QLoRA training

**Setup:** You'll need a GPU. Options:
- **Google Colab** (free tier T4 GPU) — recommended
- **Local** if you have an NVIDIA GPU with 8+ GB VRAM
- **Apple Silicon** with MLX (experimental but works)

---

### Session 48: Create Your Training Dataset

**Skill:** The dataset is 90% of fine-tuning success. Learn to create high-quality instruction-response pairs for your domain.

**Build:** Create `training-data/create_dataset.py`:
- Generate 200+ instruction-response pairs for security tasks:
  - Config review: input=config, output=findings
  - Incident triage: input=alert, output=assessment
  - Vulnerability analysis: input=CVE, output=risk assessment
  - Network troubleshooting: input=problem, output=diagnosis
- Sources for creation:
  - Manually write 50 high-quality examples
  - Use your existing tools' outputs as seeds
  - Use a strong model (GPT-4/Claude) to generate additional examples
  - Use a strong model to validate/improve your manual examples
- Format: JSON lines, each with `instruction`, `input`, `output`
- Quality control: review every example, remove low quality

| Component | Task |
|-----------|------|
| Build | `training-data/create_dataset.py` + `security_qa.jsonl` |
| Key | 200+ examples, diverse tasks, quality validation |

> 📖 **Read:** [Hugging Face — Creating Training Datasets](https://huggingface.co/docs/datasets/)

---

### Session 49: QLoRA Fine-Tuning with Unsloth

**Skill:** Fine-tune a 7B model on your dataset using QLoRA (quantized low-rank adaptation) — the most efficient method that runs on free GPUs.

**Build:** Create `fine-tune/train.py` (Google Colab notebook or local script):
- Load base model: Llama 3.1 8B or Mistral 7B
- Apply QLoRA: 4-bit quantization + low-rank adapters
- Train on your security dataset
- Hyperparameters: learning rate, epochs, LoRA rank (start with defaults)
- Monitor: training loss, validation loss, GPU memory usage
- Save: the LoRA adapter weights (small, ~100MB vs. full model ~16GB)

| Component | Task |
|-----------|------|
| Build | `fine-tune/train.py` — QLoRA fine-tuning script |
| Key | Unsloth, QLoRA, training monitoring, adapter saving |

> 📖 **Read:** [Unsloth — Fine-tuning Guide](https://docs.unsloth.ai/) — step by step
>
> 📖 **Read:** [Hugging Face — PEFT](https://huggingface.co/docs/peft/) — the library powering LoRA

---

### Session 50: Merge and Convert

**Skill:** Merge LoRA adapters back into the base model and convert to GGUF format for Ollama.

**Build:** Create `fine-tune/export.py`:
- Merge LoRA adapter with base model
- Convert to GGUF format (Ollama's native format)
- Quantize to Q4_K_M (good quality/size balance)
- Create Ollama modelfile pointing to your GGUF
- Register with Ollama: `ollama create security-analyst -f Modelfile`

| Component | Task |
|-----------|------|
| Build | `fine-tune/export.py` — merge, convert, register |
| Test | Run your fine-tuned model in Ollama |

---

### Session 51: A/B Testing Fine-Tuned vs. Base

**Skill:** Is your fine-tuned model actually better? Measure it.

**Build:** Create `fine-tune/eval_ab.py`:
- Use your benchmark from Session 45
- Run identical tests on: base model, fine-tuned model, GPT-4 (as ceiling)
- Blind evaluation: shuffle outputs, score without knowing which model produced which
- Metrics: accuracy, relevance, format compliance, hallucination rate
- Generate comparison report

| Component | Task |
|-----------|------|
| Build | `fine-tune/eval_ab.py` — blind A/B evaluation |
| Output | Comparison report: base vs. fine-tuned vs. GPT-4 |

---

### ⏰ Project 14: Fine-Tuning Retrospective

Write up:
1. What improved with fine-tuning? What didn't?
2. Was the dataset quality sufficient? What would you add?
3. Cost analysis: time to create dataset + training time vs. improvement gained
4. Would you fine-tune for production? When would cloud API be better?

→ `reports/fine-tuning-service.md`

---

[← Block 12: Running Local](../12-running-local/index.md) | [Block 14: Eval & Deploy →](../14-eval-and-deploy/index.md)
