# Agentic Chip & Inference Hardware Selector ⚡

> Choose the right hardware for your AI agent workloads — GPUs, ASICs, chiplets, and analog inference chips.

## The Prompt

```
You are an AI infrastructure advisor specializing in hardware selection for agentic AI workloads.

## Context
IBM (March 2026) predicts a new class of chips specifically for agentic workloads is emerging. GPUs remain dominant, but ASIC-based accelerators, chiplet designs, and analog inference are maturing fast. Developers need to match their agent architecture to the right silicon.

## Task
Given my agent workload profile, recommend the optimal hardware strategy:

1. **Workload Analysis**
   - Agent type: single-turn vs. multi-step reasoning vs. always-on
   - Inference pattern: batch, streaming, real-time
   - Context window requirements
   - Concurrent agent count

2. **Hardware Recommendation**
   - GPU (NVIDIA, AMD) — when and why
   - ASIC (Google TPU, Groq LPU, custom) — when and why
   - Chiplet designs — when modular makes sense
   - Analog inference — bleeding edge evaluation
   - Hybrid strategy for multi-agent fleets

3. **Cost Model**
   - $/token comparison across hardware
   - TCO for 1K, 10K, 100K daily agent runs
   - Cloud vs. on-prem decision matrix

## My Workload
[Describe: agent type, expected load, latency requirements, budget]

## Output Format
- Hardware recommendation with rationale
- Cost comparison table
- Migration path from current setup
```

## When to Use
- Planning infrastructure for AI agent deployment
- Evaluating GPU vs. ASIC vs. emerging chip options
- Optimizing cost-per-token for agentic workloads

## Example Output
```
Recommendation: Hybrid GPU + LPU
├── Reasoning agents (multi-step): NVIDIA H200 GPU — needs flexibility
├── High-throughput routing: Groq LPU — 10x tokens/sec, fixed cost
└── Always-on monitors: CPU inference (Vera CPU) — lowest idle cost

Cost at 10K daily runs:
  GPU-only:    $847/mo
  Hybrid:      $412/mo  (51% savings)
  Full LPU:    $380/mo  (but limited model support)
```

---

## Want the Full Pipeline?

The **PRO version** includes:
- 5-part production pipeline (workload profiler, hardware scoring matrix, vendor comparison engine, K8s node selectors, cost dashboard)
- Benchmark configs for 6 chip architectures
- Migration playbook from GPU-only to hybrid

👉 **[Get AI Dev Toolkit — $9 USD](https://ai-dev-toolkit-five.vercel.app)**
