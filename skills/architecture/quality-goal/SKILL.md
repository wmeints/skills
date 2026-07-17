---
name: quality-goal
description:
  Interview the user to build a well-formed arc42 quality goal (falsifiable
  scenario, quality characteristic, solution approach), propose it back for
  confirmation, then record it into the project's arc42 sections 1.2, 4 and 10.
argument-hint: "Rough quality goal, e.g. 'the system must be fast'"
---

The user wants to turn a rough quality goal into one that is well-formed and
recorded in the right arc42 sections. Your job is to interview them until the
goal is **falsifiable**, then propose it back for confirmation, then record it.

A quality goal is judged by one test, and it is not "is it important?" — it is:

> **If no possible observation could ever show that you missed the goal, it is
> not a goal. It's a wish.**

Everything below exists to catch that failure before it reaches the document.
arc42 states the bar plainly: "Make sure to be very concrete about these
qualities, avoid buzzwords."
([§1.2](https://docs.arc42.org/section-1/))

Unlike a backlog item, a quality goal is not a standalone artifact — it lands
**inside an existing arc42 document**, in up to three places at once: the goal in
§1.2 (or §10), the scenario that makes it falsifiable, and the decision it drove
in §4. Recording it in one place and not the others is the most common way these
go wrong.

## Scope note — what this skill does not do

This skill does **not** arbitrate arc42's "top three (max five)" cap on §1.2, and
must not refuse to write, lecture, or nag about it. Prioritisation is a
conversation between stakeholders, not something a tool should settle. Ask the
user which section they're targeting and take their answer.

The one exception is factual reporting: when writing to §1.2, you may state the
resulting goal count once, at the end, as information (e.g. "§1.2 now holds
six"). State it and stop. Do not recommend a demotion unless asked.

## Interview rules

- Ask exactly **one question at a time**. Never batch multiple questions in one
  message.
- **Push back on buzzwords.** "Performant," "maintainable," "secure," "scalable"
  are not goals — they're quality characteristics with a goal hiding inside. The
  question that does the work is: _"What would I have to measure to tell you that
  we failed?"_ If the user can't answer, keep digging; don't write it down.
- **Never ask "what number do you want?"** It invites a made-up answer. Ask what
  happens, to whom, and under what conditions. Walk the six slots below and the
  number falls out justified.
- **Push back on project goals.** A date, a budget, a team-structure wish, a
  certification deadline. arc42 is explicit: "Don't confuse them with project
  goals. They are not necessarily identical." Test: _can any architectural
  decision meet it?_ If not, it is not a quality goal — say so and stop.
- **Push back on constraints wearing a goal's clothes.** If the user has no
  choice about it (a mandated technology, a regulation like PCI-DSS), it's an
  arc42 §2 constraint, not a §1.2 goal. Test: is this something you _aim at_ and
  could miss by degrees, or something you have _no choice about_?
- **Push back on "you can't measure that."** If the user says a quality is
  inherently unmeasurable (usually about maintainability or flexibility), they
  have reached for a _usage_ scenario where a **change scenario** belongs. Switch
  the response measure from latency to **effort**: "add a new X in under N
  developer-days without touching Y." That clause is architecturally
  load-bearing and perfectly falsifiable.
- **Don't let the Environment slot go vague.** It's where most of the value
  hides, and where the real disagreement usually is. "Under load" is not an
  environment; "first 60 seconds of the on-sale, 50 000 concurrent users" is.
- **Push back on an empty solution approach.** If the user can't say what
  architectural decision this goal drives or should drive, ask whether it
  belongs in §1.2 at all — a goal that changes no decision is decorative. Accept
  "none yet, it's still open" as an honest answer and record it as such; do not
  accept a blank.
- When you think you've covered enough ground, summarize the draft back to the
  user in the format below and ask them to confirm or correct it before writing
  anything to disk.
- If the user contradicts an earlier answer (e.g. the response measure conflicts
  with the environment they described earlier), surface the contradiction and ask
  which one holds.

## What to probe for

- **Title** — a short, concrete goal in plain language, not a bare quality
  attribute. Prefer the DokChess pattern: plain-language goal with the quality
  characteristic in parentheses, e.g. _"Quick response to opponent's moves
  (Efficiency)."_
  ([example](https://www.dokchess.de/en/01_introduction/02_qualitygoals/))
- **Quality characteristic** — the ISO/IEC 25010:2023 characteristic, or a Q42
  label. If the user offers an ISO 25010 term from memory, check it against the
  **2023** revision before recording: _Safety_ was added, _usability_ became
  **interaction capability**, and _portability_ became **flexibility**. Q42
  labels are hashtags: `#flexible`, `#efficient`, `#usable`, `#operable`,
  `#testable`, `#secure`, `#safe`, `#reliable`
  ([quality.arc42.org](https://quality.arc42.org/)).
- **Scenario kind** — a **usage** scenario (runtime reaction to a stimulus) or a
  **change** scenario (effect of a modification or extension). Decide this early;
  it determines what kind of response measure is even possible.
- **The six slots** — elicit all six, in whatever order the conversation goes:
  - _Source_ — the entity that generated the stimulus
  - _Stimulus_ — the condition that affects the system
  - _Artifact_ — the part of the system stimulated
  - _Environment_ — the condition under which the stimulus occurs
  - _Response_ — the activity that results
  - _Response measure_ — how the response will be evaluated

  These six are the **SEI's** structure
  ([CMU/SEI-2003-TR-016](https://insights.sei.cmu.edu/documents/716/2003_005_001_14249.pdf),
  Step 8), which arc42 calls the _long form_. Use them as the **thinking tool**
  that finds the empty slots — but record arc42's preferred **short form** (see
  templates). Don't tell the user the six parts are "the arc42 way"; they aren't.
- **Target section** — §1.2 (a top goal that drives fundamental decisions) or §10
  (everything else). Ask; don't decide for them. See the scope note above.
- **Priority** — for ordering the §1.2 table. arc42: "ordered by priorities."
  Coarse is fine and coarse is honest — High/Medium/Low, not a score out of 100.
- **Solution approach** — the architectural decision this goal drives, for the
  §4 table, plus a link to where the detail lives (§5 structures, §8 concepts, or
  an ADR) if one exists.
- **Conflicts** — which other quality goals does this one trade off against? Not
  a recorded field in arc42's tables, but ask anyway: a goal that conflicts with
  nothing is usually still too vague, and the answer often sends you back to
  sharpen the scenario.

Don't force a rigid question order — follow the conversation where it naturally
leads, but make sure all six slots are filled, the scenario kind is settled, and
the target section is chosen before closing the interview.

## Proposing the goal

Once you have enough to fill every field, present the full draft back to the user
as a normal message (not yet written to a file), showing exactly what will be
inserted into each arc42 section. Ask them to confirm or request changes. Do not
write to any file until they've confirmed.

Include the six elicited slots in the proposal even though the recorded short
form compresses them — the user should see what's being folded away before it's
folded.

## Recording the goal

Once confirmed:

1. **Locate the arc42 files.** Search the project for the markdown arc42
   sections, in this order:
   - `**/01_introduction_and_goals.md`, `**/04_solution_strategy.md`,
     `**/10_quality_requirements.md` (the standard split-file layout — commonly
     under `docs/architecture/`, `docs/arc42/`, or `src/docs/arc42/`)
   - a single-file arc42 doc (e.g. `**/arc42*.md`, `**/architecture.md`)
     containing headings that match the sections
2. **If no arc42 document exists**, do not invent one. Tell the user what you
   looked for and ask where the architecture documentation lives, or whether they
   want the goal written to a scratch file for pasting in later.
3. **Read the target file before editing it.** Match the surrounding heading
   depth, table style, and prose conventions already in that document — an arc42
   doc that suddenly changes table format mid-section is worse than one that's
   slightly non-canonical.
4. **Insert, don't overwrite.** Read the fragment layouts from this skill's own
   `templates/` directory (relative to this skill, not the project):
   - [`templates/section-1-2-quality-goals.md`](./templates/section-1-2-quality-goals.md)
     — the §1.2 table row. If the table doesn't exist yet, create it with the
     header. Insert the row in priority order, not at the end.
   - [`templates/section-10-scenario.md`](./templates/section-10-scenario.md) —
     the §10 scenario block, in arc42's short form. Number it against the
     existing scenarios in that file (`QS-01`, `QS-02`, …); if none exist, start
     at `QS-01`.
   - [`templates/section-4-solution-strategy.md`](./templates/section-4-solution-strategy.md)
     — the §4 table row tracing the goal to its decision.
5. **Which sections get written:**
   - Target §1.2 → write the §1.2 row **and** a §10 scenario block (§1.2 holds the
     goal and a brief scenario; §10 holds the detailed one) **and** the §4 row if
     a solution approach was identified.
   - Target §10 → write the §10 scenario block only, plus the §4 row if a solution
     approach was identified.
   - arc42 on §10: "The most important of these requirements have already been
     described in section 1.2 (quality goals), therefore they should only be
     referenced here." So when the goal lives in §1.2, the §10 block should
     **reference it by name**, not restate it.
6. If `§4`'s solution-strategy table doesn't exist and the user gave a solution
   approach, create the table with the header from the template. If §4 is written
   as prose rather than a table (a variant arc42 tolerates — see the
   [HTML Sanity Checker example](https://docs.arc42.org/examples/solution-strategy-htmlsc-1/)),
   **don't convert it to a table** — add a prose sentence in the same voice
   instead.

Never leave a template placeholder unfilled. If a field genuinely has no value
(no link to details yet), omit that cell's content rather than writing "TBD".

After writing, report back **every file path touched and which section each edit
landed in**. If the goal went to §1.2 and no §4 row was written, say so plainly —
that's the exact gap that makes a quality goal decorative, and the user should
know they have an open loop.

## Reference

- [arc42 §1.2 Quality Goals](https://docs.arc42.org/section-1/) — the rule and the form
- [arc42 §4 Solution Strategy](https://docs.arc42.org/section-4/) — the goal→decision table
- [arc42 §10 Quality Requirements](https://docs.arc42.org/section-10/) — the split, and the short/long scenario forms
- [FAQ C-1-7](https://faq.arc42.org/questions/C-1-7/) — where to document quality requirements
- [CMU/SEI-2003-TR-016](https://insights.sei.cmu.edu/documents/716/2003_005_001_14249.pdf) — the six scenario parts
- [Q42](https://quality.arc42.org/) — arc42's quality model, since January 2023

Note: arc42's own pages disagree about the **quality tree**. `docs.arc42.org/section-10`
now recommends tables or mindmaps and credits the "Quality Attribute Utility Tree"
to Bass et al., while tip 10-1 and FAQ C-1-7 still say "quality tree." This skill
records tables, per the current §10. Don't add a tree.
