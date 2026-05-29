# Workshop: Command Center (demo then teach)

## Part 1 — Demo (5 min)

1. Open a Cowork chat on the `command-center` folder.
2. Say **"morning brief."** Show: it pulled calendar + urgent mail + missed Slack with zero setup.
3. Say **"triage."** Rapid-fire a few codes. Show a draft being written in your voice — and that it's a
   *draft*, nothing sent.
4. Open `workspace/VOICE.md` in Finder, tweak it live, re-draft. "You edit the tool by editing text."

## Part 2 — Teach (10 min)

1. Open `CLAUDE.md` — "this is the whole brain: a router. It points; it doesn't do."
2. Open `flows/triage.md` — "the actual playbook lives here. One source of truth."
3. Open `connectors/gmail.md` — "each source is a small adapter with a contract: what it reads, what it
   does, what it writes."
4. **The payoff:** "Adding iMessage tomorrow is one new file in `connectors/` and one row in `CLAUDE.md`.
   That's the whole change." Contrast with a single giant skill.

## Part 3 — ICM tie-in (5 min)

Map each piece to the ICM principle it embodies: separation of concerns (connectors), canonical sources
(router points, flows own logic), plain-text edit surfaces (`workspace/`), stage contracts (connectors),
glass-box (it's all files you can read). Note the conscious divergence: ICM is a sequential pipeline;
this is a fan-out router — same principles, different shape.

## Hand-out

The repo: `StrategyLabsFulcrum/resources` → `command-center/`. Copy it, run `setup`, go.
