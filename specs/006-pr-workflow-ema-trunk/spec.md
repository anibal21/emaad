# Feature Specification: PR workflow for Ema trunk updates

**Feature**: `006-pr-workflow-ema-trunk`  
**Created**: 2026-09-06  
**Status**: Active  
**Branch**: `006-pr-workflow-ema-trunk`  
**Depends on**: `005-sdd-spec-numbering`

## Summary

Ema product changes (Option 3) MUST NOT land as direct commits to `main` by default. Each spec increment uses a **short-lived feature branch**, push, and **Pull Request into `main`**. Work on the next feature starts only after the human **approves and merges** the PR.

This is trunk-based development with **PR gates**: `main` stays the trunk; branches are short-lived and merge via review.

## User stories

1. **As maintainer**, when improving Ema I get a branch + PR per spec so I can review before it becomes truth on `main`.  
2. **As Ema (agent)**, I never treat “commit on main” as the default delivery path for Option 3.

## Requirements

- **FR-006-01**: For Option 3, create branch named `00N-short-slug` (match spec folder) from latest `main`.
- **FR-006-02**: Commit implementation only on that branch; push with `-u`; open PR targeting `main` via `gh pr create`.
- **FR-006-03**: Do not start the next Ema feature branch until the previous PR is merged (unless the human explicitly allows parallel work).
- **FR-006-04**: After merge, agent checks out `main`, pulls, then may open `00N+1`.
- **FR-006-05**: Document workflow in `method/ema-trunk.md`, CONTRIBUTING, specs/README, skill Option 3 notes.
- **FR-006-06**: Provide a GitHub PR template for Ema/spec changes.

## Non-goals

- Requiring protected-branch rules in GitHub settings (recommend, don’t automate org settings here)
- Long-lived release branches
- Changing client project (Options 1–2) flows

## Acceptance

- [ ] `ema-trunk.md` describes branch → PR → approve → merge → next from main  
- [ ] CONTRIBUTING / specs README / skill aligned  
- [ ] `.github/PULL_REQUEST_TEMPLATE.md` present  
- [ ] This change itself delivered as a PR (not a direct main commit)

## Clarifications

- Human may still say “commit on main” as an explicit override for emergencies; default is PR.
- Backfilled history (001–005) may have been direct-to-main; this spec governs **forward** work.
