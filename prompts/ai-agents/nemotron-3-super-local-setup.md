# 🟢 Nemotron 3 Super Local Setup (120B Open-Weight)

> Set up NVIDIA's Nemotron 3 Super — a 120B parameter open-weight model optimized for agentic AI — for local development and testing.

## The Prompt

```markdown
You are an AI infrastructure engineer. Help me set up NVIDIA's Nemotron 3 Super (120B parameters, mixture-of-experts, open-weight) for local development.

## Context
- Nemotron 3 Super: 120B parameter open-weight model (March 2026)
- Architecture: Mixture-of-Experts (MoE) — only activates relevant experts per query
- Optimized for: agentic AI, tool use, multi-step reasoning
- License: Open-weight (check NVIDIA's license for commercial use)
- 5x performance boost over previous Nemotron models

## My Setup
- **GPU**: [YOUR GPU — e.g., RTX 4090 24GB / A100 40GB / H100 80GB]
- **RAM**: [YOUR RAM — e.g., 32GB / 64GB / 128GB]
- **Use case**: [coding assistant | agent backend | RAG pipeline | research]

## Tasks

### 1. Assess Hardware Fit
Based on my GPU/RAM, recommend:
- Which quantization level I can run (Q4, Q5, Q6, Q8, FP16)
- Expected tokens/second at that quantization
- Whether I need model sharding across GPUs

### 2. Installation
```bash
# Option A: via Ollama (easiest)
ollama pull nemotron-3-super

# Option B: via llama.cpp (most control)
# Download GGUF from HuggingFace
# Configure for my specific GPU

# Option C: via vLLM (best for serving)
pip install vllm
vllm serve nvidia/nemotron-3-super --quantization awq
```

### 3. Quick Validation
Provide 3 test prompts that showcase Nemotron 3 Super's strengths:
- Multi-step reasoning task
- Tool-use / function-calling task  
- Code generation task

### 4. Compare with Alternatives
Show me a quick comparison for my use case:
| Model | Size | Speed | Quality | Cost |
|-------|------|-------|---------|------|
| Nemotron 3 Super | 120B | ? | ? | Free |
| GPT-5.4 | API | Fast | High | $$ |
| Claude Opus 4.6 | API | Fast | High | $$ |
| Qwen 3.5 | Various | ? | ? | Free |
```

## Example Output

For an RTX 4090 (24GB):
- **Quantization**: Q4_K_M (fits in 24GB VRAM)
- **Speed**: ~15-20 tokens/sec
- **Best for**: Local coding assistant, agent prototyping
- **Not ideal for**: Production serving at scale

## What You Get (Free)

✅ Hardware assessment and quantization guide
✅ Three installation paths (Ollama, llama.cpp, vLLM)
✅ Validation prompts
✅ Model comparison table

## 🔒 Pro Version Includes

The **[AI Dev Toolkit Pro](https://dohko04.github.io/ai-dev-toolkit/)** ($9) includes:

- 🚀 **Production serving pipeline** — vLLM + NGINX + auto-scaling config
- 🔄 **Multi-model routing** — Route between Nemotron local + cloud APIs based on task complexity
- 💰 **Cost optimizer** — Calculate exact savings vs API calls for your usage patterns
- 🧪 **Benchmark suite** — Compare Nemotron vs cloud models on YOUR specific tasks
- 🏗️ **Agentic AI pipeline** — Full agent system using Nemotron as the backbone

---

*Part of [awesome-ai-prompts-for-devs](https://github.com/dohko04/awesome-ai-prompts-for-devs) — Production-ready AI prompts for developers*
