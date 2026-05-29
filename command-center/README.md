# Command Center

A simple inbox workspace for Claude. It triages your Gmail and Slack, drafts replies in your voice, and
gives you a morning brief over your calendar — plus an optional ClickUp scan. Native Claude connectors,
**nothing to install.**

## What it is

A folder of plain markdown files. Claude reads them and acts. You can open and edit any of them — this
is a tool you shape by editing text, not code.

```
command-center/
  CLAUDE.md          ← the router: tells Claude what to do when you say "triage" etc.
  setup.md           ← run once to get started
  flows/             ← the playbooks (triage, morning-brief)
  connectors/        ← one file per source (gmail, slack, calendar, clickup)
  workspace/         ← your stuff: todos, followups, VOICE (you edit these)
```

## Get started (Cowork)

1. Copy this `command-center/` folder into `~/Documents/Claude/Projects/` (or anywhere you like).
2. Connect Gmail, Slack, and Google Calendar in Claude's connector settings (ClickUp optional).
3. Open a chat pointed at the folder and say **"setup"**.
4. Then say **"morning brief"** or **"triage."**

## Daily use

- **"morning brief"** — your day at a glance: calendar, urgent mail, missed Slack. No actions.
- **"triage"** — work through your inboxes: Claude categorizes, you rapid-fire `draft / remind / read /
  delete / skip`. Replies are always drafts you approve.
- Say **"just triage Slack"** to scope it to one source.

## Make it yours

- Edit `workspace/VOICE.md` so drafts sound like you.
- Edit `flows/triage.md` to change how triage behaves.
- **Add a new source** (e.g. iMessage): add one file in `connectors/` and one row in `CLAUDE.md`.

## Power-user (Code tab)

In the desktop Code tab you can make the flows auto-trigger from natural language: ask Claude to
"generate skill stubs for the flows." It creates `.claude/skills/` files that just point at the flow
files — so there's still one source of truth. (Cowork doesn't use skills; it uses `CLAUDE.md`.)
