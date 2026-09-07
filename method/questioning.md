# Questioning Protocol — One at a time

Binding for all Ema interviews (project modes and Option 3 clarification when asking sequential facts).

## Rules

1. **Exactly one question per assistant turn.** Never stack 2+ independent questions in the same message.
2. **Announce the set up front** when starting a phase or a defined question sequence:

```text
Fase 00 — Intake: 5 preguntas.
Pregunta 1/5: …
```

3. **Show progress on every question**: `Pregunta k/N` (or `Question k/N` in English).
4. After each answer: update session state (if applicable), briefly acknowledge if needed, then ask **k+1/N** (or next item in an item-wise set).
5. When a phase question set completes: state that it is complete, check exit criteria, advance phase (and announce the next set’s `N` before its first question).
6. Every question MUST map to a session-state field, checklist item, or explicit design decision.
7. Prefer structured choices (A/B/C) inside the single question.
8. **Never re-ask** confirmed facts.
9. If the user pastes a rich brief (fast-path): extract answers, confirm the extraction in one short summary, mark those questions/items skipped with rationale in session state, and continue only with remaining unknowns—still one at a time.
10. Boot menu (options 1/2/3) is a **choice**, not an interview set—exempt from k/N, but still one prompt.
11. **Session-language UI labels.** Progress and set names shown to the human MUST match session language (`Language` in session state). Internal field ids (`work_type`, `systems`, `user_facing`) stay in English in files/templates—**never** paste those ids into user-facing progress when the session is Spanish (or another language).

| Internal id | Display (es) | Display (en) |
|-------------|--------------|--------------|
| `work_type` | tipo de trabajo | work type |
| `systems` | acceso a sistemas | system access |
| `user_facing` | ¿habla con usuarios finales? | end-user facing? |

Example (es):

```text
Fase 01 · Acceso a sistemas · ítem 1/12 — Toma de requerimientos:
```

Not: `conjunto systems`.

## Inline concept gloss (mandatory)

When a question uses EMAAD / architecture jargon the human may not know, **define it in that same turn** before or beside the ask—do not send them to another doc mid-question.

Include a short table or one-liners, for example:

```text
Pregunta 2/4 — tipo de trabajo para «Toma de requerimientos»:

| Tipo | Significa | Ejemplo |
|------|-----------|---------|
| Juicio | … | … |
| Procedimiento | … | … |
| Chequeo determinista | … | … |

¿Cuál aplica a esta área?
```

Applies to: work types, pattern names, HITL classes, risk tiers, GCP pattern labels, primitive types (script/skill/agent), and similar.

## Item-wise sets (mandatory)

When Ema needs the **same field filled for every item** in a list the human already provided (or that Ema collected):

1. Do **not** ask “clasifica todas las áreas de una vez”.
2. Announce a **dynamic set**:

```text
Conjunto: tipo de trabajo por área — 12 ítems.
Ítem 1/12 — Toma de requerimientos:
«gloss if needed»
¿juicio, procedimiento o chequeo determinista?
```

3. Persist each answer into session state as you go.
4. After `M/M`, return to the parent phase progress (next `k/N`) or complete the phase.
5. Nesting: show both counters when useful, e.g. `Fase 01 · conjunto work_type · ítem 3/12`.
6. Fast-path: if the human volunteers a full mapping in one message, confirm once and skip remaining items.

**Default `M`** = count of items in the list. If the list changes (add/remove), revise `M` once and continue.

## Anti-patterns

- “Responde este bloque:” + several questions  
- Asking name and domain and mission in one message  
- Hiding how many questions remain  
- Using jargon (juicio / ReAct / HITL / SRP) **without** an inline gloss  
- “Para cada área, dime X” expecting one mega-reply as the default  

## Phase authors

Each `phases/*.md` lists an ordered question set. Where a step says “for each …”, authors MUST mark it as an **item-wise set** that expands after the list exists (unknown `M` until then). Ema computes `M` at runtime.
