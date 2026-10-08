---
name: implement-it
description: Implement and verify exactly one ready Ticket from TODO.md; use when the user names an issue ID and its acceptance criteria can be completed in the current repository.
license: MIT
---

# Implement It

Implement exactly one explicitly named Ticket from the current `TODO.md`.

## Start

1. Require an issue ID; ask if absent. Never infer one.
2. Read the board and repository instructions. Find the ID exactly once as a Ticket. Missing, duplicate, malformed, or `Done` tickets are read-only failures.
3. Validate the Parent Spec reference, required `Belongs to ticket` field, and every blocker. The Spec must resolve unambiguously. `Belongs to ticket` must be `None` or resolve uniquely to a Ticket; it is grouping, not a blocker. Each blocker must resolve uniquely to a Ticket in `## Done`. If any reference is missing, ambiguous, or invalid, stop read-only and report why. If a card in `## Blocked` has become unblocked, move it to `## Ready`; if a `## Ready` card has an incomplete blocker, stop and report the inconsistent state.
4. Confirm concrete, unambiguous acceptance criteria. Ask focused questions if needed.

## Implement and verify

1. Read the Spec and relevant code/tests. Before editing, reread `TODO.md` and confirm the card is still unique and Ready (or In Progress for a retry); move Ready cards to `## In Progress`. Implement only its criteria using repository conventions; stop and ask if scope changes materially.
2. Run focused checks and a behavior-level smoke check on the real surface or closest integration seam. Review correctness, regressions, security, and scope; fix issues and rerun affected checks. Remove throwaway artifacts.
3. Re-read the board before updating it. Confirm this exact card is still unique and In Progress; preserve all other card content. If it changed concurrently, do not overwrite it.
4. Check only independently verified criteria. Move the card to `## Done` only when all pass; otherwise leave it In Progress. When a blocker completes, move cards in `## Blocked` to `## Ready` only if every blocker is now Done. Report observed checks and completion state.

`TODO.md` contains only Ticket cards under `## Ready`, `## In Progress`, `## Blocked`, and `## Done`; column position is status. Do not add Specs, reminders, or prose. IDs are stable `I-NNN`; never reuse or renumber them. Do not create GitHub Issues or separate ticket files.

Do not commit or create branches/PRs unless explicitly requested. Report the ticket ID, changed files, focused checks, smoke evidence, and status.
