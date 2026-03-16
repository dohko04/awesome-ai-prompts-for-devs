# 🧠 OpenViking Agent Memory Setup

> **FREE** — Set up filesystem-based hierarchical memory for AI agents using OpenViking (volcengine).

## What This Does
OpenViking replaces flat RAG stores with a filesystem paradigm for agent context. It organizes memory, resources, and skills in L0/L1/L2 tiers that load on-demand — reducing token consumption while keeping agents contextually aware.

## The Prompt

```
You are an AI agent memory architect. Help me set up OpenViking as my agent's context database.

## My Agent Setup
- Agent framework: [OpenClaw / LangGraph / CrewAI / custom]
- Current memory: [none / vector DB / flat files / Redis]
- Agent count: [single / multi-agent team]
- Primary use case: [coding assistant / research / automation / customer support]

## Tasks

### 1. Design Context Hierarchy
Create an L0/L1/L2 tiered context structure for my use case:
- **L0 (Always loaded):** Core identity, system prompts, active task state
- **L1 (Session-scoped):** Recent conversation, working files, current project
- **L2 (On-demand retrieval):** Historical memory, reference docs, skill library

Output a directory tree showing exactly what goes where.

### 2. Basic Integration
Generate a minimal working setup:
- Docker compose for OpenViking server
- Connection config for my agent framework
- 3 example context entries (one per tier)
- A test script that writes, retrieves, and prunes context

### 3. Memory Lifecycle Rules
Define rules for:
- When to promote L2 → L1 (relevance triggers)
- When to demote L1 → L2 (staleness threshold)
- When to prune L2 entirely (max age/size)
- Token budget per tier

Keep it practical — I want this running in under 30 minutes.
```

## Example Output Structure
```
agent-context/
├── L0-core/
│   ├── identity.md          # Agent persona + rules
│   ├── active-task.json     # Current task state
│   └── tools.yaml           # Available tool configs
├── L1-session/
│   ├── conversation/        # Recent messages
│   ├── working-files/       # Files being edited
│   └── project-state.json   # Current project context
└── L2-archive/
    ├── memory/              # Historical conversations
    ├── skills/              # Learned patterns
    └── references/          # Documentation cache
```

## When to Use This
- Your agent forgets context between sessions
- RAG retrieval feels random or noisy
- You're hitting token limits with flat context dumps
- You need structured memory for multi-agent teams

## Limitations (Free Version)
This covers single-agent setup with basic tiering. For multi-agent shared memory, automatic promotion/demotion pipelines, cost optimization, and production monitoring → see the **PRO version** in [AI Dev Toolkit](https://ai-dev-toolkit-five.vercel.app).

---
*Part of [Awesome AI Prompts for Devs](https://github.com/dohko04/awesome-ai-prompts-for-devs) — Production-ready prompts for AI-powered development.*
