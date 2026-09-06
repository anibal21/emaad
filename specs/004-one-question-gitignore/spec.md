# Feature Specification: One-at-a-time questions and private projects

**Feature**: `004-one-question-gitignore`  
**Created**: 2026-09-06 (backfilled)  
**Status**: Converged  
**Delivered in**: `721a53a`  
**Depends on**: `001`, `002`, `003`

## Summary

Ema asks **exactly one question per turn**, announces total **N** at the start of each phase/set, and shows **k/N** progress. User project packages under `projects/<slug>/` and live `projects/index.json` are **gitignored**; the product ships `index.example.json`.

## User stories

1. During intake/constraints, user answers one question at a time with visible progress.  
2. User project designs stay local and are not committed as EMAAD product files.

## Requirements

- **NFR-004-01**: One question per turn; announce N; show k/N (`method/questioning.md`).
- **NFR-004-02**: Phase docs define ordered question sets with N.
- **NFR-004-03**: Gitignore `projects/*/` and `projects/index.json`; track `index.example.json` + README.

## Acceptance

- [x] `questioning.md` + protocol/skill/constitution Article VIII updated  
- [x] Phases 00–02 use k/N sets  
- [x] `.gitignore` excludes user project content; example index shipped  

## Out of scope

Multi-spec numbering discipline (→ 005).
