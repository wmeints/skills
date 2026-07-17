<!--
  arc42 §1.2 Quality Goals — table row fragment.

  Goes in 01_introduction_and_goals.md, under the "Quality Goals" heading.

  arc42 prescribes the form: "A table with the most important quality goals and
  concrete scenarios, ordered by priorities."  https://docs.arc42.org/section-1/

  The goal cell follows the DokChess pattern — plain-language goal with the
  quality characteristic in parentheses. It keeps the goal readable while
  anchoring it to a standard vocabulary, which is what "avoid buzzwords" means
  in practice.  https://www.dokchess.de/en/01_introduction/02_qualitygoals/

  The scenario cell here is DELIBERATELY BRIEF — one sentence. The detailed
  scenario belongs in §10. Do not paste the full six-part scenario into this
  table; §1.2 is a summary that a stakeholder reads in ninety seconds.

  If the table already exists, insert the row in PRIORITY ORDER. If it doesn't,
  create it with the header below.
-->

| Priority | Quality goal | Scenario |
| -------- | ------------ | -------- |
| {priority} | **{goal in plain language}** ({quality characteristic}) | {one-sentence scenario, including the response measure} |

<!--
  Filled example:

  | Priority | Quality goal | Scenario |
  | -------- | ------------ | -------- |
  | High | **Never sell the same seat twice** (Functional correctness) | Under 50 000 concurrent buyers in the first 60 seconds of an on-sale, no seat is ever confirmed to two fans — zero double-sales, verified against the gate scan log. |
  | High | **Survive the on-sale spike** (Time behaviour) | A fan tapping *Buy* during the first 60 seconds of an on-sale with 50 000 concurrent fans sees a confirmed seat in under 2 seconds at p95. |

  Note both scenarios name the same environment. That is not duplication — it is
  the conflict, made visible. Two goals that bite in the same situation are the
  ones the architecture has to reconcile.
-->
