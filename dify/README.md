# Feishu Project (Meego) — Dify Plugin

Connect your Dify agents directly to **Feishu Project (Meego)**, ByteDance's enterprise project management platform, via the official MCP server.

## Highlights

- **Zero-config OAuth** — Authorization Code + PKCE + Dynamic Client Registration. Users click "Authorize", log in once, and tokens auto-refresh.
- **50+ tools** — work items, MQL search, WBS plans, comments, work hours, charts, views, attachments, deliverables, resource libraries.
- **Both regions** — `project.feishu.cn` (China) and `meegle.com` (International).
- **Remote MCP** — no local Node.js or CLI install required.

## Setup

1. Install this plugin from the Dify Marketplace.
2. Select your **Service Region**:
   - 🇨🇳 China — `https://project.feishu.cn/mcp_server/v1`
   - 🌏 International — `https://meegle.com/mcp_server/v1`
3. Click **Authorize**. Dify opens a browser tab for Feishu/Lark login.
4. Add tool calls to any Agent or Workflow node — all 50+ Meego tools appear automatically.

## Example Prompts

> "List my P0 stories in the X project that are due this week."
>
> "Create a bug in the Y project: title 'Login crashes on iOS 17', priority P1, assign to me."
>
> "Show the current WBS draft rows for work item 12345, grouped by phase."

## Requirements

- Dify ≥ 1.6.0 (for native MCP client support)
- A Feishu Project (Meego) account with at least one project workspace.

## Source

Open source on GitHub: https://github.com/bytedance/feishu-project-dify-plugin
Underlying MCP server: official, operated by ByteDance / Lark.
Related: [`@lark-project/meegle` CLI](https://github.com/larksuite/meegle-cli) — the CLI is itself an MCP client that talks to the same server.

## License

MIT (this plugin). Meego MCP server usage is subject to Feishu/Lark Terms of Service.
