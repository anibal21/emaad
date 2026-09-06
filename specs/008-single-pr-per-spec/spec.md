# Feature Specification: One PR per Ema spec

**Feature**: `008-single-pr-per-spec`  
**Created**: 2026-09-06  
**Status**: Converged  
**Branch**: `008-single-pr-per-spec`  
**Depends on**: `006-pr-workflow-ema-trunk`, `007-inline-concepts-itemwise-sets`

## Summary

Ema Option 3 must open **exactly one Pull Request per spec increment**. Do **not** open a second “mark Converged” PR after merge. Spec status becomes **Converged** on the feature branch when acceptance criteria are met (included in that same PR). Human merge to `main` is the only approval gate.

## Problem

After 006/007 we shipped: (1) feature PR then (2) converge-stamp PR. That doubles review noise without adding product value.

## Requirements

- **FR-008-01**: `method/ema-trunk.md` forbids post-merge converge-only PRs.
- **FR-008-02**: Before requesting review, set spec + `specs/README.md` to **Converged** on the feature branch (meaning: implementation complete; awaiting merge).
- **FR-008-03**: Optional follow-up after merge is limited to `git checkout main && git pull` and deleting the local/remote feature branch—not a new PR.
- **FR-008-04**: Close obsolete open converge stamp PR #4 as superseded; include 007 Converged status in this PR if still missing on main.
- **FR-008-05**: Update CONTRIBUTING + PR template accordingly.

## Acceptance

- [x] ema-trunk / CONTRIBUTING / PR template say one PR only  
- [x] 007 marked Converged in this PR (so #4 can be closed)  
- [x] This change ships as a single PR  

## Out of scope

GitHub branch protection settings in the org UI.
