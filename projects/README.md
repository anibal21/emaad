# Projects

Client architecture design sessions live here—one folder per project.

## Layout

```text
projects/
  index.json          # Registry Ema reads for "proyecto en curso"
  <slug>/
    session-state.md
    architecture-blueprint.md
    agents/
    skills/
    ...
```

## `index.json` schema

```json
{
  "version": 1,
  "updated": "YYYY-MM-DD",
  "projects": [
    {
      "slug": "kebab-case-id",
      "name": "Human display name",
      "status": "Draft | Review | Approved | Draft / Security Incomplete",
      "ema_mode": "project_new | project_continue",
      "domain": "optional short label",
      "created": "YYYY-MM-DD",
      "updated": "YYYY-MM-DD",
      "path": "projects/kebab-case-id"
    }
  ]
}
```

Ema **must** update this file when creating a project (boot Option 1) and when status/`updated` changes on continue (Option 2).

## Note

This folder is for **design packages** produced with Ema—not for improving Ema herself (that is boot Option 3 on the repo trunk).
