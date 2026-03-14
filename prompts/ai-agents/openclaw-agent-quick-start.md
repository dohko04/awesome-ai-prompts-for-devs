# OpenClaw Agent Quick Start

> Deploy your own always-on AI agent using OpenClaw — the fastest-growing open-source AI framework (302K+ GitHub stars, featured at GTC 2026 Build-a-Claw).

## Why This Matters (March 2026)

OpenClaw is the #1 open-source AI agent framework. NVIDIA is featuring it at GTC 2026 with a "Build-a-Claw" event where attendees deploy personal always-on agents. With 302K+ stars and adoption by companies from Silicon Valley to Beijing, OpenClaw is becoming the standard for persistent, tool-using AI agents.

## The Prompt

```
You are an expert in OpenClaw, the open-source AI agent framework (302K+ GitHub stars).

I want to build a personal always-on AI agent for: [DESCRIBE PURPOSE - e.g., code review, inbox management, project tracking, DevOps monitoring]

My setup:
- Preferred LLM provider: [OpenAI/Anthropic/local Ollama]
- Messaging platform: [Telegram/Discord/Slack]
- Main tools I use: [GitHub, Linear, Notion, etc.]

Help me build a complete OpenClaw agent:

1. **Agent Identity (SOUL.md):**
   - Define the agent's personality, expertise, and communication style
   - Set clear boundaries (what it should/shouldn't do autonomously)
   - Define proactive behaviors (when to reach out vs stay silent)

2. **Tool Configuration:**
   - Which OpenClaw skills to enable for my use case
   - MCP server connections for my tools
   - File system access scope (what directories it can read/write)
   - API integrations setup

3. **Always-On Behavior:**
   - Heartbeat configuration (what to check periodically)
   - Cron jobs for scheduled tasks
   - Message channel setup (how I'll communicate with it)
   - Memory system (daily notes + long-term MEMORY.md)

4. **Safety Rails:**
   - What requires my approval before acting
   - Rate limits on external actions (emails, API calls, deployments)
   - Data privacy rules (what never leaves the system)
   - Escalation triggers (when to alert me immediately)

Generate:
- A complete SOUL.md file
- A TOOLS.md with my specific integrations
- A HEARTBEAT.md with periodic check schedule
- Example cron job definitions for my top 3 automated tasks
```

## Example Output Structure

```
SOUL.md → Agent personality + rules
TOOLS.md → Integration configs
HEARTBEAT.md → Periodic check schedule
cron-jobs.md → 3 automated task definitions
```

## Quick Customization

| Use Case | Key Skills | Heartbeat Focus |
|-----------|-----------|-----------------|
| DevOps Monitor | exec, web_fetch | Server health, deploy status |
| Code Reviewer | GitHub MCP, exec | PR queue, CI failures |
| Inbox Manager | email skill | Unread count, urgent flags |
| Project Tracker | Linear/Notion MCP | Sprint progress, blockers |

## Tips

- Start with 1-2 skills, add more as you trust the agent
- Set heartbeat to every 30 min initially, adjust based on needs
- Always define "ask first" vs "do autonomously" boundaries
- Use `memory/YYYY-MM-DD.md` files to build agent context over time

---

> 🔒 **Want the full production pipeline?** The [AI Dev Toolkit Pro](https://ai-dev-toolkit-five.vercel.app) includes multi-agent orchestration, advanced memory architectures, skill development templates, deployment configs for cloud + local, and enterprise security patterns. 130+ production-ready frameworks for $9.

