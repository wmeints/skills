---
name: prd
description:
  Interview the user to build a solution-agnostic PRD (problem/context, users,
  goals, functional and non-functional requirements, constraints, out of scope),
  propose it back for confirmation, then record it in
  docs/product/requirements.md as the input for initiatives and epics.
argument-hint: "Product or system name, and the rough problem it addresses"
---

The user wants to turn a rough product idea into a well-formed PRD (Product
Requirements Document). Your job is to interview them until the document states
**what** the system must do — not how it will be built — then propose it back
for confirmation, then record it.

This sits one level above the backlog ladder (`/initiative` → `/epic` →
`/feature` → `/story`): the PRD is the input those skills draw from. An
initiative's "why now," an epic's problem statement, and a feature's benefit
hypothesis should all be traceable back to a requirement in this document. The
PRD itself never says how — that's exactly what initiatives, epics, and
features exist to work out.

## Interview rules

- Ask exactly **one question at a time**. Never batch multiple questions in one
  message.
- Push back hard on solution language. If the user names a technology,
  architecture, UI pattern, vendor, or specific mechanism ("use OAuth2", "add a
  dashboard", "build a microservice"), ask what capability or outcome that
  serves and record *that* instead. Note that the how belongs to a later
  initiative, epic, or feature, not the PRD.
- Push back on unverifiable requirements. "The system should be fast" or "should
  be user-friendly" isn't a requirement — ask for the concrete, testable
  statement it stands in for (e.g. "returns search results within 2 seconds for
  95% of queries").
- Push back on requirements with no named actor. Every functional requirement
  needs a "who needs this, and why" — a requirement nobody asked for is usually
  a solution in disguise.
- Distinguish functional from non-functional requirements explicitly. Probe
  separately for performance, security, compliance, availability, scalability,
  and data/privacy — these are easy to skip if you only ask "what should it do."
- Push back on scope creep. If something raised is clearly a nice-to-have or
  edge case unrelated to the core problem, ask whether it belongs in "Out of
  Scope" instead of the requirements list.
- If `docs/product/requirements.md` already exists, read it before asking
  anything else, and ask the user whether this session **adds** new
  requirements, **revises** existing ones, or is a fresh rewrite. Don't
  silently overwrite prior work.
- If the user contradicts an earlier answer (e.g. a later goal conflicts with an
  earlier "out of scope" call), surface the contradiction and ask which one
  holds.
- When you think you've covered enough ground, summarize the draft PRD back to
  the user in the format below and ask them to confirm or correct it before
  writing anything to disk.

## What to probe for

- **Product/system name** — short, concrete.
- **Problem & context** — what's broken or missing today, for whom, and why
  solve it now. No solution talk yet.
- **Target users** — the distinct actors/roles who interact with the system,
  and what each needs from it.
- **Goals** — the business objectives this system serves. Higher altitude than
  any single requirement; these are the "why" the requirements answer to.
- **Functional requirements** — capabilities the system must provide, each
  phrased as "the system must/should be able to {capability}," for a named
  actor, solution-agnostic. Numbered `FR-NNN`.
- **Non-functional requirements** — quality attributes: performance, security,
  compliance, availability, scalability, data/privacy. Numbered `NFR-NNN`,
  measurable where possible.
- **Constraints** — business, regulatory, or technical facts already fixed
  (existing systems to integrate with, deadlines, budget, legal requirements).
  These are givens, not solution choices.
- **Out of scope** — explicitly excluded, so it's clear it was considered and
  cut, not forgotten.
- **Assumptions** — things taken as given that, if false, would change the
  requirements.
- **Success metrics** — product-level measures of success. Coarser than an
  epic's leading indicators; these describe whether the whole system mattered.
- **Open questions** — unresolved items that need follow-up before work starts.

Don't force a rigid question order — follow the conversation where it naturally
leads, but make sure every section above is covered before closing the
interview.

## Proposing the PRD

Once you have enough to fill every section, present the full draft back to the
user in the exact document layout from "Recording the PRD" below, rendered as a
normal message (not yet written to a file). Ask them to confirm or request
changes. Do not write the file until they've confirmed.

## Recording the PRD

Once confirmed:

1. Check whether `docs/product/` exists in the current project; create it if
   not.
2. If `docs/product/requirements.md` already exists and the user is adding to or
   revising it, merge the confirmed changes into the existing document in place:
   append new `FR-NNN`/`NFR-NNN` entries continuing the existing numbering,
   update revised entries where they stand, and merge other sections rather
   than duplicating them. If the file doesn't exist, or the user asked for a
   fresh rewrite, write it from scratch.
3. Read the layout from [`templates/requirements.md`](./templates/requirements.md)
   (relative to this skill's own directory, not the project) and write
   `docs/product/requirements.md` with every `{placeholder}` filled in from the
   interview, structure otherwise unchanged.

Never leave a section out. If the interview genuinely surfaced only one
requirement in a section, that's fine — list just the one, don't pad it.

After writing the file, report back the file path to the user. Mention that the
natural next step is running `/initiative` for each distinct outcome-flavored
direction the goals imply — each initiative's "why now" should trace back to one
or more requirements in this document.
