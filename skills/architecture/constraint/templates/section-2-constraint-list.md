<!--
  arc42 §2 Architecture Constraints — bullet-list fragment.

  Use this INSTEAD of section-2-constraint.md when the document already records
  its constraints as an enumeration rather than a table. Do not convert an
  existing bullet list into a table just because arc42's .Form sentence says
  "Simple tables of constraints with explanations."

  Why this form is legitimate — two reasons, both from arc42 itself:

  1. arc42's own official §2 example is a bullet list, not a table, and its
     preamble licenses this explicitly: "Key constraints can often be explained as
     simple enumeration in plain text."
     https://docs.arc42.org/examples/constraints-1/

  2. That example is HTML Sanity Checker — Gernot Starke's own project. An arc42
     author does not use a table for his own §2:

       HSC shall be:
       * Platform-independent and should run on the major operating systems
         (Windows(TM), Linux, and Mac-OS(TM))
       * Integrated with the Gradle build tool
       * Runnable from the command line
       * Developed under a liberal open-source license

     https://github.com/aim42/htmlSanityCheck/blob/develop/src/docs/arc42/chapters/chap-02-Constraints.adoc

  The tradeoff to be honest about: the bullet form makes the MOTIVATION easy to
  drop, and HSC's own example drops it. That is a real cost — a bare bullet tells
  a future reader nothing about who imposed the constraint or whether it still
  holds. Keep the motivation in the bullet (an em-dash clause does the job) unless
  the surrounding document has established the opposite convention.

  Append the bullet to the existing list. Do not restructure the list.
-->

- **{the given, as a noun phrase}** — {why it exists, who imposed it, and what it costs}

<!--
  Filled example, bare form (matching HSC's own convention — motivation omitted;
  acceptable only when the document already reads this way):

  - Runnable from the command line
  - Developed under a liberal open-source license

  Filled example, with motivation (preferred — same form, one clause more, and a
  future reader can actually act on it):

  - **Implementation in Java** — usage as an example in Java-centered trainings and Java conferences.
  - **Hosting on-site (not SaaS only)** — companies may not want to expose usage data to a SaaS provider.
  - **Authentication via the company-wide OAuth provider** — mandated by the central architecture team; this team cannot deviate unilaterally.

  If the list grows past a handful and the constraints clearly cluster, ASK the
  user whether to introduce arc42's optional category split (technical /
  organizational and political / conventions). The template says "if needed" —
  never impose three headings on a document with two constraints.
-->
