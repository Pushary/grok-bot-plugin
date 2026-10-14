<p align="center">
  <img src="assets/logo.png" alt="Pushary" width="72" height="72" />
</p>

<h1 align="center">Pushary for Grok Bot</h1>

<p align="center">Get a push on your phone when a Bot finishes or fails, and answer its questions from your phone.</p>

---

## What it does

Your Bots keep working on their cloud computer after you close the laptop. Pushary tells you how that went, on your phone, in the same inbox as your other AI agents such as Claude Code, Codex and Cursor.

1. **Notify.** When a routine run or a long task finishes, or fails in a way the Bot cannot fix, the Bot sends you a push with the result. Tap it for the detail.
2. **Ask.** When a Bot needs a decision only you can make, it asks you through Pushary: yes or no, a choice of options, or a short answer. You answer from the Pushary phone or Mac app, and the Bot carries on.
3. **Remind.** A Bot can set a one-time personal reminder that Pushary delivers later.

The bundled rule tells each Bot when to reach you and when to stay quiet: one push per routine run at most, and no questions that a Grok Bot approval card is already asking.

## What connecting does

Before you sign in, know what is shared.

- Adding Pushary connects Grok Bot to Pushary's hosted MCP server at `https://pushary.com/api/mcp/mcp`. You sign in with your Pushary account in the browser. Grok Bot's documentation says the sign-in stays on its connector service and your Bots use the tools without receiving it.
- A Bot sends Pushary only what it puts in a tool call: the notification or question text, optional detail such as a summary or an error message, the Bot's name and a session id. Pushary stores these so they show in your inbox and history. The rule tells Bots to leave passwords, keys, codes, payment details and private message contents out.
- Pushary does not read your Grok Bot conversations, your Bot's computer, or anything you connected to Grok Bot.
- The connection can only ask questions, read and cancel them, propose a task boundary for you to approve, send notifications and schedule reminders. It cannot read or change your Pushary policies, subscribers, campaigns or API keys.

Read the [privacy policy](https://pushary.com/privacy) for retention details.

## What you need

- A paid Pushary plan for your own agents, such as Agent, Agent Pro or Team. Eligible web sign-ups get a trial; see [pricing](https://pushary.com/pricing). Partner plans embed approvals in your own product and do not include this.
- The Pushary app on your phone, or the Pushary Mac app, signed in to the same account. Get them at [pushary.com/download](https://pushary.com/download).

## Install

1. In Grok Bot, open **Connect apps**, search for **Pushary** and choose **Add**.
2. Sign in with your Pushary account when the browser opens, and allow access.
3. Ask a Bot: "Use Pushary to ask me 'Did this reach you?' as a yes or no question, with agentName 'Grok Bot - Setup check'. Wait for my answer and tell me what I chose."
4. Answer on your phone. The Bot should tell you your answer.

If searching **Connect apps** finds no Pushary, add it as a custom MCP server instead. Send a Bot: "Add a custom MCP server called pushary at https://pushary.com/api/mcp/mcp". Choose **Add it**, leave any OAuth Client ID and Secret empty, then **Authorize** and sign in. Attach it to a chat with `@pushary`. A custom server does not bring the rule; the [full guide](https://pushary.com/docs/agents/guides/grok-bot) has instructions to give your Bots.

Full guide: [pushary.com/docs/agents/guides/grok-bot](https://pushary.com/docs/agents/guides/grok-bot).

## What it does not do

- It does not replace Grok Bot's approval cards. Grok Bot still decides which actions need your approval and shows its own card for them.
- It cannot stop a Bot in the middle of a task. The Bot chooses when to call Pushary.
- A question nobody answers expires after about ten minutes. An expired question is never treated as a yes.
- All the services you connect by signing in to Pushary, such as Claude and every Bot, share one limit: 10 notifications or reminders per 5 minutes and 25 open questions.
- Your answer reaches the Bot that asked. It cannot start a new Bot task.

## Disconnect

Remove Pushary from **Connect apps** in Grok Bot to stop your Bots using the sign-in connection. Your Pushary account and its history stay as they are.

## What is in the plugin

| Part | File | What it does |
|------|------|--------------|
| MCP server | `mcp.json` | Connects Grok Bot to six Pushary tools: `send_notification`, `ask_user`, `wait_for_answer`, `cancel_question`, `schedule_reminder` and `propose_scope` |
| Rule | `rules/pushary.mdc` | Always-on guidance: when a Bot should notify you, when it should ask, and what it must leave out |

This plugin is for Grok Bot only. For the Cursor editor, use [Pushary for Cursor](https://github.com/Pushary/cursor-plugin), which also gates risky commands.

## Support

Questions or problems: [business@pushary.com](mailto:business@pushary.com). Security reports: see [SECURITY.md](SECURITY.md).

## License

MIT
