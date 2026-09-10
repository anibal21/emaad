# Feature Specification: Self-explanatory interview questions

**Feature**: `011-self-explanatory-questions`  
**Created**: 2026-09-09  
**Status**: Converged  
**Branch**: `011-self-explanatory-questions`  
**Depends on**: `007-inline-concepts-itemwise-sets`, `009-language-preference`, `010-itemwise-skill-cards`

## Summary

Ema must **not assume** the human already knows method vocabulary (`workflow`, `skill`, `handoff`, `HITL`, `operator_invocable`, progress labels, etc.). Every question is **self-explanatory in that turn**: short definition + concrete example + then the ask. “Inline gloss” is mandatory for any non-everyday term, including EMAAD method words—not only rare architecture jargon.

## Requirements

- **FR-011-01**: Before asking the human to choose/confirm a method concept, Ema defines it in the **same message** in the session language (or OriginalName + gloss for technical proper nouns).
- **FR-011-02**: Prefer **example-first** when the term is structural (skill vs workflow, handoff, blast radius, etc.): one plain-language sentence + one micro-example, then the question.
- **FR-011-03**: Phase Ask tables and templates that introduce field names (e.g. Phase 05 `workflows`) MUST instruct Ema to gloss that field on first use in the set (and again if the human asks what it means).
- **FR-011-04**: Anti-pattern: questions that only make sense if the reader already knows EMAAD (`¿Al menos un workflow?` with no definition).
- **FR-011-05**: If the human says they do not understand, restate with a simpler gloss and **re-ask the same field**—do not skip or stack new topics.

## Acceptance

- [x] Spec 011 + plan/tasks  
- [x] `method/questioning.md` self-explanatory rule + anti-patterns  
- [x] `interview-protocol.md` + Phase 05 + designer skill pointer  
- [x] `specs/README.md` indexes 011  
- [x] Single PR to `main`

## Out of scope

Changing one-question-per-turn; adding new locales; auto-generated glossary UI outside chat.
