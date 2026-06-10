# Feishu Project (Meego) MCP Server

> Official MCP server endpoints, setup guides, and marketplace listings for **Feishu Project** (also known as **Meego** / **Meegle** / **Lark Project**) — ByteDance's enterprise project management platform.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![MCP](https://img.shields.io/badge/MCP-2025--03--26-blue)](https://modelcontextprotocol.io)
[![OAuth 2.1](https://img.shields.io/badge/OAuth-2.1%20%2B%20PKCE%20%2B%20DCR-green)](https://datatracker.ietf.org/doc/html/draft-ietf-oauth-v2-1)

## What is this?

Feishu Project ships an **official, hosted MCP server** that exposes 50+ project-management tools (work items, MQL search, WBS plans, comments, work hours, charts, views, attachments, …) over standards-compliant **Streamable HTTP + OAuth 2.1**.

This repo contains:
- The two production MCP endpoints (China + International).
- Drop-in configuration for Claude Desktop, Cursor, Dify, Cherry Studio, Cline, and any MCP-compatible client.
- Marketplace listing manifests for Dify, Smithery, and the official MCP Registry.
- A complete end-user setup guide.

## Endpoints

| Region | Endpoint |
|---|---|
| 🇨🇳 China | `https://project.feishu.cn/mcp_server/v1` |
| 🌏 International | `https://meegle.com/mcp_server/v1` |

**No API key needed.** OAuth 2.1 Authorization Code + PKCE + Dynamic Client Registration ([RFC 7591](https://datatracker.ietf.org/doc/html/rfc7591)) — clients auto-register and log users in via browser.

## Quick Start

### Claude Desktop

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

### Cursor

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

### Dify (≥ 1.6.0)

Install the **Feishu Project (Meego)** plugin from the Dify Marketplace, pick your region, click "Authorize". See [`dify/`](./dify/) for the source.

### Other clients

See [`docs/USER_GUIDE.md`](./docs/USER_GUIDE.md) for Cherry Studio, Cline, Continue, 5ire, and headless/CI environments (Device Code flow).

## Tool Coverage

| Domain | Capabilities |
|---|---|
| Work Items | get / create / update / batch-get / MQL query / metadata |
| Workflow | transition nodes & states, update node fields |
| Subtasks | full CRUD |
| Comments | add / list with @mentions |
| Work Hours | record listing, team schedules |
| Relations | related-item listing, type metadata |
| My Work | to-dos, overdue, completed |
| Views | fixed views, multi-project views |
| Charts | listing and detail |
| People | team listing, user search |
| Attachments | upload / download |
| Deliverables | root and source listing |
| Resource Library | template creation, config inspection |
| WBS Plan Tables | draft & published rows, edit / publish / reset |

Run `tools/list` after connecting for the exact catalog with parameter schemas.

## Related Projects

- **[`@lark-project/meegle`](https://github.com/larksuite/meegle-cli)** — the official CLI; itself an MCP client that talks to the same server. Use it for terminal automation or as a reference implementation.

## License

MIT. Use of the Feishu Project MCP server is subject to:
- [Feishu Terms of Service](https://www.feishu.cn/terms) / [Privacy](https://www.feishu.cn/privacy) (China)
- [Lark Terms of Service](https://www.larksuite.com/user-terms-of-service) / [Privacy](https://www.larksuite.com/privacy-policy) (International)
