# ⚡ Claude Code + Codex Power User Setup

> Claude Code is #1 (46% most-loved), Codex is the fastest-growing newcomer. Here's how to set up both for maximum output.

## Claude Code Setup Prompt

```
I'm setting up Claude Code for a new project. Generate the optimal configuration.

PROJECT: {{description}}
LANGUAGE: {{language}}
FRAMEWORK: {{framework}}
REPO SIZE: {{small|medium|large|monorepo}}

Create:

1. **CLAUDE.md** — Project context file with:
   - Architecture overview
   - Key commands (build, test, lint, deploy)
   - Code conventions Claude must follow
   - Safety rules (files to never touch, destructive operations)
   - Testing requirements

2. **Recommended Claude Code flags/settings** for this project:
   - Model selection (opus vs sonnet for different tasks)
   - Context window strategy for repo size
   - Permission boundaries

3. **Power user aliases** — Shell aliases for common workflows:
   - Quick fix: "cc-fix" → claude code with error context
   - Feature: "cc-feat" → claude code with spec template
   - Review: "cc-review" → claude code in review mode

4. **5 starter prompts** tailored to this specific project type
   that demonstrate Claude Code's agentic capabilities
   (file creation, multi-file edits, running tests, etc.)
```

## Codex Setup Prompt

```
I'm setting up OpenAI Codex as an async coding agent alongside Claude Code.

PROJECT: {{same project}}
REPO URL: {{github_url}}

Create:

1. **Codex task templates** for:
   - Bug fixes (input: issue description → output: PR)
   - Feature implementation (input: spec → output: branch)
   - Test generation (input: module path → output: test file)
   - Refactoring (input: code smell → output: clean code)

2. **When to use Codex vs Claude Code:**
   - Codex: async background tasks, batch operations, PR generation
   - Claude Code: interactive sessions, debugging, exploration

3. **Integration workflow:**
   - How to queue tasks in Codex while working in Claude Code
   - Review flow for Codex-generated PRs
```

## Quick Decision Matrix

| Task | Use Claude Code | Use Codex |
|------|:-:|:-:|
| Interactive debugging | ✅ | ❌ |
| "Fix this bug" with context | ✅ | ❌ |
| Generate 10 test files | ❌ | ✅ |
| Batch refactoring across files | ❌ | ✅ |
| Architecture exploration | ✅ | ❌ |
| Async PR from issue | ❌ | ✅ |
| Learning new codebase | ✅ | ❌ |

## Pro Tips

1. **Use Claude Code for thinking, Codex for doing** — Claude Code excels at interactive problem-solving; Codex at cranking through well-defined tasks.
2. **Share the same CLAUDE.md/AGENTS.md** — Both tools benefit from the same project context.
3. **Queue Codex tasks while you code** — Fire off 3 Codex tasks, keep building in Claude Code. Review Codex PRs later.

---

> 🔥 **Get the complete setup kit.** The [AI Dev Toolkit](https://dohko04.gumroad.com/l/ai-dev-toolkit) ($9) includes pre-built CLAUDE.md templates for 12 frameworks, Codex task configs, shell alias packages, and a setup script that configures everything in one command.
