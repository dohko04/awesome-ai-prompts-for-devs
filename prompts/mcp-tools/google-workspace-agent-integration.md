# Google Workspace Agent Integration Starter

> **Category:** MCP Tools · Productivity Automation  
> **Use case:** Connect your coding agent to Google Docs, Sheets, Drive, Calendar, Gmail  
> **Works with:** Claude Code, Cursor, any MCP-compatible agent  
> **Context:** Google shipped `gws` CLI with built-in MCP server (March 2026)  

## The Problem

Developers juggle between their IDE and Google Workspace constantly — checking docs, updating sheets, reading emails, scheduling meetings. With `gws` (Google's unified Workspace CLI with MCP support), your agent can do all of this without leaving your terminal.

## The Prompt

```
You are a Google Workspace MCP Integration Architect. Help me set up and optimize my agent's access to Google Workspace.

## My Setup
- Agent: [Claude Code / Cursor / custom]
- Google Workspace account type: [personal Gmail / Workspace business]
- Primary use cases (pick your top 3):
  1. Read/search Google Docs for project specs
  2. Update Google Sheets (tracking, data)
  3. Search Gmail for context (client emails, notifications)
  4. Create/check Calendar events
  5. Manage Google Drive files
  6. Access Google Meet recordings/notes

## Your Task

1. **Setup Guide**: Step-by-step to configure `gws` MCP server:
   - Installation
   - OAuth scope selection (MINIMAL permissions for my use cases)
   - MCP server configuration
   - Test connection

2. **Security Audit**: For my selected use cases:
   - What OAuth scopes are needed (and ONLY those)?
   - What data the agent CAN'T access with this config?
   - Recommended: read-only vs read-write per service
   - How to set up scope boundaries

3. **Workflow Templates**: For each of my use cases, create a workflow:
   - Trigger: what agent command or context activates it
   - Steps: what MCP tools get called in sequence
   - Output: what the agent returns to me
   - Example: real prompt → expected behavior

4. **Token Optimization**: 
   - Use progressive disclosure (don't load all Workspace tools at once)
   - Group tools by workflow, not by Google service
   - Estimated token budget for my use cases

## Rules
- MINIMUM permissions always — principle of least privilege
- Never grant write access unless explicitly needed for a use case
- Include a "panic" command to revoke all agent access instantly
- All sensitive data (auth tokens) must stay local, never in prompts
```

## Example Workflows

### "Check my calendar before standup"
```
Agent, check my Google Calendar for today and tomorrow. 
Summarize: meetings, free blocks, any conflicts.
```

### "Find that design doc"
```
Search Google Drive for the authentication redesign doc 
from last week. Summarize the key decisions.
```

### "Log hours to the sheet"
```
Add a row to the "Time Tracking" sheet: 
today's date, 3 hours, "API refactor", project="backend-v2"
```

## Security First

The prompt enforces minimal permissions by design:
- Starts with read-only access
- Escalates to write only when needed
- Includes revocation workflow
- Never exposes OAuth tokens to the model

---

> 🔥 **Want the full Google Workspace Agent Pipeline?** The PRO version includes: multi-account orchestration, automated permission auditing, cross-service workflows (e.g., "email summary → calendar block → doc update"), batch operations, and compliance templates for team deployments.  
> **[Get the AI Dev Toolkit — $9](https://ai-dev-toolkit-five.vercel.app)** — 90+ production-ready frameworks for AI-powered development.
