# Phase 00 — Intake

## Purpose

Establish greenfield vs brownfield, domain, mission, stakeholders, and compliance.

Entered after **Hola Ema** → boot menu → **Option 1 or 2** (not Option 3). Name/slug are set during boot Option 1 before this phase.

## Preconditions

| Boot choice | Preconditions |
|-------------|----------------|
| Option 1 | `projects/<slug>/` created; index entry added; `ema_mode: project_new` |
| Option 2 | Project selected from `projects/index.json`; session-state loaded; `ema_mode: project_continue` |

## Question set — **N = 5**

Follow [`../questioning.md`](../questioning.md): one question per turn.

Announce: `Fase 00 — Intake: 5 preguntas.`

| k | Ask |
|---|-----|
| 1 | Within this project: **greenfield** or **brownfield** (existing agents/skills/MCP)? |
| 2 | Primary domain: software delivery, support, research, ops, or other? (If other, specify.) |
| 3 | In one paragraph: what should the agent ecosystem achieve? |
| 4 | Who are the human users and who approves (HITL)? |
| 5 | Compliance or hard deadlines? (SOC2, HIPAA, internal AI policy, date—or “ninguno”) |

Option 2: if resuming mid-phase, continue at the next unanswered `k`.

## Extract into session state

- `project_slug`, `ema_mode`, `mode` (greenfield|brownfield), `domain`, `mission`, `stakeholders`, `compliance`
- `path`: `projects/<slug>/`

## Exit criteria

- All 5 answers recorded  
- Project folder + index entry exist and match  

## Next

Phase 01 Domain map
