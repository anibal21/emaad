# Specs index (SDD)

EMAAD follows **Spec-Driven Development**: each meaningful product change gets a numbered folder under `specs/`. The method, skill, and templates are the *implementation* of those specs. The constitution is binding across all specs.

Delivery to trunk: **one short-lived branch + one Pull Request → `main`** (see `method/ema-trunk.md`). Do not land Ema product changes directly on `main` by default. Do not open a second PR only to mark Converged.

## Numbering

| ID | Folder | Status | Summary |
|----|--------|--------|---------|
| 001 | [001-architecture-designer](./001-architecture-designer/) | **Foundation (frozen)** | Baseline Ema/EMAAD method (phases, harness, templates, skill) |
| 002 | [002-boot-menu-projects](./002-boot-menu-projects/) | Converged | Hola Ema boot menu; `projects/`; trunk Option 3 |
| 003 | [003-gcp-primitive-selection](./003-gcp-primitive-selection/) | Converged | GCP agentic patterns + Script→Skill→Agent selection |
| 004 | [004-one-question-gitignore](./004-one-question-gitignore/) | Converged | One question per turn (`k/N`); gitignore user projects |
| 005 | [005-sdd-spec-numbering](./005-sdd-spec-numbering/) | Converged | Formalize multi-spec discipline + backfill 002–004 |
| 006 | [006-pr-workflow-ema-trunk](./006-pr-workflow-ema-trunk/) | Converged | Branch + PR gate for Ema updates; no direct main by default |
| 007 | [007-inline-concepts-itemwise-sets](./007-inline-concepts-itemwise-sets/) | Converged | Inline concept gloss + item-wise sets for per-item fields |
| 008 | [008-single-pr-per-spec](./008-single-pr-per-spec/) | Converged | One PR per spec; no post-merge converge stamp |
| 009 | [009-language-preference](./009-language-preference/) | Converged | Language gate es/en + technical terms + UI labels |

Next change → **`010-<short-slug>/`** on a new branch from merged `main`, with **one** PR.

## Rules

1. **Do not append new requirements to a frozen/converged spec.** Open the next number.
2. **001 stays frozen** as the foundation snapshot. Later specs may *refine* behavior; if they conflict, the newer converged spec + constitution win (constitution always wins on principles).
3. **Option 3:** create `00N` spec + branch → implement → set status **Converged on the branch** → **one PR to `main`** → wait for approve/merge (`method/ema-trunk.md`).
4. **Trunk = `main`.** Feature branches are short-lived; next feature starts after merge unless parallel work is explicitly allowed.
5. Mark status: `Draft` → `Active` → **`Converged` (on feature branch when work is done, before/at PR)** → merged to trunk. Never a second PR only for the status flip.
6. Abandoned specs: `Abandoned`.
7. UI language is workspace-configured (es/en); technical proper nouns stay original with parenthetical gloss (`009`).

## Mapping commits / PRs (historical)

| Spec | Notes |
|------|--------|
| 001–005 | Early direct-to-`main` history (pre-PR gate) |
| 006 | PR #1; mistaken follow-up stamp PR #2 (process debt) |
| 007 | PR #3; stamp PR #4 superseded by 008 |
| 008 | Single-PR rule; closes the double-PR pattern |
| 009 | Language preference config; supersedes open progress-label PR #6 |
