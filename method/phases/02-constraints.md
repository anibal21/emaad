# Phase 02 — Constraints

## Purpose

Surface binding constraints that drive pattern choice and harness strength.

## Question set — **N = 14**

Follow [`../questioning.md`](../questioning.md): one question per turn.

Announce: `Fase 02 — Constraints: 14 preguntas.`

| k | Ask |
|---|-----|
| 1 | How large is specialized knowledge per domain? (small / medium / large) |
| 2 | One team or multiple teams owning capabilities? |
| 3 | Need parallel specialists with isolated context? (yes/no) |
| 4 | Multi-stage conversational flows with capability unlocks? (yes/no) |
| 5 | Must specialists speak to users, or only a supervisor? |
| 6 | What are the highest blast-radius actions? |
| 7 | Multi-tenant or sensitive data boundaries? (yes/no + brief note) |
| 8 | Prefer interactive speed or higher quality when they conflict? |
| 9 | Target agent platforms? (Cursor, Claude Code, LangGraph, custom, unknown) |
| 10 | Predefined steps vs open-ended work? |
| 11 | Must a **model** orchestrate, or can fixed workflow/code drive order? |
| 12 | Budget for multiple model calls per request? (yes / limited / no) |
| 13 | Mid-flow human approvals required? (yes/no) |
| 14 | Could a **non-agentic** single model call solve most of this? (yes/no) |

If banned tools/network destinations are still unknown after k=9, ask one extra question and announce revised total once (`N = 15`).

## Produce

- Constraints checklist (true/false) aligned to `architecture-decision.md`  
- `gcp_requirements` draft (A–E)  
- Risk summary (top 5)  

## Exit criteria

- All answers recorded  
- Binding constraints marked  
- Human confirms priorities if tradeoffs conflict  

## Next

Phase 03 Pattern selection
