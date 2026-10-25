# Source and coverage

The historical public-release sections were checked on **21 October 2026** against:

- [Burrow Skills at 788d634](https://github.com/GoblinKing-Burrow/Burrow-Skills/tree/788d634f61044f6048b2a8dbcb4613fe8a9d3703): four skill directories and original Tinker and Trixie artwork at `docs/assets/hero.png`.
- [Burrow at aa5a30d](https://github.com/GoblinKing-Burrow/Burrow/tree/aa5a30da683a3a8ea919025f107ff53f182ef8d6): operator UI, catalog, storage, Git import, synchronization, and explicit loading.

## Release boundary

The historical public snapshot identifies itself as **2026.10.19**. It includes automatic adoption of the runtime skill, but not the dedicated Core/mod-managed catalog. Current implementation was rechecked **25 October 2026** against Core `3bf50374d3601c821e787912d52b9044eaf649ec`, UI `0610bac85b2e636b79bbdf09fc3a95c3a519fa5a`, and skill-library `b81616ef9c8168d7fe9dcc8bd8e244149401fcc7`.

The managed catalog is implemented: `managed-skills.mjs` reconciles Core plus loaded-mod declarations, records revision/content metadata and removes no-longer-desired managed copies after successful reconciliation. The current UI displays managed skill versions in mod inventory. This is a source review, not a live fetch test or a claim that an installed older runtime has upgraded. The public links below remain historical evidence rather than current-HEAD claims.

## Implementation map

| Behavior | Public source |
| --- | --- |
| Text creation, local file loading, assignments, lifecycle, deletion | [SkillsSettings.tsx](https://github.com/GoblinKing-Burrow/Burrow/blob/aa5a30da683a3a8ea919025f107ff53f182ef8d6/ui/src/features/settings/SkillsSettings.tsx) |
| Preview and install | [SkillRepositoryImport.tsx](https://github.com/GoblinKing-Burrow/Burrow/blob/aa5a30da683a3a8ea919025f107ff53f182ef8d6/ui/src/features/settings/SkillRepositoryImport.tsx) |
| Git source controls and status | [SkillSourceSettings.tsx](https://github.com/GoblinKing-Burrow/Burrow/blob/aa5a30da683a3a8ea919025f107ff53f182ef8d6/ui/src/features/settings/SkillSourceSettings.tsx) |
| Supported Git transports, paths, package validation | [git-skill-fetch.mjs](https://github.com/GoblinKing-Burrow/Burrow/blob/aa5a30da683a3a8ea919025f107ff53f182ef8d6/backend/src/git-skill-fetch.mjs) |
| Revision checks, publication, failures, local-change detection | [skill-git-sync.mjs](https://github.com/GoblinKing-Burrow/Burrow/blob/aa5a30da683a3a8ea919025f107ff53f182ef8d6/backend/src/skill-git-sync.mjs) |
| Ownership, assignment storage, bundled publication | [postgres-skill-settings-store.mjs](https://github.com/GoblinKing-Burrow/Burrow/blob/aa5a30da683a3a8ea919025f107ff53f182ef8d6/backend/src/postgres-skill-settings-store.mjs) |
| Source persistence and text detachment | [postgres-skill-sources.mjs](https://github.com/GoblinKing-Burrow/Burrow/blob/aa5a30da683a3a8ea919025f107ff53f182ef8d6/backend/src/postgres-skill-sources.mjs) |
| Catalog precedence and availability | [skill-catalog.mjs](https://github.com/GoblinKing-Burrow/Burrow/blob/aa5a30da683a3a8ea919025f107ff53f182ef8d6/backend/src/skill-catalog.mjs) |
| Explicit list and load | [skill-tool-executor.mjs](https://github.com/GoblinKing-Burrow/Burrow/blob/aa5a30da683a3a8ea919025f107ff53f182ef8d6/backend/src/skill-tool-executor.mjs) |
| No automatic planner selection of full skill bodies | [prompt-skill-selection.mjs](https://github.com/GoblinKing-Burrow/Burrow/blob/aa5a30da683a3a8ea919025f107ff53f182ef8d6/backend/src/prompt-skill-selection.mjs) |

## Operating-skill reconciliation

The review began from the instruction content published at `788d634` (the runtime instruction body dates to 11 October and is unchanged in the earlier public `a993f80` snapshot). Each skill was compared with the current implementation, rather than restricting the review to recent commits. The guide pages introduced at `aba373f` were reviewed in the same pass.

- Runtime: operator-timezone scheduling, native memory/tool contracts, Git sync failure handling, and release-dependent managed ownership.
- Backdoor: [system-mod tool definitions at 381b6f5](https://github.com/GoblinKing-Burrow/Burrow-Backdoor/blob/381b6f50e545063e2a4434c1f56658f8b7d6d7f0/src/mod.mjs), scoped diagnostics, and durable Core mod-management receipts.
- Node Goblin: remote execution remains separate from home-Burrow access; Backdoor supplies the companion path.
- GSS: assigned-record discovery, protected references, caller binding, and revocation were rechecked; no instruction change was needed.

Instruction files do not carry a complete historical source-version matrix. Their Git history establishes the content baseline; it does not prove which runtime release every earlier sentence was tested against. Current source links are in the [library](library.md).

## Limits of this guide

This is a code-grounded operator guide, not a claim that every described operation was exercised against a live installation. Application behavior depends on your installed release. The operating skills were reconciled with the public runtime and current mod implementations on 21 October 2026. Backdoor guidance now covers the system mod’s diagnostics and administrative operations; see the [compatibility note](library.md). Live schemas, permissions, and current application documentation remain authoritative.

The original artwork and skills retain the [Burrow Skills repository license](https://github.com/GoblinKing-Burrow/Burrow-Skills/blob/788d634f61044f6048b2a8dbcb4613fe8a9d3703/LICENSE). The documentation does not grant additional software or data access.
