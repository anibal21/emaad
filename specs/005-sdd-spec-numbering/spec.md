# Feature Specification: Multi-spec SDD numbering

**Feature**: `005-sdd-spec-numbering`  
**Created**: 2026-09-06  
**Status**: Converged  
**Depends on**: `001`–`004`

## Summary

Stop treating `001` as a living catch-all. Freeze foundation; backfill historical increments as `002`–`004`; require each new Ema improvement to open `006+` with its own spec/plan/tasks. Document the index and update Option 3 trunk workflow.

## User stories

1. Maintainer opens a new improvement → creates `specs/00N-slug/` before (or while) changing method.  
2. Reader understands product history via `specs/README.md`.

## Requirements

- **FR-005-01**: `specs/README.md` indexes all specs and numbering rules.
- **FR-005-02**: `001` marked Foundation (frozen); no new FRs appended there.
- **FR-005-03**: Backfill `002`–`004` specs for prior converged work.
- **FR-005-04**: `method/ema-trunk.md` and CONTRIBUTING require next-number specs for behavior changes.
- **FR-005-05**: Constitution notes numbered specs as the unit of product change (under Article I).

## Acceptance

- [x] Specs 001–005 documented as above  
- [x] Trunk + contributing instructions updated  
- [x] README points to specs index  

## Out of scope

Rewriting git history; splitting method files further.
