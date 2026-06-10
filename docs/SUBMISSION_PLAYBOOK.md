# Submission Playbook — 6 Marketplaces

| # | Marketplace | Submission Path | Effort | Review Time | Asset |
|---|---|---|---|---|---|
| 1 | **Claude Desktop** | No marketplace — direct config publish to docs | 0.5 day | None | `claude-desktop/claude_desktop_config.json` |
| 2 | **Cursor** | PR to `pontusab/cursor.directory` | 0.5 day | 1-3 days | `cursor/mcp.json` |
| 3 | **Dify Marketplace** | PR to `langgenius/dify-plugins` | 1 day (package + test) | 3-7 days | `dify/*` |
| 4 | **Smithery.ai** | PR to `smithery-ai/registry` | 0.5 day | 1-2 days | `smithery/smithery.yaml` |
| 5 | **MCP Registry (official)** | PR to `modelcontextprotocol/registry` | 0.5 day | 1-2 weeks | `mcp-registry/server.json` |
| 6 | **Feishu/Lark official docs** | Publish user guide on help center | 0.5 day | Internal | `docs/USER_GUIDE.md` |

## Day-1 Action Plan (assuming all assets are committed)

1. **Morning** — internal smoke test
   - Paste `claude-desktop/claude_desktop_config.json` into your own Claude Desktop.
   - Verify the OAuth flow opens, completes, and at least 3 tool calls succeed.
   - Repeat with Cursor.
2. **Afternoon** — public PRs (all 5 can be submitted in parallel)
   - Create `github.com/bytedance/feishu-project-dify-plugin` repo, push `dify/*`.
   - Open PR to `langgenius/dify-plugins`.
   - Open PR to `smithery-ai/registry`.
   - Open PR to `modelcontextprotocol/registry`.
   - Open PR to `pontusab/cursor.directory`.
3. **Evening** — publish docs
   - Push `docs/USER_GUIDE.md` to a public location (GitHub README or Feishu help center).
   - Optional: Announce on Twitter/X with the user guide URL.

## Day-2 to Day-14 — Follow-up

- Respond to PR reviewer comments.
- Reply to early-user GitHub issues.
- Track install counts via Smithery and Dify analytics.

## Open RD Asks (block nothing, but improve)

1. **Issuer mismatch on overseas endpoint** — `meegle.com/.well-known/oauth-authorization-server` returns `issuer: https://project.larksuite.com`, but `oauth-protected-resource` lists `authorization_servers: ["https://meegle.com/b/auth/mcp"]`. Strict OAuth clients may reject. Align them.
2. **`scopes_supported` is empty** — fine for now; consider populating with semantic scopes (e.g., `workitem:read`, `workitem:write`) so users can grant least privilege.
3. **`bearer_methods_supported` is empty** — should be `["header"]` per RFC 8707 § 2.
