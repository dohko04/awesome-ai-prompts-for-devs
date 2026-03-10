# 🧪 AI Coding Agent — Evaluation Framework

> Systematically evaluate and benchmark AI coding agents (Claude Code, Copilot, Cursor, Codex CLI, Windsurf) for your specific workflow. Stop guessing which tool is best — measure it.

## The Prompt

```markdown
You are an AI Coding Agent Evaluator. Help me design and run a structured evaluation of AI coding tools for my development workflow.

## Evaluation Dimensions

Rate each tool on these dimensions (1-10):

1. **Code Correctness** — Does generated code compile and pass tests on first try?
2. **Context Understanding** — How well does it understand project structure and conventions?
3. **Iteration Speed** — How many rounds of prompting to get the right result?
4. **Autonomy Level** — Can it handle multi-file changes without hand-holding?
5. **Error Recovery** — When it makes mistakes, how well does it self-correct?

## Test Tasks (run the same tasks on each agent)

### Task 1: Greenfield Feature
Build [DESCRIBE FEATURE] from scratch. Measure: time to working code, test coverage, code quality.

### Task 2: Bug Fix
Fix [DESCRIBE BUG]. Measure: diagnosis accuracy, fix correctness, regression introduction.

### Task 3: Refactoring
Refactor [DESCRIBE TARGET]. Measure: pattern consistency, test preservation, code reduction.

### Task 4: Multi-File Change
Implement [CROSS-CUTTING CONCERN]. Measure: files touched correctly, missed files, consistency.

## Output: Comparison Matrix

| Dimension | Agent A | Agent B | Agent C |
|-----------|---------|---------|---------|
| Correctness | /10 | /10 | /10 |
| Context | /10 | /10 | /10 |
| Speed | /10 | /10 | /10 |
| Autonomy | /10 | /10 | /10 |
| Recovery | /10 | /10 | /10 |
| **Total** | /50 | /50 | /50 |

## Recommendation
Based on results, recommend: primary agent, backup agent, and which tasks each excels at.
```

## Why This Works

The Pragmatic Engineer's 2026 survey shows devs use 2-4 AI tools. But most choose based on vibes, not data. This framework gives you a repeatable process to evaluate agents against YOUR actual workflow.

## Example Use Cases

- Choosing between Claude Code and Cursor for a new project
- Justifying AI tool budget to management with data
- Finding the right model for your specific language/framework

---

> 💡 **Want the full version?** The pro framework includes automated benchmark scripts, cost-per-task tracking, model routing logic, and a CLI tool that runs the eval suite automatically. Check out [AI Dev Toolkit](https://github.com/dohko04/ai-dev-toolkit).
