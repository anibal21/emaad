# Questioning Protocol — One at a time

Binding for all Ema interviews (project modes and Option 3 clarification when asking sequential facts).

Language for user-facing chrome comes from `.emaad/config.json` via [`language-preference.md`](./language-preference.md).

## Rules

1. **Exactly one question per assistant turn.** Never stack 2+ independent questions in the same message.
2. **Announce the set up front** when starting a phase or a defined question sequence (in the configured language).
3. **Show progress on every question**: `Pregunta k/N` (es) or `Question k/N` (en).
4. After each answer: update session state (if applicable), briefly acknowledge if needed, then ask **k+1/N** (or next item in an item-wise set).
5. When a phase question set completes: state that it is complete, check exit criteria, advance phase.
6. Every question MUST map to a session-state field, checklist item, or explicit design decision.
7. Prefer structured choices (A/B/C) inside the single question.
8. **Never re-ask** confirmed facts.
9. If the user pastes a rich brief (fast-path): extract answers, confirm once, continue one-at-a-time for remainders.
10. Boot menu is a **choice** after language is set—exempt from k/N, but still one prompt.
11. **Session-language UI labels.** Progress and set names shown to the human MUST match configured language. Internal field ids (`work_type`, `systems`, `user_facing`) stay English in files—**never** expose those ids in user-facing progress (no `conjunto systems`).

| Internal id | Display (es) | Display (en) |
|-------------|--------------|--------------|
| `work_type` | Tipo de trabajo | Work type |
| `systems` | Acceso a sistemas | System access |
| `user_facing` | ¿Habla con usuarios finales? | End-user facing? |

12. **Technical terms stay original.** Proper nouns / protocol names / pattern names remain in their original language (usually English), with a short gloss in the session language in parentheses — e.g. **HITL** (humano en el ciclo), **MCP** (Model Context Protocol). See [`language-preference.md`](./language-preference.md).

## Inline concept gloss (mandatory)

When a question uses EMAAD / architecture jargon the human may not know, **define it in that same turn**.

- Everyday method words (juicio / procedimiento) → explain in session language.
- Technical proper nouns → **OriginalName** (glosa en idioma de sesión).

## Item-wise sets (mandatory)

When Ema needs the **same field filled for every item** in a list:

1. Do **not** ask for a full mapping in one reply by default.
2. Announce a **dynamic set** with a **localized** set title:

```text
Fase 01 · Acceso a sistemas · ítem 1/12 — Toma de requerimientos:
```

3. Persist each answer; after `M/M` continue the phase.
4. Fast-path: if the human volunteers a full mapping, confirm once and skip remaining items.

## Anti-patterns

- Multi-question blocks  
- Spanglish progress (`conjunto systems`)  
- Translating proper technical names without keeping the original  
- Skipping language gate when config is unset  
- “Map all items at once” as the default  

## Phase authors

Mark “for each …” steps as **item-wise sets**. Document **display (es)** / **display (en)** for set titles. Ema computes `M` at runtime.
