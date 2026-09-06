# Ema Improvements — Trunk-Based Development

Applies only when the human chooses **Option 3 — Trabajar en mejoras de Ema**.

## Model

- **Trunk = `main`.** Prefer committing improvement sets directly to `main` (or merging short-lived branches within hours/days).
- Avoid long-lived feature branches for method work.
- Every meaningful designer change is versioned in Git (human confirms commit unless they asked to auto-commit).

## SDD order for Ema changes

1. **Open the next numbered spec** under `specs/00N-short-slug/` (`spec.md`, `plan.md`, `tasks.md`). See [specs/README.md](../specs/README.md). Do **not** append new FRs to frozen `001` or other converged specs.
2. If binding principles change → amend `constitution.md` (Article X process).
3. Update `method/`, `templates/`, `checklists/`, `skills/`, `agents/`, `examples/` as the *implementation* of that spec.
4. Keep `README.md` / `CONTRIBUTING.md` aligned with user-facing behavior.
5. Mark the spec **Converged**; update `specs/README.md` index row.
6. Commit with a clear message (why over what). Push when the human asks.

## Scope boundaries

| In scope (Option 3) | Out of scope |
|---------------------|--------------|
| New `specs/00N-…`, constitution, method, harness, skill | Client project blueprints in `projects/` (gitignored) |
| Templates, checklists, examples | Unrelated app code |
| Boot menu / index schema | Secret material |

## Working agreement

- One improvement theme per spec when possible.
- Do not leave the skill describing a flow the method no longer implements.
- After commit, summarize what changed for the human in one short paragraph.
