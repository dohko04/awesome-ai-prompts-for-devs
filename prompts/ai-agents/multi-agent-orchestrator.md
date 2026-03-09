# Multi-Agent Orchestration Planner (Free)

> Design multi-agent systems with clear roles, communication patterns, and tool assignments. Works with CrewAI, LangGraph, OpenAI Swarm, or custom frameworks.

## The Prompt

```
You are a multi-agent systems architect. Help me design an agent orchestration for my use case.

USE CASE: {{use_case}}
FRAMEWORK PREFERENCE: {{crewai|langgraph|swarm|custom}}
AVAILABLE TOOLS/APIS: {{tools_list}}

Design the following:

## 1. Agent Definitions
For each agent:
- Role name and one-line purpose
- System prompt (concise, focused)
- Tools assigned
- Input/output contract

## 2. Orchestration Pattern
Choose and justify one:
- Sequential pipeline
- Hierarchical (manager + workers)  
- Collaborative (peer-to-peer)
- Event-driven

## 3. Communication Flow
- Diagram the data flow between agents (text-based)
- Define handoff conditions
- Error handling: what happens when an agent fails?

Limit to 3-5 agents maximum. Simpler is better.
```

## When to Use

- Building AI-powered workflows (content pipelines, data processing, code review bots)
- Replacing complex single-prompt chains with specialized agents
- Designing systems where different LLMs handle different tasks

---

> 🔥 **Want production-ready agent templates?** The [AI Dev Toolkit](https://ai-dev-toolkit-five.vercel.app) ($9) includes:
> - 6 complete agent architectures with code (CrewAI + LangGraph)
> - Ready-to-run agent configs for: code review, content pipeline, data analysis, customer support, DevOps automation, research assistant
> - MCP integration patterns for agent tool use
> - Evaluation framework for testing agent performance
> - Common failure patterns and how to fix them
