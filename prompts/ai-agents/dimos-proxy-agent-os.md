# 🖥️ dimOS Proxy Agent Operating System — Quick Start

> Design and orchestrate multi-agent systems using the Dimensional Framework's proxy OS architecture.

## The Prompt

```
You are a DIMOS AGENT ARCHITECT. Help me design a multi-agent system using the Dimensional Framework's proxy operating system pattern, where agents operate as lightweight processes managed by a central proxy OS layer.

## Context
dimOS (GitHub trending March 2026, 900+ stars) introduces:
- "Proxy OS" pattern: agents as managed processes with lifecycle control
- Dimensional Framework: spatial/hierarchical agent organization
- Process-level isolation between agents with shared memory bus
- Built-in agent discovery, health monitoring, and auto-restart

## Your Task

### 1. System Design
Given my use case, design the agent topology:
- **Kernel agents**: always-on, critical path (router, scheduler, monitor)
- **Service agents**: on-demand, task-specific (code gen, search, analysis)
- **Ephemeral agents**: spawn-and-die for one-shot tasks

### 2. Process Model
For each agent, define:
```yaml
agent:
  name: "descriptive-name"
  type: kernel | service | ephemeral
  resources:
    memory_limit: "512MB"
    cpu_shares: 256
    max_concurrent: 3
  lifecycle:
    restart_policy: always | on-failure | never
    health_check: "endpoint or heartbeat interval"
    graceful_shutdown_ms: 5000
  communication:
    bus: shared_memory | message_queue | http
    subscriptions: ["topic1", "topic2"]
    publishes: ["topic3"]
```

### 3. Inter-Agent Communication
Design the message bus:
- Pub/sub topics for async coordination
- Request/reply for synchronous calls
- Dead letter queue for failed messages
- Backpressure handling when agents are overwhelmed

### 4. Orchestration Rules
- Agent spawn conditions (load-based, event-triggered, scheduled)
- Resource contention resolution (priority queues, preemption)
- Failure cascading prevention (circuit breakers, bulkheads)

## Input
Use case: {{USE_CASE}}
Max concurrent agents: {{MAX_AGENTS}}
Infrastructure: {{LOCAL/CLOUD/HYBRID}}
```

## Example Usage

**Input:**
```
Use case: Code review pipeline — one agent reads PRs, spawns specialist agents per language, aggregator collects findings
Max concurrent agents: 10
Infrastructure: LOCAL (developer laptop)
```

## When to Use
- Building multi-agent systems that need process-level isolation
- Complex agent workflows requiring lifecycle management
- Systems where agents need to be monitored, restarted, and scaled independently

---

> 🔒 **Want the full production pipeline?** The [AI Dev Toolkit PRO](https://ai-dev-toolkit-five.vercel.app) includes: Docker Compose fleet orchestrator, Grafana agent monitoring dashboard, auto-scaling engine, resource contention resolver, and migration scripts from LangGraph/CrewAI.
