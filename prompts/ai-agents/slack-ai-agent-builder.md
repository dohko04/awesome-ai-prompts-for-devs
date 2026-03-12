# Slack AI Agent Builder 🤖💬

> Build an AI agent that lives inside Slack — searches company data, drafts content, and takes actions across workflows. Inspired by Salesforce's Agentforce Slackbot rebuild (March 2026).

## The Prompt

```
You are a Slack AI Agent architect. I need to build an intelligent bot that operates inside Slack as a workplace AI agent.

My context:
- Team size: [TEAM_SIZE]
- Primary use cases: [e.g., answer questions from company docs, draft responses, summarize channels, create tickets]
- Data sources: [e.g., Confluence, Google Drive, Notion, internal APIs]
- Tech stack: [e.g., Node.js, Python, hosted on Railway/Vercel]

Design a Slack AI Agent with:

1. **Architecture** — Slack Bolt app structure with event subscriptions (app_mention, message.im, shortcuts)
2. **Context retrieval** — How to connect company data sources for RAG-powered answers
3. **Action handlers** — Slash commands and interactive actions the agent can perform
4. **Conversation memory** — Thread-aware context within Slack conversations
5. **Permission model** — Channel-based access control (which channels the agent monitors, who can trigger actions)

For each component, provide:
- Implementation approach (code structure, not full code)
- Key Slack API methods to use
- Error handling strategy
- Rate limiting considerations

Output as a structured implementation plan I can start building today.
```

## When to Use

- Building internal AI assistants for your team
- Replacing manual workflows with conversational AI
- Creating context-aware bots that understand your company's data
- Automating repetitive Slack-based tasks (standup summaries, ticket creation, doc search)

## Example Output Preview

The prompt generates a structured plan covering Slack Bolt setup, RAG pipeline for company docs, action handlers for common workflows, and a permission model. You'll get actionable architecture — not just theory.

## Tips

- Start with `app_mention` events before expanding to ambient listening
- Use Slack's Block Kit for rich interactive responses
- Implement thread-based memory to maintain conversation context
- Rate limit: Slack allows ~1 message/second per channel

---

> 💡 **Want the full production version?** The [AI Dev Toolkit](https://surviveai.gumroad.com/l/ai-dev-toolkit) includes the **Enterprise Slack Agent Pipeline PRO** with multi-tenant architecture, Agentforce integration patterns, analytics dashboard, and deployment configs for 5 cloud providers.
