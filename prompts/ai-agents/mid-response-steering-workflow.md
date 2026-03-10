# 🎯 Mid-Response Steering Workflow

Leverage GPT-5.4's mid-response steering to guide AI through complex tasks in real-time — adjusting course while the model is still thinking, instead of waiting for a bad output and starting over.

## The Prompt

```
You are a Task Planning AI using mid-response steering. Before executing anything, you MUST first present an upfront plan.

## My Task
{TASK_DESCRIPTION}

## Your Process

### Step 1: Present Your Plan (BEFORE doing anything)
Show me a numbered plan of what you intend to do:

📋 **Proposed Plan:**
1. [First major step] — estimated effort/tokens
2. [Second major step] — estimated effort/tokens  
3. [Third major step] — estimated effort/tokens
...

⚡ **Decision Points** (where I might want to redirect):
- After step {N}: [what might change here]
- After step {N}: [alternative path available]

**Total estimated thinking tokens**: ~{estimate}
**Approach**: {conservative | balanced | exploratory}

### Step 2: Wait for My Steering Input
I will respond with one of:
- ✅ "Go" — execute the full plan
- 🔄 "Adjust {step}" — modify a specific step before proceeding
- ❌ "Scrap and replan" — throw away this plan, start fresh  
- ✂️ "Skip to {step}" — skip earlier steps
- 🎚️ "More detail on {step}" — expand a step before committing

### Step 3: Execute with Checkpoints
After each major step, briefly show:
- ✅ What was completed
- 📊 Key result/finding from this step
- ➡️ Proceeding to step {N} (or "🛑 Unexpected finding: {detail} — should I continue or adjust?")

This lets me course-correct mid-execution without wasting tokens.
```

## Example Usage

**Task**: "Refactor our authentication module from session-based to JWT, maintaining backward compatibility"

The AI would first present a plan (e.g., "1. Audit current auth flow, 2. Design JWT schema, 3. Write migration layer..."), then you steer: "Skip the audit, I already know the flow — here's the current schema: {...}".

## When to Use

- Complex refactoring or architecture tasks
- Research + implementation workflows
- Any task where you've seen AI go down the wrong path
- Multi-file changes where early decisions affect later steps

## Tips

- Works best with GPT-5.4 Thinking mode (shows internal plan)
- For shorter tasks (<500 tokens output), skip steering — overhead isn't worth it
- Combine with system-level instructions for consistent steering behavior

---

> 💡 **Want the production-ready version?** The [AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app) includes the **Adaptive Steering Pipeline Pro** with: multi-model steering chains (use cheap models for planning, expensive for execution), automated steering rules engine, token budget optimization, batch steering for CI/CD pipelines, and reusable steering templates for 15+ common dev workflows.
