# Boot Menu — After "Hola Ema"

Canonical first interaction. Do **not** jump into phase 00 until the human picks a mode.

## Present exactly these options

Match the user's language. Spanish default when the greeting is `Hola Ema`:

```text
¿Qué quieres hacer?

1. Trabajar en un nuevo proyecto
2. Trabajar en un proyecto en curso
3. Trabajar en mejoras de Ema
```

English if they greeted with `Hi Ema` / `Hello Ema`:

```text
What do you want to do?

1. Work on a new project
2. Continue an existing project
3. Work on improvements to Ema
```

Wait for a clear choice (number or paraphrase). Do not invent a fourth default path.

---

## Option 1 — Nuevo proyecto

1. Ask for **display name** and propose a **slug** (`kebab-case`, unique).
2. Confirm path: `projects/<slug>/`.
3. Create the folder and seed from templates:
   - `session-state.md`
   - (other cards later as phases progress)
4. **Update** `projects/index.json` immediately (append entry; bump `updated`).
5. Set session field `ema_mode: project_new`.
6. Continue with [`phases/00-intake.md`](./phases/00-intake.md) (greenfield lean; skip "which project" questions).

### Index entry shape

```json
{
  "slug": "acme-support",
  "name": "Acme Support",
  "status": "Draft",
  "ema_mode": "project_new",
  "domain": "",
  "created": "2026-09-06",
  "updated": "2026-09-06",
  "path": "projects/acme-support"
}
```

If `projects/index.json` is missing, create it by copying `projects/index.example.json`.

---

## Option 2 — Proyecto en curso

1. Read `projects/index.json`.
2. If empty: say so and offer Option 1.
3. List projects by **name** (and slug/status) for easy selection.
4. On choice: load `projects/<slug>/session-state.md` (and blueprint if present).
5. Set `ema_mode: project_continue`.
6. Summarize last phase / status; ask where to resume (or continue from recorded phase).
7. On meaningful progress, refresh `updated` + `status` in the index.

Never invent projects that are not in the index. If a folder exists but is missing from the index, offer to **register** it (add index entry) before continuing.

---

## Option 3 — Mejoras de Ema

1. Set `ema_mode: ema_improve`. Do **not** create a client project folder.
2. Follow [`ema-trunk.md`](./ema-trunk.md): trunk-based work on the designer itself (`main`).
3. Clarify what to improve (method, skill, harness, templates, docs, examples).
4. Apply SDD: update `specs/` when the *what* changes; then method/skill/templates; keep constitution in sync.
5. Version with Git commits on `main` (or short-lived PR branches that merge fast to `main`—no long-lived feature branches as the default model).
6. Do not write client architecture packages under `projects/` unless the improvement is an example under `examples/`.

---

## Hard rules

- Boot menu is mandatory after Hola Ema (unless already mid-session with clear context to resume Option 2/3).
- Project artifacts live under `projects/<slug>/`, never under a loose `sessions/` path.
- `projects/index.json` is the source of truth for Option 2 listings.
- Option 3 changes are designer product changes and must be committed when the human asks to version (or when they confirm a change set is done).
