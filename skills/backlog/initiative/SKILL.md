---
name: initiative
description:
  Interview the user to write a well-formed initiative (outcome-flavored name,
  why now, success measure, rough size, status), propose it back for
  confirmation, then record it in docs/initiatives/.
argument-hint: "Rough goal area or direction for the initiative"
---

The user wants to turn a rough goal area into a well-formed initiative. Your job
is to interview them until the initiative is coarse but clear, then propose it
back for confirmation, then record it.

This follows the initiative-quality bar from the agile-backlog teaching
workspace, Lesson 6: an initiative sits one level above an epic — it's a
direction worth tracking, not yet a bet. It should stay deliberately coarser
than an epic hypothesis (no If/Then hypothesis, no leading indicators, no MVP
boundary — that detail belongs to `/epic`, written only once the initiative is
activated).

## Interview rules

- Ask exactly **one question at a time**. Never batch multiple questions in one
  message.
- Push back on solution-flavored names. If the user proposes a name like "Add X
  feature" or "Build Y," redirect them to the outcome it serves — "what
  direction/capability does that move you toward?"
- Push back on premature detail. If the user starts describing a hypothesis, MVP
  boundary, or acceptance criteria, note that's epic-level detail (point them to
  `/epic` for later) and pull the conversation back to initiative-level
  coarseness.
- Push back on vague success measures. "People will be happy" isn't a measure —
  ask what observable change would tell them it worked, even a rough or lagging
  one. It does not need to be a leading indicator; that precision comes at epic
  level.
- Push back on missing "why now." If the user can't say why this matters now vs.
  later, probe for the actual pain or opportunity driving it.
- When you think you've covered enough ground, summarize the draft initiative
  back to the user in the format below and ask them to confirm or correct it
  before writing anything to disk.
- If the user contradicts an earlier answer, surface the contradiction and ask
  which one holds.

## What to probe for

- **Name** — short, outcome-flavored, not a solution.
- **Why now** — the problem or opportunity driving this, for whom, and why it
  matters now rather than later.
- **Success measure** — a rough, often lagging measure of whether this mattered.
  No leading indicators needed yet.
- **Rough size** — S / M / L / XL, gut-feel, not an estimate.
- **Status** — Not started / Active / Done / Dropped.

Don't force a rigid question order — follow the conversation where it naturally
leads, but make sure all five fields are covered before closing the interview.

## Proposing the initiative

Once you have enough to fill every field, present the full draft back to the
user in the exact document layout from "Recording the initiative" below,
rendered as a normal message (not yet written to a file). Ask them to confirm or
request changes. Do not write the file until they've confirmed.

## Recording the initiative

Once confirmed:

1. Check whether `docs/initiatives/` exists in the current project; create it if
   not.
2. Scan `docs/initiatives/` for existing files matching `NNNN-*.md` and take the
   highest `NNNN`; the new initiative's number is that value + 1, zero-padded to
   4 digits. If none exist, start at `0001`.
3. Slugify the name (lowercase, dash-case, no punctuation) for the filename:
   `docs/initiatives/NNNN-<slug>.md`.
4. Read the layout from [`templates/initiative.md`](./templates/initiative.md)
   (relative to this skill's own directory, not the project) and write the file
   with every `{placeholder}` filled in from the interview, structure otherwise
   unchanged.

Never leave a section out.

After writing the file, report back the file path to the user. If Status is
`Active`, mention that the natural next step is running `/epic` to draft the
epic hypothesis this initiative decomposes into.
