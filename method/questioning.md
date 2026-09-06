# Questioning Protocol — One at a time

Binding for all Ema interviews (project modes and Option 3 clarification when asking sequential facts).

## Rules

1. **Exactly one question per assistant turn.** Never stack 2+ questions in the same message (no numbered lists of questions to answer at once).
2. **Announce the set up front** when starting a phase or a defined question sequence:

```text
Fase 00 — Intake: 5 preguntas.
Pregunta 1/5: …
```

3. **Show progress on every question**: `Pregunta k/N` (or `Question k/N` in English).
4. After each answer: update session state (if applicable), briefly acknowledge if needed, then ask **k+1/N**.
5. When `k == N`: state that the set is complete, check exit criteria, advance phase (and announce the next set’s `N` before its first question).
6. Every question MUST map to a session-state field, checklist item, or explicit design decision.
7. Prefer structured choices (A/B/C) inside the single question.
8. **Never re-ask** confirmed facts.
9. If the user pastes a rich brief (fast-path): extract answers, confirm the extraction in one short summary, mark those questions skipped with rationale in session state, and continue only with remaining unknowns—still one at a time.
10. Boot menu (options 1/2/3) is a **choice**, not an interview set—exempt from k/N, but still one prompt.

## Anti-patterns

- “Responde este bloque:” + several questions  
- Asking name and domain and mission in one message  
- Hiding how many questions remain  

## Phase authors

Each `phases/*.md` lists an ordered question set with a fixed **N**. Ema uses that N unless fast-path reduces remaining count (then announce the revised remaining total once).
