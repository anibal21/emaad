# Ema Improvements — Trunk + Pull Request workflow

Applies when the human chooses **Option 3 — Trabajar en mejoras de Ema**.

## Model

- **Trunk = `main`.** `main` is always the integration line.
- **No direct commits to `main` by default** for Ema product changes.
- Each spec increment uses a **short-lived feature branch** → **Pull Request** → human **approve + merge** → delete branch.
- Start the **next** feature only from updated `main` after merge (unless the human explicitly allows parallel PRs).

This is trunk-based development with a **PR review gate**.

## Branch naming

```text
00N-short-slug
```

Examples: `006-pr-workflow-ema-trunk`, `007-hitl-templates`.  
Prefer matching the `specs/00N-short-slug/` folder name.

## SDD + Git order (mandatory)

1. `git checkout main && git pull`
2. Create next numbered spec folder `specs/00N-short-slug/` (`spec.md`, `plan.md`, `tasks.md`). See [specs/README.md](../specs/README.md).
3. `git checkout -b 00N-short-slug`
4. If binding principles change → amend `constitution.md` (Article X).
5. Implement in `method/`, `templates/`, `checklists/`, `skills/`, `agents/`, `examples/`, docs.
6. Update `specs/README.md` index (status Active until merged).
7. Commit on the **feature branch** (clear why-focused message).
8. `git push -u origin HEAD`
9. Open PR to `main`:

```bash
gh pr create --base main --title "…" --body "…"
```

Use `.github/PULL_REQUEST_TEMPLATE.md`. Link the spec folder. Include Test plan.

10. **Stop and wait** for the human to review, approve, and merge.
11. After merge: `git checkout main && git pull`; mark spec **Converged** if not already done on the branch; then ready for `00N+1`.

## Explicit override

Only commit/push straight to `main` if the human clearly orders an emergency exception. Record that override in the commit/PR notes when possible.

## Scope boundaries

| In scope (Option 3) | Out of scope |
|---------------------|--------------|
| Specs `00N`, constitution, method, harness, skill | Client packages in `projects/` (gitignored) |
| Templates, checklists, examples, docs | Unrelated app code |
| Branch + PR delivery | Long-lived feature branches |

## Working agreement

- One improvement theme per spec/PR when possible.
- Do not leave the skill describing a flow the method no longer implements.
- After the PR is opened, give the human the PR URL and a one-paragraph summary; do not assume merge.
