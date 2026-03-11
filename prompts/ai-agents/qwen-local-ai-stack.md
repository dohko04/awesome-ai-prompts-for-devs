# 🏠 Qwen 3.5 On-Device AI Stack Builder

> Configure and deploy Qwen 3.5 Small (0.8B–9B) for local AI development — matching cloud model performance on your laptop.

## The Prompt

```
You are a LOCAL AI DEPLOYMENT ENGINEER specializing in Qwen 3.5 Small series models. Help me set up a complete on-device AI development stack.

## My Setup
- Hardware: {{HARDWARE}} (e.g., MacBook M3 16GB, RTX 4060 laptop, iPhone 16)
- Use case: {{USE_CASE}} (e.g., code completion, chat assistant, RAG, agent)
- Privacy requirements: {{PRIVACY}} (e.g., strict offline, occasional cloud fallback OK)

## What I Need
1. **Model Selection** — Which Qwen 3.5 variant fits my hardware:
   - 0.8B: phones, IoT, ultra-fast inference
   - 3B: laptops with 8GB RAM, good quality/speed balance
   - 9B: 16GB+ RAM, matches models 13× its size

2. **Runtime Setup** — Step-by-step installation:
   - Ollama (easiest): `ollama run qwen3.5:9b`
   - llama.cpp (fastest): GGUF quantization guide
   - vLLM (serving): local API server for multiple clients

3. **Quantization Strategy** — Pick the right precision:
   - Q4_K_M: best quality/size ratio for most hardware
   - Q5_K_M: slightly better quality, ~20% more RAM
   - Q8_0: near-full quality for 32GB+ machines

4. **Integration** — Connect to my dev workflow:
   - VS Code / Cursor: local completion endpoint
   - CLI agent: pipe to Claude Code / aider with local fallback
   - RAG pipeline: embeddings + retrieval with local model

Output a complete setup script and config files I can run immediately.
```

## Quick Start Example

```bash
# Install Ollama + Qwen 3.5 9B (matches GPT-4 class on many benchmarks)
curl -fsSL https://ollama.com/install.sh | sh
ollama pull qwen3.5:9b

# Test it
ollama run qwen3.5:9b "Write a Python function to parse JSON logs"

# Use as local API (OpenAI-compatible)
# Endpoint: http://localhost:11434/v1/chat/completions
```

## Hardware Requirements (Qwen 3.5 Small)

| Model | RAM Needed | Speed (tokens/s) | Best For |
|-------|-----------|-------------------|----------|
| 0.8B Q4 | 1GB | 100+ t/s | Mobile, IoT, autocomplete |
| 3B Q4 | 3GB | 50-80 t/s | Laptop coding assistant |
| 9B Q4 | 6GB | 25-40 t/s | Full dev assistant, RAG |
| 9B Q8 | 10GB | 15-25 t/s | Maximum quality local |

## When to Use

- You need AI coding assistance without sending code to the cloud
- Working on air-gapped or compliance-restricted environments
- You want to cut API costs while maintaining decent quality
- Building edge/mobile AI features

## Limitations (Free Version)

This gives you a working local setup. The **PRO version** in the [AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app) includes:
- Hybrid routing: auto-switch between local Qwen and cloud models based on task complexity
- Performance benchmarking script comparing local vs cloud on YOUR codebase
- Complete RAG pipeline with local embeddings (no API needed)
- Docker compose for team-wide local AI server
- Cost calculator: local GPU cost vs API spend over 30/90/365 days

---

*Part of [Awesome AI Prompts for Devs](https://github.com/dohko04/awesome-ai-prompts-for-devs) — curated by Dohko 🐉*
