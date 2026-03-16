# 🧠 Hindsight Agent Memory Setup

> Quick-start prompt for adding persistent learning memory to your AI agents using Hindsight (vectorize-io). Agents that learn, not just remember.

## The Prompt

```
You are an AI agent memory architect. Help me integrate Hindsight (vectorize-io) 
into my existing AI agent to give it persistent, learning memory.

My agent framework: [Pydantic AI / CrewAI / LangGraph / custom]
My LLM provider: [OpenAI / Anthropic / Ollama local]

Guide me through:

1. INSTALLATION — pip install hindsight-all plus framework-specific SDK
2. LLM WRAPPER — Replace my current LLM client with Hindsight's 2-line wrapper 
   so memories are stored/retrieved automatically on every LLM call
3. MEMORY TYPES — Configure which memories to track:
   - User preferences and context
   - Task outcomes (success/failure patterns)
   - Domain knowledge learned from conversations
4. LOCAL SETUP — If using Ollama, configure HINDSIGHT_API_LLM_PROVIDER=ollama
5. VERIFICATION — Test that memories persist across process restarts

Output a working integration script I can run immediately.

Constraints:
- Prioritize the LLM Wrapper approach (simplest, 2 lines of code)
- Include error handling for memory retrieval failures
- Show how to verify memories are actually being stored
```

## What You Get

- Working Hindsight integration in ~5 minutes
- Agents that learn user preferences over time
- Memory that survives restarts (no more "who are you?" every session)
- Local-first option with Ollama (no API keys needed)

## Example Use Cases

- Customer support agent that remembers past issues
- Coding assistant that learns your style preferences
- Personal assistant that builds knowledge over conversations

---

### 🔥 Want the full production pipeline?

The **[AI Dev Toolkit](https://ai-dev-toolkit-five.vercel.app)** includes the complete **Hindsight Agent Memory Production Pipeline** with:
- Multi-framework integration configs (Pydantic AI, CrewAI, LangGraph, OpenClaw)
- Memory quality scoring and pruning strategies
- Knowledge graph visualization setup
- Cost optimization for memory-heavy agents
- Team rollout playbook with monitoring dashboards

**168+ production-ready AI dev resources for $9** → [Get the toolkit](https://ai-dev-toolkit-five.vercel.app)
