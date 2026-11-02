# Source and coverage

The historical public-release sections were checked on **21 October 2026** against:

- [Burrow Skills at 788d634](https://github.com/GoblinKing-Burrow/Burrow-Skills/tree/788d634f61044f6048b2a8dbcb4613fe8a9d3703): four skill directories and original Tinker and Trixie artwork at `docs/assets/hero.png`.
- [Burrow at aa5a30d](https://github.com/GoblinKing-Burrow/Burrow/tree/aa5a30da683a3a8ea919025f107ff53f182ef8d6): operator UI, catalog, storage, Git import, synchronization, and explicit loading.

## Full reconciliation — 1 November 2026

All nine guides and six existing instruction payloads were reviewed against current implementation: skill library `1f464f48b651a78c3c90599ffee674a627cf67e3`, Core `8b5889115680bcdbf698f1b93126254e1cf4d2e6`, UI `e6d3fe7b17da1c68d380f1e28482fd9c5819cdef`, assembly `fe851c4e546c9bf9f53f861e24f918474432c296`, Backdoor `b03239d3cae16a5b6f7cfd5174cf7bb88cdff01a`, Node Goblin `120d19f576c4b3c496bc7b91e0e485f7634df73c`, and GSS `a80eef571c775a8b98891684811c669f34881d95`. These pins identify reviewed source, not installed or publicly promoted versions.

Runtime instructions in all three owning copies now cover one-time scheduling and assigned-ToDo task jobs, saved extra instructions, skipped targets and one-time consumption. Node Goblin instructions now use the supported update-and-restart path rather than implying that start/connect restarts an existing daemon. Backdoor and GSS instruction contracts remain current. No frontmatter version was changed. Static checks cover frontmatter, hashes, instruction-body alignment, named tool registrations and reference paths; no skill scripts, application tests or external chat calls were executed.

The full review includes optional Git import/preview and ownership, assignments/lifecycle, source sync/recovery, managed-catalog declaration/refresh/precedence, explicit loading and all companion instruction boundaries. Other documented components contain no additional `SKILL.md` payloads at the reviewed heads.

## Historical ordinary maintenance — 31 October 2026

The six existing instruction payloads retain their previously reviewed bytes: four in the skill library and one bundled runtime copy each in Core and the assembly. No skill metadata/version was changed. Skill-library head `078031793d93118e463c0c780feefa3dd109e257` and Backdoor head `cfc215e7f71594a2f5d6f3d34e165ea37ebce113` are unchanged from the previous documentation receipts.

This pass rechecked managed source selection, startup/lifecycle/periodic refresh, installed metadata, catalog ownership and explicit load semantics against Core `8275b6bedf1fcd969fb5289cf0b673a80ddc8146`. Assembly `203c3ed2d634680bb98a6e04bb75247cd9b3e2c2` contains the public skill version stamping and readiness validation described in [managed skills](managed-skills.md). These are current implementation pins, not proof of a public promotion or an installed instance's refresh.

The guides now distinguish ordinary library controls from managed operating skills, explain the three Mods version values and revision/hash freshness checks, and avoid using a managed companion ID as the optional-import example. Native peer discovery and A2A remain separate from Backdoor diagnostics. Non-executing checks cover six frontmatter blocks, relative references, unchanged payload hashes, identical runtime instruction bodies and Backdoor's named tool registrations. No application tests, skill execution or external chat calls were run; unchanged source retains the previous dated review.

## Instruction maintenance baseline — 30 October 2026

The first explicit nightly skill-text inventory found four instruction payloads in the skill library and two additional copies of the runtime skill in Core and the assembled Burrow source. The other documented component/mod repositories contain no `SKILL.md` payloads at the inspected heads. The inventory records file hashes separately from package versions; no application or skill version was bumped for documentation maintenance.

Current source pins are skill library `9bb95549b00429f99ccdaf30c804134ee4418738`, Core `bea2171508d1821440ed5c554a688768848699c9`, assembly `23bf37de7a7353732005123c3c44b7f2822463bb`, Backdoor `a8c40cd0210be6c5db734a0b5af9c0d39700d182`, Node Goblin `1fa350d02469f3b9ab126afe3d1bb1606cde0599`, and GSS `58290bcf92459f6e215e19fe9dad954aad712a63`.

Backdoor's existing instruction text already describes the 35-tool implementation, independent full-API grant, arguments, full response formats, native A2A separation and durable lifecycle preference. Its library summary and managed-import guidance were stale and are corrected. Runtime instructions now explain the implemented minion-depth boundary and A2A reply-cycle response; all three runtime copies remain aligned. GSS and Node Goblin instructions retain their current text after basic schema/CLI checks. Validation checks instruction frontmatter, references and source names without executing skills or contacting external chat services. This ordinary pass does not claim a full runtime test or exhaustive review of unchanged source.

## Native A2A instruction delta — 29 October 2026

Skill-library commit `c56400e5ccbf2af74e94e52ec9b08fb4a48fab76` updates runtime and Backdoor instructions to prefer native peer messaging and discovery, without diagnostic prerequisites. This ordinary delta review does not re-certify unchanged instructions or prove availability on an older installed runtime. No application tests or live messages were run.

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

