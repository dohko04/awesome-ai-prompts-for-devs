# 🧠 Agent Memory System Designer

Design persistent memory for AI agents — the missing piece that turns a chatbot into a true autonomous agent. In 2026, agent memory is becoming a first-class primitive, not a hack.

## The Prompt

```
You are an AI Agent Memory Architect. I need to design a memory system for an autonomous AI agent.

Agent purpose: {AGENT_PURPOSE}
Framework: {FRAMEWORK} (e.g., LangGraph, CrewAI, OpenClaw, custom)
Runtime: {RUNTIME} (e.g., long-running daemon, session-based, cron-triggered)

Design a complete memory system:

1. **Memory Types**: For this agent, define which memory layers it needs:
   - **Working Memory**: What context stays in the current session (token budget: ~4K tokens max)
   - **Short-Term Memory**: What persists between turns but resets daily (format: structured markdown or JSON)
   - **Long-Term Memory**: What survives indefinitely (curated knowledge, learned preferences, key decisions)
   - **Episodic Memory**: Specific events/interactions worth remembering (with timestamps)

2. **Storage Strategy**:
   - File-based (markdown files, JSON) — simple, version-controllable
   - Vector DB (embeddings for semantic search) — when and why
   - Hybrid approach — recommend the right mix
   - Include specific file paths and naming conventions

3. **Memory Operations**: Define how the agent:
   - **Writes**: When does it save to memory? What triggers a write?
   - **Reads**: How does it load context at session start? Priority order?
   - **Consolidates**: How does it merge daily notes into long-term memory?
   - **Forgets**: What gets pruned and when? (token budget management)

4. **Memory Schema**: Output a concrete schema for each memory type:
   - Working memory template
   - Daily log template (e.g., `memory/YYYY-MM-DD.md`)
   - Long-term memory structure (`MEMORY.md`)
   - Index/manifest file if needed

5. **Implementation**: Provide:
   - Pseudocode for the memory lifecycle (boot → read → work → write → shutdown)
   - Specific prompts/instructions to embed in the agent's system prompt
   - Edge cases: what happens when memory is corrupted, too large, or contradictory?

Output as a complete technical spec I can implement today.
```

## Example Usage

> "A customer support agent that remembers user preferences, past tickets, and company policy updates — running as a LangGraph workflow triggered by new tickets"

## When to Use

- Building agents that need to remember context across sessions
- Designing AI assistants with personalization
- Any autonomous agent that runs on a schedule (cron, heartbeat)

## Pro Tips

- Start with file-based memory — it's debuggable and version-controllable
- Keep working memory under 4K tokens to leave room for actual work
- Consolidate daily logs weekly, not in real-time (saves tokens)

---

> 💡 **Want more?** This is 1 of 7 free agent prompts. The [**Full AI Dev Toolkit**](https://ai-dev-toolkit-five.vercel.app) includes 25+ agent prompts with complete memory implementations, multi-agent orchestration patterns, and production-ready agent templates — all for **$9 USD**.
