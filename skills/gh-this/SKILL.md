---
name: gh-this
description: Safely turn the current directory into a GitHub repository; use when the user asks to publish this project, requiring explicit visibility and confirmation of every file and remote action.
license: MIT
---

# GH This

Initialize a GitHub repository from the current directory without losing files or history. Never create GitHub Issues.

## Confirm and preflight

1. Get the repository name (`name` for the authenticated account or `owner/name`), optional description, and explicit **public** or **private** visibility. Never infer visibility.
2. Before mutation, confirm `git`, `gh`, and `gh auth status`; inspect worktree, branch, staged changes, and remotes; resolve the canonical GitHub target. Reuse only a matching `origin`. If authentication fails, changes are staged, the target exists without a matching `origin`, or `origin` conflicts, stop. Never switch branches, rewrite history, or replace remotes.
3. For an existing repo, tell the user which branch and existing history the push will publish.

## Select files

- For a non-Git directory, list exact candidate paths using Git ignore semantics, including nested `.gitignore` files. Exclude `.git`, dependencies/build outputs, and known secret or credential paths (including `.env` variants) without opening or printing their contents. Omit suspicious or uncertain paths.
- For an existing worktree, show exact modified/untracked paths that would be committed. Apply the same secret and generated-file exclusions.
- Ask which exact paths to publish. A directory approval is not blanket approval.
- Never create or edit `TODO.md`; `tick-it` creates the ticket-only Kanban board when it adds the first approved tickets.

## Confirm, then execute

1. Show the canonical `owner/name`, description, visibility, exact approved paths, exclusions, branch/history, and every local/remote action. Include a missing `README.md` if it will be created. Ask for explicit confirmation. Make no local or remote changes before it.
2. After confirmation, create a missing `README.md` with the repository name and supplied description, and initialize Git only if absent. Stage only approved paths plus that README; never use a blanket add. Recheck the index and stop if user changes are staged.
3. Commit only those paths, then create the confirmed GitHub repository if needed, add/use the matching `origin` without replacing any remote, and push only the confirmed branch.
4. If a later step fails, preserve earlier successful changes and report the exact partial state. Never roll back automatically or claim an unobserved success.

Do not inspect secret contents or expose credentials, discard files, amend commits, or change the user's branch.
