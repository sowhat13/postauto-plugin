# Postauto for Claude Code

Draft, schedule and publish social posts from Claude Code, over Postauto's
MCP server, signed in with OAuth. No key to paste.

```bash
claude plugin marketplace add sowhat13/postauto-plugin
claude plugin install postauto@postauto
```

Then `/mcp` inside Claude Code and follow the browser to sign in. The server
offers the whole tool set, resources under `postauto://` and a set of prompts;
the skill in this plugin tells Claude the order a run goes in and what reaches
an audience.

Documentation: https://postauto.io/mcp
