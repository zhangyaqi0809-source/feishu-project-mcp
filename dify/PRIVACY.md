# Privacy Policy

This Dify plugin connects your Dify agent directly to the official Feishu Project (Meego) MCP server, operated by Beijing Douyin Information Service Co., Ltd. (ByteDance) and its international affiliates (Lark Technologies Pte. Ltd. for the `meegle.com` region).

## Data Flow

1. The plugin is a thin MCP client wrapper. All API calls travel directly from your Dify instance to:
   - `https://project.feishu.cn/mcp_server/v1` (China region), or
   - `https://meegle.com/mcp_server/v1` (International region).
2. Authentication uses **OAuth 2.0 Authorization Code flow with PKCE**, plus **Dynamic Client Registration (RFC 7591)**. No long-lived secret is stored in this plugin's code.
3. Access tokens and refresh tokens are persisted by the Dify runtime's credential store; this plugin never logs, exports, or forwards them.

## Data Collection by This Plugin

**None.** This plugin does not run any telemetry, analytics, error-reporting, or background job. It is configuration-only.

## Data Collected by Feishu Project (Meego)

Subject to Feishu / Lark's own privacy policies:
- [Feishu Privacy Policy (China)](https://www.feishu.cn/privacy)
- [Lark Privacy Policy (International)](https://www.larksuite.com/privacy-policy)

## User Rights

- Revoke authorization at any time in the Feishu Project authorized-apps panel.
- Uninstall the plugin from Dify to delete all locally stored tokens.

## Contact

For privacy concerns related to this plugin specifically: open an issue at https://github.com/bytedance/feishu-project-dify-plugin
For Feishu Project platform privacy questions: privacy@feishu.cn
