# 🧠 LLM Context Budget Optimizer

> **Category:** Context Engineering · **Works with:** Claude, ChatGPT, Gemini  
> **Trending:** March 2026 — Context windows are huge now, but smart context selection still beats dumping everything in

## The Prompt

```
You are a context engineering specialist. Analyze my project and design an optimal context budget strategy that maximizes AI coding assistant output quality while minimizing token waste.

**My Setup:**
- AI Tool: [e.g., Cursor / Claude Code / GitHub Copilot]
- Project Size: [e.g., 50 files, ~15k lines / monorepo with 200+ files]
- Language: [e.g., TypeScript + Python]
- Context Window: [e.g., 200k tokens]

## Analyze & Optimize:

### 1. Context Prioritization Matrix
Rank these context sources by impact-per-token for MY project type:
- Current file being edited
- Import chain (files imported by current file)
- Type definitions / interfaces
- Test files for current module
- README / docs
- Git diff (recent changes)
- Error logs / stack traces
- Package.json / dependency versions
- .cursor/rules or AGENTS.md

### 2. Dynamic Context Loading Strategy
Design a system that loads context based on the TASK:
- **Bug fixing** → error logs + stack trace + relevant source + tests
- **New feature** → architecture docs + similar existing features + types
- **Refactoring** → full module + dependents + test coverage
- **Code review** → diff + original code + project conventions

### 3. Context Compression Techniques
For each file type, suggest compression:
- Strip comments vs. keep (when do comments help the LLM?)
- Type-only imports (skip implementation details)
- Summarize large files vs. include full
- Tree-sitter based: extract only relevant functions

### 4. Anti-Patterns to Avoid
- What context HURTS more than it helps?
- When does MORE context reduce output quality?
- Common token-wasting patterns in [my AI tool]

### 5. Measurable Output
Provide a context budget allocation like:
| Context Source | Token Budget | Priority | When to Include |
|---|---|---|---|
| Current file | 4k | Always | Every request |
| Types/Interfaces | 3k | High | Code generation |
| ... | ... | ... | ... |

Generate a concrete, copy-paste configuration for my AI tool.
```

## Example Output

```yaml
# .context-budget.yml — for Claude Code / Cursor
strategy: dynamic
max_context: 180000  # leave 20k for output

priorities:
  critical:  # always included
    - current_file
    - error_context  # when debugging
    - type_definitions: { depth: 2 }
    
  high:  # included when relevant
    - import_chain: { max_depth: 3, types_only: false }
    - test_files: { for: current_module }
    - git_diff: { commits: 3 }
    
  medium:  # included if budget allows
    - similar_files: { max: 3, by: "function_signature" }
    - docs: { only: ["README", "ARCHITECTURE"] }
    
  low:  # rarely needed
    - package_json
    - ci_config
    - changelog

compression:
  strip_comments: true  # except JSDoc on public APIs
  collapse_imports: true
  summarize_files_over: 500  # lines
```

## Why This Matters (March 2026)

GitHub's Octoverse data shows TypeScript surged 66% partly because **types give LLMs better context**. But most devs still dump random files into context and wonder why AI output is mediocre. Context engineering — choosing WHAT goes into the prompt — is the highest-leverage skill for AI-assisted development in 2026.

## Use Cases

- Optimizing Cursor / Claude Code workflows
- Building custom RAG pipelines for codebases
- Reducing AI API costs (fewer tokens = less spend)
- Improving AI code generation accuracy by 2-3x

---

> 💡 **Want the complete context engineering playbook?** This prompt scratches the surface. The full [AI Dev Toolkit](https://ai-dev-toolkit-five.vercel.app) ($9) includes task-specific context templates, auto-compression scripts, and proven budget allocations tested across 50+ real codebases.
