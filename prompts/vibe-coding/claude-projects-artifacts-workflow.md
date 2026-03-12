# Claude Projects & Artifacts Dev Workflow

> Leverage Claude's newly-free Projects and Artifacts features for organized, reusable dev workflows.

**Why now:** As of March 2026, Anthropic made Projects and Artifacts available on Claude's free plan — previously Pro-only features that let you persist context and generate interactive outputs.

## The Prompt

```
You are my development assistant inside a Claude Project. This project contains my codebase context, coding standards, and architecture docs.

CONTEXT RULES:
1. Always reference Project Knowledge files before answering
2. Generate code as Artifacts (type: application/vnd.ant.code) so I can copy/iterate
3. When I upload a file, analyze it against existing Project Knowledge first
4. Maintain consistency with the coding standards in this project

WORKFLOW:
- For new features → generate as Code Artifact with tests
- For debugging → reference project files, show diff as Artifact
- For architecture decisions → create Markdown Artifact with ADR format
- For API design → generate OpenAPI spec as Artifact

ARTIFACT NAMING:
- [component]-[type]-[version] (e.g., auth-service-v2, api-schema-v1)

Always explain WHY you chose an approach based on the project context, not just generic best practices.
```

## How to Use

1. **Create a Project** in Claude with your repo's key files (README, architecture docs, coding standards)
2. **Set this as the Project Instructions** (system prompt)
3. **Upload files** as Project Knowledge — they persist across conversations
4. **Every conversation** in the project automatically has full context

## Project Knowledge Suggestions

| File | Purpose |
|------|---------|
| `README.md` | Project overview & setup |
| `ARCHITECTURE.md` | System design decisions |
| `.cursorrules` or `AGENTS.md` | Coding standards |
| `package.json` / `pyproject.toml` | Dependencies context |
| `schema.prisma` / `models.py` | Data model reference |

## Example Output

Ask: "Add rate limiting to the API gateway"

Claude generates a **Code Artifact** with the implementation that matches your project's existing patterns, plus a **Markdown Artifact** with the ADR documenting the decision.

## Limitations (Free Plan)

- Projects: limited number of projects and knowledge files
- Artifacts: full functionality but with free-tier message limits
- For heavy usage, team workflows, and API access → need Pro plan

---

> 💡 **Want the full system?** The [AI Dev Toolkit](https://dohko04.gumroad.com/l/ai-dev-toolkit) includes a complete Claude Projects production workflow with 12 project templates, artifact patterns for every dev task, and team onboarding guides. $9 one-time.
