<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="assets/SL-Logo-Horizontal-White.png">
    <img src="assets/SL-Logo-Horizontal-Black.png" alt="Strategy Labs" width="320">
  </picture>
</p>

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
  workspace/         ← your stuff: todos, followups, VOICE, people, clients (you edit these)
```

## Download it

Paste this into Terminal. It drops a copy into `~/Documents/Claude/Projects/command-center` (your
personal notes stay in that copy — they never touch the shared repo):

```bash
mkdir -p ~/Documents/Claude/Projects && \
git clone --depth=1 https://github.com/StrategyLabsFulcrum/resources.git /tmp/sl-resources && \
cp -R /tmp/sl-resources/command-center ~/Documents/Claude/Projects/command-center && \
rm -rf /tmp/sl-resources && \
echo "✅ Command Center ready — open a Cowork chat on the folder and say setup"
```

(First time you use `git`, macOS may prompt you to install the Xcode command line tools — say yes.)

## Get started (Cowork)

1. Run the download command above (or copy the `command-center/` folder anywhere you like).
2. Connect Gmail, Slack, and Google Calendar in Claude's connector settings (ClickUp optional).
3. Open a chat pointed at the folder and say **"setup"**.
4. Then say **"morning brief"** or **"triage."**

## Daily use

- **"morning brief"** — your day at a glance: calendar, urgent mail, missed Slack. No actions.
- **"triage"** — work through your inboxes: Claude shows a numbered list, you rapid-fire `draft / remind /
  read / delete / skip` by number (e.g. `1: draft, 3-5: delete`). Replies are always drafts you approve.
- Prefer a slower pass? Say **"triage one at a time"** — Claude recommends an action per message and you
  just confirm.
- Say **"just triage Slack"** to scope it to one source.

## Make it yours

- Edit `workspace/VOICE.md` so drafts sound like you.
- Fill in `workspace/clients.md` and `workspace/people.md` — Claude will recognize names that come up,
  prioritize client and `[VIP]` contacts, and draft with context. (They also grow as you go: Claude
  offers to add unfamiliar names that keep appearing.)
- Edit `flows/triage.md` to change how triage behaves.
- **Add a new source** (e.g. iMessage): add one file in `connectors/` and one row in `CLAUDE.md`.

## Power-user (Code tab)

In the desktop Code tab you can make the flows auto-trigger from natural language: ask Claude to
"generate skill stubs for the flows." It creates `.claude/skills/` files that just point at the flow
files — so there's still one source of truth. (Cowork doesn't use skills; it uses `CLAUDE.md`.)
