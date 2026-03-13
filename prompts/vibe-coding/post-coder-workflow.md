# Post-Coder Engineering Workflow

> Design your role as an engineer when AI writes 80%+ of the code. Based on the "Coding After Coders" shift (NYT March 2026) — what developers actually do now.

## The Prompt

```markdown
You are a senior engineering workflow consultant. Help me redesign my daily workflow for the post-coder era where AI agents (Claude Code, Copilot, Cursor) write most of the code.

## My Current Setup
- **AI tools I use:** [LIST YOURS: e.g., "Claude Code for implementation, Copilot for autocomplete, ChatGPT for design discussions"]
- **My role:** [DESCRIBE: e.g., "full-stack dev", "tech lead", "solo founder"]
- **Team size:** [NUMBER or "solo"]
- **What I still code manually:** [e.g., "architecture decisions, security-critical paths, complex algorithms"]

## Design My Post-Coder Workflow

### 1. Task Classification Matrix
For each type of work I do, classify it:
- **DELEGATE** → AI writes it, I review (80% of tasks)
- **PAIR** → I guide AI in real-time, iterating together (15%)
- **MANUAL** → I write this myself, AI assists at most (5%)

### 2. Review-First Engineering
Since I'm now primarily a reviewer:
- What's my code review checklist for AI-generated code?
- What are the common failure patterns to watch for?
- How do I maintain deep understanding of a codebase I didn't write?

### 3. Specification as the New Coding
Help me structure my "specs" that I feed to AI:
- What level of detail gets the best output?
- Template for describing a feature to an AI coder
- How to break large features into AI-digestible chunks

### 4. Quality Gates
Define the gates between AI output and production:
- Automated checks that catch AI-specific mistakes
- Manual review priorities (what humans catch that AI misses)
- Testing strategy when AI writes both code AND tests

## Output
Give me a concrete daily workflow schedule with specific blocks for:
delegation, review, specification writing, learning, and manual coding.
Include tool-specific tips for my setup.
```

## When to Use

- Transitioning from "I write code" to "I direct AI that writes code"
- Onboarding team members to AI-augmented workflows
- Solo devs scaling output with AI tools
- Tech leads restructuring team processes around AI coding

## Example Output

Generates a personalized daily schedule like:
- 9:00-9:30 — Specification writing (3 features detailed for AI)
- 9:30-11:00 — Delegation round (launch AI on all 3 features)
- 11:00-12:00 — Deep review of yesterday's AI output
- Afternoon — Architecture decisions, edge cases, manual coding

## Tips

- The spec you write IS the code now — invest time in clear specs
- Review AI code like you'd review a junior dev's PR: trust but verify
- Keep coding manually sometimes to maintain your skills and intuition

---

> 💡 **Want the full production version?** The [AI Dev Toolkit](https://ai-dev-toolkit-five.vercel.app) PRO includes: team delegation matrix templates, AI code review checklists for 6 frameworks, specification-to-implementation pipelines, quality gate automation configs, and a 30-day transition plan from traditional to post-coder engineering.
