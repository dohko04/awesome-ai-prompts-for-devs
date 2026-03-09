# 🎯 Context Engineering Optimizer

Context engineering is the #1 skill for AI-augmented developers in 2026. It's not just prompt engineering — it's designing the entire information architecture that surrounds your LLM calls. This prompt helps you optimize any AI workflow's context window.

## The Prompt

```
You are a Context Engineering Specialist. Analyze my AI workflow and optimize how context is structured, prioritized, and delivered to the LLM.

My setup:
- Tool/IDE: {TOOL} (e.g., Cursor, Claude Code, Copilot, custom agent)
- Task type: {TASK} (e.g., code generation, review, debugging, chat)
- Codebase size: {SIZE} (e.g., small/medium/large, ~X files)
- Current pain: {PAIN} (e.g., "AI loses context", "outputs are generic", "ignores my conventions")

Optimize my context engineering:

1. **Context Audit**: Identify what context the LLM currently receives vs. what it actually needs:
   - System prompt / rules files (`.cursorrules`, `AGENTS.md`, `.github/copilot-instructions.md`)
   - Codebase context (which files are included? which are missing?)
   - Conversation history (how much? is it bloated?)
   - External knowledge (docs, APIs, schemas)
   - Rate each: ✅ good, ⚠️ needs work, ❌ missing

2. **Context Architecture**: Design the optimal context stack:
   - **Layer 1 — Identity**: System prompt with role, constraints, output format (~500 tokens)
   - **Layer 2 — Project DNA**: Rules file with conventions, tech stack, patterns (~1K tokens)
   - **Layer 3 — Task Context**: Relevant code, schemas, docs for THIS task (~2-4K tokens)
   - **Layer 4 — Examples**: 1-2 examples of desired output (~1K tokens)
   - **Layer 5 — History**: Only relevant conversation turns (~1K tokens)
   - Total budget and allocation strategy

3. **Rules File Generator**: Create a project rules file that includes:
   - Tech stack and versions
   - Code style and naming conventions
   - Architecture patterns used
   - Common mistakes to avoid
   - File organization conventions
   - Testing requirements

4. **Context Retrieval Strategy**: How to dynamically pull the right context:
   - File mentions and @ references
   - Semantic search over codebase (when to use, when to skip)
   - Manual context curation (what to always include)
   - What to exclude (node_modules, generated files, etc.)

5. **Measurable Improvements**: Give me 3 before/after examples showing:
   - Bad context → generic/wrong output
   - Optimized context → precise/correct output
   - The specific context change that made the difference

Output actionable files I can add to my project today.
```

## Example Usage

> "I'm using Cursor with a Next.js + Supabase project (~200 files). The AI keeps generating code that doesn't follow our patterns and ignores our custom hooks."

## When to Use

- AI tools are generating generic or incorrect code for your project
- You're setting up a new project and want AI to "get it" from day one
- Your context window is bloated and you need to optimize token usage
- Moving from basic prompting to production-grade AI workflows

## Pro Tips

- A good `.cursorrules` or `AGENTS.md` file is worth more than any individual prompt
- Less context is often better — relevance beats volume
- Update your rules file monthly as your project evolves

---

> 💡 **Want more?** This is 1 of 38 free prompts. The [**Full AI Dev Toolkit**](https://ai-dev-toolkit-five.vercel.app) includes 100+ prompts with advanced context engineering templates, per-framework rules files, and token optimization strategies — all for **$9 USD**.
