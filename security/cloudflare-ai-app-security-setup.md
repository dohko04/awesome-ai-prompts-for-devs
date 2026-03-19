# Cloudflare AI App Security Layer Setup

> Cloudflare's AI Security for Apps went GA on March 18 2026 — a security layer that discovers and protects AI-powered applications regardless of model or hosting provider. Use this prompt to set up protection for your AI apps.

## The Prompt

```
You are a security engineer specializing in AI application protection.

I'm deploying AI-powered features in my application and need to set up a security layer that protects against prompt injection, data exfiltration, and model abuse.

My setup:
- Application type: [WEB_APP / API / AGENT]
- AI provider(s): [OpenAI / Anthropic / local / multi-provider]
- Hosting: [CLOUD_PROVIDER]
- Traffic volume: [REQUESTS_PER_DAY]

Help me configure:

1. **Discovery**: Scan my application to identify all AI-powered endpoints and data flows
2. **Input Validation**: Set up prompt injection detection rules for user inputs
3. **Output Filtering**: Configure PII/sensitive data leak prevention on AI responses
4. **Rate Limiting**: Design rate limits specific to AI endpoints (token-aware, not just request-based)
5. **Monitoring**: Set up alerts for anomalous AI usage patterns

For each configuration, provide the actual config/code, not just descriptions.
```

## What You Get (Free)
- Basic AI endpoint discovery checklist
- Simple input validation rules

## What the PRO Version Adds
The full **AI App Security Pipeline** ($9 in the AI Dev Toolkit) includes:
- 🛡️ Complete WAF rule set optimized for AI endpoints (Cloudflare, AWS WAF, nginx configs)
- 🔍 Automated AI endpoint discovery script (scans routes, detects hidden LLM calls)
- 🧪 Red team prompt injection test suite (50+ attack vectors with expected blocks)
- 📊 Grafana dashboard for AI security monitoring (token abuse, injection attempts, data leaks)
- 💰 Cost-based abuse detection (flags unusual token consumption patterns)

👉 **Get the full toolkit**: https://ai-dev-toolkit-five.vercel.app
