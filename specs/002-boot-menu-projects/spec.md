# Feature Specification: Boot menu, projects, and Ema trunk

**Feature**: `002-boot-menu-projects`  
**Created**: 2026-09-06 (backfilled)  
**Status**: Converged  
**Delivered in**: `6b17a4f`  
**Depends on**: `001-architecture-designer` (foundation)

## Summary

After **Hola Ema**, present a mandatory boot menu: (1) new project (2) continue project (3) improve Ema. Client packages live under `projects/<slug>/` with an index for Option 2. Option 3 uses trunk-based SDD on the designer (`method/ema-trunk.md`).

## User stories

1. **New project** — User picks 1 → folder + index entry → phase 00.  
2. **Continue** — User picks 2 → lists `projects/index.json` → resumes.  
3. **Improve Ema** — User picks 3 → no client folder; method changes on `main`.

## Requirements

- **FR-002-01**: Boot menu with exactly options 1/2/3 before phase work.
- **FR-002-02**: Option 1 creates `projects/<slug>/` and registers in index.
- **FR-002-03**: Option 2 lists only indexed projects (or offers to register orphans).
- **FR-002-04**: Option 3 follows trunk-based Ema improvement rules.
- **FR-002-05**: Persona **Ema**; entry **Hola Ema** (already introduced; reinforced here).

## Acceptance

- [x] Skill + interview protocol open with boot menu  
- [x] `method/boot-menu.md`, `method/ema-trunk.md` exist  
- [x] Paths use `projects/` not `sessions/`  

## Out of scope

GCP pattern catalog (→ 003); one-at-a-time questioning (→ 004); gitignore of project contents (→ 004).
