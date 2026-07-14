---
name: feature
description:
  Interview the user to build a well-formed feature (parent epic, benefit
  hypothesis, acceptance criteria), propose it back for confirmation, then
  record it in docs/product/features/.
argument-hint: "Rough capability or feature idea, and the epic it belongs to"
---

The user wants to turn a rough capability idea into a well-formed feature. Your
job is to interview them until the feature has a clear benefit hypothesis and
outcome-focused acceptance criteria, then propose it back for confirmation, then
record it.

This follows the feature-quality bar from the agile-backlog teaching workspace,
Lesson 4: a feature sits between an epic and its stories. It needs a **benefit
hypothesis** (the quantifiable value a stakeholder gets) and **acceptance
criteria** (the minimum conditions for that benefit to count as delivered) — not
a hypothesis as sweeping as an epic's, and not INVEST-checked like a story, but
a real, falsifiable claim of value.

## Interview rules

- Ask exactly **one question at a time**. Never batch multiple questions in one
  message.
- Push back if there's no parent epic named. A feature without a parent epic is
  either actually an epic itself, or a stray idea that hasn't been placed in the
  backlog yet — resolve which before continuing.
- Push back on solution-first answers. If the user describes only what to build,
  pull them back to who benefits and how much.
- Push back on vague benefit hypotheses. "This will be better for users" isn't
  quantifiable — ask what specifically improves, for whom, and by roughly how
  much.
- Push back on acceptance criteria that dictate implementation instead of
  outcome. Acceptance criteria describe what's done (the outside), not how it's
  built (the inside) — e.g. "exact button color" is not an acceptance criterion.
- Push back on acceptance-criteria sprawl. Typically 3-5 criteria are enough; a
  much longer list usually means the feature needs splitting (see Lesson 3
  story-splitting patterns — the same patterns apply one level up) or the PO is
  over-specifying.
- When you think you've covered enough ground, summarize the draft feature back
  to the user in the format below and ask them to confirm or correct it before
  writing anything to disk.
- If the user contradicts an earlier answer, surface the contradiction and ask
  which one holds.

## What to probe for

- **Title** — a short, concrete name for the feature (not a solution
  description).
- **Parent epic** — which epic this feature rolls up under.
- **Benefit hypothesis** — the quantifiable value a stakeholder/user gets once
  this feature ships.
- **Acceptance criteria** — the minimum, outcome-focused conditions for that
  benefit to count as delivered.

Don't force a rigid question order — follow the conversation where it naturally
leads, but make sure all four areas are covered before closing the interview.

## Proposing the feature

Once you have enough to fill every field, present the full draft back to the
user in the exact document layout from "Recording the feature" below, rendered
as a normal message (not yet written to a file). Ask them to confirm or request
changes. Do not write the file until they've confirmed.

## Recording the feature

Once confirmed:

1. Check whether `docs/product/features/` exists in the current project; create
   it if not.
2. Scan `docs/product/features/` for existing files matching `NNNN-*.md` and
   take the highest `NNNN`; the new feature's number is that value + 1,
   zero-padded to 4 digits. If none exist, start at `0001`.
3. Slugify the title (lowercase, dash-case, no punctuation) for the filename:
   `docs/product/features/NNNN-<slug>.md`.
4. Read the layout from [`templates/feature.md`](./templates/feature.md)
   (relative to this skill's own directory, not the project) and write the file
   with every `{placeholder}` filled in from the interview, structure otherwise
   unchanged.

Never leave a section out. If the interview genuinely surfaced only one
acceptance criterion, that's fine — list just the one, don't pad it.

After writing the file, report back the file path to the user. Mention that
`Status` should be updated later to `Validated` or `Falsified` once the
acceptance criteria are met and the benefit is actually observed — that's what
closes the feature instead of leaving it open-ended.
