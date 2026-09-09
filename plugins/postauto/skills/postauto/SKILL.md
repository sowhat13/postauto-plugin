---
name: postauto
description: Use when the user wants to draft, schedule, queue, publish or report on social posts across their connected channels through Postauto, or asks what a network accepts.
---

# Postauto

Postauto is connected as the `postauto` MCP server. Its tools are listed in
the order a run uses them; the `postauto://guide` resource carries the same
order with what each step is for.

## Before writing

1. `account_status` says how much of the plan is left this month.
2. `list_accounts` gives the channel ids every write takes. When the person
   names a client rather than channels, `resolve_client` turns the name into
   channel ids and refuses an ambiguous one: ask, never guess.
3. `get_network_rules` (or `postauto://networks/{network}`) says how each
   network counts text, which shapes a post can take there, what each shape
   accepts as a file, and which settings are required. `split_into_thread`
   counts the way one network counts.

## Writing

- `create_post` with no departure saves a draft that waits for a person. Pass
  `idempotencyKey` on every mutating call so a retry after a timeout cannot
  do it twice.
- `scheduledAt`, `nextSlot` and `publishNow` all reach an audience, now or on
  a delay, and none of it can be undone. Say so before using them.
- `overrides` gives one channel its own text; `parts` sends a thread to X,
  Bluesky or Threads; `mediaByAccount` picks which files one channel sends.
- `update_post` revises a post that has not gone out, keeping its id, share
  link and tags. Prefer it over delete and recreate.

## Finishing and repairing

- `publish_post` sends an approved post now; `retry_target` flies one failed
  channel again. Both ask the person first in Claude Code.
- `list_notifications` is the only place a failure on a post you did not
  publish yourself reaches you. `acknowledge_notifications` closes what you
  dealt with, and only that.

## Prompts the server offers

`draft_week`, `review_and_publish`, `repair_failures`, `weekly_report` and
`connect_feed` are one-message workflows; use them when the ask matches.
