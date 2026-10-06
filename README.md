# ppl for Grok Build

**ppl** is the personal CRM for AI agents. Your agent's own intelligence is the thinking layer; ppl is the durable memory underneath it: the people who matter, what they care about, and what needs to happen next.

This plugin bundles ppl's hosted MCP server so Grok Build agents get ppl's full tool surface (86 tools) with a one-click install.

## What it does

- **Morning briefings**: birthdays, overdue reconnects, due reminders and tasks
- **Remember**: store facts on a contact's timeline so no agent forgets them
- **Log**: notes, calls, gifts, journal entries
- **Manage**: tasks, reminders, contacts (full read/write/delete)
- **Recall**: semantic and keyword search over everything ppl knows

## Setup

No local install. The MCP server is hosted at `https://withppl.com/mcp` (Streamable HTTP).

On first connect, the agent guides you through the one-approval connect flow at **https://withppl.com/agents**. You never have to copy a token by hand; the agent handles the token.

## Session habit

Every session, before answering, the agent calls `get_briefing`, `get_next_action`, and `ask_memory` so it starts with what ppl knows. Anything it learns goes back in via `remember`.

## Links

- ppl: https://withppl.com
- Agent docs: https://withppl.com/agents
- MCP registry: `io.github.ppl-crm/ppl`
