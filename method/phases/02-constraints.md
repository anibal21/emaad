# Phase 02 — Constraints

## Purpose

Surface binding constraints that drive pattern choice and harness strength.

## Ask

### Context & ownership

1. How large is specialized knowledge per domain (small / medium / large)?  
2. One team or multiple teams owning capabilities?  
3. Need parallel specialists with isolated context?  

### Interaction & state

4. Multi-stage conversational flows with unlocks?  
5. Must specialists speak to users, or only a supervisor?  

### Risk & scale

6. Highest blast-radius actions?  
7. Multi-tenant or sensitive data boundaries?  
8. Latency sensitivity (interactive chat vs async jobs)?  
9. Expected skill catalog size at 6 months?  

### Platform

10. Target agent platforms (Cursor, Claude Code, LangGraph, custom, unknown)?  
11. Any banned tools/models/network destinations?  

### GCP agentic requirements (seed for phase 03)

See `method/gcp-agentic-patterns.md`. Ask briefly:

12. Predefined steps vs open-ended work?  
13. Must a **model** orchestrate, or can fixed workflow/code drive order?  
14. Prefer speed or quality when they conflict?  
15. Budget for multiple model calls per request?  
16. Mid-flow human approvals required?  
17. Could a **non-agentic** single model call solve most of this?  

## Produce

- Constraints checklist (true/false) aligned to `architecture-decision.md`  
- `gcp_requirements` draft (A–E)  
- Risk summary (top 5)  

## Exit criteria

- Binding constraints marked  
- Human confirms priorities if tradeoffs conflict (e.g., isolation vs latency)  

## Next

Phase 03 Pattern selection
