---
name: setup-arc42
description:
  Scaffold a fresh arc42 architecture documentation set under docs/architecture,
  one markdown file per top-level arc42 section, each with its canonical
  subheadings and a one-line introduction — structure only, no invented content.
argument-hint: "Optional: the system name to use in the headings"
---

The user wants an empty arc42 skeleton to start writing architecture
documentation into. Your job is to create the twelve top-level section files
under `docs/architecture/`, each carrying arc42's canonical subheadings and a
very short introduction to what that section is for — and **nothing else**.

This skill scaffolds; it does not interview and it does not author. Once the
skeleton exists, `/quality-goal` and the other architecture skills fill it in.

## The one rule

**Write structure, not content.** Every heading is a slot the user will fill.
Do not describe their system, do not guess at their constraints, do not add
"TODO", "TBD", placeholder tables, example diagrams, or lorem text under a
subheading. An empty subheading is the correct output — it is an honest signal
that nothing has been decided yet. A subheading with a plausible-sounding
invented sentence under it is the failure mode this skill exists to avoid,
because the next reader cannot tell your guess from the team's decision.

The only prose you write is the one- or two-sentence introduction directly under
each top-level heading, stating what belongs in that section. That text comes
from the templates — don't improvise it.

## Before writing

1. **Check whether `docs/architecture/` already holds an arc42 document.** Look
   for files matching `docs/architecture/*.md`, and for a single-file arc42 doc
   elsewhere (`**/arc42*.md`, `**/architecture.md`).
2. **If any arc42 section file already exists, stop and ask.** Do not overwrite.
   Report what you found and offer the choices: create only the **missing**
   section files and leave existing ones untouched (the safe default), pick a
   different directory, or cancel. Never silently replace a file that has
   content in it — that content is somebody's work.
3. **If `docs/architecture/` doesn't exist**, create it. No need to ask.
4. If the user gave a system name as an argument, use it in the `# ` title line
   of each file (e.g. `# 1. Introduction and Goals — Payment Gateway`). If they
   didn't, don't ask for one and don't invent one — just use the plain section
   titles.

## Writing the files

Read each layout from this skill's own `templates/` directory (relative to this
skill, not the project) and write it to `docs/architecture/` under the matching
filename below, structure unchanged:

| Template                                                                         | Writes to                                        |
| -------------------------------------------------------------------------------- | ------------------------------------------------ |
| [`templates/01_introduction_and_goals.md`](./templates/01_introduction_and_goals.md) | `docs/architecture/01_introduction_and_goals.md` |
| [`templates/02_architecture_constraints.md`](./templates/02_architecture_constraints.md) | `docs/architecture/02_architecture_constraints.md` |
| [`templates/03_context_and_scope.md`](./templates/03_context_and_scope.md)       | `docs/architecture/03_context_and_scope.md`      |
| [`templates/04_solution_strategy.md`](./templates/04_solution_strategy.md)       | `docs/architecture/04_solution_strategy.md`      |
| [`templates/05_building_block_view.md`](./templates/05_building_block_view.md)   | `docs/architecture/05_building_block_view.md`    |
| [`templates/06_runtime_view.md`](./templates/06_runtime_view.md)                 | `docs/architecture/06_runtime_view.md`           |
| [`templates/07_deployment_view.md`](./templates/07_deployment_view.md)           | `docs/architecture/07_deployment_view.md`        |
| [`templates/08_concepts.md`](./templates/08_concepts.md)                         | `docs/architecture/08_concepts.md`               |
| [`templates/09_architecture_decisions.md`](./templates/09_architecture_decisions.md) | `docs/architecture/09_architecture_decisions.md` |
| [`templates/10_quality_requirements.md`](./templates/10_quality_requirements.md) | `docs/architecture/10_quality_requirements.md`   |
| [`templates/11_technical_risks.md`](./templates/11_technical_risks.md)           | `docs/architecture/11_technical_risks.md`        |
| [`templates/12_glossary.md`](./templates/12_glossary.md)                         | `docs/architecture/12_glossary.md`               |

These filenames are arc42's own markdown distribution names, and `/quality-goal`
searches for exactly `01_introduction_and_goals.md`, `04_solution_strategy.md`
and `10_quality_requirements.md`. Don't rename them — the other architecture
skills won't find them.

Sections **2, 4, 9, 11 and 12 have no numbered subsections** in arc42. Their
files are a title and an introduction, and that's correct — don't invent
subheadings to make them look like the others.

Sections **6 and 8 have open-ended subsections** (one per runtime scenario, one
per crosscutting concept). Their templates carry a single illustrative
placeholder heading showing the numbering pattern. Leave it as the template has
it; the user renames and multiplies it as they write.

## After writing

Report the directory and the number of files created. Then point at the natural
next steps, briefly:

- `/quality-goal` records a falsifiable quality goal into §1.2, §4 and §10.
- `/constraint` rules on a candidate §2 constraint and records it — or redirects
  it to §9, to `/quality-goal`, or to a link, which is the outcome arc42 actually
  prefers ("try to avoid documentation of constraints").
- §3 (context) and §5 (building blocks) are usually the first sections worth
  filling by hand — they're what every other section refers back to.

§2 is worth a word of warning when you point at it: it is **not** in arc42's
minimal documentation set ([FAQ B-4](https://faq.arc42.org/questions/B-4/)), and
arc42 advises linking to constraints documented elsewhere rather than restating
them. An empty §2 is a legitimate resting state, not a gap to be filled.

Don't offer to fill the sections in yourself unless the user asks.

## Reference

- [arc42 documentation](https://docs.arc42.org/home/) — the twelve sections
- [arc42 downloads](https://arc42.org/download) — the official markdown templates
