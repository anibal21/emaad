# Phase 01 — Domain Map

## Purpose

Decompose the problem into capability domains and work types (judgment vs deterministic), then note systems access and user-facing flags.

## Question set

Follow [`../questioning.md`](../questioning.md) — including **inline gloss**, **item-wise sets**, and **session-language labels**.

### Greenfield

Announce at start (es): `Fase 01 — Mapa de dominios` (1 lista + 3 conjuntos ítem a ítem; M = nº de áreas).

| Step | Kind | Internal id | Display (es) | Ask |
|------|------|-------------|--------------|-----|
| A | Phase question | — | Lista de áreas | List the major capability areas (about 5–12 bullets). |
| B | Item-wise set | `work_type` | **Tipo de trabajo** | For each area: juicio / procedimiento / chequeo determinista (+ gloss). |
| C | Item-wise set | `systems` | **Acceso a sistemas** | For each area: ¿necesita conectarse a sistemas en vivo (APIs, repos, tickets, ERP, navegador, etc.)? Si sí, ¿cuáles? |
| D | Item-wise set | `user_facing` | **¿Habla con usuarios finales?** | For each area: yes/no (cliente u otros usuarios finales, no solo el operador Tech Lead). |

Progress example (es):

```text
Fase 01 · Acceso a sistemas · ítem 1/12 — Toma de requerimientos:

¿Esta área necesita conectarse a sistemas en vivo?
| Opción | Significa |
| Sí | Lee/escribe APIs, repos, tickets, ERP, etc. |
| No | Solo conversación / docs locales |

Responde sí o no (si sí, nombra los sistemas).
```

### Brownfield

Same as greenfield, then:

| Step | Kind | Ask |
|------|------|-----|
| E | Phase question | Inventory current agents, skills, workflows, scripts, MCP servers and known pain points. |

## Produce

- Domain table: `domain | work_type | systems | user_facing | notes`  
- Brownfield inventory + pain list (if applicable)  

## Exit criteria

- Domain table complete for all listed areas  
- Clear candidates for scripts vs skills vs agents  

## Next

Phase 02 Constraints
