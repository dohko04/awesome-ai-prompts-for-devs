# DGX Spark + OpenClaw Local Agent Builder

> Build always-on, local-first AI agents on NVIDIA DGX Spark — no cloud required. Based on NVIDIA's GTC 2026 Build-a-Claw event and OpenClaw Playbook.

## Context

NVIDIA's DGX Spark ($3,000, Grace Blackwell desktop) + OpenClaw (fastest-growing open-source agent framework) enables developers to run persistent AI agents locally. This prompt helps you design and deploy your first local agent.

## The Prompt

```
You are a local AI agent architect specializing in NVIDIA DGX Spark deployments.

I want to build an always-on AI agent that runs locally on DGX Spark hardware.

**My use case:** [DESCRIBE: e.g., "code review agent that monitors my repos", "personal research assistant that tracks arxiv papers", "DevOps agent that monitors my infrastructure"]

Help me design this agent:

1. **Agent Definition**
   - Name and personality for the agent
   - Core capabilities (3-5 tools it needs)
   - Communication channel (Telegram, Discord, Slack, etc.)

2. **Local Architecture**
   - Which local LLM to run on DGX Spark (128GB unified memory)
   - Memory/context strategy for always-on operation
   - Tool integration plan (files, APIs, databases)

3. **OpenClaw Configuration**
   - Basic SOUL.md template for the agent's personality
   - HEARTBEAT.md for proactive behavior
   - Tool permissions and safety boundaries

4. **Deployment Checklist**
   - Hardware requirements check
   - Network/firewall setup for messaging integration
   - Monitoring and restart strategy

Output a complete setup guide I can follow in under 30 minutes.
```

## Example Output

The prompt generates a structured deployment plan including agent personality, local model selection (e.g., Llama 4 70B or Nemotron on DGX Spark), OpenClaw config files, and a step-by-step setup checklist.

## When to Use

- You have or plan to buy DGX Spark hardware
- You want AI agents that don't depend on cloud APIs
- Privacy-sensitive workflows (medical, legal, financial data)
- After attending GTC 2026 Build-a-Claw workshop

## Limitations

This free version covers single-agent local deployment. For multi-agent teams, cost optimization across local+cloud hybrid, production monitoring dashboards, and enterprise security configs, see the **[AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app)** — 170+ production-ready frameworks.

---

*Part of [Awesome AI Prompts for Devs](https://github.com/dohko04/awesome-ai-prompts-for-devs) — Free samples from the AI Dev Toolkit.*
