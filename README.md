# Skills

Claude Code skills that interview you, propose a well-formed artifact, and record
it to disk. Each one enforces the quality bar that actually applies to the thing
you're writing, instead of one generic "write a document" template — and none of
them writes anything until you've confirmed the draft.

## Categories

### Backlog

From the product requirements down through the four altitudes of an agile
backlog: **PRD → initiative → epic → feature → story**.

| Skill      | Command       | Quality bar                                                                 | Writes to                              |
| ---------- | ------------- | --------------------------------------------------------------------------- | -------------------------------------- |
| PRD        | `/prd`        | Solution-agnostic requirements — the "what," not the "how"                  | `docs/product/requirements.md`         |
| Initiative | `/initiative` | Outcome-flavored, coarse, DEEP "detailed appropriately"                     | `docs/initiatives/NNNN-<slug>.md`      |
| Epic       | `/epic`       | Falsifiable hypothesis (problem, If/Then, leading indicators, MVP boundary) | `docs/product/epics/NNNN-<slug>.md`    |
| Feature    | `/feature`    | Benefit hypothesis + outcome-focused acceptance criteria                    | `docs/product/features/NNNN-<slug>.md` |
| Story      | `/story`      | Full INVEST — Independent, Negotiable, Valuable, Estimable, Small, Testable | `docs/product/stories/NNNN-<slug>.md`  |

The philosophy behind why each level looks the way it does — and how to use the
skills together — is written up in
[`docs/backlog-management.md`](docs/backlog-management.md).

### Architecture

Skills for [arc42](https://arc42.org/) architecture documentation. Unlike a
backlog item, these artifacts aren't standalone files — they land inside an
existing arc42 document, often in several sections at once.

| Skill        | Command         | Quality bar                                                                       | Writes to                        |
| ------------ | --------------- | --------------------------------------------------------------------------------- | -------------------------------- |
| Quality goal | `/quality-goal` | Falsifiable scenario — if no observation could show you missed it, it's a wish    | arc42 §1.2, §4 and §10 |

## Install

```sh
# All skills
npx skills add wmeints/skills --all

# Just one, e.g. epic
npx skills add wmeints/skills --skill epic
```

Uses the [`skills` CLI](https://www.npmjs.com/package/skills) — add `-g` to
install globally (`~/.claude/skills/`) instead of project-scoped.

### Manual install

Copy the skill directory you want into your Claude Code skills folder:

```sh
# Personal (all projects)
cp -r skills/backlog/epic ~/.claude/skills/epic

# Or project-scoped
cp -r skills/architecture/quality-goal .claude/skills/quality-goal
```

Each skill is self-contained — `SKILL.md` plus a `templates/` folder — so copying
the directory is all that's needed.

## Usage

Run the matching slash command, e.g. `/epic` or `/quality-goal`. Every skill
follows the same shape:

1. Interviews you one question at a time, pushing back on vagueness and
   solution-first thinking — and, depending on the skill, on missing hypotheses,
   oversized scope, failed INVEST checks, or unfalsifiable quality goals.
2. Proposes the full draft back to you and waits for confirmation.
3. Writes the file — auto-numbered against whatever's already in the target
   folder for backlog items, or inserted into the right sections of the existing
   document for architecture skills.

## License

[MIT](LICENSE)
