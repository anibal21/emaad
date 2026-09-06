# EMAAD Method

This folder is the **runtime** of EMAAD. An agent loads `skills/emaad-designer`, then executes these documents in order during a design conversation.

## How to run

1. Read [`../constitution.md`](../constitution.md)
2. User says **Hola Ema** → [`boot-menu.md`](./boot-menu.md)
3. Follow [`interview-protocol.md`](./interview-protocol.md)
4. Options 1–2: walk [`phases/`](./phases/) 00 → 09 under `projects/<slug>/`
5. Option 3: [`ema-trunk.md`](./ema-trunk.md)
6. Apply decision aids and harness docs when a phase references them
7. Fill [`../templates/`](../templates/) and verify with [`../checklists/`](../checklists/)

## Document index

| Doc | Purpose |
|-----|---------|
| [boot-menu.md](./boot-menu.md) | Post-greeting options 1 / 2 / 3 |
| [ema-trunk.md](./ema-trunk.md) | Trunk-based improvements to Ema |
| [interview-protocol.md](./interview-protocol.md) | Global conversation rules |
| [architecture-decision.md](./architecture-decision.md) | Pattern selection tree |
| [primitive-taxonomy.md](./primitive-taxonomy.md) | Skills / Workflows / Agents / Scripts / MCP |
| [srp-and-boundaries.md](./srp-and-boundaries.md) | Single responsibility rules |
| [token-optimization.md](./token-optimization.md) | Context & cost strategy |
| [human-in-the-loop.md](./human-in-the-loop.md) | Approval design |
| [harness/](./harness/) | Security harness |
| [phases/](./phases/) | Phase-by-phase interview |

## Status meanings for blueprints

| Status | Meaning |
|--------|---------|
| `Draft` | Interview in progress |
| `Draft / Security Incomplete` | Synthesis attempted without harness |
| `Review` | Package complete; awaiting human acceptance |
| `Approved` | Human accepted; all gates passed or residual risks owned |
