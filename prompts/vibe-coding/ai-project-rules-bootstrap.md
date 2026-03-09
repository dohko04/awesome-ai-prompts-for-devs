# AI Project Rules Bootstrap Kit 🚀

> Generate all AI coding agent config files for your project in one shot. Cursor rules, CLAUDE.md, Copilot instructions, and AGENTS.md — ready to drop in.

**Why this matters:** In 2026, every AI coding tool reads project-specific rules. The right config files make AI assistants 10x more useful. This prompt generates ALL of them at once.

## The Prompt (Free Version)

```
You are an AI Developer Environment Architect. Your job is to analyze a project and generate configuration files for ALL major AI coding assistants.

## My Project
- **Name:** [project name]
- **Language/Framework:** [e.g., TypeScript/Next.js, Python/FastAPI, Rust]
- **Description:** [1-2 sentences about what it does]
- **Key patterns:** [e.g., REST API, monorepo, microservices, serverless]
- **Testing:** [e.g., Jest, pytest, none yet]
- **Package manager:** [e.g., npm, pnpm, pip, cargo]

## Generate These Files

### 1. `.cursor/rules/project.mdc` (Cursor AI Rules)
Include:
- Project context and conventions
- File structure overview
- Preferred patterns and anti-patterns
- Testing requirements
- Import conventions

### 2. `CLAUDE.md` (Claude Code / Claude CLI)
Include:
- Build & test commands (single test, all tests, lint)
- Code style rules
- Project-specific conventions
- Key architecture decisions

### 3. `.github/copilot-instructions.md` (GitHub Copilot)
Include:
- Language and framework preferences
- Code style guidelines
- Testing patterns
- Security considerations

### 4. `AGENTS.md` (Multi-agent / OpenClaw / Custom)
Include:
- Project overview for autonomous agents
- Directory structure guide
- How to run, test, and deploy
- Safety rules (what NOT to do)

## Rules for Generation
- Be SPECIFIC to my project, not generic
- Include actual file paths and command examples
- Each file should be self-contained (agents read only one)
- Prefer strictness over permissiveness
- Include "don't" rules (common mistakes to avoid)

Generate all 4 files with clear separators. Each should be copy-paste ready.
```

## Example Output Structure

The prompt generates 4 ready-to-use files:

```
📁 your-project/
├── .cursor/rules/project.mdc    ← Cursor reads this automatically
├── CLAUDE.md                     ← Claude Code reads this
├── .github/copilot-instructions.md  ← Copilot reads this
└── AGENTS.md                     ← Multi-agent systems read this
```

## Pro Tips

- Run this prompt ONCE when starting a project, then iterate
- Update these files as your project evolves — AI tools get smarter with better context
- Add `.cursor/rules/` to `.gitignore` if you want personal rules, or commit for team sharing

---

## 🔒 Want More?

The **[AI Dev Toolkit](https://ai-dev-toolkit-five.vercel.app)** ($9) includes:
- **Framework-specific templates** (Next.js, FastAPI, Rails, Laravel, Go, Rust) with pre-filled rules
- **MCP server config generator** — connect AI tools to your APIs, databases, and services
- **Team-scale rules** — shared conventions for engineering teams with multiple AI tools
- **Auto-update prompt** — regenerate rules when your project changes
- **100+ battle-tested prompts** for every stage of development

[**Get the Full Toolkit →**](https://ai-dev-toolkit-five.vercel.app)
