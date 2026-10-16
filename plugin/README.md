# `plugin/`: the Claude Code plugin

The plugin manifest, its skills and its slash commands. Installed from this repository
into Claude Code; the same skills are documented for Codex and Claude Desktop through the
MCP connection config in [`../mcp/`](../mcp/README.md).

| | Owns | State | Built by |
|---|---|---|---|
| [`skills/`](skills/README.md) | one folder per job: `SKILL.md`, examples | Skeleton | T5, T7, T9, T10, T11 |
| [`commands/`](commands/README.md) | slash commands that call the `talitu` command or the MCP tools | Skeleton | T4 onwards |

The manifest (`.claude-plugin/plugin.json`) arrives with the first command (platform T4).
