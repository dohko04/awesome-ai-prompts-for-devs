# MCP Enterprise Integration Architect

> 🔥 **Trending (March 2026):** MCP hit 97M+ SDK downloads and joined the Linux Foundation. Every enterprise is now connecting their entire tech stack through MCP. This prompt designs your organization's MCP integration strategy.

## The Prompt

```markdown
You are an enterprise architect specializing in MCP (Model Context Protocol) integrations. Help me design an MCP integration plan for my organization.

## My Current Stack
- **Internal tools:** [e.g., Jira, Confluence, Slack, custom dashboards]
- **Data sources:** [e.g., PostgreSQL, S3, Snowflake, internal APIs]
- **AI tools in use:** [e.g., Claude Code, Cursor, Copilot]
- **Team size:** [number of developers]

## What I Need
1. **MCP Server inventory** — Which of my tools need MCP servers? Prioritize by impact.
2. **Authentication layer** — Design OAuth2/API key management for MCP connections
3. **Data governance** — What data should/shouldn't flow through MCP? Build a classification
4. **Rollout plan** — Phase 1 (quick wins) → Phase 2 (core systems) → Phase 3 (full integration)

## Output Format
For each MCP server recommendation:
- Server name & purpose
- Data it exposes (read/write capabilities)
- Security considerations
- Implementation complexity (low/med/high)
- Expected developer productivity gain

Also provide a `mcp_config.json` template connecting the top 3 priority servers.
```

## Sample Output (Preview)

The full prompt generates a complete enterprise MCP blueprint including:
- ✅ Prioritized server inventory with ROI estimates
- ✅ Security architecture with least-privilege access
- ✅ Phased rollout timeline
- ✅ Ready-to-use config templates

> 💡 **Want the full version?** The complete prompt includes pre-built configs for 15+ enterprise tools (Jira, GitHub, Slack, Datadog, PagerDuty, etc.) plus a security audit checklist.
>
> 👉 **[Get the AI Dev Toolkit — 55+ pro prompts for $9](https://ai-dev-toolkit-five.vercel.app)** — Pay with ETH, instant access.

---
*Part of [Awesome AI Prompts for Devs](https://github.com/dohko04/awesome-ai-prompts-for-devs) · Built by [Dohko](https://github.com/dohko04)*
