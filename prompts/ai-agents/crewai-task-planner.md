# 🚢 CrewAI Task Planner

Generate complete CrewAI crew configurations with agents, tasks, tools, and execution flow.

## The Prompt

```
You are a CrewAI expert. Generate a complete crew configuration for: {GOAL}

Output a working Python implementation with:

1. **Agents** (use @agent decorator pattern):
   - role: specific job title
   - goal: what this agent optimizes for
   - backstory: context that shapes behavior (1-2 sentences)
   - tools: list of tools this agent can use
   - allow_delegation: true/false with reasoning

2. **Tasks** (use @task decorator pattern):
   - description: clear, actionable instruction
   - expected_output: exact format of the result
   - agent: which agent handles this
   - context: list of tasks this depends on (for data flow)

3. **Crew Configuration**:
   - process: sequential or hierarchical (justify choice)
   - manager_llm: if hierarchical
   - verbose: true for debugging

4. **Include**:
   - All necessary imports
   - Tool definitions (use crewai_tools where possible)
   - A main() function that kicks off the crew
   - Environment variable handling for API keys

Goal: {GOAL}
Available tools needed: {TOOLS: e.g., web search, file read/write, API calls}
LLM preference: {LLM: e.g., gpt-4o, claude-sonnet, ollama/llama3}
```

## Example

```
Goal: Research a topic, write a technical blog post, and create social media threads
Tools: web search, file write
LLM: gpt-4o
```

## When to Use

- Rapid prototyping of agent teams
- Learning CrewAI patterns
- Generating boilerplate you can customize

---

> 🔥 **The free version gets you started. The [AI Dev Toolkit](https://dohko04.gumroad.com/l/ai-dev-toolkit) ($9) gets you shipping.** Includes 10+ pre-built crews for real dev workflows: CI/CD agents, code review crews, documentation pipelines, and more.
