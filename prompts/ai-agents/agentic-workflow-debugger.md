# 🔬 Agentic Workflow Debugger

> When your AI agent goes off the rails — loops, hallucinates tool calls, or silently fails — use this prompt to systematically diagnose and fix the issue. Works with any framework: LangGraph, CrewAI, AutoGen, OpenAI Swarm, or custom implementations.

## The Prompt

```markdown
You are an expert debugger for agentic AI workflows. I have an agent system that isn't working correctly. Help me systematically diagnose and fix it.

## System Description
- **Framework:** [LangGraph | CrewAI | AutoGen | OpenAI Swarm | Custom]
- **Number of agents:** [single | multi-agent with roles]
- **Tools available:** [list the tools/functions agents can call]
- **LLM backbone:** [model name and provider]
- **Orchestration pattern:** [sequential | parallel | hierarchical | graph-based]

## The Problem
[Describe what's going wrong — be specific about the failure mode]

## Failure Mode Analysis — Check Each:

### 1. Infinite Loops & Recursion
- Is the agent calling the same tool repeatedly with identical inputs?
- Is there a missing exit condition in the workflow graph?
- Are two agents delegating back and forth without progress?
→ **Fix pattern:** Add max-iteration guards, state-based exit conditions, or a "progress detector" that halts after N identical states.

### 2. Tool Call Failures
- Is the agent generating malformed tool call arguments?
- Is it hallucinating tool names that don't exist?
- Are tool responses too large, causing context overflow?
→ **Fix pattern:** Add strict argument schemas, validate tool names before execution, truncate/summarize tool outputs.

### 3. Context Window Overflow
- Is the conversation history growing unbounded?
- Are tool responses (e.g., full file contents) bloating the context?
- Is the agent losing track of its objective mid-conversation?
→ **Fix pattern:** Implement sliding window memory, summarize old messages, use a dedicated "state" object instead of raw chat history.

### 4. Planning Failures
- Is the agent skipping steps in a multi-step task?
- Does it misunderstand which tool to use for which subtask?
- Is it confusing roles in a multi-agent setup?
→ **Fix pattern:** Add explicit planning step, use structured output for plans, give each agent a clearer system prompt with examples.

### 5. State Management
- Is shared state being overwritten by concurrent agents?
- Are intermediate results lost between steps?
- Is the agent repeating work it already completed?
→ **Fix pattern:** Use immutable state transitions, add checkpointing, implement a "completed tasks" tracker.

## What I Need
1. **Root cause diagnosis** — which failure mode(s) apply
2. **Trace analysis** — walk through the likely execution path step by step
3. **Specific fixes** — code changes or configuration adjustments
4. **Prevention** — guardrails to add so this doesn't happen again

If you need more information about a specific part of the system, ask targeted questions before diagnosing.
```

## When to Use

- Your LangGraph agent enters an infinite loop between nodes
- CrewAI tasks silently fail or produce garbage output
- Multi-agent systems have agents "talking past each other"
- An agent works for simple inputs but breaks on complex ones
- You're debugging agentic vibe coding sessions that go off track

## Pro Tips

- Always include the **actual error logs or trace** when using this prompt — vague descriptions get vague answers
- The most common issue in 2026 is **context overflow** — agents accumulate too much history
- For multi-agent systems, debug ONE agent at a time by isolating its inputs/outputs
- Use this alongside observability tools (LangSmith, Braintrust, Phoenix) for real traces

---

> 💡 **This is 1 of 100+ battle-tested prompts.** The full AI Dev Toolkit includes agent architecture templates, LangGraph workflow generators, and multi-agent orchestration patterns.
>
> **[Get 100+ prompts like this → AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app)**
