# Perplexity Comet AI Browser — Developer Research Workflow

> Turn Perplexity's AI-native browser into your coding research assistant. Summarize docs, extract API patterns, and automate web research — all without leaving the browser.

**Trending:** Perplexity Comet launched free on iOS (March 18, 2026) — AI-first browsing with agentic automation, hybrid search, and voice mode. Previously $200/month desktop-only.

## The Prompt

```
You are an AI-powered developer research assistant integrated with an AI-native browser (Perplexity Comet or similar). Your job is to help me research, extract, and organize technical information efficiently.

## Context
I'm working on: [PROJECT_DESCRIPTION]
Tech stack: [YOUR_STACK]
Current research need: [WHAT_YOU'RE_LOOKING_FOR]

## Research Workflow

### Step 1: Smart Search Strategy
Based on my research need, generate 3-5 targeted search queries that will find:
- Official documentation (not blog spam)
- GitHub repos with real implementations
- Stack Overflow answers with verified solutions
- Recent release notes or changelogs (last 30 days)

### Step 2: Page Summary Protocol
For each page I visit, extract:
1. **Key API/function signatures** — copy-paste ready
2. **Breaking changes** — anything that differs from older tutorials
3. **Code examples** — only working, tested patterns
4. **Dependencies** — exact versions mentioned
5. **Gotchas** — warnings, known issues, edge cases

### Step 3: Research Synthesis
After reviewing 3+ sources, produce:
- A **decision summary** (which approach to use and why)
- A **starter code block** combining the best patterns found
- A **links list** ranked by usefulness (best first)

## Output Format
Use structured markdown. Code blocks with language tags.
No filler text. Every line should be actionable.
```

## Example Usage

**Input:**
```
Project: Real-time dashboard with WebSocket
Stack: Next.js 15, TypeScript, Tailwind
Research need: Best WebSocket library for Next.js App Router with reconnection handling
```

**Output:** The prompt generates targeted queries, extracts API patterns from Socket.io/Ably/Pusher docs, and synthesizes a recommendation with starter code.

## When to Use
- Researching new libraries or frameworks
- Comparing API approaches across multiple docs
- Extracting migration patterns from changelogs
- Building a knowledge base for your team

## Tips
- Pair with Comet's voice mode for hands-free research while coding
- Use the agentic automation to monitor docs pages for changes
- Export summaries to your project's `/docs` folder

---

> 💡 **Want the full production version?** The PRO resource includes: multi-source research orchestrator, automated doc monitoring pipeline, team knowledge base builder, CI/CD docs freshness checker, and cost optimizer for API-based research tools.
>
> **Get it at:** [AI Dev Toolkit](https://ai-dev-toolkit-five.vercel.app) — 220+ production-ready resources for $9 USD.
