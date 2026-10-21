# Source and coverage

The public-release sections were checked on **21 October 2026** against:

- [Burrow Skills at 788d634](https://github.com/GoblinKing-Burrow/Burrow-Skills/tree/788d634f61044f6048b2a8dbcb4613fe8a9d3703): four skill directories and original Tinker and Trixie artwork at `docs/assets/hero.png`.
- [Burrow at aa5a30d](https://github.com/GoblinKing-Burrow/Burrow/tree/aa5a30da683a3a8ea919025f107ff53f182ef8d6): operator UI, catalog, storage, Git import, synchronization, and explicit loading.

## Release boundary

The public runtime identifies its release as **2026.10.19**. It includes automatic adoption of the official runtime skill, but not the newer dedicated Core/mod-managed catalog. The separately labeled **forthcoming managed-skills system** describes implementation reviewed on 21 October 2026; no public release version is claimed for it here. Confirm your installed runtime and mod support before expecting that behavior.

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

## Limits of this guide

This is a code-grounded operator guide, not a claim that every described operation was exercised against a live installation. Application behavior depends on your installed release. The Backdoor skill retains earlier read-only deployment language; see the [compatibility note](library.md) before using it with a newer mod. Live schemas, permissions, and current application documentation remain authoritative.

The original artwork and skills retain the [Burrow Skills repository license](https://github.com/GoblinKing-Burrow/Burrow-Skills/blob/788d634f61044f6048b2a8dbcb4613fe8a9d3703/LICENSE). The documentation does not grant additional software or data access.
