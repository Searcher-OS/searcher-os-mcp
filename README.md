# Searcher OS — MCP Server

Connect your AI agent to [Searcher OS](https://searcheros.ai), the operating system for acquisition entrepreneurs sourcing and buying small to mid-sized businesses.

This is a **remote, hosted MCP server**. There is nothing to install or self-host — you point your MCP client at a URL and authenticate. This repository contains the published server manifest and connection documentation; the server itself is a managed service.

Listed in the [Official MCP Registry](https://registry.modelcontextprotocol.io) as `ai.searcheros/searcher-os`.

---

## Connection

| | |
|---|---|
| **Streamable HTTP** | `https://searcheros.ai/api/mcp/mcp` |
| **Auth** | OAuth 2.1 (preferred) or Bearer API key |
| **Discovery** | `https://searcheros.ai/.well-known/mcp.json` |

> Note the doubled path segment on the Streamable HTTP endpoint. It is `/api/mcp/mcp`, not `/api/mcp` — the latter returns 404.

### OAuth (recommended)

Most clients discover everything they need on their own. Add the server URL and your client will walk you through browser-based sign-in and consent — no key to copy, and access is revocable from your account.

```json
{
  "mcpServers": {
    "searcher-os": {
      "url": "https://searcheros.ai/api/mcp/mcp"
    }
  }
}
```

### API key

For headless clients that don't implement the OAuth flow. Generate a key under **Settings → LLM Connect → Advanced: API Key**.

```json
{
  "mcpServers": {
    "searcher-os": {
      "url": "https://searcheros.ai/api/mcp/mcp",
      "headers": {
        "Authorization": "Bearer YOUR_API_KEY"
      }
    }
  }
}
```

Treat the key like a password — it carries the same access to your pipeline that you have.

---

## Tools

40 tools across 12 categories. Reviewed acquisition guides are also available as MCP resources.

| Category | Tools | What it covers |
|---|---:|---|
| Knowledge | 2 | Search and read reviewed acquisition guides with source citations |
| Context | 2 | Connectivity check plus profile, buy boxes, pipeline summary, feed stats |
| Pipeline | 9 | Pipeline health, view, create, update, move, and kill deals |
| Feed | 5 | Search deals, count, statistics, save, dismiss |
| Buy Box | 1 | List acquisition criteria (price, industry, location) |
| Inbox | 4 | List, view, link, and ignore inbound broker email |
| Broker CRM | 4 | List, view, create brokers; log interactions |
| CIM Analysis | 4 | List, view analysis, search CIM documents, append supplementary financials |
| Confirmation | 4 | List pending, check status, resolve, auto-approve settings |
| Calculator | 1 | SBA 7(a) loan modeling with DSCR |
| Tasks | 2 | List and update deal tasks |
| Deal Documents | 2 | Mint upload URLs and register documents against a deal |

Free connections are read-only. Eligible trials and paid plans can also make changes. Confirmations depend on the operation, your account's auto-approve settings, and your AI client's permissions; some routine writes execute immediately. Review both account and client settings before enabling automatic actions.

The connected AI receives the data returned by its tool calls. Its privacy and retention terms apply in addition to [Searcher OS's privacy policy](https://searcheros.ai/privacy).

---

## Requirements

- Any Searcher OS account can connect, including **Free**. Free is read-only and the deal feed is delayed by 21 days.
- Eligible 7-day trials, **Searcher**, and **Deal Team** plans can also save deals, add notes, and update the pipeline.
- You can create a free account during the OAuth connection flow without a payment card.
- Rate limit: 100 requests/minute per connection.

The server uses Streamable HTTP. The legacy HTTP+SSE transport is no longer supported.

---

## Example prompts

Once connected, talk to your pipeline in plain language:

- *"What's in my pipeline at the LOI stage, and which deals have gone stale?"*
- *"Find manufacturing businesses in Texas under $3M with SDE above $400K."*
- *"Summarize the CIM for the HVAC deal and flag anything odd in the add-backs."*
- *"Run the numbers on a $2.4M purchase at 10% down and tell me the DSCR."*
- *"Move Riverside Plumbing to Due Diligence and log that I spoke with the broker."*

---

## Links

- [Searcher OS](https://searcheros.ai)
- [Connection help](https://searcheros.ai/help/mcp-connection)
- [LLM Connect settings](https://searcheros.ai/settings/llm-connect)
- [Registry entry](https://registry.modelcontextprotocol.io/v0.1/servers/ai.searcheros%2Fsearcher-os/versions/latest)
- [What is MCP?](https://searcheros.ai/blog/what-is-mcp-model-context-protocol)

## Support

Connection problems, access questions, or bug reports: [support@searcheros.ai](mailto:support@searcheros.ai), or open an issue here.

---

Searcher OS is a commercial hosted service. This repository holds its public MCP manifest and documentation only; it is not the product source and carries no license to the service itself. Use of the server is governed by the [Searcher OS terms](https://searcheros.ai/terms).
