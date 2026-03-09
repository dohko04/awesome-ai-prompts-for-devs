# Agentic RAG Pipeline Builder 🧠📚

> Design RAG systems where agents decide WHAT to retrieve and HOW to use it.

Agentic RAG is the 2026 upgrade from basic "stuff context" RAG. The AI decides when to search, what to retrieve, and how to synthesize — not just blind vector lookup.

## The Prompt (Free Version)

```
You are a RAG Pipeline Architect specializing in agentic retrieval systems.

## Context
Agentic RAG = AI agent that intelligently decides:
- WHEN to retrieve (not every query needs retrieval)
- WHAT to search for (query rewriting, decomposition)
- WHERE to look (multiple sources, routing)
- HOW to use results (synthesis, citation, follow-up)

## My Project
- **Knowledge base:** [describe your data — docs, codebase, wiki, etc.]
- **Use case:** [Q&A, code assistant, support bot, research, etc.]
- **Stack:** [LangChain / LlamaIndex / custom]
- **Vector DB:** [Pinecone / Chroma / Qdrant / Weaviate / pgvector]
- **LLM:** [GPT-4o / Claude / Gemini / local]

## Generate
1. Architecture diagram (mermaid) showing agent flow
2. Query router — classify intent and route to right retrieval
3. Retrieval agent with query decomposition
4. Answer synthesis with source citations
5. Evaluation criteria for retrieval quality

## Constraints
- Handle multi-hop questions (need info from multiple chunks)
- Include fallback when retrieval returns low-confidence results
- Add re-ranking step before synthesis
```

## What You Get (Free)
- Basic agentic RAG architecture
- Query routing logic
- Single-source retrieval pattern

## 🔥 Full Version — AI Dev Toolkit ($9)

The complete version includes:
- **Multi-source routing** (vector DB + SQL + API + web search)
- **Hybrid search** (semantic + keyword + metadata filtering)
- **Adaptive chunking strategies** (by doc type)
- **Complete LangChain + LlamaIndex implementations**
- **Eval pipeline** with RAGAS metrics
- **Production deployment** with caching, rate limiting, observability
- **3 complete example apps** (codebase Q&A, docs bot, research agent)

👉 **[Get the full toolkit → ai-dev-toolkit-five.vercel.app](https://ai-dev-toolkit-five.vercel.app)**

---
*Part of [Awesome AI Prompts for Devs](https://github.com/dohko04/awesome-ai-prompts-for-devs) by Dohko*
