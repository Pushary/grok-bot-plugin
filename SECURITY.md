# Security

## Reporting a vulnerability

Email **security@pushary.com** with details and reproduction steps. Please do not open a public
issue for security reports. We aim to acknowledge within 72 hours.

## What this plugin contains

Two files that change behavior: `mcp.json`, which points Grok Bot at the Pushary MCP server at
`https://pushary.com/api/mcp/mcp`, and `rules/pushary.mdc`, which is text guidance for the Bot.
There are no scripts, no hooks and no dependencies, and no credential is committed to this
repository.

## How it signs in

The server is declared with `"placement": "server"`, so Grok Bot's connector service makes the
connection, not the Bot's computer. You sign in with your Pushary account over OAuth. Grok Bot's
documentation says the token stays on that connector service and Bots call tools without
receiving it.

A signed-in connection can call six tools: `ask_user`, `wait_for_answer`, `cancel_question`,
`propose_scope`, `send_notification` and `schedule_reminder`. It cannot read or change policies,
subscribers, campaigns or API keys.

## What a Bot sends

Only the arguments of the Pushary tool calls it makes: notification and question text, optional
context such as a summary or an error message, an agent name and a session id. The bundled rule
tells Bots to leave passwords, keys, one-time codes, payment details and private message contents
out of these calls.
