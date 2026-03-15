# NVIDIA N1 Laptop AI Dev Setup

> Get ready for NVIDIA's ARM-based N1/N1X laptop CPUs — optimize your AI dev workflow for local inference on NVIDIA's first Windows laptop chips.

## The Prompt

```
You are an AI development environment architect specializing in ARM-based local inference.

NVIDIA is launching the N1 and N1X laptop CPUs — ARM-based chips designed to power Windows laptops with integrated AI acceleration. I need to prepare my development environment.

## Context
- NVIDIA N1: entry-level ARM laptop CPU with NPU
- NVIDIA N1X: high-performance variant for creator/dev laptops
- Both target Windows on ARM ecosystem
- Designed to work alongside NVIDIA GPUs for hybrid inference
- Expected to compete with Apple M-series and Qualcomm Snapdragon X

## My Current Setup
- [YOUR_CURRENT_LAPTOP]
- [YOUR_PRIMARY_LANGUAGE: e.g., Python, TypeScript]
- [YOUR_AI_WORKLOADS: e.g., local LLMs, image gen, RAG pipelines]

## Tasks

1. **Compatibility Audit**: List which of my current AI tools/frameworks support ARM-native Windows:
   - Python (ARM64 wheels availability)
   - CUDA/cuDNN on ARM
   - Docker for ARM64 Windows
   - Key ML libraries (PyTorch, ONNX Runtime, llama.cpp)

2. **Local Inference Setup Plan**: Create a migration checklist for running models locally on N1/N1X:
   - ONNX Runtime optimization for ARM NPU
   - llama.cpp ARM NEON optimizations
   - Model quantization targets (INT4/INT8 for NPU)
   - Memory management (unified memory architecture)

3. **Hybrid GPU+NPU Pipeline**: Design a workflow that routes:
   - Small models → NPU (always-on, power efficient)
   - Medium models → CPU inference (N1X advantage)
   - Large models → discrete GPU (if available)
   - Show the routing decision tree

4. **Dev Environment Checklist**: What to install day-one:
   - Windows ARM64 dev tools
   - NVIDIA AI SDK for N1
   - Recommended VS Code extensions for ARM debugging
   - Container setup (Docker ARM64 vs WSL2)

Output as a structured migration plan with priority levels (P0 = do now, P1 = week 1, P2 = month 1).
```

## When to Use
- Preparing for NVIDIA N1/N1X laptop launch (GTC 2026)
- Setting up local AI inference on ARM Windows
- Evaluating NVIDIA laptop CPUs vs Apple M-series for AI dev

## Example Output Structure
```
## N1/N1X Migration Plan

### P0 — Pre-Launch (Do Now)
- [ ] Audit Python packages for ARM64 wheel availability
- [ ] Test ONNX Runtime ARM optimizations with your models
- [ ] Benchmark current workloads to establish baselines

### P1 — Week 1 (Post-Launch)
- [ ] Install NVIDIA N1 AI SDK
- [ ] Configure hybrid NPU/GPU routing
- [ ] Migrate top 3 inference workloads

### P2 — Month 1 (Optimization)
- [ ] Profile power vs performance tradeoffs
- [ ] Implement model quantization pipeline
- [ ] Set up CI/CD for ARM64 targets
```

## Limitations (Free Version)
- Basic migration checklist only
- No automated compatibility scanner
- No benchmark suite or cost comparison calculator

---

> 💡 **Want the full N1 Production Pipeline?** The [AI Dev Toolkit PRO](https://ai-dev-toolkit-five.vercel.app) ($9) includes automated ARM compatibility scanner, benchmark suite, multi-device routing optimizer, and CI/CD templates for ARM64 targets.
