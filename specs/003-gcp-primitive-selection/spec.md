# Feature Specification: GCP patterns and primitive selection

**Feature**: `003-gcp-primitive-selection`  
**Created**: 2026-09-06 (backfilled)  
**Status**: Converged  
**Delivered in**: `5ae6f02`  
**Depends on**: `001`, `002`

## Summary

Ema must interview using [Google Cloud agentic design pattern](https://docs.cloud.google.com/architecture/choose-design-pattern-agentic-ai-system) questions, record `gcp_pattern`, map to EMAAD orchestration labels, and systematically choose **scripts, skills, and agents** (prefer Script → Skill → Agent).

## User stories

1. User answers use-case/requirement questions → Ema recommends GCP + EMAAD pattern with tradeoffs.  
2. From domain units, Ema proposes justified primitive lists—not ad hoc agents.

## Requirements

- **FR-003-01**: Apply `method/gcp-agentic-patterns.md`; record `gcp_pattern` / `gcp_requirements`.
- **FR-003-02**: Use `method/primitive-selection.md` for every script/skill/agent recommendation.
- **FR-003-03**: Ask whether non-agentic solution suffices before multi-agent.
- **FR-003-04**: Wire phases 02–06 and blueprint/session templates for GCP + primitives fields.

## Acceptance

- [x] GCP + primitive docs exist and are linked from skill/decision matrix  
- [x] Architecture decision framework includes GCP steps  
- [x] Templates capture `gcp_pattern` and primitives  

## Out of scope

Boot menu (002); questioning cadence (004).
