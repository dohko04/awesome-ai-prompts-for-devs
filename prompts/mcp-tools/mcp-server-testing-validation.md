# 🧪 MCP Server Testing & Validation

MCP (Model Context Protocol) is becoming the universal standard for connecting AI agents to tools. But most MCP servers ship without tests. This prompt generates a complete test suite for any MCP server.

## The Prompt

```
You are an expert in Model Context Protocol (MCP) server development and testing. I need a comprehensive test suite for my MCP server.

My MCP server details:
- **What it does:** {SERVER_DESCRIPTION}
- **Tools exposed:** {TOOLS_LIST: e.g., search_docs, create_ticket, query_database}
- **Transport:** {TRANSPORT: stdio | SSE | streamable-http}
- **Language:** {LANGUAGE: TypeScript | Python}
- **Auth:** {AUTH: none | API key | OAuth}

Generate a complete test suite covering:

### 1. Connection & Handshake Tests
- Server starts and responds to `initialize` request
- Correct capabilities are advertised
- Protocol version negotiation works
- Graceful handling of malformed initialize requests

### 2. Tool Discovery Tests
- `tools/list` returns all expected tools
- Each tool has valid JSON Schema for inputs
- Tool descriptions are non-empty and useful
- No duplicate tool names

### 3. Tool Execution Tests
For each tool ({TOOLS_LIST}), generate:
- **Happy path**: valid input → expected output
- **Edge cases**: empty strings, null values, maximum lengths
- **Error cases**: missing required params, wrong types, invalid values
- **Timeout handling**: what happens if the underlying service is slow?
- Verify output matches the declared schema

### 4. Security Tests
- Prompt injection via tool inputs (e.g., "ignore previous instructions" in a search query)
- SQL injection if tool queries a database
- Path traversal if tool accesses files
- Auth token validation (reject expired/invalid tokens)
- Rate limiting behavior

### 5. Performance Tests
- Response time under normal load (single request latency)
- Concurrent request handling (10, 50, 100 simultaneous)
- Memory leak detection (1000 sequential requests)
- Large payload handling (oversized inputs)

### 6. Integration Tests
- End-to-end: connect real MCP client → call tools → verify results
- Test with at least 2 different MCP clients (Claude Desktop, Cursor, custom)
- Verify JSON-RPC 2.0 compliance for all responses
- Test reconnection behavior after disconnect

Output as:
- Complete test files I can run with {LANGUAGE === 'TypeScript' ? 'vitest' : 'pytest'}
- A CI/CD pipeline config (GitHub Actions) that runs these tests
- A test fixtures file with sample inputs/outputs
```

## Example Usage

```
Server: MCP server that connects to a PostgreSQL database and exposes query/schema tools
Tools: run_query, list_tables, describe_table, explain_query
Transport: stdio
Language: TypeScript
Auth: none (local only)
```

## Tips

- Always test the unhappy paths — that's where MCP servers break in production.
- Use snapshot testing for tool schemas to catch accidental breaking changes.
- Test with real MCP clients, not just unit tests — protocol quirks are real.
- Add a "smoke test" that connects and lists tools as your CI health check.

---

> 🚀 **Ship MCP servers with confidence.** The [AI Dev Toolkit](https://ai-dev-toolkit-five.vercel.app) ($9) includes production-ready MCP server templates, test suites, and deployment configs for the most common integrations (databases, APIs, file systems, and more).
