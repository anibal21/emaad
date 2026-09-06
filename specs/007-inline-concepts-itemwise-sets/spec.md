# Feature Specification: Inline concepts and item-wise data sets

**Feature**: `007-inline-concepts-itemwise-sets`  
**Created**: 2026-09-06  
**Status**: Converged  
**Merged**: PR https://github.com/anibal21/emaad/pull/3 (`88c7b13`)  
**Depends on**: `004-one-question-gitignore`, `006-pr-workflow-ema-trunk`

## Summary

When Ema asks about specialized concepts (e.g. juicio / procedimiento / chequeo determinista), the **definition must be embedded in that question turn**—never assume the human already knows EMAAD jargon.

When a question requires filling the **same field for every item** in a collected list (domains, agents, side effects, etc.), Ema MUST run an **item-wise loop**: one item per turn, with progress `ítem i/M`, instead of asking the human to type all mappings at once.

## User stories

1. Human sees work-type options **explained in the same message** as the question.  
2. After listing 12 capabilities, Ema asks work_type for capability 1/12, then 2/12, …—human never pastes a full mapping table unless they choose fast-path.

## Requirements

- **FR-007-01**: `method/questioning.md` requires **inline concept gloss** for non-obvious terms used in a question (table or one-liners in that turn).
- **FR-007-02**: `method/questioning.md` requires **item-wise sets** for per-item field collection; announce set name, `M`, and `ítem i/M` (+ phase `k/N` when nested).
- **FR-007-03**: Phase 01 (and other phases with “for each”) rewritten to use item-wise loops after the list is captured.
- **FR-007-04**: Skill + constitution Article VIII reference the new rules.
- **FR-007-05**: Anti-patterns: “classify all of these in one reply” without offering item-wise default.

## Acceptance

- [x] questioning.md documents inline gloss + item-wise sets  
- [x] phase 01 uses item-wise work_type / systems / user_facing  
- [x] skill operating loop mentions item-wise expansion  
- [x] PR opened/merged to `main`  

## Out of scope

Changing Neorizon Factory session answers mid-flight beyond what the new protocol implies when that session resumes.
