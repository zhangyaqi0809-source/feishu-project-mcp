# Feishu Project (Meego) MCP — End-User Setup Guide

> **Audience**: developers, AI power users, and anyone who wants to use Feishu Project (Meego) inside their AI client.
>
> **TL;DR**: Paste one URL into your AI client's MCP config. Click "Authorize" when the browser opens. Done.

---

## Endpoints

| Region | URL |
| --- | --- |
| 🇨🇳 China | `https://project.feishu.cn/mcp_server/v1` |
| 🌏 International | `https://meegle.com/mcp_server/v1` |

**Authentication**: OAuth 2.0 (Authorization Code + PKCE), with Dynamic Client Registration. No manual API key — you log in to Feishu/Lark in your browser, the client takes care of the rest.

---

## Claude Desktop

Edit `~/Library/Application Support/Claude/claude_desktop_config.json` (macOS) or `%APPDATA%\Claude\claude_desktop_config.json` (Windows):

```json
{
  "mcpServers": {
    "feishu-project": {
      "url": "https://project.feishu.cn/mcp_server/v1"
    }
  }
}
```

Restart Claude Desktop → click the 🔌 icon → "Authorize" → done.

---

## Cursor

Edit `~/.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "feishu-project": {
      "url": "https://project.feishu.cn/mcp_server/v1"
    }
  }
}
```

Reload Cursor → Settings → MCP → click "Authorize".

---

## Dify (≥ 1.6.0)

Install the **Feishu Project (Meego)** plugin from the Dify Marketplace. Pick your region in the credentials panel. Click "Authorize".

---

## Cherry Studio

Settings → MCP Servers → Add → paste the URL above. Click "Connect" → "Authorize".

---

## Cline / Continue / 5ire / any MCP-compatible client

Wherever the client takes an MCP server URL, paste it. If the client supports OAuth Dynamic Client Registration (most modern ones do), authorization is automatic.

---

## Headless / CI environments

When the client cannot open a browser, use Device Code flow:

```
POST https://project.feishu.cn/goapi/v5/mcp_server/oauth/device_code
```

See [`@lark-project/meegle` CLI](https://github.com/larksuite/meegle-cli) `--device-code` flag for a reference implementation.

---

## Troubleshooting

| Symptom | Cause | Fix |
| --- | --- | --- |
| `401 Unauthorized` on first request | Expected — triggers the OAuth flow | Click "Authorize" in your client |
| Browser opens but redirects fail | Loopback `127.0.0.1` port blocked | Allow temporary inbound on the random port your client uses |
| Tools list is empty | Token expired / revoked | Disconnect and re-authorize |
| Wrong region | Authorized on China endpoint but your account is on International | Remove the entry, use `meegle.com` URL instead |

---

## Tool Catalog (high-level)

Once connected, ~50 tools are exposed across these domains:

- **Work Items** — get / create / update / batch-get / MQL query / metadata
- **Workflow** — transition nodes & states, update node fields
- **Subtasks** — full CRUD
- **Comments** — add / list (with @mentions)
- **Work Hours** — record listing, team schedules
- **Relations** — list related items, relation type metadata
- **My Work** — to-dos, overdue, completed
- **Views** — fixed views, multi-project views
- **Charts** — chart listing & detail
- **People** — team listing, user search
- **Attachments** — upload / download
- **Deliverables** — root and source listing
- **Resource Library** — template creation, config inspection
- **WBS** — draft & published plan rows, edit / publish / reset

For exact tool signatures, ask any MCP client `tools/list` after connecting.

---

## Security

- Tokens are stored by your AI client only, never by ByteDance/Lark beyond standard OAuth server-side records.
- All traffic is TLS to `*.feishu.cn` / `meegle.com`.
- Revoke at any time in the Feishu Project authorized-apps page.
- For agent-driven sessions, consider creating a dedicated Feishu account or limited-scope role to bound blast radius.
