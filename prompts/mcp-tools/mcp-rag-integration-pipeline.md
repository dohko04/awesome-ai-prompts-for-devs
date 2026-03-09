# MCP + RAG Integration Pipeline

> 🔥 **Trending (March 2026):** MCP + RAG is the power combo every AI engineer is talking about. Use MCP to structure how your AI accesses RAG-retrieved context — no more hallucinated tool calls or lost context.

## The Prompt

```markdown
You are an expert AI infrastructure engineer specializing in MCP (Model Context Protocol) and RAG (Retrieval Augmented Generation) systems.

## Context
- Project: {{PROJECT_DESCRIPTION}}
- Vector DB: {{VECTOR_DB}} (e.g., Pinecone, Qdrant, Weaviate, ChromaDB, pgvector)
- Embedding model: {{EMBEDDING_MODEL}} (e.g., text-embedding-3-large, Cohere embed-v4)
- MCP clients: {{MCP_CLIENTS}} (e.g., Claude Code, Cursor, Windsurf, Xcode 26.3)
- Codebase size: {{CODEBASE_SIZE}} files approx.

## Task
Design a complete MCP server that wraps my RAG pipeline, so any MCP-compatible AI agent can:

### 1. MCP Server Definition (TypeScript or Python)
Generate a working MCP server with these tools:
- `search_codebase` — semantic search across code with filters (language, path, recency)
- `search_docs` — search internal documentation and ADRs
- `get_context_for_task` — given a task description, retrieve the top-k most relevant files + docs
- `index_new_files` — trigger re-indexing when files change

### 2. Chunking Strategy
- Define optimal chunk sizes for code (functions/classes) vs docs (sections/paragraphs)
- Include metadata extraction: file path, language, imports, exports, last modified
- Handle large files (>500 lines) with sliding window + overlap

### 3. Retrieval Pipeline
- Hybrid search: semantic (vector) + keyword (BM25) with reciprocal rank fusion
- Re-ranking step using a cross-encoder or LLM-as-judge
- Context window budget management: pack results into {{MAX_TOKENS}} tokens max
- Include relevance scores and source attribution

### 4. MCP Configuration
Generate the `mcp.json` / `claude_desktop_config.json` entry for connecting this server to:
- Claude Code (via claude mcp add)
- Cursor (via .cursor/mcp.json)
- Any stdio-based MCP client

### 5. Evaluation & Monitoring
- Retrieval quality metrics (MRR, recall@k)
- Query latency tracking
- Cache strategy for frequent queries
- Freshness: auto-reindex on git push via hooks

## Output Format
Provide production-ready code with:
- Complete MCP server implementation (choose best language for the stack)
- Docker Compose for the vector DB + server
- Setup script (one command to get running)
- Example queries showing the pipeline in action

## Constraints
- Server must start in <5 seconds
- Search latency <500ms p95
- Must work offline (local embeddings fallback)
- Follow MCP spec 2025-03-26 or later
```

## When to Use

- You're building internal dev tools and want AI agents to search your codebase intelligently
- You have docs/wikis/ADRs scattered across repos and want unified semantic search
- You want any MCP-compatible tool (Claude Code, Cursor, Xcode) to access your knowledge base
- Your team is adopting MCP and needs a practical first server to build

## Pro Tips

1. **Start with ChromaDB locally** — zero config, then migrate to managed (Pinecone/Qdrant) when you need scale
2. **Chunk code by AST** — don't split functions in half. Use tree-sitter for language-aware chunking
3. **Cache embeddings in SQLite** — avoid re-embedding unchanged files on every index run
4. **Test with real queries** — "where is auth handled?" should return auth middleware, not random files with "auth" in comments

## Example Output Preview

The prompt generates:
- A ~200 line MCP server with 4 tools
- Docker Compose with vector DB
- One-liner setup: `npx mcp-rag-server init && docker compose up`
- Pre-configured for Claude Code + Cursor

---

> 💡 **Want the complete implementation?** The [AI Dev Toolkit](https://ai-dev-toolkit-five.vercel.app) includes a production-ready MCP+RAG server template with auth, caching, multi-repo support, and monitoring dashboards — plus 100+ more engineering prompts.
