# Phase 03 — Pattern Selection

## Purpose

Choose the primary orchestration pattern with explicit tradeoffs.

## Do

1. Apply [`../architecture-decision.md`](../architecture-decision.md) with the human (include GCP tables via [`../gcp-agentic-patterns.md`](../gcp-agentic-patterns.md)).  
2. Present recommendation + rejected alternatives (EMAAD label **and** GCP pattern).  
3. Draft primitive candidates with [`../primitive-selection.md`](../primitive-selection.md) (agents / skills / scripts).  
4. If user insists against evidence, record dissent and keep recommendation as "EMAAD default" plus "user override" section.  

## Produce

- `gcp_pattern`, `gcp_requirements`  
- `primary_pattern`, `secondary_patterns`  
- `tradeoff_statement`  
- Draft `primitives` lists  
- Short mermaid sketch of control flow  

## Exit criteria

- Gate **G-PATTERN** passed  
- Human acknowledges tradeoff sentence  
- Draft scripts/skills/agents list exists (may be refined in 04–06)  

## Next

Phase 04 Agent design
