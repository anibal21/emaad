# Plan: 006-pr-workflow-ema-trunk

## Approach

Update Option 3 trunk docs to mandate short-lived branches + GitHub PRs. Ship this change on branch `006-pr-workflow-ema-trunk` and open a PR to demonstrate the workflow.

## Implementation steps

1. Rewrite `method/ema-trunk.md`  
2. Update CONTRIBUTING, `specs/README.md`, constitution naming if needed, skill Option 3  
3. Add `.github/PULL_REQUEST_TEMPLATE.md`  
4. Push branch + `gh pr create`  

## Test plan

- [ ] PR exists against `main` with template sections filled  
- [ ] Docs state “wait for merge before next feature”  
- [ ] After approval/merge, next work starts from updated `main`
