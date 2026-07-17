<!--
  arc42 §4 Solution Strategy — table row fragment.

  Goes in 04_solution_strategy.md.

  This table is arc42's own suggestion for §4, and it is the JOINT between §1.2
  and the rest of the document — literally a goal→decision trace. If §1.2 has
  goals and this table has no matching rows, the goals are decorative: they were
  written down and then changed nothing.  https://docs.arc42.org/section-4/

  arc42 on §4: "Motivate what you have decided and why you decided that way,
  based upon your problem statement, the quality goals and key constraints. Refer
  to details in the following sections (section 5 for structural details,
  section 8 for crosscutting concepts)."

  IMPORTANT: §4 is sometimes written as prose rather than a table — a variant
  arc42 tolerates and its own HTML Sanity Checker example uses. If the target
  file is already prose, DO NOT convert it to a table. Add a sentence in the same
  voice, tracing goal to decision.
  https://docs.arc42.org/examples/solution-strategy-htmlsc-1/
-->

| Quality goal | Scenario | Solution approach | Link to details |
| ------------ | -------- | ----------------- | --------------- |
| {goal, matching the §1.2 wording exactly} | {QS-NN} | {the architectural decision, and why it follows from the goal} | {§5 / §8 / ADR link, or omit} |

<!--
  The "Quality goal" cell must match the §1.2 wording EXACTLY. This table is only
  useful as a trace if the names line up — a reviewer should be able to read §1.2,
  read §4, and see every top goal accounted for.

  Filled example:

  | Quality goal | Scenario | Solution approach | Link to details |
  | ------------ | -------- | ----------------- | --------------- |
  | Never sell the same seat twice | QS-01 | Single-writer seat allocation per event, with reservations held in an in-memory log and confirmed asynchronously. Chosen over optimistic concurrency because a double-sale is unrecoverable at the gate, whereas a slow confirmation is merely annoying. | [§5.2 Reservation engine](05_building_block_view.md#reservation-engine) |
  | Survive the on-sale spike | QS-03 | Static queue-room fronted by a CDN, admitting fans to the checkout at a rate the allocator can absorb. Accepts a wait to protect the invariant above. | [§8.3 Load shedding](08_concepts.md#load-shedding) |
  | Add a new ticket type quickly | QS-07 | Pricing rules held as data, not code, and read by checkout at request time — deliberately keeping ticket types out of the reservation engine. | [§8.1 Pricing model](08_concepts.md#pricing-model) |

  Note what the "Solution approach" cells do: each one states a decision AND the
  trade-off it accepted. "Accepts a wait to protect the invariant above" is the
  sentence a reviewer needs — it shows the conflict between two §1.2 goals being
  resolved, on purpose, in a recorded direction. A solution approach that reads
  like an untroubled feature description is usually hiding the fact that no
  trade-off was made.
-->
