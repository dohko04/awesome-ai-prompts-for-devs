# NVIDIA Open Model Ecosystem — Developer Starter Guide

> Navigate NVIDIA's unified open-weight model stack (Nemotron, Cosmos, BioNeMo, GR00T, Alpamayo) announced at GTC 2026. Pick the right model for your use case.

## When to Use

- You want to use open-weight models instead of proprietary APIs
- You need on-prem inference for data sovereignty
- You're building agents, robotics, or domain-specific AI
- You want to reduce API costs by self-hosting

## Model Selection Matrix

```yaml
# nvidia-open-model-selector.yaml
use_case_router:
  agentic_ai:
    model: "Nemotron 4"
    variants: ["nemotron-4-340b", "nemotron-4-mini"]
    strengths: "Tool use, multi-step reasoning, agent orchestration"
    deploy: "NIM container, DGX Spark, RTX workstation"
    
  physical_ai_simulation:
    model: "Cosmos 2"
    strengths: "World model, physics simulation, video generation"
    deploy: "NIM container, Omniverse integration"
    
  autonomous_vehicles:
    model: "Alpamayo"
    strengths: "Driving scene understanding, safety-critical decisions"
    deploy: "DRIVE AGX, NIM container"
    
  robotics:
    model: "Isaac GR00T 2"
    strengths: "Manipulation, locomotion, human-robot interaction"
    deploy: "Jetson, Isaac Sim, NIM container"
    
  biomedical:
    model: "BioNeMo"
    strengths: "Protein structure, drug discovery, molecular generation"
    deploy: "DGX, BioNeMo Cloud, NIM container"
    
  general_coding:
    model: "Nemotron 3 Super 120B"
    strengths: "Code generation, reasoning, instruction following"
    deploy: "NIM container, Ollama, vLLM"

decision_tree:
  - question: "Is your task agent-based (tool calling, multi-step)?"
    yes: "Nemotron 4"
    no: "Continue"
  - question: "Does it involve physical world simulation?"
    yes: "Cosmos 2 or GR00T 2"
    no: "Continue"
  - question: "Is it biomedical/drug discovery?"
    yes: "BioNeMo"
    no: "Nemotron 3 Super (general purpose)"
```

## Quick Start: Local Nemotron with NIM

```bash
# Pull and run Nemotron via NIM container
docker pull nvcr.io/nim/nvidia/nemotron-4-mini:latest

docker run -d --gpus all \
  -p 8000:8000 \
  -e NIM_MODEL=nemotron-4-mini \
  nvcr.io/nim/nvidia/nemotron-4-mini:latest

# Test
curl -s http://localhost:8000/v1/chat/completions \
  -H "Content-Type: application/json" \
  -d '{
    "model": "nemotron-4-mini",
    "messages": [{"role": "user", "content": "Write a Python function to parse CSV files"}]
  }' | jq '.choices[0].message.content'
```

## What You Get in the PRO Version

The **NVIDIA Open Model Ecosystem Production Pipeline** includes:
- Multi-model orchestrator (route between Nemotron/Cosmos/BioNeMo based on task)
- NIM container fleet manager with auto-scaling configs
- Cost comparison engine (NVIDIA NIM vs OpenAI/Anthropic per-task)
- Benchmark suite for all 6 model families
- Migration playbook from proprietary APIs to open models

---

🔗 **Get the full pipeline:** [AI Dev Toolkit](https://ai-dev-toolkit-five.vercel.app) — 240+ production-ready AI/dev resources for $9.
