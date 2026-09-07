# Phase 01 — Domain Map

## Purpose

Decompose the problem into capability domains and work types (judgment vs deterministic), then note systems access and user-facing flags.

## Question set

Follow [`../questioning.md`](../questioning.md) and [`../language-preference.md`](../language-preference.md).

### Greenfield

Announce (es): `Fase 01 — Mapa de dominios` · (en): `Phase 01 — Domain map`.

| Step | Kind | Internal id | Display (es) | Display (en) | Ask |
|------|------|-------------|--------------|--------------|-----|
| A | Phase question | — | Lista de áreas | Capability list | List major capability areas (≈5–12). |
| B | Item-wise | `work_type` | Tipo de trabajo | Work type | juicio / procedimiento / chequeo determinista (+ gloss). |
| C | Item-wise | `systems` | Acceso a sistemas | System access | Live systems needed? If yes, which? |
| D | Item-wise | `user_facing` | ¿Habla con usuarios finales? | End-user facing? | yes/no |

Progress example (es):

```text
Fase 01 · Acceso a sistemas · ítem 1/12 — Toma de requerimientos:

¿Esta área necesita conectarse a sistemas en vivo?
| Opción | Significa |
| Sí | APIs, repos, tickets, ERP, navegador, etc. |
| No | Solo conversación / docs locales |

¿Sí o no? (si sí, nombra los sistemas)
```

### Brownfield

Same as greenfield, then inventory of current agents/skills/MCP + pain points.

## Produce

- Domain table: `domain | work_type | systems | user_facing | notes`

## Exit criteria

- Domain table complete for all listed areas  

## Next

Phase 02 Constraints
