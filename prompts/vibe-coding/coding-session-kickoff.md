# 🚀 AI Coding Session Kickoff

Start any AI coding session (Cursor, Claude Code, Aider, Copilot Chat) with the right context. This prompt prevents the #1 mistake: jumping in without giving the AI enough context.

## The Prompt

```
Before we start coding, here's the context you need:

## Project
- **What**: {ONE_LINE_DESCRIPTION}
- **Stack**: {LANGUAGES_AND_FRAMEWORKS}
- **Repo structure**: {KEY_FOLDERS_AND_THEIR_PURPOSE}

## Current Task
- **Goal**: {WHAT_I_WANT_TO_BUILD_OR_FIX}
- **Acceptance criteria**: {HOW_I_KNOW_IT'S_DONE}
- **Scope**: {WHAT'S_IN_AND_OUT_OF_SCOPE}

## Constraints
- **Must use**: {EXISTING_PATTERNS_OR_LIBRARIES}
- **Must avoid**: {ANTI_PATTERNS_OR_DEPRECATED_STUFF}
- **Performance**: {ANY_PERF_REQUIREMENTS}

## Style
- Follow existing patterns in {REFERENCE_FILE_OR_FOLDER}
- {ANY_SPECIFIC_CODING_STYLE_RULES}

## How to work
1. Ask clarifying questions BEFORE writing code
2. Show your plan before implementing
3. Write tests alongside the implementation
4. Keep changes minimal — don't refactor unrelated code
5. If unsure about an approach, present 2 options with tradeoffs

Let's start. What questions do you have about the task?
```

## Why This Works

Most AI coding sessions fail because:
- ❌ No project context → AI guesses your patterns wrong
- ❌ No scope → AI over-engineers or goes off track
- ❌ No constraints → AI introduces new dependencies you don't want

This prompt solves all three in 30 seconds.

## Quick Version (for small tasks)

```
Context: {STACK} project. File: {FILENAME}. Pattern: follow existing code style.
Task: {WHAT_TO_DO}
Constraints: no new dependencies, keep it simple, add tests.
Show plan first, then implement.
```

---

> ⚡ **Get 50+ session templates for specific workflows.** The [AI Dev Toolkit](https://dohko04.gumroad.com/l/ai-dev-toolkit) ($9) includes kickoff templates for bug fixing, feature building, refactoring, migrations, API design, and more — each optimized for different AI coding tools.
