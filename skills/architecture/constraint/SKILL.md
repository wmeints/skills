---
name: constraint
description:
  Interview the user to classify a candidate architecture constraint — applying
  arc42's freedom test, filtering out design decisions, quality requirements and
  entries that shouldn't be documented at all — then record it into the project's
  arc42 section 2.
argument-hint: "Rough constraint, e.g. 'we have to use PostgreSQL'"
---

The user wants to record something in arc42 §2. Your job is to find out whether
it belongs there at all, and if it does, to make it sharp enough to be worth the
maintenance. Most of the value in this skill is in what it **stops** from being
written.

Two tests, in order. The first is the one everyone skips:

> **1. Should this be documented at all?** arc42: "At first — try to avoid
> documentation of constraints, as somebody else might already have documented
> them. Refer or link to existing documentation."
> ([FAQ C-2-3](https://faq.arc42.org/questions/C-2-3/))

> **2. Is it a constraint?** "Any requirement that constrains software architects
> in their freedom of design and implementation decisions or decision about the
> development process."
> ([§2 Contents](https://docs.arc42.org/section-2/))

Test 2 is about **freedom**, not origin. It never asks who decided.

Like a quality goal, a constraint is not a standalone artifact — it lands inside
an existing arc42 document. Unlike a quality goal, it usually lands in exactly
one place (§2), and the skill's job is mostly triage: three of the four possible
rulings send the user somewhere else.

## The misconception this skill exists to correct

The common test — _"a real constraint is something imposed on us; if we chose it,
it's a decision"_ — is **contradicted by arc42's own text**, and you must not
apply it:

- [FAQ C-2-2](https://faq.arc42.org/questions/C-2-2/) lists, as a technical
  constraint, "adherence to specific technical or architectural **decisions**
  (e.g. use of specific frameworks or libraries)." **Someone else's decision is
  legitimately your constraint.**
- The template's own Motivation says: "Constraints must always be dealt with;
  **they may be negotiable, though.**" Constraints are binding-until-renegotiated,
  **not** non-negotiable. [FAQ C-2-4](https://faq.arc42.org/questions/C-2-4/) goes
  further and *instructs* negotiation of unfavorable ones.

Be precise about how far this goes. External origin is a strong **tendency** in
arc42's material — every example in C-2-1 is externally imposed, and
[Tip 2-1](https://docs.arc42.org/tips/2-1/) says to hunt constraints by looking
outward ("if you don't know any constraints of your system, start looking at
other systems within the organization"). It is a heuristic that usually fires
correctly. It is **not a criterion**. Never rule an entry out solely because the
team chose it.

**The classification is positional, not intrinsic.** "We use PostgreSQL" is a §2
constraint or a §9 decision depending on *whose freedom is scoped by this
document*:

- Central IT mandates it; this team may not deviate → the alternatives were
  removed before design began. **Constraint.**
- This team ran a spike, compared alternatives, chose it → freedom was exercised.
  **Decision (§9).**

Same sentence, different section. This is why you must ask about **provenance and
scope** before ruling, and why you cannot rule from the sentence alone.

## Scope note — what this skill does not do

- **It does not write ADRs.** If the ruling is §9, say so, explain why, and stop.
  Don't draft the decision record.
- **It does not write quality goals.** If the ruling is §1.2/§10, hand off to
  **`/quality-goal`**, which does that job properly.
- **It does not enforce a house style on constraint wording.** arc42 documents
  **no** anti-patterns for constraints and prescribes **no** columns. Any
  "constraints must be testable"-style rule is convention, not doctrine. You may
  push for a motivation (see below) because the examples support it; do not
  invent a bar and attribute it to arc42.
- **It does not arbitrate cost and schedule.** See "Where arc42 contradicts
  itself" below. Surface the conflict, take the user's answer.

## Interview rules

- Ask exactly **one question at a time**. Never batch multiple questions in one
  message.
- **Run the C-2-3 gate first, before any classification.** Two questions:
  _"Is this already written down somewhere — a company standard, a platform
  contract, a regulation?"_ and _"Which architectural decision did this shape, or
  what would a reader misunderstand without it?"_ If it's documented elsewhere,
  the correct outcome is a **link, not a restatement** — propose that and stop.
  If it shaped no decision and aids no understanding, it fails an **arc42** bar
  (C-2-3), not a taste test — say so and recommend dropping it. This gate is the
  single most valuable thing this skill does; do not skip it because the entry
  looks plausible.
- **Ask about provenance and scope before ruling.** _"Who decided this, and could
  your team overturn it on your own authority?"_ A team that can overturn it
  unilaterally is describing a decision (§9). A team that would have to go and
  negotiate with someone else is describing a constraint — and note that
  *negotiable* does not disqualify it; *unilaterally reversible* does.
- **Never rule it out because the team chose it.** If the user says "but we
  picked it ourselves, so it's a decision," check the scope: if adherence is now
  required of the architects this document covers, C-2-2 makes it a constraint.
  Cite C-2-2 rather than asserting.
- **Push back on measurable ends.** If it states a target the system must hit —
  throughput, latency, uptime, a percentage — it's a quality requirement, not a
  constraint. Test: _does it remove options, or does it name a finish line you
  could miss by degrees?_ A finish line goes to §1.2/§10 via `/quality-goal`.
  Constraints have no metric; they have a fence.
- **Push back on vagueness — with the right citation.** "Follow company
  standards," "use best practices," "be cloud-ready" constrain nothing: no reader
  can act differently because of them. The defensible move is **not** "too vague,
  delete" — it's C-2-3: link to the actual standard and name the specific rules
  that bite this system. Ask: _"Which rule in that standard removed an option
  from you?"_
- **Push for a motivation, not a justification.** Every good published example
  pairs the constraint with *why it exists* — DokChess uses
  `Constraint | Background and / or motivation`. A constraint with no background
  is unmaintainable: nobody later knows whether it still holds. But accept
  "nobody remembers, it predates the team" as an honest answer and record it as
  such — that answer is itself useful, and often the start of a renegotiation.
- **Don't let "non-negotiable" pass unchallenged.** If the user calls something
  non-negotiable, that's fine as a practical fact but must not be the *reason*
  it's classified as a constraint. If they justify the ruling that way, correct
  it with the template's Motivation line.
- **Surface consequences.** [Tip 2-2](https://docs.arc42.org/tips/2-2/): "You
  should clarify the consequences of constraints, e.g. resulting (additional)
  costs or effort. If constraints bring unreasonable consequences… you should
  negotiate about them with the relevant stakeholders." Ask what this costs the
  team. If the answer is ugly, tell them arc42 recommends negotiating — that is
  a real, citable recommendation, not your opinion.
- If the user contradicts an earlier answer (e.g. they call it immovable, then
  describe how the team changed it last year), surface the contradiction and ask
  which one holds.
- When you've covered enough ground, summarize the draft back in the format below
  and wait for confirmation before writing anything to disk.

## The four rulings

Every candidate resolves to exactly one:

| Ruling | When | What you do |
| --- | --- | --- |
| **Constraint (§2)** | Restricts the freedom of the architects this document covers; they cannot lift it unilaterally | Record it, per below |
| **Decision (§9)** | This team selected among alternatives and could revisit that choice on its own authority | Explain the ruling; point at §9; **do not** draft the ADR |
| **Quality requirement (§1.2/§10)** | Names a measurable end the system must reach, rather than removing options | Hand off to **`/quality-goal`** |
| **Drop or link** | Fails the C-2-3 gate — documented elsewhere, or shaped no decision and aids no understanding | Propose a link to the real source, or recommend dropping it |

State the ruling **and the test that produced it**, every time. The user should
be able to defend it to a sceptic without you in the room.

## What to probe for

Only once the C-2-3 gate is passed and the ruling is §2:

- **The constraint itself** — a short, concrete statement of what is fenced off.
  Prefer the published pattern: a noun phrase naming the given, not a sentence
  arguing for it. e.g. _"Implementation in Java"_, _"Hosting on-site (not SaaS
  only)"_, _"Moderate hardware equipment"_.
- **Background / motivation** — why this exists. The best real example is SIARD's:
  _"Swiss Federal Archives staff cannot execute binary files or scripts |
  Computers used by the SFA are managed by the BIT. Users are not allowed to
  install any software on these machines."_ The motivation is what makes it
  reviewable later.
- **Category** — arc42's optional taxonomy, exact names: **technical**,
  **organizational and political**, **conventions** (programming or versioning
  guidelines, documentation or naming conventions). Note the template says "if
  needed" — if the document has fewer than a handful of constraints, don't impose
  a three-heading structure on it. FAQ C-2-2 drops "political"; the template and
  Tip 2-5 keep it. Match whatever the document already does.
- **Scope** — whose freedom this binds. Record it in the motivation when the
  document spans multiple teams and the answer isn't obvious; "mandated by the
  central platform team" is doing real work for a future reader.
- **Consequences** — what it costs (Tip 2-2). arc42 prescribes **no column** for
  this, so fold it into the motivation unless the document already has a
  consequences column.
- **Negotiability** — is anyone trying to lift it? Not a recorded arc42 field, but
  ask: if the answer is "we've been fighting this for a year," that belongs in the
  motivation, and C-2-4 is the citation that legitimises the fight.

## Where arc42 contradicts itself

**Cost and schedule.** Do not fake a confident ruling here; the primary sources
disagree, and a user who teaches or defends this will get caught.

- For §2: [C-2-2](https://faq.arc42.org/questions/C-2-2/) lists "budget, time" as
  organizational constraints. [Tip 2-3](https://docs.arc42.org/tips/2-3/):
  "Organizational constraints like time and budget are for good reason unpopular
  with development teams, because they limit the freedom of design or
  implementation decisions very strongly. Therefore disclose these types of
  constraints." **DokChess files "Schedule" under 2.2 Organizational** — a worked
  precedent, which beats an FAQ line.
- Against: [C-1-2](https://faq.arc42.org/questions/C-1-2/) lists "cost, schedule,
  marketability" as *business quality attributes*, and arc42's Q42 model treats
  Budget Constraint as an alias of the quality *affordability*.

§2 has the better-supported citation and the worked example. Recommend it, state
that the sources conflict, and take the user's answer. Don't pretend it's settled.

## Proposing the constraint

Present the full draft back as a normal message (not yet written), showing the
ruling, the test that produced it, and exactly what will be inserted into §2. Ask
them to confirm or correct. Do not write to any file until they've confirmed.

If the ruling was **not** §2, there is nothing to propose — deliver the ruling and
the redirect, and stop.

## Recording the constraint

Once confirmed:

1. **Locate the arc42 constraints file.** Search the project, in this order:
   - `**/02_architecture_constraints.md` (the standard split-file layout —
     commonly under `docs/architecture/`, `docs/arc42/`, or `src/docs/arc42/`)
   - a single-file arc42 doc (e.g. `**/arc42*.md`, `**/architecture.md`)
     containing a matching "Architecture Constraints" heading
2. **If no arc42 document exists**, do not invent one. Tell the user what you
   looked for and ask where the architecture documentation lives, or whether they
   want the constraint written to a scratch file for pasting in later. Suggest
   `/setup-arc42` if they want the skeleton laid down first.
3. **Read the target file before editing it.** Match the surrounding heading
   depth, table style, and prose conventions already in that document.
4. **Match the existing form — do not convert it.** arc42's only official guidance
   is "Simple tables of constraints with explanations," but its *own* single
   example is a bullet list, and so is Gernot Starke's own project (HTML Sanity
   Checker). Both are canonical. Read the layouts from this skill's own
   `templates/` directory (relative to this skill, not the project):
   - [`templates/section-2-constraint.md`](./templates/section-2-constraint.md) —
     the table row, plus the category table header if the table doesn't exist yet.
   - [`templates/section-2-constraint-list.md`](./templates/section-2-constraint-list.md)
     — the bullet form, for documents that use enumeration. If the document is
     already a bullet list, **add a bullet**; don't promote it to a table.
5. **Categories are optional.** If the document already uses the
   technical/organizational/conventions split, add under the right heading. If it
   doesn't and this is the third or fourth constraint, you may *ask* whether to
   introduce the split. Never impose it on a document with two constraints.
6. **Insert, don't overwrite.** Existing constraints stay exactly as they are.

Never leave a template placeholder unfilled. If a field genuinely has no value
(the motivation is lost to history), write what's true — "predates the current
team; original rationale not recorded" — rather than "TBD".

After writing, report back the **file path touched and which section the edit
landed in**. If the constraint went in without a motivation, say so plainly —
that's the gap that makes it unreviewable in a year, and the user should know
they have an open loop.

## Reference

- [arc42 §2 Architecture Constraints](https://docs.arc42.org/section-2/) — Contents, Motivation, Form
- [Raw template source](https://raw.githubusercontent.com/arc42/arc42-template/master/EN/adoc/02_architecture_constraints.adoc)
  — quote from here, not the rendered page; the shipped template contains a
  "constraints/constrains" typo and the rendered page may differ
- [FAQ C-2-1](https://faq.arc42.org/questions/C-2-1/) — "Constraints restrict your freedom in decisions"; "**often** imposed by organizations"
- [FAQ C-2-2](https://faq.arc42.org/questions/C-2-2/) — the three categories; adherence to **decisions** is a technical constraint
- [FAQ C-2-3](https://faq.arc42.org/questions/C-2-3/) — the gate: avoid documenting; link instead; the impact bar
- [FAQ C-2-4](https://faq.arc42.org/questions/C-2-4/) — constraints are negotiable, with a worked example
- [Tips 2-1 … 2-5](https://docs.arc42.org/tips/2-1/) — look outward; clarify consequences; disclose organizational constraints; differentiate categories
- [FAQ B-4](https://faq.arc42.org/questions/B-4/) — the minimal arc42 set, which **omits §2 entirely**
- [DokChess §2](https://www.dokchess.de/en/02_constraints/) — the only worked example using the full taxonomy
- [HTML Sanity Checker §2](https://github.com/aim42/htmlSanityCheck/blob/develop/src/docs/arc42/chapters/chap-02-Constraints.adoc) — an arc42 author's own §2, as a bullet list
- [SIARD Suite §2](https://github.com/sfa-siard/siard-suite/blob/main/docs/sad/src/02_architecture_constraints.adoc) — an exemplary externally-imposed constraint with real motivation

Note: arc42 draws **no** constraint-vs-requirement and **no** §2-vs-§9 boundary
anywhere — the docs pages for §1, §9 and §10 contain the word "constraint" zero
times. The rulings in this skill for those boundaries are **synthesis**, hooked on
§4's "based upon problem statement, quality goals and key constraints" (constraints
are *inputs to* decisions). They are defensible, but they are not doctrine — and
when a user is going to be quoted back at, they deserve to know which is which.
Say so if asked.
