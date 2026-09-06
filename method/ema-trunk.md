# Ema Improvements — Trunk + Pull Request workflow

Applies when the human chooses **Option 3 — Trabajar en mejoras de Ema**.

## Model

- **Trunk = `main`.** `main` is always the integration line.
- **No direct commits to `main` by default** for Ema product changes.
- Each spec increment uses **one short-lived feature branch** → **one Pull Request** → human **approve + merge** → delete branch.
- Start the **next** feature only from updated `main` after merge (unless the human explicitly allows parallel PRs).
- **Never open a second PR** only to flip status to Converged after merge.

## Branch naming

```text
00N-short-slug
```

Examples: `006-pr-workflow-ema-trunk`, `008-single-pr-per-spec`.  
Prefer matching the `specs/00N-short-slug/` folder name.

## SDD + Git order (mandatory)

1. `git checkout main && git pull`
2. Create next numbered spec folder `specs/00N-short-slug/` (`spec.md`, `plan.md`, `tasks.md`). See [specs/README.md](../specs/README.md).
3. `git checkout -b 00N-short-slug`
4. If binding principles change → amend `constitution.md` (Article X).
5. Implement in `method/`, `templates/`, `checklists/`, `skills/`, `agents/`, `examples/`, docs.
6. When acceptance criteria are met on the branch: set spec status to **Converged** and update `specs/README.md` (Converged). Meaning: *work is done; waiting for human merge*.
7. Commit on the **feature branch** (clear why-focused message).
8. `git push -u origin HEAD`
9. Open **one** PR to `main`:

```bash
gh pr create --base main --title "…" --body "…"
```

Use `.github/PULL_REQUEST_TEMPLATE.md`. Link the spec folder.

10. **Stop and wait** for the human to review, approve, and merge.
11. After merge: `git checkout main && git pull`; delete local/remote feature branch if desired. **Do not** open a follow-up PR for housekeeping status.

## Explicit override

Only commit/push straight to `main` if the human clearly orders an emergency exception. Record that override when possible.

## Scope boundaries

| In scope (Option 3) | Out of scope |
|---------------------|--------------|
| Specs `00N`, constitution, method, harness, skill | Client packages in `projects/` (gitignored) |
| Templates, checklists, examples, docs | Unrelated app code |
| **One** branch + **one** PR per spec | Long-lived branches; post-merge stamp PRs |

## Working agreement

- One improvement theme per spec/PR when possible.
- Do not leave the skill describing a flow the method no longer implements.
- After the PR is opened, give the human the PR URL and a one-paragraph summary; do not assume merge.
