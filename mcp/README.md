# `mcp/`: connection config for the hosted MCP server

Ready-to-paste configuration for connecting an AI tool to `mcp.talitu.ai`: Claude Code,
Claude Desktop, Codex and ChatGPT, one file each, and the sign-in flow a person sees
(OAuth with PKCE through the platform's identity provider, platform D10).

No token or secret is ever in these files (kit rule 2): the client obtains its own on first
connection.

State: skeleton. Built by the platform's T4, after the WorkOS spike (T1) decides the
provider and the token flow.
