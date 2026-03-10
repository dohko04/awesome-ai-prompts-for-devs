# 🏗️ AI-Optimized Type System Designer

> **When to use:** You want to design TypeScript types and interfaces that maximize AI coding assistant effectiveness — making Copilot, Cursor, and Claude Code dramatically more accurate.

## The Prompt

```
You are a Type System Architect who specializes in designing types that make AI coding assistants (Copilot, Cursor, Claude Code) significantly more effective. TypeScript's rise to #1 language (GitHub Octoverse) is driven by the "AI convenience loop" — better types = better AI suggestions = more TypeScript adoption.

## My Codebase Context
- **Project type:** [web app / API / CLI / library]
- **Current type coverage:** [strict / partial / mostly `any`]
- **AI tools I use:** [Copilot / Cursor / Claude Code / other]
- **Domain:** [e-commerce / fintech / SaaS / DevTools / other]

## What I Need

Redesign my type system for maximum AI-assistability:

### 1. Self-Documenting Types
Transform vague types into ones that carry intent:

```typescript
// ❌ AI can't infer intent
type User = { status: string; role: string; }

// ✅ AI generates correct code instantly
type UserStatus = 'active' | 'suspended' | 'pending_verification';
type UserRole = 'admin' | 'editor' | 'viewer';
type User = { status: UserStatus; role: UserRole; }
```

### 2. Branded Types for Domain Safety
Create types that prevent AI from mixing up primitives:

```typescript
type UserId = string & { readonly __brand: 'UserId' };
type OrderId = string & { readonly __brand: 'OrderId' };
// AI can't accidentally pass OrderId where UserId is expected
```

### 3. Discriminated Unions for Workflow States
Model state machines so AI handles transitions correctly:

```typescript
type PaymentState =
  | { status: 'pending'; createdAt: Date }
  | { status: 'processing'; transactionId: string }
  | { status: 'completed'; receipt: Receipt }
  | { status: 'failed'; error: PaymentError; retryCount: number };
```

### 4. Function Signatures That Guide AI
Design function types that make AI generate correct implementations:

```typescript
// ❌ AI guesses wildly
function processOrder(data: any): any

// ✅ AI generates correct implementation
function processOrder(
  order: ValidatedOrder,
  payment: AuthorizedPayment
): Promise<Result<CompletedOrder, OrderProcessingError>>
```

## Analyze My Code
Here's a sample of my current types:
[paste types or describe your domain]

Give me:
1. Redesigned types optimized for AI code generation
2. Specific examples of how each change improves AI suggestions
3. A migration path from current types to AI-optimized ones
```

## Why This Works

GitHub's 2025 Octoverse data confirms the "AI convenience loop": TypeScript surged 66% to become the #1 language specifically because static types act as guardrails for LLMs. This prompt helps you design types that exploit this loop — the better your types, the more accurate your AI tools become, the faster you ship.

## Key Principles

| Principle | Before (AI struggles) | After (AI excels) |
|---|---|---|
| Literal unions over strings | `type: string` | `type: 'create' \| 'update' \| 'delete'` |
| Branded primitives | `id: string` | `id: UserId` |
| Discriminated unions | `if (order.paid)` | `switch (order.status)` |
| Result types | `throws Error` | `Result<T, E>` |

---

> 🔥 **Want the complete AI-Native Type Engineering System?** The [AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app) includes: full type migration pipeline, AI-optimized monorepo type architecture, Zod schema generation workflows, type coverage audit tools, and advanced patterns (template literals, conditional types, mapped types) that make AI assistants 3-5x more accurate in your codebase.
