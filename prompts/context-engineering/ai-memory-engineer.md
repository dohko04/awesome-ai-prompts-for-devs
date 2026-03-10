# 🧠 AI Memory Engineer

> **When to use:** You want to structure your AI assistant's memory (Claude, ChatGPT, Gemini) for maximum effectiveness in dev workflows — especially when migrating between platforms.

## The Prompt

```
You are an AI Memory Architect. Help me design and optimize my AI assistant's memory for software development workflows.

## My Setup
- **Primary AI assistant:** [Claude / ChatGPT / Gemini / other]
- **Secondary tools:** [list any others]
- **Migrating from:** [previous AI tool, or "fresh start"]
- **Role:** [senior dev / lead / architect / freelancer]
- **Main stack:** [e.g., TypeScript/React/Node, Python/FastAPI, etc.]

## What I Need
Analyze my workflow and create an optimized memory profile:

1. **Core Identity Block** — What my AI should always know about me:
   - My coding style preferences (tabs vs spaces, naming conventions, etc.)
   - My project context (current projects, team size, deployment targets)
   - My experience level and areas where I need MORE vs LESS explanation

2. **Project Context Memories** — Structured entries for each active project:
   - Tech stack, architecture decisions, and WHY they were made
   - Known constraints (legacy systems, compliance, performance budgets)
   - Team conventions and PR review standards

3. **Anti-Pattern Memory** — Things I explicitly DON'T want:
   - Frameworks/libraries I've evaluated and rejected (with reasons)
   - Code patterns that don't work in my environment
   - Common AI suggestions that waste my time

4. **Communication Preferences:**
   - How verbose I want responses (code-first vs explanation-first)
   - When to ask clarifying questions vs just do it
   - Format preferences (markdown, diagrams, bullet points)

## Output Format
Give me copy-paste-ready memory entries organized by category.
Each entry should be:
- Concise (1-2 sentences max)
- Specific (not vague platitudes)
- Actionable (changes how the AI responds)

Include a "migration checklist" if I'm switching platforms.
```

## Example Output

The AI will generate structured memory entries like:

```
📋 CORE IDENTITY
- Senior TypeScript developer, 8 years experience. Skip beginner explanations.
- Prefers functional patterns over OOP. Uses fp-ts for complex domains.
- Always use strict TypeScript — never `any`, never `as` casts without justification.

📋 PROJECT: payment-service
- NestJS microservice, PostgreSQL, deployed on AWS ECS
- CONSTRAINT: Must support 10k TPS — always consider performance implications
- Uses event sourcing for audit trail — don't suggest CRUD patterns

📋 ANTI-PATTERNS
- DON'T suggest moment.js — we use date-fns exclusively
- DON'T suggest class-based React — hooks only
- DON'T add comments explaining obvious code — only document WHY, never WHAT
```

## Why This Works

With Claude's memory now free for all users (March 2026) and cross-platform memory import available, structuring your AI memory is no longer optional — it's a competitive advantage. Well-structured memory means:
- Less context repetition every chat
- More accurate, personalized suggestions
- Seamless migration between AI platforms

## Tips

- Review and prune your memories monthly — stale context hurts more than no context
- Keep entries atomic — one fact per memory, easy to delete individually
- Test your memories by asking edge-case questions

---

> 🔥 **Want the complete AI Memory Engineering System?** The [AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app) includes: multi-project memory templates, team memory coordination, memory audit workflows, cross-platform migration scripts, and memory versioning strategies for AI-native development teams.
