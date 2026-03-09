# 🗺️ AI-Powered Codebase Onboarding

> **Category:** Context Engineering · **Works with:** Claude, ChatGPT, Gemini  
> **Trending:** March 2026 — Context engineering is the new prompt engineering

## The Prompt

```
You are a senior developer onboarding me to a new codebase. I'll provide you with key files and you'll build me a mental model of how this project works.

**Repository:** [name / URL]
**My role:** [new hire / contractor / open source contributor / taking over maintenance]
**My experience level:** [junior / mid / senior] in [languages I know]
**Time constraint:** I need to be productive in [1 day / 1 week / 1 month]

Here's what I'm sharing with you:
1. **package.json / requirements.txt / Cargo.toml** (dependencies)
2. **Project structure** (output of `tree -L 3 --dirsfirst`)
3. **README.md** (if it exists)
4. **Main entry point** (e.g., `src/index.ts`, `main.py`)
5. **One representative feature file** (a complete vertical slice)

Based on these files, create:

## Architecture Map
- Draw the system in ASCII art (components, data flow, external services)
- Identify the architectural pattern (MVC, hexagonal, serverless, monolith, etc.)
- List the key abstractions and where they live

## Dependency Audit
- Which dependencies are core vs. utility?
- Any red flags? (outdated, deprecated, security issues)
- What's the "meta" of this stack? (what are they trying to achieve architecturally)

## Code Conventions Cheat Sheet
A quick reference of patterns I'll see everywhere:
- Naming conventions (files, functions, variables)
- Error handling pattern
- How data flows from request → response
- Testing patterns and where tests live

## "Start Here" Path
Ordered list of files to read (max 10) that will give me 80% understanding:
1. [file] — why to read it
2. [file] — why to read it
...

## First Contribution Guide
Based on the codebase patterns, write me a template for my first PR:
- Where to add new files
- What to import and how
- Which patterns to follow
- Common mistakes a newcomer would make

## Questions I Should Ask the Team
5 specific questions about this codebase that aren't answered by the code itself.
```

## When to Use

- Joining a new team or project
- Taking over an abandoned codebase
- Contributing to open source for the first time
- Onboarding contractors or junior devs to your project

## Pro Tips

1. **Feed real files, not descriptions** — Copy-paste actual file contents, not summaries
2. **Start with structure** — `tree` output + `package.json` alone gives AI 60% of the picture
3. **Use iteratively** — First pass for overview, then deep-dive into specific modules
4. **Create an AGENTS.md** — Use the output to write a contributor guide that helps both humans AND AI tools

---

> 🚀 **Want advanced onboarding workflows + AGENTS.md templates?** The [AI Dev Toolkit](https://ai-dev-toolkit-five.vercel.app) ($9) includes codebase analysis prompts, architecture documentation generators, and ready-made AGENTS.md files for popular frameworks.
