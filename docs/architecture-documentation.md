# Architecture Documentation Philosophy

This document explains the reasoning behind the skills in `skills/architecture/`
— what they assume about your documentation, why there's no fixed order to run
them in, and the one convention you should set up in your agent instructions
before you start.

## The assumption: arc42

All of these skills assume you document architecture with
[arc42](https://arc42.org/). That's the template I use, and it's baked in — the
skills write to numbered arc42 sections (§1.2, §2, §4, §10) and apply arc42's
own tests, quoting its text and FAQ rather than a generic notion of what a
"constraint" or a "quality goal" is. If you document architecture some other way,
these skills won't fit without rewriting them.

arc42 is a template, not a process. It tells you what belongs in each of twelve
sections; it doesn't tell you what order to fill them in, and neither do these
skills.

## Not a ladder

The backlog skills form a ladder — PRD down through initiative, epic, feature,
story — where each level assumes the one above it exists. The architecture skills
don't work that way. There is **no fixed order**. Architecture knowledge doesn't
arrive in a tidy sequence: a constraint surfaces in a procurement conversation, a
quality goal surfaces when someone complains about latency, and neither waits for
the other. Run whichever skill matches whatever you just learned.

The one recommendation: **run `/setup-arc42` first**. It scaffolds the twelve
section files under `docs/architecture/` with arc42's canonical headings and
nothing else — no invented content, no TODOs. The other skills don't create
structure; they insert into it. Having the correct layout on disk first means
`/quality-goal` and `/constraint` know exactly where their output lands, instead
of guessing at your file naming.

After that, reach for whichever fits:

- **`/quality-goal`** when you have a rough quality goal ("it must be fast") that
  needs to become falsifiable. It lands in up to three sections at once — the
  goal in §1.2 or §10, the scenario that makes it measurable, and the decision it
  drove in §4. Recording it in one and not the others is the usual way these go
  wrong, which is why the skill handles all three.
- **`/constraint`** when something looks like it belongs in §2. Mostly a triage
  skill: three of its four rulings send you elsewhere — link to existing
  documentation, hand it to `/quality-goal`, or record it as a decision in §9.

Neither depends on the other having run.

## Diagrams: mermaid + C4

The skills don't write diagrams, and arc42 doesn't mandate a notation. What you
draw in §3 (context and scope), §5 (building block view), §6 (runtime view) and
§7 (deployment view) is up to you and your agent — so tell your agent what you
want, or you'll get a different style in every section.

My recommendation is **[mermaid](https://mermaid.js.org/) diagrams using the
[C4 model](https://c4model.com/)'s levels** — system context, container,
component. Mermaid keeps diagrams as text in the repo, so they diff and review
like code instead of rotting as exported PNGs nobody can edit. C4 gives you a
consistent altitude per diagram, which maps onto arc42 cleanly: C4's system
context belongs in §3, containers and components in §5.

This belongs in your **agent instructions** — `AGENTS.md` or `CLAUDE.md` — not in
each prompt. It's a project-wide convention, and repeating it per conversation is
how it drifts. Something like:

```markdown
## Architecture documentation

Architecture docs follow arc42 and live in `docs/architecture/`. Draw all
diagrams as mermaid, using the C4 model's levels: system context in §3,
containers and components in §5. Never export diagrams as images — they stay
as mermaid source in the markdown.
```

I'm calling it out here because it's easy to miss: the skills work fine without
it, and you only notice the inconsistency once four sections are written in three
different notations.

## Anti-patterns worth naming

- **Filling the skeleton with guesses** — a subheading with a plausible invented
  sentence under it is worse than an empty one, because the next reader can't
  tell your guess from the team's decision. `/setup-arc42` refuses to do this;
  don't undo it by hand. I recommend deleting the subheading entirely if there's
  no reason to keep it.
- **The wish disguised as a quality goal** — "the system must be scalable," with
  no scenario. If no possible observation could show you missed it, it isn't a
  goal. It's okay to not have all possible quality goals documented. I recommend
  adding goals as they come up.
- **Restating what's already documented elsewhere** — arc42 asks you to link to
  existing documentation rather than copy it into §2. Copies go stale.
- **The origin test for constraints** — "we chose it, so it's a decision, not a
  constraint." arc42's own text contradicts this: adherence to someone else's
  decision counts, and constraints "may be negotiable." The real test is whether
  it restricts your freedom of design.
- **Diagram drift** — every section drawn in a different tool, half of them
  exported as images nobody can regenerate.
