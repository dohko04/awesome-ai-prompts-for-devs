# Claude Code MCP Elicitation — Interactive Agent Workflow

> Build MCP servers that request structured input mid-task via interactive dialogs. Use the new Elicitation and ElicitationResult hooks to create conversational, context-aware tool pipelines.

**Trending:** Claude Code v2.1.76 (March 2026) added MCP elicitation support — MCP servers can now request form fields or browser URLs mid-task, making agents interactive instead of fire-and-forget.

## The Prompt

```
You are an expert at building MCP (Model Context Protocol) servers that leverage the new elicitation feature in Claude Code v2.1.76+. Your job is to help me design interactive MCP tools that can pause, request structured input from the user, and resume with that context.

## Context
Project: [YOUR_PROJECT]
MCP server language: [TypeScript/Python]
Use case: [WHAT YOUR MCP TOOL DOES]

## Elicitation Architecture

### Step 1: Identify Elicitation Points
Analyze my MCP tool's workflow and identify moments where:
- User confirmation is needed before a destructive action
- Missing context would cause the tool to guess (bad)
- A choice between 2+ valid approaches exists
- Credentials or environment-specific values are required

For each point, define:
- **Trigger condition** — when to pause and ask
- **Form schema** — what fields to show (text, select, boolean, URL)
- **Default values** — pre-fill from context when possible
- **Timeout behavior** — what happens if user doesn't respond

### Step 2: Hook Design Pattern
For each elicitation point, generate:

```typescript
// Elicitation hook pattern
server.tool("my-tool", async (params, context) => {
  // ... initial work ...
  
  const userInput = await context.elicit({
    message: "Describe what you need from the user",
    schema: {
      type: "object",
      properties: {
        fieldName: {
          type: "string",
          description: "Why this field matters",
          default: "smart-default-from-context"
        }
      },
      required: ["fieldName"]
    }
  });
  
  if (userInput.action === "cancel") {
    return { content: [{ type: "text", text: "Cancelled by user." }] };
  }
  
  // ... continue with userInput.data ...
});
```

### Step 3: ElicitationResult Hook
Show me how to intercept and transform elicitation responses:
- Validate user input before the tool continues
- Enrich responses with additional context
- Log elicitation patterns for debugging

### Step 4: Error Handling
- What if the MCP client doesn't support elicitation?
- Graceful fallback to non-interactive mode
- Timeout handling and retry logic

## Output Format
1. Complete MCP server code with elicitation points
2. Hook configuration for claude_code_config.json
3. Test plan (how to verify elicitation works)
4. Fallback strategy for non-interactive clients
```

## When to Use This

- Building MCP servers that need user confirmation before actions
- Creating deployment tools that ask for environment/config mid-task
- Database migration tools that confirm destructive changes
- Any MCP tool where "guessing" is worse than "asking"

## Key Concepts

| Concept | What It Does |
|---------|-------------|
| `context.elicit()` | Pauses tool execution, shows form to user |
| Elicitation hook | Intercepts elicitation requests before display |
| ElicitationResult hook | Intercepts user responses before tool receives them |
| Schema validation | Ensures structured input matches expected format |
| Fallback mode | Non-interactive path when client lacks support |

## Example Use Cases

1. **Deploy tool** — "Deploy to staging or production?" → user picks → tool deploys
2. **DB migration** — "This will drop 3 columns. Confirm?" → user confirms → runs migration
3. **API key rotation** — "Enter new API key for [service]:" → user provides → tool rotates
4. **Code refactor** — "Found 3 patterns. Which refactoring approach?" → user selects → tool applies

---

> 💡 **Want the full production pipeline?** The PRO version includes a complete TypeScript MCP server template with 5 elicitation patterns, automated testing framework, CI/CD hooks config, multi-client compatibility layer, and cost tracking. → [AI Dev Toolkit PRO](https://ai-dev-toolkit-five.vercel.app)
