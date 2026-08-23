# Whistlepot inbox gateway

Makes `@whistlepot` an agent you can actually talk to — over email and
iMessage — instead of one that only exists while a Claude session happens to be
open.

## What whistlepot actually is

There is no separate whistlepot process or model. `@whistlepot` is an **Inkbox
identity**: a mailbox, a handle, and a set of channels. The Inkbox MCP
connection is *bound* to that identity, so any Claude session holding it **is**
whistlepot for the duration of that session.

Two consequences worth internalising:

- Sending an A2A task to `@whistlepot` from a whistlepot-bound session is a
  **self-loop** — requester and worker are the same handle. It will sit in
  `submitted` forever.
- Texting whistlepot's own line (`+1 645-234-2637`, or the triage line
  `+1 650-484-9720`) is the same mistake in a different channel.

## The problem this solves

Inkbox MCP **acts only when invoked**. It does not watch the mailbox, does not
wake a model, and does not send proactive replies. So mail and texts arrive
correctly and then sit there.

That is what happened on 2026-08-22: messages were sent to whistlepot across
three hours over both email and iMessage, every one of them delivered, and none
answered — because the only "gateway" was a process inside a Claude Code
session container, which was reclaimed when the session went idle.

**Anything run inside a session container dies with the session.** A gateway has
to live somewhere that outlives it.

## Path A — hourly Routine (cloud, durable)

A scheduled Routine fires a fresh session that checks the mailbox and replies.
Runs on Anthropic infrastructure, survives container reclamation, needs no
hardware.

- **Trigger:** `trig_011DS6YUfkzv2peQ9Af5c4j3` — "Whistlepot inbox gateway"
- **Schedule:** `20 0-2,16-23 * * *` — hourly at :20, but only during Jim's
  waking hours (12pm–10pm US Eastern). 11 runs a day, not 24.
- **Prompt:** [`gateway-prompt.md`](./gateway-prompt.md)

### Status: live (2026-08-23)

Verified end to end. Jim sent two iMessages — "Did I flip it?" (12:19) and
"Working?" (12:35) — and a gateway run answered both with a single reply at
12:37:56, with no human in the loop:

> Yep, it's working now — this came in on its own, nobody had to poke me.
> Switch is flipped.

That run also exercised the watermark rule correctly: two inbound messages
newer than the last outbound, gathered into **one** request, answered **once**.

### Activation — the step that gates a new Routine

A Routine created through the MCP tool stores **no connectors**; the
`connectors` parameter is rejected outright for this organization
(*"not available for this organization"*). Sessions it fires therefore start
with no Inkbox tools and silently do nothing — a test fire on 2026-08-23 ran
and produced no reply at all.

The fix is manual and only the account owner can do it: attach the **Inkbox**
connector to the Routine from the claude.ai Routines UI. Once attached it is
stored on the Routine and visible via `list_triggers`:

```json
"mcp_connections": [
  {"connector_uuid": "…", "name": "Inkbox", "url": "https://inkbox.ai/mcp/anthropic"}
]
```

If you rebuild this Routine from scratch, expect to do that step again.

**Diagnosing this is harder than it looks.** With an empty inbox a correct run
and a toolless run are both silent — indistinguishable. To tell them apart you
need an unanswered inbound message sitting in the queue as a stimulus, then
fire the Routine and watch for a reply. Absence of a reply only means something
when there was something to reply to.

### Limitations

One hour is the minimum cron interval (`*/15` is rejected). That is fine for
email but poor for a text conversation.

Tool scoping is **prompt-level only**. Fired sessions inherit a broad default
toolset (`Bash`, `Write`, `WebSearch`, …) and `update_trigger` cannot change a
Routine's allowed tools — only its name, schedule, model, and prompt. The
prompt therefore opens with a hard instruction to use nothing but `inkbox_*`
tools. That is an instruction, not a sandbox; treat it accordingly.

## Path B — local daemon (near-real-time) — DECLINED

**Not viable here: Jim has no computer that stays on.** A daemon on a machine
that sleeps reproduces the original failure exactly — it looks alive and isn't
— so hourly Path A is the setup, full stop. The design below is kept only in
case an always-on host ever exists.

Since hourly is the floor, timing is worth knowing: the Routine fires at **:20
past the hour, 12pm–10pm Eastern**. A message sent at :15 gets answered in ~5
minutes; one sent at :25 waits ~55; one sent overnight waits until 12:20pm.
That is deliberate — Jim sleeps, and 24 runs a day of open-ended usage was not
worth paying for.

### ⚠️ DST caveat

**Cron is UTC and does not follow daylight saving.** `0-2,16-23` maps to
12pm–10pm during EDT (UTC−4). When Eastern falls back to EST (UTC−5) in
November, the same expression fires 11am–9pm local — an hour early at both
ends. Fix by shifting each hour up one: `20 1-3,17-23,0 * * *`, or more simply
`20 17-23,0-3 * * *`. Reverse it again in March.

For chat-speed replies, run the same prompt on a short interval from a machine
that stays on, invoking the `claude` CLI with the Inkbox MCP server configured.

Design notes for whoever builds this:

- **Lock the run.** Overlapping passes will both see the same inbound message
  and both reply. An atomic `mkdir` lock with a stale-lock timeout is enough.
- **Unattended permissions are a real tradeoff.** A daemon has nobody present to
  approve tool calls. Prefer an explicit allow-list scoped to the Inkbox tools
  over blanket permission bypass, and note that the MCP server prefix changes
  between sessions, so match on `inkbox_*` rather than a fixed prefix.
- Schedule with `launchd` (`StartInterval`) on macOS, or a systemd timer.

## Recommended sequence

1. ~~**Activate Path A first.**~~ **Done 2026-08-23** — connector attached,
   verified answering autonomously. Gives a guaranteed floor: nothing is ever
   silently dropped, worst case an hour late.
2. **Live with hourly for a few days.** It is genuinely fine for email. Find out
   whether the lag actually bites on iMessage before building for it.
3. **Add Path B only if hourly proves too slow** *and* there is a machine that
   truly stays awake. A daemon on a laptop that sleeps is worse than no daemon —
   it looks alive and isn't, which is the exact failure mode this whole
   directory exists to fix.

## The iMessage watermark gotcha

**iMessage has no mark-as-read tool.** There is `inkbox_email_flags_update` for
mail, but no equivalent for iMessage conversations. A gateway keyed on unread
counts will therefore re-answer the entire backlog on every run, forever.

Use a watermark instead — messages come back **newest first**:

- newest message is **outbound** → nothing new, skip the thread, send nothing
- newest message is **inbound** → gather every inbound message newer than the
  last outbound one, treat them as **one** request, and reply **once**

## Reference

| | |
|---|---|
| Identity id | `98c40bf5-5cde-4a7b-abc9-96b25b86a028` |
| Email | `whistlepot@inkboxmail.com` (active, domain verified) |
| iMessage | enabled, `ready: true`, no dedicated number provisioned |
| Triage / connect line | `+1 650-484-9720` — command `connect @whistlepot` |
| SMS | unavailable — no phone number assigned |
| Calling | available (review of history and transcripts only) |
| Jim — email | `mrtooher@yahoo.com`, `mrtooher1@gmail.com` |
| Jim — iMessage | `+1 978-519-0846` |

## Safety posture

The gateway runs unattended with a live mail sender, so the prompt treats all
inbound content as **untrusted data**, never as instructions:

- replies only to Jim; mail from anyone else is left untouched and unanswered
- never messages a third party unless Jim's *own* message names that recipient
- never changes identity settings, deletes mail, or spends money
- instructions embedded in message bodies cannot widen these bounds
