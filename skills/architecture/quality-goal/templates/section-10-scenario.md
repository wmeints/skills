<!--
  arc42 §10 Quality Requirements — scenario block fragment.

  Goes in 10_quality_requirements.md, under the quality-scenarios heading
  (§10.2 in the canonical numbering).

  This is arc42's SHORT FORM — Context/Background, Source/Stimulus,
  Metric/Acceptance criteria — which is what arc42 actually favours and what the
  Q42 model uses. The six-part SEI structure (source, stimulus, artifact,
  environment, response, response measure) is arc42's "long form"; use it to
  ELICIT the scenario, then record the short form here.
  https://docs.arc42.org/section-10/

  The six parts compress cleanly and nothing is lost:
    Environment + Artifact      -> Context/Background
    Source + Stimulus           -> Source/Stimulus
    Response + Response measure -> Metric/Acceptance criteria

  Number QS-NN against the scenarios already in the file. Do NOT build a quality
  tree: current §10.1 recommends tables or mindmaps and credits the "Quality
  Attribute Utility Tree" to Bass et al. rather than to arc42.
-->

#### QS-{NN} — {short scenario title}

| | |
| --- | --- |
| **Quality goal** | {name of the §1.2 goal this refines, or "—" if this requirement lives only in §10} |
| **Characteristic** | {ISO/IEC 25010:2023 characteristic} · {Q42 label, e.g. `#efficient`} |
| **Kind** | {Usage scenario \| Change scenario} |
| **Context / background** | {the situation and the part of the system involved — environment + artifact} |
| **Source / stimulus** | {who or what acts, and what they do} |
| **Metric / acceptance criteria** | {the response, and the measure by which it is evaluated} |

<!--
  When this scenario refines a goal that is already in §1.2, the "Quality goal"
  cell REFERENCES it by name rather than restating it. arc42: "The most important
  of these requirements have already been described in section 1.2 (quality
  goals), therefore they should only be referenced here."

  Filled example (usage scenario):

  #### QS-03 — Checkout latency during on-sale

  | | |
  | --- | --- |
  | **Quality goal** | Survive the on-sale spike |
  | **Characteristic** | Performance efficiency / Time behaviour · `#efficient` |
  | **Kind** | Usage scenario |
  | **Context / background** | Peak on-sale: the first 60 seconds after tickets drop, 50 000 concurrent fans, exercising the checkout and seat-reservation path. |
  | **Source / stimulus** | A fan taps *Buy* on a chosen seat. |
  | **Metric / acceptance criteria** | The seat is held for that fan and a confirmation is shown: p95 under 2 seconds, p99 under 5 seconds. |

  Filled example (change scenario — note the measure is EFFORT, not latency;
  this is how "maintainable" becomes falsifiable):

  #### QS-07 — Adding a new ticket type

  | | |
  | --- | --- |
  | **Quality goal** | Add a new ticket type quickly |
  | **Characteristic** | Maintainability / Modifiability · `#flexible` |
  | **Kind** | Change scenario |
  | **Context / background** | Normal development, no on-sale running. Affects pricing and checkout. |
  | **Source / stimulus** | The promoter's ops team requests a new ticket type (e.g. a payment-plan instalment ticket). |
  | **Metric / acceptance criteria** | The type is added, tested and released in under 3 developer-days, with no change to the reservation engine. |
-->
