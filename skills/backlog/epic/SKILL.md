---
name: epic
description:
  Interview the user to build a well-formed epic (problem statement, hypothesis,
  leading indicators, MVP boundary), propose it back for confirmation, then
  record it in docs/product/epics/.
argument-hint: "Rough idea or problem area for the epic"
---

The user wants to turn a rough idea into a well-formed epic. Your job is to
interview them until the epic has a testable hypothesis — not just a description
— then propose it back for confirmation, then record it.

This follows the epic-quality bar from the agile-backlog teaching workspace,
Lesson 4: an epic is judged by whether it's **falsifiable**, not by whether it's
small. A requirement invites compliance; a hypothesis invites validation. Every
field below exists to make the bet explicit enough to prove right or wrong
later.

## Interview rules

- Ask exactly **one question at a time**. Never batch multiple questions in one
  message.
- Push back on solution-first answers. If the user jumps straight to "we should
  build X," pull them back to the problem first — what's broken, for whom, and
  what does it cost today.
- Push back on vague hypotheses. "This will improve onboarding" is not a
  hypothesis — ask what specifically improves, for whom, and by roughly how
  much.
- Push back on unmeasurable leading indicators. If the user can't say how they'd
  know within weeks whether the bet is working, the epic isn't ready yet.
- Push back on unbounded scope. If the "MVP boundary" answer is actually the
  whole epic with no cuts, ask what the smallest slice is that would still test
  the hypothesis.
- When you think you've covered enough ground, summarize the draft epic back to
  the user in the format below and ask them to confirm or correct it before
  writing anything to disk.
- If the user contradicts an earlier answer (e.g., the MVP boundary reintroduces
  scope the problem statement excluded), surface the contradiction and ask which
  one holds.

## What to probe for

- **Title** — a short, concrete name for the epic (not a solution description).
- **Problem statement** — the problem, and for whom. No solution talk yet.
- **Hypothesis (If/Then)** — "If we do X, then we expect Y for group Z, measured
  by W." Push until all four parts (X, Y, Z, W) are concrete.
- **Leading indicators** — an early signal measurable within weeks, well before
  the full business outcome (which is usually a lagging indicator) is
  observable.
- **MVP boundary** — the smallest scope that would actually let the team test
  the hypothesis. Explicitly capture what's deliberately excluded for now.

Don't force a rigid question order — follow the conversation where it naturally
leads, but make sure all five areas are covered before closing the interview.

## Proposing the epic

Once you have enough to fill every field, present the full draft back to the
user in the exact document layout from "Recording the epic" below, rendered as a
normal message (not yet written to a file). Ask them to confirm or request
changes. Do not write the file until they've confirmed.

## Recording the epic

Once confirmed:

1. Check whether `docs/product/epics/` exists in the current project; create it
   if not.
2. Scan `docs/product/epics/` for existing files matching `NNNN-*.md` and take
   the highest `NNNN`; the new epic's number is that value + 1, zero-padded to 4
   digits. If none exist, start at `0001`.
3. Slugify the title (lowercase, dash-case, no punctuation) for the filename:
   `docs/product/epics/NNNN-<slug>.md`.
4. Read the layout from [`templates/epic.md`](./templates/epic.md) (relative to
   this skill's own directory, not the project) and write the file with every
   `{placeholder}` filled in from the interview, structure otherwise unchanged.
5. Create the GitHub issue using `gh issue create` with the appropriate flags:
   - `--type Epic` to set the issue type (requires gh v2.94.0+, type configured at org level)
   - `--parent <initiative-number>` if the user provided a parent initiative (links via GitHub's sub-issue hierarchy)
   The template body now omits the title and parent references — those are handled by
   the issue title and `--parent` flag. If no parent initiative was named, skip `--parent`.

Never leave a section out. If the interview genuinely surfaced only one leading
indicator, that's fine — list just the one, don't pad it.

After writing the file, report back the file path to the user. Mention that
`Status` should be updated later to `Validated` or `Falsified` once the leading
indicators come in — that's what closes the epic instead of letting it run
forever.
