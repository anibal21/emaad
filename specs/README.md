# Specs index (SDD)

EMAAD follows **Spec-Driven Development**: each meaningful product change gets a numbered folder under `specs/`. The method, skill, and templates are the *implementation* of those specs. The constitution is binding across all specs.

## Numbering

| ID | Folder | Status | Summary |
|----|--------|--------|---------|
| 001 | [001-architecture-designer](./001-architecture-designer/) | **Foundation (frozen)** | Baseline Ema/EMAAD method (phases, harness, templates, skill) |
| 002 | [002-boot-menu-projects](./002-boot-menu-projects/) | Converged | Hola Ema boot menu; `projects/`; trunk Option 3 |
| 003 | [003-gcp-primitive-selection](./003-gcp-primitive-selection/) | Converged | GCP agentic patterns + Script→Skill→Agent selection |
| 004 | [004-one-question-gitignore](./004-one-question-gitignore/) | Converged | One question per turn (`k/N`); gitignore user projects |
| 005 | [005-sdd-spec-numbering](./005-sdd-spec-numbering/) | Converged | Formalize multi-spec discipline + backfill 002–004 |

Next change → **`006-<short-slug>/`** with `spec.md`, `plan.md`, `tasks.md` (and `research.md` if needed).

## Rules

1. **Do not append new requirements to a frozen/converged spec.** Open the next number.
2. **001 stays frozen** as the foundation snapshot. Later specs may *refine* behavior; if they conflict, the newer converged spec + constitution win (constitution always wins on principles).
3. **Option 3 (mejoras de Ema):** create/update the active `00N` spec *before* or *as* you change `method/` / skill (see `method/ema-trunk.md`).
4. **Trunk = `main`.** Spec folders live on main; optional short-lived branches for large specs.
5. Mark status: `Draft` → `Active` → `Converged` (or `Abandoned`).

## Mapping commits (historical)

| Spec | Approx. commits |
|------|-----------------|
| 001 | `50317a0` (+ persona Ema in same era) |
| 002 | `6b17a4f` |
| 003 | `5ae6f02` |
| 004 | `721a53a` |
| 005 | (this change set) |
