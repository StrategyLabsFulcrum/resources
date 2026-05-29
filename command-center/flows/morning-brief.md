# Flow: Morning Brief

A read-only glance at my day. No actions taken — just a briefing. Offer to triage at the end.

## Process
1. Read `../connectors/calendar.md`, `../connectors/gmail.md`, `../connectors/slack.md`, and
   `../connectors/clickup.md` (skip any not connected). Also read `../workspace/people.md` and
   `../workspace/clients.md` — use them to decode names so the brief reads in plain names and to
   prioritize known client and `[VIP]` contacts. If an unfamiliar name recurs, you may note it and
   offer to add it to `people.md` (with my ok).
2. Gather, in parallel where possible:
   - **Calendar** — today's events (chronological; flag back-to-backs and anything before 9am).
   - **Gmail** — urgent/unread since yesterday. "Urgent" = unread 🔴 RESPOND items (see
     `triage.md` categories). Cap at the top ~5; say how many more.
   - **Slack** — run all three passes in `slack.md`: unread DMs/mentions, **open questions to me** with
     no reply, and **commitments I made (especially yesterday) with no follow-up**. That last one is the
     point of the brief — resurface loops I opened and never closed. Cap each group at ~5.
   - **ClickUp** (if connected) — tasks due today or overdue.
3. Compose a short brief in this shape:

   ```
   Good morning. Here's {weekday}, {date}.

   📅 Today
   - {time} {event} ({attendees})
   ...

   🔁 Open loops — you owe   (primarily from Slack; the heart of the brief)
   - {who/where}: you said you'd {commitment} — no follow-up since {date}
   - {who/where}: asked you "{question}" — no reply
   ...

   🔴 Needs you (new since yesterday)
   - {source}: {from} — {subject}
   ...

   ✅ Due today (ClickUp)
   - {task} — {list}
   ...

   {one-line nudge, lead with open loops: e.g. "2 commitments still open from yesterday + 3 new replies needed. Want to triage?"}
   ```
   If there are no open loops, omit that section (don't fabricate one).
4. Do **not** draft, delete, or mark anything. If I say "yes, triage," follow `triage.md`.

## Audit (run before finishing)
- [ ] No messages were sent, drafted, deleted, or marked read.
- [ ] Sections for unconnected sources were omitted, not faked.
