# AMD GPU AI Agent Builder

> **Free sample** — build AI agents on AMD GPUs with open-weight models.
> Full production pipeline with multi-GPU orchestration, ROCm optimization, and fleet deployment → [AI Dev Toolkit PRO ($9)](https://ai-dev-toolkit-five.vercel.app)

## Context
AMD AI DevDay 2026 (March 19) showcased building personal AI agents on AMD GPUs using OpenClaw and open-weight models. With ROCm 6.x maturity and MI300X availability, AMD is now a viable alternative to NVIDIA for agentic AI workloads.

## Quick Setup Prompt

```
You are an AI infrastructure engineer specializing in AMD GPU deployments.

I want to build and run AI agents on AMD hardware.

My setup:
- GPU: [MI300X / MI250 / RX 7900 XTX / Radeon PRO]
- RAM: [X GB]
- Use case: [personal agent / team agents / production inference]
- Models I want to run: [Llama 3.3 / Mistral / Qwen / custom]
- Agent framework: [OpenClaw / LangGraph / CrewAI]

Please generate:

1. **Environment Setup**
   - ROCm version and driver installation commands (Ubuntu/RHEL)
   - Docker container config with AMD GPU passthrough
   - vLLM or TGI configuration optimized for my AMD GPU
   - Memory allocation strategy for my VRAM

2. **Model Deployment**
   - Best quantization for my GPU (AWQ/GPTQ/GGUF)
   - Batch size optimization for agent workloads
   - Multi-model serving (router + specialist pattern)
   - Expected tokens/sec for my hardware

3. **Agent Integration**
   - OpenClaw config for local AMD inference
   - Tool calling setup with function routing
   - Memory/context management for persistent agents
   - Fallback to cloud API when local GPU is saturated

4. **Performance Baseline**
   Generate a benchmark script that measures:
   - Single request latency (p50, p95, p99)
   - Throughput under concurrent agent requests
   - VRAM usage over time
   - Comparison baseline against equivalent NVIDIA setup

5. **Cost Analysis**
   - AMD vs NVIDIA TCO for my workload
   - Cloud (AMD instances) vs on-prem comparison
   - Break-even timeline for hardware purchase
```

## What You Get with PRO
- Multi-GPU orchestration configs (MI300X clusters)
- ROCm optimization scripts with auto-tuning
- Production Kubernetes manifests for AMD GPU pools
- Grafana monitoring dashboards for AMD inference
- Migration guide from NVIDIA CUDA to AMD ROCm
- Cost calculator with real-time cloud pricing

---

*Part of [AI Dev Toolkit](https://ai-dev-toolkit-five.vercel.app) — 220+ production-ready AI developer resources*
