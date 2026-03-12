# 🍎 Xcode Agent Skills Quick Start

> **When to use:** You're building iOS/macOS apps and want AI agents (Claude Code, Codex, Gemini) to write better Swift/SwiftUI code using agent skills.

## What Are Agent Skills?

Agent skills are instruction files that teach AI coding agents domain-specific patterns. Unlike generic prompts, they encode **years of framework expertise** — deprecated APIs, performance patterns, accessibility checks, concurrency best practices.

Xcode 26.3 supports agent skills natively via the Intelligence tab. But they also work with Claude Code, Codex CLI, and any MCP-compatible agent.

## Quick Setup (Xcode 26.3)

```
1. Open Xcode → Settings → Intelligence tab
2. Configure your preferred agent (Claude, Codex, or custom)
3. Add agent skills from: github.com/twostraws/swift-agent-skills
4. Skills are stored in .cursor/rules/ or .agent-skills/ at project root
```

## Prompt: Create Your Own Agent Skill

```markdown
You are an expert iOS engineer. Create an agent skill file for [FRAMEWORK].

The skill should:
1. Define the agent's role and expertise area
2. List deprecated APIs to NEVER use (with replacements)
3. Include performance patterns specific to [FRAMEWORK]
4. Add accessibility requirements
5. Include concurrency best practices (Swift 6 strict mode)

Format as a markdown instruction file with clear sections:
- Role Definition
- Rules (ALWAYS/NEVER)
- Code Patterns (with examples)
- Common Mistakes to Avoid

Frameworks to choose from:
- SwiftUI (Liquid Glass, new APIs)
- SwiftData (vs Core Data migration)
- Swift Testing (vs XCTest migration)
- Foundation Models (on-device AI)
- Swift Concurrency (actors, sendable)
```

## Example: SwiftUI Agent Skill (Starter)

```markdown
# SwiftUI Agent Skill

## Role
You are a SwiftUI expert targeting iOS 26+.

## Rules
- ALWAYS use `@Observable` macro (not ObservableObject)
- NEVER use `NavigationView` (use `NavigationStack`)  
- ALWAYS add `.accessibilityLabel()` to interactive elements
- Use Liquid Glass material where appropriate for iOS 26

## Patterns
### ✅ Correct
@Observable class ViewModel { var items: [Item] = [] }

### ❌ Deprecated  
class ViewModel: ObservableObject { @Published var items: [Item] = [] }
```

## Limitations (Free Version)

This starter covers basic skill creation. For production use, you need:
- Multi-framework skill orchestration (SwiftUI + SwiftData + Concurrency together)
- Auto-detection of deprecated APIs across your entire codebase
- MCP server integration for Xcode agent pipelines
- Team-wide skill distribution and versioning
- Pre-built skills for 8+ Apple frameworks

---

> 🔥 **Want the complete Xcode Agent Skills Production Pipeline?** Get all 8 framework skills + MCP integration + team distribution system → [AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app)
