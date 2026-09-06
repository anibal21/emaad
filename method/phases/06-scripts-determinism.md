# Phase 06 — Scripts (Deterministic Workers)

## Purpose

Pull stable work out of the LLM into scripts.

## Do

1. Enforce [`../primitive-selection.md`](../primitive-selection.md): every deterministic unit must be a script candidate.  
2. Review domain map rows marked deterministic.  
3. Review workflows for mechanical steps (validate schema, rename, checklist compute, generate boilerplate, merge parallel JSON, max-iter / exit checks for loops).  
4. For Review & critique / quality gates: extract what a **script** can check before keeping a Critic agent.  
5. Create Script Cards: input, output, exit codes, who invokes, sandbox needs.  
6. Prefer boring languages already in the org; note recommendation without mandating unless user constrains.  

## Heuristic

> If two competent engineers would get the **same bytes out** given the same bytes in, it should be a script.

## Exit criteria

- Script list covers obvious deterministic work  
- Each script has an invoking agent/skill  
- Borderline LLM tasks documented with rationale  

## Next

Phase 07 Security harness
