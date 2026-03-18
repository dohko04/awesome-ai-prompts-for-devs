# Agentic QA Test Generator

> Generate autonomous, self-adapting test suites that discover how your app works — inspired by SmartBear BearQ's agentic QA approach (March 2026).

## The Prompt

```
You are an Agentic QA Engineer. Your job is to autonomously explore an application, discover its behaviors, and generate tests that adapt to code changes.

Given this application context:
- App type: [web app / API / CLI / mobile]
- Tech stack: [e.g., React + Node.js + PostgreSQL]
- Key user flows: [e.g., signup → onboarding → dashboard → billing]
- Recent changes: [e.g., "refactored auth module, added SSO"]

Do the following:

1. **Exploration Map**: List every discoverable endpoint, UI flow, and state transition. Prioritize by business impact.

2. **Adaptive Test Cases**: For each critical flow, generate test cases that:
   - Test the happy path
   - Test 3 edge cases (empty inputs, boundary values, concurrent access)
   - Include a regression check tied to the recent changes

3. **Self-Healing Selectors**: For UI tests, provide 3 fallback selectors per element (data-testid → aria-label → CSS path) so tests survive refactors.

4. **Risk Score**: Rate each test area 1-5 for:
   - Change frequency (how often this code changes)
   - Business impact (revenue/user impact if broken)
   - Test coverage gap (how undertested it is)

Output format: Markdown with code blocks for test snippets (use your best guess for the testing framework based on the stack).
```

## Example Output (snippet)

### Exploration Map
| Flow | Endpoints | Priority |
|------|-----------|----------|
| User Signup | POST /api/auth/register, GET /onboarding | 🔴 Critical |
| Billing | POST /api/billing/subscribe, webhook /stripe | 🔴 Critical |
| Dashboard | GET /api/dashboard, WebSocket /ws/updates | 🟡 High |

### Adaptive Test: User Signup
```javascript
describe('User Signup Flow', () => {
  it('completes happy path', async () => {
    // Happy path with valid data
  });
  
  it('handles duplicate email gracefully', async () => {
    // Edge case: existing user
  });
  
  it('regression: SSO redirect works after auth refactor', async () => {
    // Tied to recent change
  });
});
```

## When to Use
- After any major refactor (let the agent re-discover your app)
- Sprint planning (generate test coverage for new features)
- CI/CD quality gates (catch what static tests miss)

---

> 🔒 **Want the full pipeline?** The [AI Dev Toolkit](https://ai-dev-toolkit-five.vercel.app) PRO version includes: multi-framework test orchestrator, CI/CD integration configs, cost calculator for agentic QA platforms, and a self-healing test maintenance system. **213+ production-ready resources for $9.**
