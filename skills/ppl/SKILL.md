---
name: ppl
description: Use the ppl personal CRM for relationship briefings, finding people, recording user-authorized notes and interactions, and managing follow-ups. Use when the user asks to work with their ppl contacts or relationship memory.
---

# ppl: the personal CRM for AI agents

Use ppl as durable relationship memory for the user's requested CRM work. Check relevant records before answering about a person. Keep confirmed facts distinct from suggestions and inferences; store only information appropriate to the user's request and permissions.

## Connect

If the MCP server is already connected, use it. Otherwise explain the available setup paths:

- In an HTTP MCP client supporting OAuth, add `https://withppl.com/mcp` and complete its browser authorization.
- This Cursor plugin uses the required `PPL_API_TOKEN` variable. Configure it in Cursor's dashboard under Plugins → Configure using a scoped ppl credential. See `https://withppl.com/agents` for setup instructions.
- If the client provides HTTP requests and a secure credential store, start the agent connect flow with `POST https://withppl.com/api/agent/connect/request` and JSON `{"client_name":"Cursor ppl"}`. Show the returned `data.approve_url` to the user, then poll `data.poll_url` at the server's requested interval until approved, refused or expired. Approval returns `data.api_token` once. Store it securely and configure the client's Bearer header through its supported mechanism. Do not claim Cursor's plugin variable has been configured unless it actually has.

Never include a token in chat, source code, logs or a shared file. If secure configuration is unavailable, direct the user to the dashboard setup. Missing scopes require a new scoped credential or reconnection; never bypass approval.

## Read and act

Discover the server's tools and argument schemas instead of assuming a fixed tool count. The hosted server currently advertises 120 grouped tools.

- `agent.briefing.get`: birthdays, reconnects, reminders and tasks needing attention.
- `agent.actions.next`: a suggested next relationship action.
- `memory.search` or `memory.semantic.search`: relevant relationship memory.
- `memory.remember`: record an authorized fact with `contact_id` and `fact`.

Retrieve a briefing when the user asks for relationship priorities. Search the relevant person's memory for person-specific work. Do not fetch the whole CRM for unrelated coding tasks.

For queued work, use `agent.inbox.list`, claim a request before working, report progress, and complete it only after the requested action succeeds. Respect approval requirements and scope limits. Report actual outcomes; do not describe a draft or queued message as delivered. Check My agents in ppl for access controls, pause and revocation.
