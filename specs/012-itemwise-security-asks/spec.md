# Feature Specification: Item-wise security harness interview

**Feature**: `012-itemwise-security-asks`  
**Created**: 2026-09-09  
**Status**: Converged  
**Branch**: `012-itemwise-security-asks`  
**Depends on**: `007-inline-concepts-itemwise-sets`, `010-itemwise-skill-cards`, `011-self-explanatory-questions`

## Summary

Phase 07 (Security harness) must **not** ask vague whole-catalog questions (e.g. “¿Dónde viven los secretos?”). Ema walks **item-wise** over each external system / MCP from the session allowlist draft, and over High-tier skills when asking review ownership—same discipline as domain-map fields and skill cards. Each turn is self-explanatory (`011`).

## Requirements

- **FR-012-01**: Build the item list for secrets/MCP from session `primitives.mcp` (and any other live systems named in the domain map). If empty, ask once whether there are zero external systems, then continue.
- **FR-012-02**: For **each** system/MCP, ask where **that** system’s secrets live (one question per item), with gloss + example.
- **FR-012-03**: For **each** MCP server, walk allowlist/scopes/agents-allowed as an item-wise set (or a short fixed field sequence per server, one field per turn)—never one question for “all MCPs”.
- **FR-012-04**: For skill production review: either ask per **High** (and optionally Medium) risk-tier skill who reviews it, or confirm a single reviewer **only after** listing those skills—default is **per High-tier skill** item-wise.
- **FR-012-05**: Audit sink may be one question if there is a single org sink; if multiple sinks are named, ask per sink. Do not bundle secrets+MCP+audit in one prompt.
- **FR-012-06**: Anti-pattern: Phase 07 “Ask” blocks that are only four general bullets without item-wise expansion.

## Acceptance

- [x] Spec 012 + plan/tasks  
- [x] `method/phases/07-security-harness.md` rewritten item-wise  
- [x] `questioning.md` anti-pattern + display labels  
- [x] Designer skill pointer  
- [x] `specs/README.md` indexes 012  
- [x] Single PR to `main`

## Out of scope

Implementing vault tooling; changing OWASP control tables themselves; auto-waiving gates.
