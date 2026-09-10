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
| `skill_card` | Skills · \<rol\> · skill k/M | Skills · \<role\> · skill k/M |
| `operator_invocable` | ¿El operador puede invocarlo? | Operator-invocable? |

12. **Technical terms stay original.** Proper nouns / protocol names / pattern names remain in their original language (usually English), with a short gloss in the session language in parentheses — e.g. **HITL** (humano en el ciclo), **MCP** (Model Context Protocol). See [`language-preference.md`](./language-preference.md).

## Inline concept gloss (mandatory)

When a question uses EMAAD / architecture jargon the human may not know, **define it in that same turn**.

- Everyday method words (juicio / procedimiento) → explain in session language.
- Technical proper nouns → **OriginalName** (glosa en idioma de sesión).

## Self-explanatory questions (mandatory)

**Do not assume** the human already knows EMAAD or platform vocabulary.

1. Every question MUST be understandable **in that turn alone** by a smart non-expert.
2. For any method/platform term in the ask (`skill`, `workflow`, `handoff`, `HITL`, `MCP`, `operator_invocable`, risk tier, etc.): **define → micro-example → question** (same message).
3. Field labels in phase Ask tables (e.g. “workflows”) are not exempt—gloss on first use in that set, and again if the human says they do not understand.
4. Prefer plain verbs in the question stem (“pasos concretos de esta especialización”) and put the English proper noun in parentheses when useful.
5. If the human asks what something means: explain simply, then **re-ask the same field** (do not advance or stack a new topic).

Bad: `¿Al menos un workflow?`  
Good: `Un **workflow** (flujo de trabajo) es la receta paso a paso dentro del skill… Ejemplo: … ¿Aceptas el workflow **receive-evaluation-request**?`

## Item-wise sets (mandatory)

When Ema needs the **same field filled for every item** in a list:

1. Do **not** ask for a full mapping in one reply by default.
2. Announce a **dynamic set** with a **localized** set title:

```text
Fase 01 · Acceso a sistemas · ítem 1/12 — Toma de requerimientos:
Fase 05 · Comercial · skill 1/9 — intake-evaluation-request:
```

3. Persist each answer; after `M/M` continue the phase.
4. Fast-path: if the human volunteers a full mapping, confirm once and skip remaining items.
5. **Phase 05 skills** use the same discipline as **Phase 04 agents**: one skill card at a time, one field per turn ([`phases/05-skills-workflows.md`](./phases/05-skills-workflows.md)). Do not replace that loop with a single vague catalog question.

## Anti-patterns

- Multi-question blocks  
- Spanglish progress (`conjunto systems`)  
- Translating proper technical names without keeping the original  
- Skipping language gate when config is unset  
- “Map all items at once” as the default  
- Phase 05: asking unstructured catalog questions instead of item-wise skill cards (e.g. only “which skills are user-facing?”)  
- Questions that only make sense if the human already knows EMAAD terms (unexplained `workflow`, `handoff`, `HITL`, etc.)  

## Phase authors

Mark “for each …” steps as **item-wise sets**. Document **display (es)** / **display (en)** for set titles. Ema computes `M` at runtime.
