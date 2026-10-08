# Skills Lite

A portable set of agent skills for planning and shipping software work:

- **`plan-it`** — interview through the decision tree, align on the shared vision, then write a complete plan.
- **`gh-this`** — safely adopt the current directory as a GitHub repository with explicit file selection and publication approval.
- **`spec-it`** — turn agreed context into a testable spec outside the ticket board.
- **`tick-it`** — break a spec into approved, dependency-aware tickets.
- **`implement-it`** — implement and verify one ready ticket.

## Install

Install any skill from this repository into an agent supported by the [Skills CLI](https://github.com/vercel-labs/skills):

```bash
npx skills@latest add lvcasmadeit/skills-lite
```

The CLI prompts you to choose skills and agent targets. For OMP/Pi, install one skill explicitly with:

```bash
npx skills@latest add lvcasmadeit/skills-lite --skill plan-it --agent pi
```

OMP discovers Pi-targeted project installs from `.agents/skills/`. Update installed skills with:

```bash
npx skills@latest update
```

For a custom or unsupported harness, copy any desired `skills/<skill-name>/` directory into the skill directory configured for that harness.

## Ticket board

`TODO.md` is a Kanban board of tickets only. It contains no Specs, ordinary reminders, or status prose. The board columns are the ticket states; move a card instead of copying it.

```markdown
# TODO

## Ready

## In Progress

## Blocked

## Done
```

Each ticket card includes its stable `I-NNN` ID, title, parent Spec reference, comma-separated blocker IDs (or `None`), user-facing outcome, and acceptance criteria:

```markdown
### I-001 — <title>
**Parent:** <spec path or title>
**Blocked by:** None
**What to build:** <user-visible outcome>
**Acceptance criteria:**
- [ ] <observable condition>
```

- `Ready` means every blocker is done; `Blocked` means at least one blocker is not.
- Specs belong in the project's existing spec convention; `spec-it` asks where to save if none exists. Never put Specs or ordinary TODO items in `TODO.md`.
- `tick-it` creates the board when it writes the first approved tickets. `gh-this` does not create an empty board.
- Allocate IDs after the highest existing numeric suffix; never reuse or renumber them.

## License

The collection is released under the MIT License. See [`LICENSE`](LICENSE).
