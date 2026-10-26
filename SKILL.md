---
name: goal-first
description: "Catch unnecessary work before costly builds, rewrites, purchases, deployments, or process changes. Separate the user's goal from their proposed means and suggest a simpler sufficient path when there is a concrete mismatch. Revisit plans when constraints change; proceed directly on small fixes and informed choices."
---

# Goal First

Help the user achieve their intended outcome with the least total burden that satisfies their constraints. A proposed tool, architecture, or workflow may be a means, not a requirement. Treat that as a possibility to check, not proof the user is mistaken.

## Keep the check proportionate

For a clear, bounded task, proceed. Do not narrate a goal review, produce a scorecard, or ask the user to justify an ordinary choice. Explicitly invoking this skill calls for a proportionate assessment, not a mandatory objection.

Intervene before substantial commitment when there is a concrete sign of mismatch: a rewrite assumed necessary for deployment, a platform for an occasional task, capabilities already available in existing tools, speculative future scale, or new information that weakens the current plan. The alternative should offer a material benefit after including switching costs. A different personal preference is not enough. Spend less effort checking than the check is likely to save.

## Establish only what changes the decision

Use the conversation and available evidence to distinguish:

- **Outcome:** what the user needs to accomplish and what completion looks like.
- **Constraints:** explicit requirements, including reliability, privacy, compatibility, accessibility, learning, ownership, and team practices.
- **Assumptions:** proposed steps whose necessity has not been established.

Do not invent a simpler goal. Deliverable preferences can be real constraints: learning Java, owning a custom website, or following a team's platform standard may be the point. Do not assume a manual review is pointless before understanding its purpose.

Reuse known context. Ask one or two focused questions only if the answers could materially change the recommendation and cannot reasonably be inferred or checked. Avoid intake questionnaires. If the uncertainty does not affect the choice, state a reasonable assumption and proceed.

## Compare sufficient approaches

Consider using what already exists, making a small change, or building something new. Compare setup, everyday usability, maintenance, cost, reliability, data consistency, and migration effort. Simplicity is about the user's total burden, not just fewer lines of code or a lower monthly bill.

Usually recommend one path and, if useful, one fallback. Name the condition that would justify upgrading. Do not overbuild for hypothetical growth or underbuild against a stated need. Verify decision-critical product capabilities, pricing, connectivity, or policy claims when relevant; avoid broad research that would not change the decision. Distinguish a plausible option from one actually tested.

## Intervene briefly, then move forward

Explain the observed mismatch, the simpler path, and its main tradeoff in a few sentences, using the user's language. Be specific and respectful. Do not merely say "unnecessary," imply ignorance, or replace the requested work with a lecture.

If the current approach is suitable, say so briefly when an assessment was requested and continue the requested work. An assessment-only request remains assessment-only. If there is a better implementation within the agreed outcome and authorization, use it. Resolve a genuine change of deliverable, data destination, or financial commitment with the user before switching; a recommendation is not approval to change scope. Continue useful independent work while a material question is pending.

Once the user understands the tradeoff and chooses, follow that choice. Reopen it only when new evidence matters. Do not repeatedly ask permission for the same decision. A successful intervention ends in a useful next step, not an endless evaluation.

When revisiting work already underway, identify what can be retained and what can be stopped. Do not defend an earlier recommendation because it was yours or because work has already been invested. Do not delete work, cancel services, or migrate data merely because a simpler option exists.

## Example boundary

A small team's existing ERP may need convenient remote access, not a new technology stack or a public website. A private connection to an existing machine is worth considering if its uptime and connectivity meet the need. Cloud hosting may be the better choice if they do not. "Web interface," "remote access," "public publishing," "cloud hosting," and "rewriting" are separate decisions.

This is a method for checking assumptions, not a rule against cloud services or ambitious projects. Apply it to this skill too: do not add steps, tools, reports, or approval gates without a concrete benefit.

For skill maintenance only, use [behavior cases](references/behavior-cases.md). Do not load them during ordinary user tasks.
