---
name: tick-it
description: Break an approved spec, plan, or clearly identified request into dependency-aware vertical-slice tickets; use when implementation needs a reviewable sequence of small, verifiable tasks in TODO.md.
license: MIT
---

# Tick It

Turn one approved source into dependency-aware implementation tickets in `TODO.md`. The source may be an approved Spec, plan, or clearly identified conversation. Do not invent requirements, write Spec records, create ordinary TODOs, or create GitHub Issues or separate ticket files.

## Draft

1. Inspect applicable repository instructions, terminology, relevant code and tests, and the current `TODO.md`. If the source is ambiguous, ask which source to use before drafting.
2. Split work into tracer-bullet vertical slices: each ticket delivers a narrow, complete behavior or contract that can be implemented and verified independently. Avoid layer-only tickets unless a real technical dependency requires them.
3. For a wide mechanical refactor that cannot land incrementally, use expand–migrate–contract: add compatible support, migrate callers/data, then remove obsolete support. Do not use this sequence for ordinary feature work.
4. Add only genuine blocker edges: the dependent ticket cannot be built or meaningfully verified until the blocker is complete. Never add ordering-only dependencies. Blockers must be existing or proposed Tickets.
5. For each ticket, show its title, parent Spec, `Belongs to` parent Ticket ID (or `None`), blockers, user-facing outcome, and concrete acceptance criteria.
6. Show the whole proposed ticket set, proposed IDs, and dependency graph. Ask the user to review source alignment, granularity, dependencies, and criteria. Iterate and show the revised set until explicitly approved. Make no file changes before approval.

## Validate and write

1. After approval, allocate stable IDs in dependency order, following the highest numeric suffix in the current board; never reuse or renumber IDs. Re-read the latest `TODO.md` immediately before writing and recalculate. If IDs or dependencies changed, show the updated proposal and obtain approval again.
2. Before writing, validate unique IDs, every blocker references a Ticket, every non-`None` `Belongs to` reference resolves to one existing or proposed Ticket, and both dependency graphs are acyclic. Reject self-links and ambiguous/missing parents. If invalid, revise and validate again.
3. Append one card per approved ticket to its status column. New cards go in `## Ready` when unblocked, or `## Blocked` when they have incomplete blockers. Use this format:

   ```markdown
   ### I-001 — <ticket title>
   **Parent Spec:** <Spec path or title>
   **Belongs to ticket:** None | I-... parent Ticket ID
   **What to build:** <user-facing outcome>

   **Acceptance criteria:**
   - [ ] <observable, verifiable condition>
   ```

4. `TODO.md` contains only Ticket cards under `## Ready`, `## In Progress`, `## Blocked`, and `## Done`. Create those columns only when writing the first approved tickets. Preserve existing cards and add missing columns, but if non-ticket content or cards outside the board are present, stop and ask before changing anything. Never add Specs, reminders, or prose.
5. Report the added IDs and blocker graph. Never claim a ticket is implemented or complete.

## Board conventions

IDs are stable `I-001`, `I-002`, and upward; allocate after the highest numeric suffix. `Belongs to ticket` identifies the parent/grouping Ticket and is not a blocker. Column position is the only status: move cards, never duplicate them. `Ready` requires every blocker to be Done; `Blocked` means at least one blocker is not. Blocker IDs are comma-separated. Move cards to `Done` only after every acceptance criterion passes.
