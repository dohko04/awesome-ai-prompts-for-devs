# 🏗️ Agent Architect

Design multi-agent systems with clear roles, communication patterns, and tool assignments.

## The Prompt

```
You are an AI Agent Architect. I need to build a multi-agent system for: {TASK_DESCRIPTION}

Follow this process:

1. **Agent Decomposition**: Break the task into specialized agent roles. Each agent should have:
   - A clear, single responsibility
   - Defined inputs and outputs
   - Specific tools it needs access to

2. **Communication Pattern**: Recommend one of:
   - Sequential (pipeline): Agent A → Agent B → Agent C
   - Hierarchical (manager): Manager agent delegates to workers
   - Collaborative (mesh): Agents communicate peer-to-peer
   - Hybrid: Mix of the above
   
   Justify your choice for this specific task.

3. **For each agent, define**:
   - Name and role description
   - System prompt (concise, actionable)
   - Tools required (web search, code execution, file I/O, APIs, etc.)
   - Input format and output format
   - Error handling: what happens if this agent fails?

4. **Orchestration Logic**:
   - Entry point and exit conditions
   - State management approach
   - How agents share context
   - Maximum iterations / timeout strategy

5. **Output the design as a structured spec** I can implement in LangGraph, CrewAI, or AutoGen.

Task: {TASK_DESCRIPTION}
Tech stack: {TECH_STACK}
Framework preference: {FRAMEWORK: LangGraph | CrewAI | AutoGen | any}
```

## Example Usage

```
Task: Build a system that monitors GitHub repos for security vulnerabilities, 
      analyzes them, and creates fix PRs automatically.
Tech stack: Python, GitHub API, OpenAI
Framework preference: LangGraph
```

## Tips

- Start with 2-3 agents max. Add complexity only when needed.
- Always include a "supervisor" or "router" agent for systems with 3+ agents.
- Define clear exit conditions to avoid infinite loops.

---

> 🚀 **Need production-ready agent templates?** The [AI Dev Toolkit](https://dohko04.gumroad.com/l/ai-dev-toolkit) ($9) includes pre-built agent systems for code review, documentation, testing, and deployment — ready to plug into your workflow.
