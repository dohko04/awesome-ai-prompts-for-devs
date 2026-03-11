# Gemini Workspace Automation Builder

> Design AI-powered automations using Google's new Gemini Workspace integration (March 2026) — cross-file context, smart drafting, and data-connected workflows across Docs, Sheets, Slides and Drive.

## Why This Matters Now

As of March 11, 2026, Google rolled out deep Gemini integration into Workspace for AI Ultra and Pro subscribers. Gemini can now:

- **Pull context from your files and emails** to generate documents
- **Create entire spreadsheets** from natural language descriptions
- **Build presentations** that reference your existing Drive content
- **Answer questions about your Drive** without opening files

This changes how developers build internal tools, automate reporting, and create data pipelines using Google Workspace as the substrate.

## Prompt

```markdown
You are a Google Workspace Automation Architect specializing in Gemini-powered workflows.

I need to automate the following workflow using Gemini's new Workspace capabilities:

**My workflow:** {{DESCRIBE_YOUR_WORKFLOW}}
**Data sources:** {{LIST_GOOGLE_DRIVE_FILES_SHEETS_DOCS_EMAILS}}
**Output format:** {{DOCS/SHEETS/SLIDES/COMBINED}}
**Frequency:** {{ONE_TIME/DAILY/WEEKLY/ON_TRIGGER}}

Design a complete Gemini Workspace automation:

1. **Source Mapping**
   - Which files/emails should Gemini reference?
   - What context connections matter (e.g., Sheet A feeds Doc B)?
   - Privacy considerations — what should NOT be included?

2. **Prompt Chain Design**
   - Write the exact Gemini prompts for each step
   - Include source selection instructions (the "@" mention syntax)
   - Handle edge cases (missing data, conflicting sources)

3. **Output Template**
   - Structure the final output (Doc/Sheet/Slides)
   - Include formatting instructions Gemini should follow
   - Add validation checkpoints

4. **Integration Points**
   - How to trigger this via Apps Script or API
   - How to chain multiple Gemini operations
   - Error handling when Gemini can't access a source

Provide the complete automation blueprint with copy-paste prompts.
```

## Example Use Cases

### Weekly Team Report Automation
```
My workflow: Generate a weekly team status report every Friday
Data sources: Team standup notes (Google Doc), Sprint board export (Sheet), Last week's report (Doc)
Output format: Google Doc with executive summary + detailed breakdown
Frequency: Weekly (Friday 4pm)
```

### Client Proposal Generator
```
My workflow: Create client proposals from meeting notes and pricing sheets
Data sources: Meeting transcript (Doc), Pricing matrix (Sheet), Proposal template (Doc), Company overview (Slides)
Output format: Google Doc proposal + Google Slides presentation
Frequency: On trigger (after client meeting)
```

## Limitations of the Free Version

This prompt gives you the core automation design pattern. The **[Pro version ($9)](https://dohko04.gumroad.com/l/ai-dev-toolkit)** includes:

- 🔧 **Complete Apps Script templates** for scheduling Gemini automations
- 🔗 **Multi-step pipeline orchestrator** — chain 5+ Gemini operations with error recovery
- 📊 **Token cost calculator** for Workspace API calls
- 🏗️ **Production patterns** — retry logic, rate limiting, audit logging
- 🔄 **Comparison matrix**: Gemini Workspace vs. Notion AI vs. Copilot for enterprise

---

*Part of the [AI Dev Toolkit](https://dohko04.gumroad.com/l/ai-dev-toolkit) — 90+ production-ready AI/dev resources for $9.*
