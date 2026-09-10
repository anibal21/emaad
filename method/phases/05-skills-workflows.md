# Phase 05 — Skills & Workflows

## Purpose

Package domain knowledge as **skills** (paquetes de especialización) with progressive disclosure and task **workflows**, using the **same interview discipline as Phase 04 agent cards**.

## Do

1. Start from the draft skill list in phase 03 / session `primitives.skills` + `agent_skill_map` ([`../primitive-selection.md`](../primitive-selection.md)).  
2. Prefer **narrow** skills; consolidate later only with evals ([`../srp-and-boundaries.md`](../srp-and-boundaries.md)).  
3. Walk skills **item-wise**, grouped by owning agent in the **same order** as phase 04 agent cards when roles exist.  
4. For each skill: draft a Skill Card from `templates/skill-card.md` via the Ask sequence below.  
5. Ensure each skill has ≥1 workflow **or** a documented skill-body-only reason.  
6. Plan coexistence: descriptions must not steal triggers from siblings.  
7. Ask when something still looks like an agent but is really a skill—downgrade when possible (one question; do not derail the item-wise loop).  

## Ask per skill (item-wise — mandatory)

Announce the set when starting an agent’s skills, e.g.:

```text
Fase 05 · Comercial · skill 1/9 — intake-evaluation-request
Phase 05 · Commercial · skill 1/9 — intake-evaluation-request
```

One field per turn (propose a default the human can accept or rewrite). **Gloss every field name** on first use in the set (self-explanatory questions — [`../questioning.md`](../questioning.md)); e.g. when asking for workflows, define **workflow** (receta paso a paso dentro del skill) with a micro-example before the choice.

| Step | Field | Ask (es gloss) |
|------|-------|----------------|
| 1 | `purpose` | Propósito / mandato en una frase (SRP del skill) — qué problema resuelve este paquete |
| 2 | `trigger` | Description / frases que disparan el skill (cuándo debe activarse) |
| 3 | `workflows` | ≥1 **workflow** (flujo de pasos concretos) name + when to use it (or skill-body-only reason) |
| 4 | `owner` | Agente dueño (already known if grouped—confirm if needed) |
| 5 | `operator_invocable` | ¿El operador puede invocarlo a mano? (**Sí** / **No**) — gloss: elegir el skill tú mismo vs solo uso interno entre agentes |
| 6 | `must_not` | Qué no debe hacer este skill |
| 7 | `risk_tier` | Low / Medium / High (only if not obvious from HITL/MCP) — gloss blast/risk briefly |

Skip a step only when already confirmed and unchanged (never re-ask). Shared skills appearing under multiple agents: define **once**, then reference.

### Display labels

| Internal | Display (es) | Display (en) |
|----------|--------------|--------------|
| skill card loop | Skills · \<rol\> · skill k/M | Skills · \<role\> · skill k/M |

## Ask once after all skill cards (optional short set)

| k | Ask |
|---|-----|
| 1 | Where will skill source of truth live (git path under the client package)? |
| 2 | Who owns evals/reviews for High-tier skills? |

Do **not** replace the item-wise loop with a single vague catalog question (e.g. “which skills are user-facing?”)—that is captured per skill as `operator_invocable`.

## Produce

- Skill Cards (session state and/or `projects/<slug>/skills/*.md`)  
- Workflow names linked on each card  
- Role bundles = agent → skills map (refined)  

## Exit criteria

- Every judgment/procedure domain has a skill or explicit deferral  
- Each skill has ≥1 workflow or documented skill-body-only reason  
- Every skill card has purpose, trigger, owner, operator_invocable, must_not  
- Role bundles defined if catalog will grow  

## Next

Phase 06 Scripts
