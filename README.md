# Talitu: agent kit

What a person installs into their AI tools to build, publish and run forms with Talitu:
a Claude Code plugin with skills and slash commands, the MCP connection config for Claude
Code, Claude Desktop, Codex and ChatGPT, and worked examples. It ships as its own
repository with its own versions and licence. The platform, `talitu-platform`, holds it as
a git submodule so one checkout shows both sides; neither imports the other.

The rules for this repository are in [`CLAUDE.md`](CLAUDE.md). The authority for what it
does is the approved V1 Implementation Plan in the platform repository, and the decisions it
cites are rows in that repository's `docs/DECISIONS.md` (D14 is the kit's).

> The form builder your AI agent can use.

## Layout

```text
agent-kit/
  plugin/                 the Claude Code plugin
    skills/               one folder per job: a short SKILL.md, references/, templates/, examples/
    commands/             slash commands, for example /lead-magnet, /publish, /connect
  mcp/                    connection config for the hosted MCP server, per client
  examples/               worked briefs and the drafts they produce, all made up
  tests/                  the skills scored against their example sets
```

Each folder's README says what it owns and which platform task builds it.

## How it talks to Talitu

Only through three published things: the `talitu` command (the CLI, published to PyPI as
`talitu-cli` and built in the platform's `python/talitu_cli`), the hosted MCP server at
`mcp.talitu.ai` and, for automations a skill helps someone write, the published `talitu`
Python client on PyPI. All three call the public REST API with the person's own token. The kit
holds no platform code, no copy of a client and no database access of any kind.

## What it is for

| Skill or command | Does |
|---|---|
| `using-talitu` | tells an agent which surface to use: the `talitu` command when it has a terminal, the MCP tools when it is inside a chat client, the published `talitu` Python client when it is writing an automation. Written now; the others arrive with their platform tasks |
| `/lead-magnet` | turns an offer, audience and campaign brief into an editable calculator, quiz or diagnostic draft through the platform's `generate_form_draft` operation, with its sources cited. It never publishes without the person's approval |
| `/publish` | asks the person to approve, then publishes the draft as an immutable form version on a yes and returns the hosted URL and embed snippet; a no leaves it unpublished (platform D25) |
| `/connect` | connects a workspace destination (webhook, Slack, then Zapier and HubSpot) and sends a test lead packet |
| `/leads` | shows recent submissions with their score, reasons and recommended next action |

Every skill reads the workspace's forms, routes and settings from the platform at run time,
never from files here.

The skills are plain folders with a `SKILL.md`. The Claude Code plugin is one way to install
them; Codex and other agents that read skill folders install the same folders, and the MCP
connection config under `mcp/` covers the clients that have no terminal.

## State

Skeleton: READMEs only. Built by the platform's T4 (`talitu login`, the MCP connection
config, the plugin manifest), T5 and T7 (`/lead-magnet`, `/publish`), T10 and T11
(`/connect`) and T9 (`/leads`). Publishing the plugin and pinning the CLI version is T14.

Licence: Apache-2.0, pending the founder's confirmation (platform D34); until the `LICENSE`
file lands, all rights reserved. Security reports: [`SECURITY.md`](SECURITY.md).
