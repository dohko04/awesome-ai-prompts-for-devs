# 🌐 World AgentKit — Human Verification for AI Agents

> Build AI agents that can prove a real human is behind their actions using World ID + x402 protocol.

## The Prompt

```
You are an AI AGENT IDENTITY ARCHITECT. Help me integrate World AgentKit into my AI agent system so agents can verify human identity before performing sensitive actions (purchases, account changes, data access).

## Context
World AgentKit (by Tools for Humanity, March 2026) enables:
- Proof-of-humanity via World ID (iris/biometric verification)
- Integration with x402 protocol (Coinbase + Cloudflare) for agent commerce
- Merchants can require human verification before processing agent requests

## Your Task

### 1. Architecture Assessment
Analyze my agent system and identify:
- Which agent actions need human verification (purchases, auth, PII access)
- Which can remain autonomous (search, read-only, caching)
- Risk tiers: LOW (no verification) → MEDIUM (session token) → HIGH (real-time World ID)

### 2. Integration Blueprint
Design the verification flow:
```
Agent Request → Action Classifier → Risk Tier Check
  → LOW: proceed directly
  → MEDIUM: cached World ID session (TTL: 1h)
  → HIGH: real-time World ID verification via AgentKit SDK
    → x402 payment authorization (if commerce)
    → Execute action with proof-of-humanity header
```

### 3. Implementation Skeleton
Provide starter code for:
- AgentKit SDK initialization
- World ID verification middleware
- x402 payment flow integration
- Action classification function

### 4. Security Checklist
- [ ] World ID tokens validated server-side (never trust client)
- [ ] x402 payment limits enforced per-agent
- [ ] Verification results cached with short TTL
- [ ] Fallback flow when World ID service is unavailable
- [ ] Audit log for all verified vs. unverified actions

## Input
Agent system: {{AGENT_DESCRIPTION}}
Actions requiring verification: {{ACTION_LIST}}
Commerce enabled: {{YES/NO}}
```

## Example Usage

**Input:**
```
Agent system: Shopping assistant that browses products and makes purchases
Actions requiring verification: checkout, payment, address change
Commerce enabled: YES
```

## When to Use
- Building AI agents that transact on behalf of users
- E-commerce platforms accepting agent traffic
- Any system where you need proof a human authorized an agent's action

---

> 🔒 **Want the full production pipeline?** The [AI Dev Toolkit PRO](https://ai-dev-toolkit-five.vercel.app) includes: TypeScript/Python SDK integration, x402 payment orchestrator, multi-agent verification architecture, Grafana monitoring, and CI/CD compliance gates.
