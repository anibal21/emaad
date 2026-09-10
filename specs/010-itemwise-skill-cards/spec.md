# Feature Specification: Item-wise skill cards (agent-parity interview)

**Feature**: `010-itemwise-skill-cards`  
**Created**: 2026-09-09  
**Status**: Converged  
**Branch**: `010-itemwise-skill-cards`  
**Depends on**: `007-inline-concepts-itemwise-sets`, `009-language-preference`

## Summary

Phase 05 (Skills & workflows) must interview **skill by skill** with the same discipline as Phase 04 agent cards: announce progress, one field per turn, persist to session state, propose defaults the human can accept or rewrite.

Vague whole-catalog questions (e.g. “which skills are user-facing vs internal?” as a single undifferentiated prompt) are **anti-patterns** unless framed as a short confirm after item-wise work—or skipped in favor of per-skill fields (`operator_invocable` yes/no).

## Requirements

- **FR-010-01**: Phase 05 walks the draft skill list (from phase 03 primitives) **item-wise**, grouped by owning agent in the same order used for agent cards when roles exist.
- **FR-010-02**: For each skill, Ema fills a **Skill Card** using the field sequence in `method/phases/05-skills-workflows.md` (purpose → trigger → workflows → owner → operator_invocable → must_not → risk tier as needed)—**one question per turn**.
- **FR-010-03**: Progress chrome uses session language, e.g. `Fase 05 · Comercial · skill 1/9 — intake-evaluation-request` (es) / `Phase 05 · … · skill k/M` (en).
- **FR-010-04**: `templates/skill-card.md` includes interview fields aligned with that sequence (purpose/mandate, must_not, operator_invocable).
- **FR-010-05**: `method/questioning.md` documents skill item-wise sets alongside domain-map sets; anti-pattern: unstructured catalog questions in phase 05.

## Acceptance

- [x] Spec 010 + plan/tasks  
- [x] Phase 05 rewritten for agent-parity item-wise skill cards  
- [x] questioning.md + skill-card template + designer skill note  
- [x] specs/README.md indexes 010  
- [x] Single PR to `main`

## Out of scope

Auto-generating skill file trees on disk during interview; changing Script→Skill→Agent selection rules; phase 06 scripts interview depth.
