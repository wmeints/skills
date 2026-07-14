# Backlog Management Philosophy

This document explains the reasoning behind the four skills in `skills/backlog/`
— why each backlog level looks the way it does, and how to use them together.
It's the write-up behind a small self-taught course on agile backlog management;
sources are linked throughout rather than asserted.

## The core idea: altitude changes the quality bar

A common mistake is judging every backlog item by the same checklist — usually
"is it small." That works for stories, and actively hurts everything above them.

Each skill has a dedicated set of checks to make sure the item is of adequate
quality.

## The ladder

### PRD

A PRD sits above the ladder entirely: it's the one document that states **what**
the system must do — problem, users, goals, functional and non-functional
requirements, constraints — with zero solution talk. No hypothesis, no
initiative sizing, no epics; those all live downstream and answer **how**.

Every initiative's "why now," every epic's problem statement, and every
feature's benefit hypothesis should trace back to a requirement recorded here.
Without that traceability, initiatives drift into solving problems the PRD never
named.

Use `/prd` to write or update it, before activating initiatives.

### Initiative

An initiative is one notch above an epic: a named direction ("cross-team skill
sharing," "faster onboarding") with a rough why-now and success measure, sized
only as a gut-feel S/M/L/XL. No hypothesis, no MVP boundary yet — that detail is
premature at this altitude and gets thrown away when the plan shifts.

This is distinct from Scrum's **Product Goal**, which is singular — the one
long-term objective the whole backlog serves right now
(Scrum.org)[^1]. Initiatives
are the plural list of goal-areas underneath it; not every one gets activated at
once.

Use `/initiative` to write one.

### Epic

A requirement invites compliance ("build exactly this"). At epic altitude you
don't yet know enough to say that honestly — you're betting on a large,
mostly-unvalidated idea. A **hypothesis** invites validation instead: "if we do
X, then we expect Y for group Z, measured by W."

This framing, including the _problem statement → hypothesis → leading indicators
→ MVP boundary_ structure, is adapted from SAFe's Lean Business Case / Epic
Hypothesis Statement
(agility-at-scale.com)[^2].
It's a synthesis, not a Scrum Guide term — there's no single widely-cited "good
epic checklist" outside scaled frameworks, and this is the most rigorous one
available.

The **MVP boundary** and **leading indicators** are what stop the classic "epic
that never shrinks" anti-pattern: without them, an epic has no way to be
declared done or wrong, so it just absorbs work forever.

Use `/epic` to write one, once an initiative is activated.

### Feature

A feature is the user-facing capability inside an epic — narrower than the
epic's bet, broader than one sprint's work. It needs two things: a **benefit
hypothesis** (the quantifiable value a stakeholder gets) and **acceptance
criteria** (the minimum conditions for that benefit to count as delivered). Both
terms come from SAFe's feature definition
(airfocus glossary)[^3].

Acceptance criteria describe the outside (what's done), never the inside (how
it's built) — dictating exact UI details in acceptance criteria is a common
Product Owner failure mode
(Roman Pichler[^4]; Age of Product[^5]).
Three to five criteria is typical; a much longer list usually means the feature
needs splitting.

Use `/feature` to write one, under an existing epic.

### Story

**INVEST** — Independent, Negotiable, Valuable, Estimable, Small, Testable — was
coined by Bill Wake and popularized by Mike Cohn
(Agile Alliance glossary[^6]; Cohn's "User Stories Applied"[^7]).
It's the only level where chasing "small" is correct — and even here, chasing
Small _first_, ahead of Valuable and Independent, is the trap: it produces tiny
pieces that hide risk (nothing ships until they're reassembled) instead of
reducing it.

When a story fails Small, the fix is to **split it properly**, not force it into
one oversized item. Richard Lawrence's story-splitting patterns
(Humanizing Work guide[^8])
reduce every good split to: find the core complexity, list its variations, slice
through it once completely. Splitting by architecture layer ("backend story" +
"frontend story") is the anti-pattern to avoid — it breaks Independent and
usually Valuable, since nothing ships until both land.

Use `/story` to write one, under an existing feature. The skill will push back
and point you at splitting patterns if what you describe is really an epic or
feature wearing a story's clothes.

## The shape of a healthy backlog

Put together, a healthy backlog is a **cone**, not a flat pile:

```
Top    (next 1-2 sprints)  Stories     — fully INVEST
Middle (next quarter)      Features    — benefit hypothesis + acceptance criteria
Bottom (this year+)        Epics       — problem statement + hypothesis only
(above the epics)          Initiatives — name + why-now + rough success measure
(above it all)             PRD         — solution-agnostic requirements
```

Detail should track how soon you'll act on an item, not how important it feels.
This is Mike Cohn and Roman Pichler's **DEEP** — Detailed appropriately,
Estimated, Emergent, Prioritized
(Mountain Goat Software[^9])
— the backlog-level counterpart to INVEST at the story level.

## Anti-patterns worth naming

- **Feature soup** — a flat wish list with no epics or initiatives grouping it;
  nobody can see the strategy.
- **Too detailed too early** — writing full stories (or full epic hypotheses)
  for work a year out. Wasted the moment the plan changes.
- **Wrong-level clothing** — an item that needs five other items done first
  before it delivers any value is an epic wearing a story's clothes; an "epic"
  that's really one sprint of work is a story wearing an epic's clothes.
- **The epic that never shrinks** — no MVP boundary or leading indicators, so it
  absorbs work forever instead of closing.
- **Refining alone** — the Product Owner writes detail in isolation instead of
  with the delivery team, so shared understanding never actually forms.

Sources: Roman Pichler, "Seven Product Backlog Mistakes to Avoid"[^4]; Stefan
Wolpers, "27 Product Backlog and Refinement Anti-Patterns"[^5].

## Using the skills together

1. Start with `/prd` to capture what the system must do — problem, users,
   goals, requirements — with no solution talk.
2. Run `/initiative` for each rough goal area the PRD implies. Keep it coarse —
   no hypothesis yet.
3. Once an initiative is `Active`, run `/epic` to give it a falsifiable
   hypothesis and an MVP boundary.
4. Under that epic, run `/feature` for each user-facing capability it needs,
   with its own benefit hypothesis and acceptance criteria.
5. Under each feature, run `/story` for each sprint-sized slice. If a story
   fails Small, split first (Lesson 3's patterns) and run `/story` again per
   slice.

Every skill follows the same shape: interview one question at a time → propose
the full draft → wait for confirmation → write an auto-numbered file. Nothing is
written to disk until you've confirmed it.

[^1]: https://www.scrum.org/resources/what-product-goal
[^2]: https://agility-at-scale.com/safe/lpm/lean-business-case/
[^3]: https://airfocus.com/glossary/minimum-requirements-for-feature/
[^4]: https://www.romanpichler.com/blog/product-backlog-mistakes/
[^5]: https://age-of-product.com/28-product-backlog-anti-patterns/
[^6]: https://agilealliance.org/glossary/invest/
[^7]: https://www.mountaingoatsoftware.com/uploads/articles/User-Stories-Applied-Mike-Cohn.pdf
[^8]: https://www.humanizingwork.com/the-humanizing-work-guide-to-splitting-user-stories/
[^9]: https://www.mountaingoatsoftware.com/blog/make-the-product-backlog-deep
