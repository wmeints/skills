# Backlog Skills

Claude Code skills that interview you, propose a well-formed backlog item, and record it to disk — for the four altitudes of an agile backlog: **initiative → epic → feature → story**.

Each skill enforces the quality bar that actually applies at its level, instead of one generic "write a ticket" template:

| Skill | Command | Quality bar | Writes to |
|---|---|---|---|
| Initiative | `/initiative` | Outcome-flavored, coarse, DEEP "detailed appropriately" | `docs/initiatives/NNNN-<slug>.md` |
| Epic | `/epic` | Falsifiable hypothesis (problem, If/Then, leading indicators, MVP boundary) | `docs/product/epics/NNNN-<slug>.md` |
| Feature | `/feature` | Benefit hypothesis + outcome-focused acceptance criteria | `docs/product/features/NNNN-<slug>.md` |
| Story | `/story` | Full INVEST — Independent, Negotiable, Valuable, Estimable, Small, Testable | `docs/product/stories/NNNN-<slug>.md` |

The philosophy behind why each level looks the way it does — and how to use the skills together — is written up in [`docs/backlog-management.md`](docs/backlog-management.md).

## Install

Copy the skill directory you want into your Claude Code skills folder:

```sh
# Personal (all projects)
cp -r skills/backlog/epic ~/.claude/skills/epic

# Or project-scoped
cp -r skills/backlog/epic .claude/skills/epic
```

Repeat for `initiative`, `feature`, and `story`. Each skill is self-contained — `SKILL.md` plus a `templates/` folder — so copying the directory is all that's needed.

## Usage

Run the matching slash command for the altitude you're working at, e.g. `/epic`. Each skill:

1. Interviews you one question at a time, pushing back on vagueness, solution-first thinking, and — depending on the level — missing hypotheses, oversized scope, or failed INVEST checks.
2. Proposes the full draft back to you and waits for confirmation.
3. Writes the file, auto-numbered against whatever's already in the target folder.

See [`docs/backlog-management.md`](docs/backlog-management.md) for the reasoning behind each level and worked examples.

## License

[MIT](LICENSE)
