# NVIDIA Foundry Local — Quick Setup Guide

> **GTC 2026 Keynote (March 16):** Jensen Huang announced Foundry Local — run NVIDIA models on-premises with full data sovereignty. No cloud, no API costs, your data never leaves your machine.

## What You Get
Run AI inference locally using NVIDIA's open-weight models. OpenAI-compatible API — just change your `base_url`.

## Quick Start

```bash
# 1. Check your GPU
nvidia-smi --query-gpu=name,memory.total --format=csv,noheader

# 2. Deploy with Docker
docker run -d --gpus all \
  -p 8000:8000 \
  -e FOUNDRY_MODEL=nemotron-4-70b-instruct \
  nvcr.io/nvidia/foundry-local:latest

# 3. Use it (OpenAI-compatible!)
curl http://localhost:8000/v1/chat/completions \
  -H "Content-Type: application/json" \
  -d '{"model":"nemotron","messages":[{"role":"user","content":"Hello!"}]}'
```

## Python — Drop-in Replacement

```python
from openai import OpenAI

# Just change base_url — all your existing code works
client = OpenAI(base_url="http://localhost:8000/v1", api_key="local")

response = client.chat.completions.create(
    model="nemotron",
    messages=[{"role": "user", "content": "Review this code for security issues..."}]
)
print(response.choices[0].message.content)
```

## Model Sizing Guide

| Model | GPU Needed | Best For |
|-------|-----------|----------|
| nemotron-mini-4 | RTX 4060 (8GB) | Fast classification, routing |
| nemotron-4-70b | A100 80GB | General tasks, code review |
| nemotron-4-340b | DGX Spark | Complex reasoning, planning |

## Why Go Local?
- **$0 API costs** after hardware
- **Data never leaves your machine** (HIPAA, SOC2, GDPR ready)
- **No rate limits** — your GPU, your rules
- **Works offline** — no internet required

---

> 🔒 **Want the full pipeline?** The PRO version includes: infrastructure readiness scanner, Docker Compose production configs, data governance & compliance YAML, cloud-vs-local cost calculator, and Prometheus/Grafana monitoring dashboard.
>
> **[Get AI Dev Toolkit — $9](https://ai-dev-toolkit-five.vercel.app)**
