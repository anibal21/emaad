# Phase 00 — Intake

## Purpose

Establish project identity, greenfield vs brownfield *within* the client domain, domain, and success definition.

Entered after **Hola Ema** → boot menu → **Option 1 or 2** (not Option 3).

## Preconditions

| Boot choice | Preconditions |
|-------------|----------------|
| Option 1 | `projects/<slug>/` created; index entry added; `ema_mode: project_new` |
| Option 2 | Project selected from `projects/index.json`; session-state loaded; `ema_mode: project_continue` |

For Option 1, slug/name may already be set—do not re-ask unless correcting.

## Ask (batch)

1. Confirm project name / slug (Option 1: finalize; Option 2: confirm loaded).  
2. Within this project: greenfield architecture or brownfield (existing agents/skills/MCP)?  
3. Primary domain: software delivery, support, research, ops, other?  
4. In one paragraph: what should the agent ecosystem achieve?  
5. Who are the human users and approvers?  
6. Hard deadlines or compliance regimes (SOC2, HIPAA, internal AI policy)?  

## Extract into session state

- `project_slug`, `ema_mode`, `mode` (greenfield|brownfield), `domain`, `mission`, `stakeholders`, `compliance`
- `path`: `projects/<slug>/`

## Exit criteria

- Mission statement confirmed  
- Greenfield/brownfield selected  
- Project folder + index entry exist and match  

## Next

Phase 01 Domain map
