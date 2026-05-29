# Flow: Morning Brief

A read-only glance at my day. No actions taken — just a briefing. Offer to triage at the end.

## Process
1. Read `../connectors/calendar.md`, `../connectors/gmail.md`, `../connectors/slack.md`, and
   `../connectors/clickup.md` (skip any not connected). Also read `../workspace/people.md` and
   `../workspace/clients.md` — use them to decode names so the brief reads in plain names and to
   prioritize known client and `[VIP]` contacts. If an unfamiliar name recurs, you may note it and
   offer to add it to `people.md` (with my ok). And read `../workspace/todos.md` and
   `../workspace/followups.md` — my existing ledger of to-dos and people awaiting a reply.
2. Gather, in parallel where possible:
   - **Calendar** — today's events (chronological; flag back-to-backs and anything before 9am).
   - **Gmail** — urgent/unread since yesterday. "Urgent" = unread 🔴 RESPOND items (see
     `triage.md` categories). Cap at the top ~5; say how many more.
   - **Slack** — run all three passes in `slack.md`: unread DMs/mentions, **open questions to me** with
     no reply, and **commitments I made (especially yesterday) with no follow-up**. That last one is the
     point of the brief — resurface loops I opened and never closed. Cap each group at ~5.
   - **Ledger** — from `todos.md`: items due today or overdue. From `followups.md`: people who've been
     waiting a while (flag anything aging, e.g. 3+ days). This is the persistent record; resurface it.
   - **ClickUp** (if connected) — tasks due today or overdue.
3. Compose a short brief in this shape:

   ```
   Good morning. Here's {weekday}, {date}.

   📅 Today
   - {time} {event} ({attendees})
   ...

   🔁 Open loops — you owe   (the heart of the brief: live Slack loops + aging followups.md, deduped)
   - {who/where}: you said you'd {commitment} — no follow-up since {date}
   - {who/where}: asked you "{question}" — no reply
   - {person}: waiting on your reply since {date}   (from followups.md)
   ...

   🔴 Needs you (new since yesterday)
   - {source}: {from} — {subject}
   ...

   📝 On your plate (due today / overdue, from todos.md)
   - [ ] {todo} — due {date}
   ...

   ✅ Due today (ClickUp)
   - {task} — {list}
   ...

   {one-line nudge, lead with open loops: e.g. "2 commitments still open from yesterday + 1 todo due today + 3 new replies needed. Want to triage?"}
   ```
   Omit any section that's empty (don't fabricate one). Dedupe the open-loops list so a Slack commitment
   already logged in `followups.md` shows once.
4. Do **not** draft, delete, mark, or edit anything — including `todos.md`/`followups.md`. The brief only
   reads. If I say "yes, triage," follow `triage.md`.

## Audit (run before finishing)
- [ ] No messages were sent, drafted, deleted, or marked read.
- [ ] `todos.md` / `followups.md` were read, not modified.
- [ ] Sections for unconnected/empty sources were omitted, not faked.
