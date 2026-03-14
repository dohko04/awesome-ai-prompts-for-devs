# AI Code Hallucination Detector

> **Trending:** March 14, 2026 (Guardian exposé on Amazon Kiro) | **Category:** Core Dev

## The Problem

AI coding agents hallucinate. They import packages that don't exist, call APIs that were never real, and generate config options they invented. This is the #1 reliability issue in AI-augmented development.

## The 7 Types of Code Hallucinations

1. **Phantom Imports** — Importing packages that don't exist
2. **Invented APIs** — Calling methods that aren't real (e.g., `prisma.user.findManyAndCount()`)
3. **Stale Patterns** — Using deprecated APIs from older versions
4. **Config Fabrication** — Inventing configuration options
5. **Plausible Nonsense** — Code that compiles but has subtle logic errors
6. **Documentation Drift** — Comments that don't match the code
7. **Security Hallucinations** — Generating insecure code that looks secure

## Quick Check: Add to Your RULES.md

```markdown
## Anti-Hallucination Rules
1. NEVER import a package without checking it exists in package.json
2. NEVER call an API method without verifying it exists in the library's types
3. ALWAYS check the installed version, not your training data
4. Flag uncertainty: "I think this API exists but please verify"
```

## Basic Phantom Import Detector

```bash
# Check if all imports resolve to installed packages
grep -rn "from ['\"]" --include="*.ts" src/ | \
  grep -v node_modules | \
  grep -v "from ['\"]\./" | \
  sed "s/.*from ['\"]//; s/['\"].*//" | \
  sort -u | while read pkg; do
    BASE=$(echo "$pkg" | sed 's|/.*||')
    [ ! -d "node_modules/$BASE" ] && echo "❌ PHANTOM: $pkg"
  done
```

---

> 🔒 **Want the full detection pipeline?** The PRO version includes: TypeScript AST API checker, pre-commit hooks, hallucination scoring dashboard, CI/CD GitHub Actions workflow, and prevention prompt templates.
>
> **[Get the AI Dev Toolkit — $9 USD](https://ai-dev-toolkit-five.vercel.app)**
