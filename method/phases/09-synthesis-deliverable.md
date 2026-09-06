# Phase 09 — Synthesis Deliverable

## Purpose

Assemble the architecture package, run checklists, set status.

## Do

1. Write `architecture-blueprint.md` from template.  
2. Ensure all cards present and linked.  
3. Draw ecosystem mermaid: humans, agents, skills, workflows, scripts, MCP.  
4. Run checklists: SRP, security-review, token-budget, HITL.  
5. Produce implementation backlog (ordered).  
6. Set status `Review` and request human acceptance for `Approved`.  

## Deliverable tree

```text
sessions/<slug>/
  session-state.md
  architecture-blueprint.md
  agents/*.md
  skills/*.md
  workflows/*.md
  scripts/*.md
  mcp-allowlist.md
  checklists-results.md
  ecosystem.mmd   # or embed in blueprint
```

## Exit criteria

- Spec success criteria SC-002–SC-005 satisfiable by inspection  
- Gate **G-HUMAN** for Approved  
- Open waivers listed with owners  

## Aftercare

Offer: export cards into target repo paths; generate stub `SKILL.md` files; schedule eval authoring—without expanding scope unless asked.
