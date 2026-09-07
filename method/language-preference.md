# Language preference (workspace)

Runs on **every** Ema entry (`Hola Ema` / `Hi Ema` / address by name), **before** the boot menu.

## Config location

| File | Role |
|------|------|
| `.emaad/config.json` | Live user config (**gitignored**) |
| `.emaad/config.example.json` | Template committed in the repo |

Schema:

```json
{
  "version": 1,
  "language": "es",
  "updated": "YYYY-MM-DD"
}
```

Allowed `language` values for now: `"es"` | `"en"`.

If the file is missing or `language` is absent/invalid → treat as **unset**.

## Gate flow

1. Load `.emaad/config.json` if present.
2. **If language set:** greet briefly in that language → go to [`boot-menu.md`](./boot-menu.md).
3. **If unset:**

```text
(es offer / bilingual welcome OK once)

¡Bienvenido/a a Ema! / Welcome to Ema!

¿En qué idioma quieres usar Ema?
1. Español
2. English

Which language do you want to use with Ema?
1. Español
2. English
```

4. Wait for a clear choice (1/2 or Español/English).
5. Write `.emaad/config.json` with the choice (create `.emaad/` if needed).
6. Confirm in the chosen language, then open the boot menu **in that language**.

Do **not** proceed to boot options 1/2/3 until language is saved.

## After preference exists

- All user-facing interview chrome (menus, progress, glosses for non-technical explanations) uses `language`.
- Session state `Language` field should match config when starting/resuming project sessions (copy from config if empty).

## Technical terms (mandatory)

Proper technical names stay in their **original language** (usually English). Add a short gloss in the session language in parentheses.

Examples when `language=es`:

- `work type` → keep classifications as needed, but say: **ReAct** (razonar → actuar → observar)
- **MCP** (Model Context Protocol; protocolo de contexto del modelo)
- **HITL** (human-in-the-loop; humano en el ciclo)
- **Pull Request** (solicitud de fusión a la rama principal)
- **skill** / **agent** / **script** — may stay as skill / agent / script with (paquete de especialización) / (agente) / (script determinista) on first use in a phase

Do **not** invent Spanish calques for proper nouns (no “Solicitud de Tirón”).

## Changing language later

If the human asks to change language (“cambia a inglés”), update `.emaad/config.json` and continue in the new language. Do not require restarting the whole method unless mid-sentence ambiguity demands a brief confirm.
