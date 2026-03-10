# ⚡ ChatGPT Skills Architect for Developers

> **When to use:** You want to design reusable ChatGPT Skills (March 2026 feature) that automate your repetitive dev workflows — code reviews, commit messages, PR descriptions, release notes, and more.

## The Prompt

```
You are a ChatGPT Skills Designer specializing in developer automation. Help me design reusable Skills for my development workflow.

## What are ChatGPT Skills?
Skills are saved, reusable workflow automations in ChatGPT. Instead of re-typing complex prompts, you trigger a Skill and it executes a consistent, high-quality workflow every time.

## My Development Context
- **Primary language(s):** [TypeScript / Python / Go / etc.]
- **Framework(s):** [React / NestJS / FastAPI / etc.]
- **Common repetitive tasks I do with AI:**
  - [e.g., write commit messages, review PRs, generate tests, write docs]
- **Team conventions:** [any specific standards]

## Design Skills for these workflows:

### Skill 1: Smart Commit Message Generator
**Trigger:** Paste a git diff
**Output:** Conventional commit message with:
- Type (feat/fix/refactor/docs/test/chore)
- Scope (auto-detected from files changed)
- Subject line (imperative, <72 chars)
- Body (what changed and why, if diff is significant)
- Breaking change footer (if applicable)

### Skill 2: PR Description Writer
**Trigger:** Paste branch diff or list of commits
**Output:** Structured PR description with:
- Summary of changes
- Motivation/context
- Testing done
- Screenshots needed? (flag if UI changes detected)
- Checklist (tests, docs, migration)

### Skill 3: Code Review Prep
**Trigger:** Paste code for review
**Output:** Self-review checklist:
- Potential bugs or edge cases
- Performance considerations
- Security red flags
- Naming and readability issues
- Test coverage gaps

### Skill 4: Release Notes Generator
**Trigger:** Paste list of merged PRs or commits since last release
**Output:** User-facing release notes:
- ✨ New features
- 🐛 Bug fixes
- ⚡ Performance improvements
- 🔒 Security updates
- 💥 Breaking changes (with migration guide)

For each Skill, provide:
1. The exact Skill configuration (system prompt + instructions)
2. Example input → output
3. Edge cases it handles
4. When NOT to use it (limitations)
```

## Why This Matters

ChatGPT Skills (released March 9, 2026) let you save complex prompts as one-click automations. For developers, this means:
- **Consistency:** Every commit message, PR description, and review follows the same standard
- **Speed:** No more re-typing your favorite prompts
- **Team alignment:** Share Skills across your team for uniform output

## Example Skill Output

**Input (diff):**
```diff
+ export function validateEmail(email: string): boolean {
+   return /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(email);
+ }
```

**Skill Output:**
```
feat(auth): add email validation utility

Add regex-based email validation function for use in
registration and profile update flows.
```

---

> 🔥 **Want 15+ pre-built developer Skills with advanced workflows?** The [AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app) includes: complete Skill library for dev teams, multi-step pipeline Skills (review → test → deploy), Skills that integrate with your CI/CD, team Skill sharing templates, and advanced Skills for architecture decisions, incident response, and sprint planning.
