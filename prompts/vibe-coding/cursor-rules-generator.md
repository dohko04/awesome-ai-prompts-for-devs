# ⚡ Cursor AI Rules Generator

> **Category:** Vibe Coding · **Works with:** ChatGPT, Claude, Gemini  
> **Trending:** March 2026 — Cursor is the fastest-growing AI-powered IDE

## The Prompt

```
Generate a `.cursor/rules` configuration for my project. Here's my stack:

**Language:** [e.g., TypeScript]
**Framework:** [e.g., Next.js 15, App Router]
**Styling:** [e.g., Tailwind CSS v4]
**Database:** [e.g., PostgreSQL + Drizzle ORM]
**Testing:** [e.g., Vitest + Playwright]
**Deployment:** [e.g., Vercel]

Generate rules following this structure:

## Rule Format
Each rule should be a separate `.mdc` file in `.cursor/rules/` with:
- A clear description of WHEN it applies (glob pattern or context)
- Concise, actionable instructions (not essays)
- Real code examples for patterns you want enforced

## Must Include Rules For:
1. **Code style** — naming conventions, file structure, imports order
2. **Framework patterns** — the RIGHT way to use [framework] (e.g., Server Components by default, 'use client' only when needed)
3. **Error handling** — standard error patterns for this stack
4. **Database** — query patterns, migration conventions
5. **Testing** — test file naming, what to test, what to mock
6. **Git** — commit message format, branch naming

## Quality Criteria:
- Each rule must be <50 lines (Cursor loads them into context — keep them lean)
- Use glob patterns to auto-attach rules: `*.test.ts`, `src/api/**`, etc.
- Include ONE good example and ONE anti-pattern per rule
- No generic advice — every rule must be specific to MY stack
```

## How to Use

1. Replace the bracketed values with your actual stack
2. Paste into ChatGPT/Claude/Gemini
3. Copy generated `.mdc` files into `.cursor/rules/`
4. Cursor auto-loads relevant rules based on file context

## Example Output (snippet)

```markdown
<!-- .cursor/rules/nextjs-components.mdc -->
---
description: Next.js component patterns
globs: ["src/app/**/*.tsx", "src/components/**/*.tsx"]
---

- Default to Server Components. Only add 'use client' when using hooks, event handlers, or browser APIs.
- Colocate loading.tsx and error.tsx with page.tsx in route folders.

✅ Good:
export default async function UsersPage() {
  const users = await db.query.users.findMany();
  return <UserList users={users} />;
}

❌ Bad:
'use client'
export default function UsersPage() {
  const [users, setUsers] = useState([]);
  useEffect(() => { fetch('/api/users')... }, []);
}
```

---

> 💡 **This is 1 of 27 free prompts.** The [Full AI Dev Toolkit](https://ai-dev-toolkit-five.vercel.app) includes **100+ prompts** with complete `.cursor/rules` templates for 10+ popular stacks (Next.js, Django, Rails, Go, Rust, and more), plus advanced Cursor workflows — **$9 one-time**.
>
> [**Get the Full Toolkit →**](https://ai-dev-toolkit-five.vercel.app)
