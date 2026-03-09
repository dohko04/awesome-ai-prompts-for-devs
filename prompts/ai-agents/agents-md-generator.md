# 📋 AGENTS.md / Project Rules Generator

> Claude Code is the #1 AI coding tool in 2026. The key to getting great results? A well-crafted AGENTS.md file. This prompt generates one for any project.

## The Prompt

```markdown
You are a Project Rules Generator for AI coding assistants. Given a project description, generate a comprehensive AGENTS.md (for Claude Code) or equivalent rules file.

## Project Info
- **Name:** {{PROJECT_NAME}}
- **Language/Framework:** {{TECH_STACK}}
- **Description:** {{PROJECT_DESCRIPTION}}
- **Team Size:** {{TEAM_SIZE}}

## Generate Rules For:

### 1. Code Style & Conventions
Based on the tech stack, define:
- Naming conventions (files, variables, functions, classes)
- Import ordering
- Error handling patterns
- Logging standards

### 2. Architecture Rules
- Directory structure expectations
- Where new files should go
- Module boundaries (what imports what)
- API patterns (REST conventions, response formats)

### 3. Testing Requirements
- Test file naming and location
- Minimum coverage expectations
- Test patterns (unit, integration, e2e)
- What MUST be tested vs what's optional

### 4. Git & PR Rules
- Branch naming convention
- Commit message format
- PR description template
- What requires review vs auto-merge

### 5. AI-Specific Instructions
- Things the AI should NEVER do (e.g., "don't delete migrations")
- Preferred approaches (e.g., "use composition over inheritance")
- Context files to always read first
- Common mistakes to avoid in this codebase

## Output Format
Generate a complete AGENTS.md file in markdown, ready to drop into the project root.
```

## Example Output (React + TypeScript)

```markdown
# AGENTS.md

## Project: MyApp
React 19 + TypeScript + Vite + TailwindCSS

## Code Style
- Use functional components only
- Name components in PascalCase: `UserProfile.tsx`
- Use `const` arrow functions for components
- Colocate styles: component + styles in same directory
- Imports order: react → external → internal → types → styles

## Architecture
```
src/
  components/    # Shared UI components
  features/      # Feature-based modules
  hooks/         # Custom hooks
  lib/           # Utilities and helpers
  types/         # Shared TypeScript types
```

## Testing
- Tests next to source: `Component.test.tsx`
- Use React Testing Library (not Enzyme)
- Test behavior, not implementation
- Every new component needs at least 1 test

## AI Rules
- NEVER modify `src/lib/auth.ts` without asking
- ALWAYS use the existing `useApi` hook for API calls
- PREFER server components where possible
- READ `docs/ARCHITECTURE.md` before major changes
```

## Supported Frameworks

Works great for: React, Next.js, Python/Django, FastAPI, Node/Express, Go, Rust, Ruby on Rails, and more.

## 💡 Want More?

The **[AI Dev Toolkit](https://github.com/dohko04/ai-dev-toolkit)** ($9) includes:
- 🏗️ **15+ pre-built AGENTS.md templates** for popular stacks
- 🔄 **Auto-generator script** that analyzes your codebase and creates rules
- 🎯 **Cursor Rules + Copilot Instructions** equivalents for all templates
- 📊 **Rules effectiveness tracker** to measure AI output quality improvement

---

*Part of [Awesome AI Prompts for Devs](https://github.com/dohko04/awesome-ai-prompts-for-devs) by Dohko*
