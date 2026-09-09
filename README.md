# Postauto for Claude Code

Draft, schedule and publish social posts to your connected channels from
Claude Code, over Postauto's MCP server. Sign in with OAuth in the browser;
there is no key to paste.

```bash
claude plugin marketplace add sowhat13/postauto-plugin
claude plugin install postauto@postauto
```

Then run `/mcp` inside Claude Code and follow the browser to sign in.

## What is in here

This repository is the distribution: a Claude Code plugin marketplace carrying
one plugin. The plugin is a pointer, not a program.

| File | What it is |
| --- | --- |
| `.claude-plugin/marketplace.json` | The marketplace entry `claude plugin marketplace add` reads |
| `plugins/postauto/.claude-plugin/plugin.json` | The plugin's own manifest |
| `plugins/postauto/.mcp.json` | The one line that matters: the MCP endpoint to connect to |
| `plugins/postauto/skills/postauto/SKILL.md` | The skill: which tool to call, in what order, and what reaches an audience |

Postauto itself is a hosted service. Nothing here runs on your machine except
the MCP client Claude Code already has, and nothing here holds a credential.

## What you get once connected

Typed tools for the whole loop: read the plan and the channels, ask a network
what it accepts, draft, schedule, publish, and report on what went out. Plus
resources under `postauto://` and a set of one-message prompts.

Two things the skill is careful about, and you should be too:

- **Publishing cannot be undone.** `publishNow`, `scheduledAt` and `nextSlot`
  all reach a real audience. Claude asks before using them.
- **Every write takes an idempotency key**, so a retry after a timeout cannot
  post twice.

## Requires

A Postauto account. Sign up at [postauto.io](https://postauto.io).

## Links

- Documentation: https://postauto.io/mcp
- The MCP endpoint: `https://api.postauto.io/api/mcp`

## Licence

MIT. See [LICENSE](LICENSE).
