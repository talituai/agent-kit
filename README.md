# MCPForm.io: agent kit

What a person installs into their AI tools to build, publish and run forms with MCPForm.io:
a Claude Code plugin with skills and slash commands, the MCP connection config for Claude
Code, Claude Desktop, Codex and ChatGPT, and worked examples. It ships as its own
repository with its own versions and licence. The platform, `mcpform-platform`, holds it as
a git submodule so one checkout shows both sides; neither imports the other.

The rules for this repository are in [`CLAUDE.md`](CLAUDE.md). The authority for what it
does is the approved V1 Implementation Plan in the platform repository, and the decisions it
cites are rows in that repository's `docs/DECISIONS.md` (D14 is the kit's).

> The form builder your AI agent can use.

## Layout

```text
agent-kit/
  plugin/                 the Claude Code plugin
    skills/               one folder per job: SKILL.md, examples/
    commands/             slash commands, for example /lead-magnet, /publish, /connect
  mcp/                    connection config for the hosted MCP server, per client
  examples/               worked briefs and the drafts they produce, all made up
  tests/                  the skills scored against their example sets
```

Each folder's README says what it owns and which platform task builds it.

## How it talks to MCPForm.io

Only through two published things: the `mcpform` command (the CLI, published to PyPI as
`mcpform-cli` and built in the platform's `python/mcpform_cli`) and the hosted MCP server at
`mcp.mcpform.io`. Both call the public REST API with the person's own token. The kit holds no
platform code, no generated client and no database access of any kind.

## What it is for

| Skill or command | Does |
|---|---|
| `/lead-magnet` | turns an offer, audience and campaign brief into an editable calculator, quiz or diagnostic draft through the platform's `generate_form_draft` operation, with its sources cited. It never publishes |
| `/publish` | publishes a reviewed draft as an immutable form version and returns the hosted URL and embed snippet |
| `/connect` | connects a workspace destination (webhook, Slack, then Zapier and HubSpot) and sends a test lead packet |
| `/leads` | shows recent submissions with their score, reasons and recommended next action |

Every skill reads the workspace's forms, routes and settings from the platform at run time,
never from files here.

## State

Skeleton: READMEs only. Built by the platform's T4 (`mcpform login`, the MCP connection
config, the plugin manifest), T5 and T7 (`/lead-magnet`, `/publish`), T10 and T11
(`/connect`) and T9 (`/leads`). Publishing the plugin and pinning the CLI version is T14.
