# 🌐 Page-Agent: Natural Language Web Automation

> Build in-page GUI agents that control web interfaces with natural language — no backend, no headless browser, pure JavaScript.

Based on Alibaba's Page-Agent (trending GitHub, March 2026) — an open-source JS library that embeds AI agents directly into web pages.

## The Prompt

```
You are a Web GUI Agent Architect specializing in natural language web automation using in-page agents.

Given my web application:
- **App type:** [e.g., dashboard, e-commerce, SaaS admin panel]
- **Key user flows:** [e.g., "create invoice", "filter reports by date", "bulk update records"]
- **Tech stack:** [e.g., React, Vue, vanilla JS]
- **Target users:** [e.g., non-technical ops team, QA testers, power users]

Design a Page-Agent integration that:

1. **Agent Setup**
   - Identify the 5 most automatable user flows
   - Map each flow to natural language commands (e.g., "create a new invoice for $500 to Acme Corp")
   - Define DOM element targeting strategy (aria-labels, data-attributes, CSS selectors)

2. **Command Architecture**
   - Create a command vocabulary (verb + object + parameters)
   - Design fallback behavior when elements aren't found
   - Handle multi-step flows with state tracking

3. **Safety Layer**
   - Classify commands as safe (read) vs destructive (write/delete)
   - Require confirmation for destructive actions
   - Implement undo capability where possible

4. **Quick Start**
   - Provide the minimal integration code (<20 lines)
   - Include 3 example commands with expected behavior
   - Show how to add custom command handlers

Output as a structured implementation plan with code snippets.
```

## Example Output

For a project management dashboard:

| Command | Action | Safety |
|---------|--------|--------|
| "Show all overdue tasks" | Filter + sort tasks | ✅ Safe |
| "Assign task #42 to Maria" | Update assignment | ⚠️ Confirm |
| "Delete completed sprint" | Remove sprint data | 🔴 Double confirm |

### Minimal Integration
```javascript
import { PageAgent } from '@anthropic/page-agent';

const agent = new PageAgent({
  model: 'claude-sonnet',
  safeMode: true,
  selectors: {
    tasks: '[data-testid="task-row"]',
    filters: '.filter-panel button',
  }
});

agent.on('command', async (cmd) => {
  if (cmd.destructive) await agent.confirm(cmd);
  return agent.execute(cmd);
});
```

## When to Use This

- **QA automation** — test user flows with natural language
- **Internal tools** — let non-technical users operate complex dashboards
- **Accessibility** — voice-controlled web navigation
- **Demo automation** — script product demos with plain English

## Limitations of This Free Version

- Basic command architecture only
- No multi-agent coordination
- No enterprise patterns (auth, audit logging, rate limiting)

---

> 🔥 **Want the full production pipeline?** The [AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app) includes multi-agent web orchestration, A/B testing integration, enterprise governance patterns, and 149+ more production-ready resources.
