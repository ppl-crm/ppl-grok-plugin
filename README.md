# ppl for Cursor and Grok Build

**ppl** is the personal CRM for AI agents. Keep relationship notes, birthdays, interactions and follow-ups available across sessions and authorized agents.

This plugin bundles a CRM skill and the hosted Streamable HTTP MCP endpoint at `https://withppl.com/mcp`. The server currently advertises 120 grouped tools; clients should discover its current tool list and schemas.

## What you can do

- Read a briefing of birthdays, reminders, tasks and overdue follow-ups.
- Find a person and retrieve relevant relationship memory.
- Record notes, calls, gifts and journal entries.
- Manage contacts, reminders and tasks within your granted permissions.
- Pick up requested work and return an outcome for human review.

## Cursor setup

Install the plugin, then open the Cursor dashboard's **Plugins → Configure** and set its required `PPL_API_TOKEN` variable to a scoped ppl credential. Start at [ppl's agent setup](https://withppl.com/agents). The token is sent only as an Authorization header to the hosted ppl server; never commit it or paste it into chat.

Clients with OAuth support can instead configure the hosted endpoint directly and complete browser authorization. That path does not need this plugin's token variable.

The agent connect flow is also available to clients with HTTP access and secure credential storage: request a connection, show the returned approval URL, and poll for approval. Browser approval alone does not automatically configure Cursor's plugin variable. See [connection instructions](https://withppl.com/guides/cursor).

After setup, ask: “Read my ppl briefing and suggest one useful follow-up.” Check **Settings → My agents** in ppl for access and activity. Pause or revoke access there. Existing credentials retain their granted scopes; reconnect if a needed permission is missing. Suggested actions and message drafts do not bypass human approval.

## Other clients

The repository also retains its Grok Build manifest. Use the client's supported secure credential configuration for `PPL_API_TOKEN`. No local MCP server process is needed.

## Links

- [ppl](https://withppl.com)
- [Agent docs](https://withppl.com/agents)
- Official MCP Registry: `io.github.ppl-crm/ppl`
