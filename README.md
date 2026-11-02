# AI Developer Toolkit MCP

The documentation, as a tool your agent can call.

Your agent already guesses at Cursor flags, Claude Code hooks and Codex config. Point it here instead and it reads the guide — mid-prompt, without you leaving the editor. A public, **read-only** MCP endpoint over every guide on AI-assisted development, in EN and PL, from [developertoolkit.ai](https://developertoolkit.ai). No account, no API key.

## Connect

A remote HTTP server — nothing to install, nothing to keep running.

```bash
claude mcp add --transport http dtk https://developertoolkit.ai/mcp
```

Cursor (`.cursor/mcp.json`):

```json
{
  "mcpServers": {
    "dtk": {
      "type": "http",
      "url": "https://developertoolkit.ai/mcp"
    }
  }
}
```

Codex (`~/.codex/config.toml`):

```toml
[mcp_servers.dtk]
url = "https://developertoolkit.ai/mcp"
```

Any MCP client that speaks Streamable HTTP works — including ChatGPT connectors, where you paste the endpoint URL directly.

## Tools

| Tool | In | Out |
|---|---|---|
| `search` | `{ query }` | `{ results: [{ id, title, url, snippet, lang }] }` — ranked across both languages; a Polish query returns Polish articles. |
| `fetch` | `{ id }` | `{ id, title, text, url, metadata }` — the complete article as markdown, not an extract. |

Corpus: every guide on developertoolkit.ai — Cursor, Claude Code and OpenAI Codex, from first setup through hooks, MCP, testing, CI and deployment — rebuilt on each deploy. Both tools are read-only.

Discovery: [server card](https://developertoolkit.ai/mcp/server-card) · [AI catalog](https://developertoolkit.ai/.well-known/ai-catalog.json)

Info: https://developertoolkit.ai/en/mcp/ · Contact: contact@wondel.ai · [Wondel.ai](https://wondel.ai) — product studio building consumer AI experiences (text, image, video, voice), Warsaw, Poland.
