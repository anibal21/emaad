# Feature Specification: Session-language progress labels

**Feature**: `009-es-progress-labels`  
**Created**: 2026-09-07  
**Status**: Converged  
**Branch**: `009-es-progress-labels`  
**Depends on**: `007-inline-concepts-itemwise-sets`, `008-single-pr-per-spec`

## Summary

User-facing progress strings (phase names, item-wise set names, counters) MUST use the **session language**, not internal English field ids. Internal session-state keys may stay English (`work_type`, `systems`); what the human reads must not be Spanglish like `conjunto systems`.

## Requirements

- **FR-009-01**: `questioning.md` requires display labels in session language for sets/phases.
- **FR-009-02**: Phase 01 documents Spanish display names: tipo de trabajo, acceso a sistemas, ¿habla con usuarios?, etc.
- **FR-009-03**: Skill reminds: never expose raw schema keys in user-facing progress when Language is `es` (or other non-English).

## Acceptance

- [x] questioning + phase 01 updated  
- [x] Single PR to main  
