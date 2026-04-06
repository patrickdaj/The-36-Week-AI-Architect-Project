# ⚡ Block 23–24 Quick Reference — Fine-Tuning

## Sessions at a Glance

| # | Session | You Build | Key Tools |
|---|---------|-----------|-----------|
| 48 | Create Your Training Dataset | `training-data/create_dataset.py` + `security_qa.jsonl` | Hugging Face Datasets, JSONL |
| 49 | QLoRA Fine-Tuning with Unsloth | `fine-tune/train.py` | Unsloth, QLoRA, PEFT |
| 50 | Merge and Convert | `fine-tune/export.py` + Ollama Modelfile | llama.cpp, GGUF, Ollama |
| 51 | A/B Testing Fine-Tuned vs. Base | `fine-tune/eval_ab.py` | Blind evaluation, metrics |
| S14 | Fine-Tuning Retrospective | `reports/fine-tuning-service.md` | Written analysis |

## Setup Commands

```bash
# Google Colab (recommended) — run these in a Colab notebook:
!pip install unsloth "huggingface_hub[cli]" datasets trl peft

# Local (NVIDIA GPU with CUDA):
pip install unsloth datasets trl peft bitsandbytes

# Apple Silicon (MLX alternative):
pip install mlx-lm datasets
```

## Key Files

```
training-data/
├── create_dataset.py       # Dataset generation/curation
├── security_qa.jsonl        # Training data (200+ examples)
└── validate.py              # Quality check

fine-tune/
├── train.py                 # QLoRA training script
├── export.py                # Merge LoRA + convert to GGUF
├── eval_ab.py               # A/B comparison evaluation
└── Modelfile                # Ollama model definition

reports/
└── fine-tuning-service.md   # Service retrospective
```
