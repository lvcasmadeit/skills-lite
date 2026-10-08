---
name: plan-it
description: Run a decision-aware planning interview for a feature, project, or change; use when requirements or implementation choices need alignment before work begins.
license: MIT
---

# Plan It

Turn the request into an actionable, decision-complete plan approved by the user. This skill is self-contained: do not rely on another skill or implement the plan.

## Interview

1. Read the request and conversation; carry forward stated preferences and settled answers. Inspect relevant repository instructions, facts, and plan conventions with tools instead of asking about discoverable facts. Avoid unrelated or sensitive files.
2. Map material decisions for this work (such as scope, behavior, constraints, interfaces, data/state, failures, compatibility, and verification) as a decision tree.
3. In each round, ask together every question answerable on the current frontier. Give each a concise recommendation and tradeoff. Defer questions dependent on unresolved choices; ask no filler questions or questions tools can answer.
4. Use the host's structured question UI when available; otherwise ask numbered chat questions with clear options, recommendations, and room for the user's own answer.
5. After each response, update the tree and continue to the next frontier. If an answer changes a decision, reopen only its dependent branches; retain all other settled answers.
6. When no material decisions remain, summarize the shared vision, scope, decisions, and relevant risks or assumptions, then explicitly ask whether the user agrees. A correction is not confirmation: revise only affected branches, ask newly answerable questions, and return to this alignment check. Do not write a plan or implement before explicit confirmation.

## Plan

After confirmation, write a self-contained, actionable plan to the project's existing plan convention or the host's designated plan destination. Inspect to identify the destination; do not guess. If neither exists, ask where to save it.

`TODO.md` is reserved for ticket cards; never write plans there.

Include context and outcome, implementation steps in dependency order, key behavior/interface decisions, relevant verification, resolved tradeoffs and constraints, assumptions, and non-goals. Omit empty boilerplate. Do not implement unless the user separately asks to begin after approval. Report the exact destination and unresolved prerequisites; claim a write only if it succeeded.
