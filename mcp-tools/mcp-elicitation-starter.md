# MCP Elicitation Starter — Interactive Dialogs for AI Agents

> Build MCP servers that ask smart questions instead of guessing. New in Claude Code v2.1.76+.

## What Is MCP Elicitation?

MCP Elicitation lets your MCP server **pause mid-task to ask the user a structured question** — confirmations, selections, text input, even OAuth URLs. Instead of your agent guessing wrong, it asks.

## Quick Start

```typescript
// minimal-elicitation-server.ts
import { Server } from "@modelcontextprotocol/sdk/server/index.js";
import { StdioServerTransport } from "@modelcontextprotocol/sdk/server/stdio.js";

const server = new Server({
  name: "elicitation-starter",
  version: "1.0.0",
}, { capabilities: { tools: {}, elicitation: {} } });

server.setRequestHandler("tools/call", async (request) => {
  if (request.params.name === "deploy") {
    // Ask user to confirm before deploying
    const result = await server.elicit({
      message: "⚠️ Deploy to production?",
      requestedSchema: {
        type: "object",
        properties: {
          confirm: { type: "boolean", title: "Confirm deploy" },
          environment: {
            type: "string",
            enum: ["staging", "production"],
            title: "Target environment"
          }
        },
        required: ["confirm", "environment"]
      }
    });
    
    if (result.action === "reject" || !result.content?.confirm) {
      return { content: [{ type: "text", text: "Deploy cancelled." }] };
    }
    
    return { content: [{ type: "text", text: `✅ Deployed to ${result.content.environment}` }] };
  }
});

const transport = new StdioServerTransport();
await server.connect(transport);
```

## When to Elicit

| Situation | Elicit? | Why |
|-----------|---------|-----|
| Destructive operation (DELETE, DROP) | ✅ Always | Can't undo |
| Multiple valid approaches (>3) | ✅ Yes | Agent shouldn't guess |
| Need API key/credentials | ✅ Yes | Security |
| Formatting choices | ❌ No | Trivial |
| Git operations (can undo) | ❌ No | Recoverable |

## 3 Elicitation Patterns

**1. Confirmation Gate** — "Are you sure?"
```typescript
await server.elicit({
  message: "Delete all test data?",
  requestedSchema: { type: "object", properties: { confirm: { type: "boolean" } } }
});
```

**2. Strategy Selector** — "Which approach?"
```typescript
await server.elicit({
  message: "Choose migration strategy",
  requestedSchema: {
    type: "object",
    properties: {
      strategy: { type: "string", enum: ["conservative", "balanced", "aggressive"] }
    }
  }
});
```

**3. Progressive Disclosure** — "Start simple, drill down"
```typescript
const basic = await server.elicit({ /* basic config */ });
if (basic.content.replicas > 3) {
  await server.elicit({ /* advanced autoscaling config */ });
}
```

## Install & Test

```bash
npm install @modelcontextprotocol/sdk
npx tsx minimal-elicitation-server.ts
# Add to Claude Code: claude mcp add elicitation-starter -- npx tsx minimal-elicitation-server.ts
```

---

> 🔓 **Want the full pipeline?** The PRO version includes: multi-step elicitation orchestration, Elicitation Hook system for Claude Code extensions, 5 advanced patterns (URL auth, credential collection, batched forms), testing framework, CI/CD quality gates, and cost calculator. → [AI Dev Toolkit](https://ai-dev-toolkit-five.vercel.app)
