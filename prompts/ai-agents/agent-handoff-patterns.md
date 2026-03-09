# 🔄 AI Agent Handoff Patterns

> Design reliable agent-to-agent handoffs for multi-agent systems. The #1 failure point in agent architectures isn't the LLM — it's the handoff.

**Works with:** CrewAI, LangGraph, AutoGen, OpenAI Swarm, Claude Code agent teams, custom agent frameworks

## The Problem

You built a multi-agent system. Agent A does research, Agent B writes code, Agent C reviews. Sounds great in theory. In practice, Agent B gets a garbled mess from Agent A because nobody designed the handoff protocol. Sound familiar?

## The Prompt (Free Version)

```markdown
You are an expert AI agent architect specializing in multi-agent systems.

## My Agent System
- **Framework:** [CrewAI / LangGraph / AutoGen / custom]
- **Agents:** [list your agents and their roles]
- **Pipeline:** [describe the flow: Agent A → Agent B → Agent C]
- **Current issue:** [what's breaking in the handoffs]

## Design Handoff Protocols

For each agent-to-agent transition in my pipeline:

### 1. Output Schema
Define a structured output format for the sending agent:
```json
{
  "task_id": "string",
  "status": "complete | partial | failed",
  "output": { ... },
  "confidence": 0.0-1.0,
  "metadata": {
    "tokens_used": "number",
    "sources_consulted": ["..."],
    "warnings": ["..."]
  },
  "next_agent_instructions": "string"
}
```

### 2. Validation Gate
Before the receiving agent starts, validate:
- Required fields are present and non-empty
- Output quality meets minimum threshold
- No contradictions with prior agent outputs
- Context window budget for receiving agent

### 3. Fallback Strategy
If handoff fails:
- Retry with simplified output (compress context)
- Route to human review
- Skip to next viable agent in pipeline
- Log failure pattern for debugging

### 4. Context Compression
The receiving agent doesn't need everything. For each handoff, specify:
- What to PASS (essential for next task)
- What to STORE (save to memory/DB, not in context)
- What to DROP (intermediate reasoning, not needed)

Provide concrete code examples for my specific framework.
```

## Usage Example

### Input
```
Framework: LangGraph
Agents: Researcher (web search), Planner (task breakdown), Coder (implementation)
Pipeline: Researcher → Planner → Coder
Issue: Coder receives too much raw research data and runs out of context
```

### Output (what the prompt generates)

```python
# LangGraph handoff schema
from pydantic import BaseModel
from typing import List, Optional

class ResearchHandoff(BaseModel):
    """Researcher → Planner handoff"""
    task_id: str
    findings: List[str]         # Max 5 key findings, 1 sentence each
    recommended_approach: str    # 2-3 sentences
    relevant_urls: List[str]    # Max 3 reference URLs
    confidence: float
    
class PlannerHandoff(BaseModel):
    """Planner → Coder handoff"""
    task_id: str
    steps: List[dict]           # {step: str, files: [str], est_lines: int}
    tech_decisions: dict        # {decision: rationale}
    constraints: List[str]      # Hard requirements
    context_budget: int         # Max tokens for coder context
```

## Key Principles

| Principle | Why It Matters |
|-----------|---------------|
| **Schema-first** | Structured data > free text between agents |
| **Compress aggressively** | Each handoff should lose 60-80% of tokens |
| **Validate before accepting** | Bad input = bad output, every time |
| **Fail fast** | Better to stop than propagate garbage |
| **Log everything** | Handoff logs are your #1 debugging tool |

---

## 🚀 Full Toolkit Version

The complete **Agent Handoff Patterns** system in the [AI Dev Toolkit](https://ai-dev-toolkit-five.vercel.app) includes:

- **8 handoff pattern templates** — for every common agent topology (chain, fan-out, fan-in, supervisor, debate)
- **Framework-specific implementations** — ready-to-use code for CrewAI, LangGraph, AutoGen, and Swarm
- **Handoff debugging prompt** — diagnose exactly where your multi-agent pipeline breaks
- **Context budget calculator** — automatically allocate context windows across agent chains
- **Agent communication protocol** — standardized message format that works across frameworks
- **Real-world examples** — 4 complete multi-agent systems with production-grade handoffs

[**Get the Full Toolkit (100+ prompts) → $9**](https://ai-dev-toolkit-five.vercel.app)

---

*Part of [Awesome AI Prompts for Devs](https://github.com/dohko04/awesome-ai-prompts-for-devs) by [Dohko](https://github.com/dohko04)*
