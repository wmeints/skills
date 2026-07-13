---
name: story
description: Interview the user to build a well-formed user story (parent feature, story statement, testable acceptance criteria), enforcing INVEST, propose it back for confirmation, then record it in docs/product/stories/.
argument-hint: "Rough piece of work, and the feature it belongs to"
---

The user wants to turn a rough piece of work into a well-formed story. Your job is to interview them until the story passes INVEST (Lesson 2 of the agile-backlog teaching workspace), then propose it back for confirmation, then record it.

Unlike epics and features, a story is judged by size and testability, not just value — it must be **Independent, Negotiable, Valuable, Estimable, Small, Testable**. Every interview rule below exists to catch one INVEST letter failing before the story gets written down.

## Interview rules

- Ask exactly **one question at a time**. Never batch multiple questions in one message.
- Push back if there's no parent feature named. A story without a parent feature is either actually a feature itself, or not yet placed in the backlog — resolve which before continuing.
- **Independent** — ask whether this story can ship without another unbuilt story landing first. If it's blocked on something else, say so explicitly rather than pretending it's independent.
- **Negotiable** — if the user dictates exact UI copy, field order, or other implementation detail with nothing left to discuss with the team, push back: the story should state the outcome, not the full solution.
- **Valuable** — if the story is really a technical task ("refactor X," "add a column to Y") with no direct user/stakeholder benefit, say so — that belongs inside another story's implementation, not as its own story.
- **Estimable** — if the team genuinely couldn't size this yet (too much unknown), suggest a spike story first (Lesson 3's "Break Out a Spike" pattern) instead of guessing.
- **Small** — if this sounds like more than a few days of work, or the user is describing multiple scenarios/variations bundled together, do NOT record it as one story. Point them at the story-splitting patterns (Lesson 3 / `reference/story-splitting-patterns.html` in the teaching workspace) and have them pick one slice to record now; the rest become separate `/story` runs later.
- **Testable** — every acceptance criterion must be a concrete pass/fail check. "Improve the experience" is not testable; push for the observable behavior.
- When you think you've covered enough ground, summarize the draft story back to the user in the format below and ask them to confirm or correct it before writing anything to disk.
- If the user contradicts an earlier answer, surface the contradiction and ask which one holds.

## What to probe for

- **Title** — a short, concrete name for the story.
- **Parent feature** — which feature this story rolls up under.
- **Story statement** — "As a {user}, I want {capability}, so that {benefit}."
- **Acceptance criteria** — concrete Given/When/Then scenarios, including negative/edge cases. Typically 3-5; more usually means it still isn't Small.
- **Explicitly out of scope** — anything deliberately cut to keep the story Small.

Don't force a rigid question order — follow the conversation where it naturally leads, but make sure all INVEST letters have been checked before closing the interview.

## Proposing the story

Once you have enough to fill every field, present the full draft back to the user in the exact document layout from "Recording the story" below, rendered as a normal message (not yet written to a file). Ask them to confirm or request changes. Do not write the file until they've confirmed.

## Recording the story

Once confirmed:

1. Check whether `docs/product/stories/` exists in the current project; create it if not.
2. Scan `docs/product/stories/` for existing files matching `NNNN-*.md` and take the highest `NNNN`; the new story's number is that value + 1, zero-padded to 4 digits. If none exist, start at `0001`.
3. Slugify the title (lowercase, dash-case, no punctuation) for the filename: `docs/product/stories/NNNN-<slug>.md`.
4. Read the layout from [`templates/story.md`](./templates/story.md) (relative to this skill's own directory, not the project) and write the file with every `{placeholder}` filled in from the interview, structure otherwise unchanged.

Never leave a section out. If the interview genuinely surfaced only one acceptance criterion, that's fine — list just the one, don't pad it.

After writing the file, report back the file path to the user. Mention that `Status` moves to `Ready` once the team agrees it meets their Definition of Ready, and `Done` once it ships and the acceptance criteria are verified.
