<!--
  arc42 §2 Architecture Constraints — table row fragment.

  Goes in 02_architecture_constraints.md, under the relevant category heading
  (§2.1 Technical / §2.2 Organizational and political / §2.3 Conventions) if the
  document uses them, or directly under the §2 heading if it doesn't.

  arc42's only guidance on form is: "Simple tables of constraints with
  explanations."  https://docs.arc42.org/section-2/

  That is the WHOLE official specification. arc42 prescribes NO columns — there is
  no official justification column and no consequences column. The two-column
  "constraint + why" shape below is the de-facto standard across every published
  example, not a rule:

    DokChess  | Constraint | Background and / or motivation |
    SPOUD     | Constraint | Explanation                    |
    SIARD     | Constraint | Explanation, Background        |

  A four-column form with Type/Rationale/Impact circulates on practitioner blogs.
  It is somebody's house extension, NOT arc42. Don't reach for it by default.

  IMPORTANT — if the document is already a BULLET LIST, do not promote it to a
  table. Use section-2-constraint-list.md instead. arc42's own single official
  example is a bullet list, and so is Gernot Starke's own project. Both forms are
  canonical; consistency within the document beats matching the .Form sentence.

  The MOTIVATION cell is the one that matters. A constraint without background is
  unmaintainable: in a year nobody can tell whether it still holds, who to ask, or
  whether it's worth renegotiating. arc42 explicitly permits renegotiation —
  "Constraints must always be dealt with; they may be negotiable, though" — and
  the motivation is what makes that conversation possible.

  Fold CONSEQUENCES into the motivation unless the document already has a column
  for them. Tip 2-2 asks you to clarify consequences ("e.g. resulting (additional)
  costs or effort") but does NOT ask for a column.
  https://docs.arc42.org/tips/2-2/

  If the table already exists, append the row. If it doesn't, create it with the
  header below.
-->

| Constraint | Background and / or motivation |
| ---------- | ------------------------------ |
| **{the given, as a noun phrase}** | {why it exists, who imposed it, and what it costs} |

<!--
  Filled examples — all real, from published arc42 documents.

  Technical (DokChess):
  https://www.dokchess.de/en/02_constraints/01_technical/

  | Constraint | Background and / or motivation |
  | ---------- | ------------------------------ |
  | **Implementation in Java** | Usage as an example in Java-centered trainings and Java conferences. |
  | **Moderate hardware equipment** | Operating DokChess on a standard notebook in order to show the software in the context of workshops and conferences on such a device. |

  Organizational (SIARD Suite, Swiss Federal Archives) — the best published
  example of a genuinely external constraint carrying its full motivation:

  | Constraint | Explanation, Background |
  | ---------- | ----------------------- |
  | **Swiss Federal Archives (SFA) staff cannot execute binary files or scripts** | Computers (aka Bundeslaptops) used by the SFA are managed by the Bundesamt für Informatik und Telekommunikation (BIT). Users are not allowed to install any software on these machines. |

  Note what the SIARD motivation does: it names the imposing party (BIT), so a
  future architect knows exactly who to negotiate with. That is the difference
  between a constraint and a shrug.

  Conventions (DokChess §2.3):

  | Constraint | Background and / or motivation |
  | ---------- | ------------------------------ |
  | **Coding guidelines for Java** | Java coding conventions of Sun / Oracle, checked using CheckStyle. |

  A constraint the team chose itself is still a constraint if adherence is now
  required of the architects this document covers — FAQ C-2-2 counts "adherence to
  specific technical or architectural decisions" as a technical constraint. When
  provenance isn't obvious, put it in the motivation:

  | Constraint | Background and / or motivation |
  | ---------- | ------------------------------ |
  | **Authentication via the company-wide OAuth provider** | Mandated by the central architecture team in 2024 after evaluating three options; this team cannot deviate unilaterally. Costs us ~2 weeks of integration work per new service. |
-->
