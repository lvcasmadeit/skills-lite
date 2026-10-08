---
name: spec-it
description: Turn settled product or engineering context into a complete, behavior-focused spec; use when scope and intent are understood and need recording before implementation or ticketing.
license: MIT
---

# Spec It

Synthesize the current request, conversation, and repository context into one complete spec. Do not re-interview the user or ask them to repeat settled decisions.

## Prepare

1. Read applicable repository instructions and inspect relevant terminology, contracts, behavior, tests, and the existing spec convention. Use repository evidence; distinguish unresolved decisions from settled facts and do not invent details.
2. Identify the highest useful test seam: a realistic, observable behavior or contract that verifies the change at the broadest useful level. Consider existing test conventions and dependencies. Propose the seam and briefly explain why it is appropriate. If there is no runtime or test harness, propose a concrete behavior-level alternative and state its limitation.
3. Present a concise spec draft and ask the user to confirm or correct the proposed test seam before writing. This is a focused approval gate, not a requirements interview. If corrected, update the seam and relevant spec decisions, then ask for confirmation again.
4. After seam approval, save the spec using the project's existing spec convention. If no convention or clear destination exists, ask where to save it; do not guess or write elsewhere.

## Write

Include these sections, with concrete, non-duplicative content tied to the agreed scope:

- **Problem Statement** — user or system need and why it matters.
- **Solution** — intended outcome and behavior.
- **User Stories** — numbered stories in “As a …, I want …, so that …” form.
- **Implementation Decisions** — established constraints and decisions; avoid speculative design.
- **Testing Decisions** — approved test seam, expected behavior-level coverage, and any verification limitation.
- **Out of Scope** — explicit boundaries; use `None` if needed.
- **Further Notes** — relevant compatibility, error behavior, dependencies, or unresolved points; use `None` if needed.

Keep the spec complete and concise; preserve the project's format and content. Never write Specs to `TODO.md` or create tickets/GitHub Issues from this skill.
