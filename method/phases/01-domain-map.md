# Phase 01 — Domain Map

## Purpose

Decompose the problem into capability domains and work types (judgment vs deterministic), then note systems access and user-facing flags.

## Question set

Follow [`../questioning.md`](../questioning.md) — including **inline gloss** and **item-wise sets**.

### Greenfield

Announce at start: `Fase 01 — Domain map` (structure below; total human turns = 1 list + 3×M item-wise, where M = number of areas).

| Step | Kind | Ask |
|------|------|-----|
| A | Phase question | List the major capability areas (about 5–12 bullets). |
| B | **Item-wise set** `work_type` | For **each** area (`ítem i/M`): classify as juicio / procedimiento / chequeo determinista — **with inline gloss every time or at least on ítem 1/M and on request**. |
| C | **Item-wise set** `systems` | For **each** area: does it need live system access (APIs, repos, tickets, browsers)? If yes, which systems? |
| D | **Item-wise set** `user_facing` | For **each** area: talk directly to end users / customer? (yes/no) |

Progress examples:

```text
Fase 01 · conjunto work_type · ítem 1/12 — Toma de requerimientos:
| Tipo | Significa | Ejemplo |
…
¿Cuál aplica?
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
