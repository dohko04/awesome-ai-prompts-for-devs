# OpenJarvis On-Device Agent Setup 🏠

> Build personal AI agents that run entirely on your device using Stanford's OpenJarvis framework. No cloud, no API keys, full privacy.

## The Prompt

```
You are an expert in Stanford's OpenJarvis framework for building on-device personal AI agents.

I want to build a local-first AI agent for: [DESCRIBE YOUR USE CASE]

My hardware:
- Device: [laptop/desktop/edge device]
- RAM: [amount]
- GPU: [model or "none"]
- OS: [macOS/Linux/Windows]

Help me set up an OpenJarvis agent with:

1. **Environment Setup**
   - Check hardware compatibility (minimum: 8GB RAM, Apple Silicon or NVIDIA GPU recommended)
   - Install OpenJarvis and dependencies
   - Select the right on-device model (Qwen 2.5, Phi-4, Llama 3.2 based on hardware)

2. **Agent Architecture**
   - Define the agent's core task and tool set
   - Configure the memory module (short-term context + long-term learning)
   - Set up tool integration (file system, calendar, browser, custom APIs)

3. **Privacy Configuration**
   - Ensure zero data leaves the device
   - Configure local-only embeddings for memory
   - Set up encrypted local storage for agent state

4. **Basic Testing**
   - Run the built-in evaluation suite
   - Test tool calling accuracy
   - Verify memory persistence across sessions

Output a complete setup guide with commands I can run right now.
```

## Example Use Cases

- **Personal coding assistant** that indexes your entire codebase locally
- **Email triager** that reads and categorizes without cloud access
- **Meeting prep agent** that pulls from local calendar + notes
- **Research assistant** that searches local documents with RAG

## Key Concepts

| Feature | OpenJarvis Approach |
|---------|-------------------|
| Models | Qwen 2.5, Phi-4, Llama 3.2 (on-device) |
| Memory | Local embeddings + learning loop |
| Tools | File system, browser, calendar, custom |
| Privacy | 100% on-device, zero cloud calls |
| Learning | Improves from local usage patterns |

## Limitations of This Free Version

This gives you a working single-agent setup. The **[AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app)** includes:

- 🔧 **Multi-agent on-device orchestration** (3+ agents coordinating locally)
- 📊 **Hardware-aware model selection engine** (auto-picks best model for your GPU/RAM)
- 🔄 **Learning loop optimization** (tune the self-improvement cycle)
- 🐳 **Docker + edge deployment configs** (deploy to Raspberry Pi, Jetson, etc.)
- 💰 **Cloud-vs-local cost calculator** (prove ROI of on-device approach)

---

*Part of [Awesome AI Prompts for Devs](https://github.com/dohko04/awesome-ai-prompts-for-devs) — 124 free prompts for AI-powered development*
