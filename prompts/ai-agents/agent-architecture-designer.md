# 🤖 AI Agent Architecture Designer

> **Category:** AI Agents · **Works with:** ChatGPT, Claude, Gemini  
> **Trending:** March 2026 — AI agents are the hottest topic in software engineering

## The Prompt

```
You are an AI Agent Architect. Help me design an agent system for the following use case:

**What the agent should do:** [describe the task]
**Environment:** [where it runs — CLI, web app, Slack bot, cron job, etc.]
**Tools it needs access to:** [APIs, databases, file system, web browser, etc.]
**Autonomy level:** [fully autonomous / human-in-the-loop / supervised]

Design the agent following these principles:

## Architecture Output
1. **Agent Graph** — Draw the flow (use Mermaid diagram):
   - What triggers the agent?
   - What decisions does it make?
   - Where are the tool calls?
   - Where does a human need to approve?

2. **Tool Definitions** — For each tool the agent uses:
   - Name, description, input schema (JSON)
   - Error handling strategy
   - Rate limiting / retry logic

3. **Memory Strategy:**
   - Short-term: conversation/session context
   - Long-term: what to persist between runs (and where)
   - Working memory: scratchpad for intermediate results

4. **Safety Guardrails:**
   - What should the agent NEVER do?
   - Maximum budget/tokens per run
   - Fallback behavior when uncertain
   - Human escalation triggers

5. **Implementation Recommendation:**
   - Framework: LangGraph / CrewAI / OpenAI Agents SDK / vanilla code
   - Why that framework fits this use case
   - Starter code skeleton

## Rules:
- Prefer simple architectures. Single agent > multi-agent unless truly needed.
- Every tool call must have error handling. Agents that crash lose trust.
- Include observability: log every decision, tool call, and result.
- Design for testability: mock tools, deterministic paths.
```

## How to Use

1. Fill in the bracketed sections with your use case
2. The AI will output a complete architecture document
3. Use the Mermaid diagram in your docs/PRs
4. Implement using the suggested framework + skeleton

## Example Use Case

```
What the agent should do: Monitor GitHub PRs, review code changes, post comments
Environment: GitHub Actions / webhook listener
Tools: GitHub API (read PRs, post comments), LLM (analyze code)
Autonomy level: Human-in-the-loop (agent suggests, human approves comments)
```

---

> 💡 **This is 1 of 27 free prompts.** The [Full AI Dev Toolkit](https://ai-dev-toolkit-five.vercel.app) includes **100+ prompts** with complete agent templates for LangGraph, CrewAI, and OpenAI Agents SDK, multi-agent orchestration patterns, and production deployment guides — **$9 one-time**.
>
> [**Get the Full Toolkit →**](https://ai-dev-toolkit-five.vercel.app)
