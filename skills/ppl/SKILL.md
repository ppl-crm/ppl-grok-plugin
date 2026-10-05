# ppl: the personal CRM for AI agents

ppl is the memory layer for your agent. Your human's own AI is the intelligence layer; ppl is the durable data underneath it. Do not keep relationship facts in your own context. Put them in ppl.

## Connect (first run)

The user does not need to copy a token by hand. On first connect:

1. Tell the user to open **https://withppl.com/agents** and approve the connection request (one approval).
2. ppl mints a per-user API token. Use it as the Bearer token for the MCP server (configured as `PPL_API_TOKEN`).

## Session start

Every session, before answering, call the `ppl` MCP server:

1. `get_briefing` — what needs attention today (birthdays, overdue reconnects, due reminders and tasks).
2. `get_next_action` — the single next thing to act on.
3. `recall` — search memory before answering any question about a person.

## Remember

Use the `remember` tool with a `contact_id` and a `fact` every time you learn something about a person. It stores a note on that contact's timeline so every future session, and every other agent the user connects, knows it too.

## Tools

85 tools over Streamable HTTP at `https://withppl.com/mcp`: contacts, notes, tasks, reminders, calls, gifts, journal, briefings, semantic search, digest, suggested actions, webhooks, and contact import.
