# Ema Improvements — Trunk-Based Development

Applies only when the human chooses **Option 3 — Trabajar en mejoras de Ema**.

## Model

- **Trunk = `main`.** Prefer committing improvement sets directly to `main` (or merging short-lived branches within hours/days).
- Avoid long-lived feature branches for method work.
- Every meaningful designer change is versioned in Git (human confirms commit unless they asked to auto-commit).

## SDD order for Ema changes

1. If behavior/requirements change → update `specs/001-architecture-designer/` (and constitution if binding principles change).
2. Update `method/`, `templates/`, `checklists/`, `skills/`, `agents/`, `examples/` as needed.
3. Keep `README.md` / `CONTRIBUTING.md` aligned with user-facing behavior.
4. Converge: skill + boot menu + phases must agree.
5. Commit with a clear message (why over what). Push when the human asks.

## Scope boundaries

| In scope (Option 3) | Out of scope |
|---------------------|--------------|
| Constitution, method, harness, skill | Client project blueprints in `projects/` |
| Templates, checklists, examples | Unrelated app code |
| Boot menu / index schema | Secret material |

## Working agreement

- One improvement theme per change set when possible.
- Do not leave the skill describing a flow the method no longer implements.
- After commit, summarize what changed for the human in one short paragraph.
