# Feature Specification: Ema language preference and UI language

**Feature**: `009-language-preference`  
**Created**: 2026-09-07  
**Status**: Converged  
**Branch**: `009-language-preference`  
**Depends on**: `008-single-pr-per-spec`  
**Supersedes**: open PR #6 (`009-es-progress-labels`) — folded into this broader language experience

## Summary

On every `Hola Ema` / `Hi Ema` entry, Ema checks workspace language config. If unset, welcome the user and ask **Español** or **English** (only those for now), persist to `.emaad/config.json`, then continue (boot menu). If already set, use it for all user-facing chrome.

**Technical terms** stay in their original language (usually English), with a short description in the session language in parentheses.

User-facing progress labels also follow the configured language (no Spanglish like `conjunto systems`).

## Requirements

- **FR-009-01**: Before boot menu, load `.emaad/config.json`; if `language` missing, run language gate (welcome + ES/EN only).
- **FR-009-02**: Persist choice to `.emaad/config.json` (gitignored); ship `.emaad/config.example.json`.
- **FR-009-03**: Re-check on every Ema entry; never skip the gate when unset.
- **FR-009-04**: After language is set, present boot menu and all interview chrome in that language.
- **FR-009-05**: Technical proper nouns / jargon remain in original form with `(description in session language)`.
- **FR-009-06**: Item-wise/phase progress labels use session language display names (folded from former progress-labels work).

## Acceptance

- [x] `method/language-preference.md` + boot/interview/skill wired  
- [x] config example + gitignore  
- [x] technical-term rule in questioning  
- [x] Single PR; close/supersede PR #6  

## Out of scope

More locales beyond es/en; per-project language overrides (workspace-level only for now).
