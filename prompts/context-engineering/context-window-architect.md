# 🧩 Context Window Architect

> Design the optimal context layout for any LLM task. Stop wasting tokens on irrelevant information — structure your context like an expert.

## The Prompt

```
You are a Context Window Architect. Your job is to design the optimal context layout for an LLM to complete a specific task.

## Task Description
{{TASK}}

## Available Context Sources
{{SOURCES}} (e.g., codebase files, docs, API specs, user data, conversation history)

## Constraints
- Model: {{MODEL}} (e.g., Claude Opus, GPT-4, Gemini)
- Max context: {{MAX_TOKENS}} tokens
- Response type: {{OUTPUT_TYPE}} (e.g., code, analysis, plan)

## Your Analysis

### 1. Context Priority Map
Rank each context source by relevance (Critical / Important / Nice-to-have / Skip):
- For each source, estimate token cost vs. information value
- Flag any sources that could cause confusion or contradictions

### 2. Optimal Layout
Design the context window structure:
```
[SYSTEM INSTRUCTION] (~X tokens)
  → Role, constraints, output format

[REFERENCE CONTEXT] (~X tokens)  
  → Most relevant docs/code, ordered by importance
  → Use XML tags or markdown headers for clear separation

[EXAMPLES] (~X tokens)
  → 1-3 few-shot examples showing expected input→output

[DYNAMIC CONTEXT] (~X tokens)
  → Retrieved/searched content specific to this request
  → Tool outputs, RAG results

[USER REQUEST] (~X tokens)
  → The actual task with all necessary details

[OUTPUT SCAFFOLD]
  → Pre-structured response format to guide generation
```

### 3. Context Anti-Patterns to Avoid
- Redundant information that wastes tokens
- Contradictory instructions across sections  
- Important context buried at the middle (lost-in-the-middle effect)
- Missing context that will cause hallucination

### 4. Compression Strategies
If context exceeds the window:
- What to summarize vs. include verbatim
- What to move to a tool call (RAG, search)
- What to split into multi-turn conversation
```

## When to Use

- Setting up a new AI-assisted workflow
- Debugging why an LLM gives poor results (often it's bad context, not bad prompts)
- Designing AGENTS.md, CLAUDE.md, or .cursorrules files
- Building RAG pipelines (what to retrieve and how to present it)

## Example

**Task:** "Review this PR for security vulnerabilities"

**Context Priority Map:**
| Source | Priority | Est. Tokens | Reason |
|--------|----------|-------------|--------|
| PR diff | Critical | ~2,000 | The actual code to review |
| Security checklist | Critical | ~500 | Standards to check against |
| Related file context | Important | ~3,000 | Understanding the codebase |
| PR description | Important | ~200 | Author's intent |
| Git blame history | Nice-to-have | ~1,000 | Past changes for context |
| Full repo README | Skip | ~800 | Not relevant to security review |

---

> 💡 **The Full Toolkit** includes advanced context engineering templates for every scenario — multi-agent context sharing, cross-model context adaptation, and production AGENTS.md generators.  
> [**Get it → $9 one-time**](https://ai-dev-toolkit-five.vercel.app)
