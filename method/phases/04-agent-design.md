# Phase 04 — Agent Design

## Purpose

Name agents with unique responsibilities, scopes, and interaction rules.

## Do

1. For single-agent + skills: define **one** lead agent card; specialists are skills unless isolation demands agents.  
2. For subagents: define supervisor + specialists (as tool-agents).  
3. For handoffs: define stage agents and transition conditions.  
4. For router: define router/synthesizer + vertical specialists.  
5. Apply [`../srp-and-boundaries.md`](../srp-and-boundaries.md).  
6. Draft Agent Cards from `templates/agent-card.md`.  

## Ask per agent

- Mandate (one sentence)?  
- Speaks to user? Y/N  
- Tools / MCP needed?  
- May call which other agents?  
- Max autonomy / budgets?  

## Exit criteria

- All agents named with SRP mandates  
- Handoff/call graph has no unauthorized edges  
- Preliminary SRP overlap scan clean (formal checklist in synthesis)  

## Next

Phase 05 Skills & workflows
