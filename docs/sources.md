# Source and coverage

The historical public-release sections were checked on **21 October 2026** against:

- [Burrow Skills at 788d634](https://github.com/GoblinKing-Burrow/Burrow-Skills/tree/788d634f61044f6048b2a8dbcb4613fe8a9d3703): four skill directories and original Tinker and Trixie artwork at `docs/assets/hero.png`.
- [Burrow at aa5a30d](https://github.com/GoblinKing-Burrow/Burrow/tree/aa5a30da683a3a8ea919025f107ff53f182ef8d6): operator UI, catalog, storage, Git import, synchronization, and explicit loading.

## Ordinary maintenance — 9 November 2026

This Monday delta starts from the 8 November full-review receipt. Inspected library `afd9ce8dc4faaa45d1b3abf1c51b93b3e9e69c96`, Core `a799735c9b0d7fbdeb49dcebfc7acb798356d476`, assembly `20523845840bb4763e0fe137d603a7f54d8c5a9d`, Backdoor `2a457afee7fee6836c9723af01b845a2cd56721c`, and Menagerie `2698696aaa336bb1507bedf275f62a43f891a8e5`. All eight existing instruction payloads were inspected; no instruction or frontmatter/version edits were needed. The three runtime bodies remain identical. Menagerie's repository companion and the expanded library guidance differ in conversational detail but retain compatible native A2A, recipient discovery and tool-authority contracts.

Backdoor source and skill text are unchanged since the full review: 35 tool names and argument tables, 22 named skill references, native A2A separation and the full API request example remain consistent. This delta does not re-certify unchanged runtime behavior. The Menagerie library's updated visit guidance is reflected in the library guide without changing resident identities or operator instructions.

Assembly `scripts/promotion/stage-snapshots.mjs` now includes all five official skills in `PUBLIC_SKILL_IDS`, snapshot paths and version stamping. The public `burrow-menagerie/SKILL.md` contents request still returned 404 during this review; the source fix is not evidence of public publication or installation sync. Managed instructions continue to follow the declared public source. No release, managed refresh or installed-state operation was performed.

Checks cover static instruction structure, source names and relative references. No application tests, skill scripts, provider calls, runtime behavior, permissions, credentials, agent identities or operator-specific instructions were changed or executed. The last full reconciliation remains 8 November.

## Sunday full reconciliation — 8 November 2026

Reviewed all eight existing instruction payloads across eleven documented source repositories: five library skills, two bundled runtime copies, and Menagerie's companion copy. Pins: skill library `b9fe974a5c831b23565c567385a4cad3d1b545c1`, Core `6b682eae6cd0dc6efa79e173b7d819fb219443b3`, assembly `1f77c9d0277585bfe1963ce3ab3d2cdf35f16b9a`, Backdoor `30b183a9e8b38b9cea4cef9c308fa39fe759e941`, Node Goblin `c8181bf1adcf5f7b445b8a59383f4690cd92c7b7`, GSS `6c3175d528fdb0ceb77a4f7a5cb71ac8b5b10945`, and Menagerie `bf8d002f32dc04753b167359b7268a9547151af8`.

The three runtime instruction bodies now describe cross-chat Forge image references and the non-executable/non-schedulable Parked task state. Evidence is Core's `action-proposal.mjs`, `forge-artifact-reference.mjs`, `task-board-store.mjs` and task-execution preflight. Full static reconciliation also covered native A2A discovery/routing/replies, scheduler scope, explicit skill loading, managed ownership and synchronization, continuity, protected bindings and Forge delivery. The nine library guides were reviewed against current import, catalog, synchronizer and operator-UI contracts.

Backdoor retains 35 registered tools; names, argument tables, required fields, discovery, full API request example and native A2A separation agree with current implementation. GSS's three assigned-record tool schemas and caller/version-bound reference consumption, Node Goblin's configure/connect/apply/pair/update/uninstall distinctions, and Menagerie's parent-visit scope and participant-authored tool rules remain consistent with their existing skills. These five non-runtime payloads are unchanged. The public Menagerie skill path still returned 404 at review; development publication is not proof of public promotion or installed delivery.

Checks are non-executing text/structure and source-reference checks, not application tests, skill-script execution or live runtime certification. Skill frontmatter/version metadata, runtime permissions, credentials, agent identities and operator-specific instructions are unchanged. Instruction publication does not establish refresh in any installed runtime.

## Ordinary maintenance — 7 November 2026

The five skill-library payloads and two bundled runtime copies were inspected at skill-library `11ad645e8f893affcb7f500a8db23835b6563ca9`, Core `f0b17efdadc57c856eb3c5cf5272a3fff2268ad1` and assembly `c057b5e4369c9c2758c8a8ead784d59ff2e1a5db`. This ordinary delta uses the 6 November receipt and the 1 November full reconciliation as its historical baselines; it does not claim another full reconciliation.

Runtime instructions now describe Core's receiving-agent A2A inbox routing, including explicit default targets and mirrored replies, and distinguish failed/partial or blocked peer answers from successful completion. The Backdoor skill corrects optional install/update `version`: it must match the inspected source's latest version, not select an arbitrary historical release. Evidence is Core's `agent-chat-tool.mjs`, `mod-distribution.mjs` and the existing Backdoor tool reference.

Backdoor `ca08786012520ee58380c501999d7c75a4dbdc92` retains its tool implementation: all 35 registered names match the reference headings and all 22 named skill references exist. The API-request example and argument contracts remain consistent; native A2A does not require Backdoor. Node Goblin `c8181bf1adcf5f7b445b8a59383f4690cd92c7b7` has documentation-only changes since the full-review pin, and GSS `5777390aa089f45de89c391672b937935733fdca` has no agent-tool implementation changes in that comparison. Their skill instructions remain unchanged.

Menagerie `e04c5e661ef6baf0d5ac787ec4c86255180a7f90` declares the new `burrow-menagerie` skill; its existing payload is retained. Managed-skill guidance now includes that declaration and separates an auxiliary synchronization failure from a successfully committed mod transition, based on Core's synchronizer, lifecycle wiring and transition regression fixtures.

Static checks cover preserved frontmatter/version metadata, matching runtime instruction bodies, Backdoor named-tool coverage and the changed Markdown's local references. No skill scripts, application/provider tests, runtime operations, permissions, credentials or agent identities were changed or executed. Publication of these source instructions does not verify refresh in an installed runtime.

## Ordinary maintenance — 6 November 2026

All six existing instruction payloads were checked at skill-library `9cbda9268ce8afeebf0dc0338b4d69d81656fbf8`, Core `4e5a505c12b236ed394b09a577a2d583b409a69f` and assembly `e8acb74a168970eb5dbfdd463745144976811b19`. The three runtime copies now match native Forge's completion-wait and automatic chat delivery contract, distinguish delivery failure from failed generation, and retain older-runtime compatibility. They also clarify fresh turn-support replay and readable profile/context record headings, with original provenance retained in receipts. Source evidence is `forge-agent-tools.mjs`, `postgres-forge-store.mjs`, `provider-turn-replay.mjs` and `prompt-assembler.mjs`.

Backdoor `8fb3fa71beabd0ffd5d13e384c2d5065ca088673` is unchanged: all 35 registered tool names, argument tables, API-request example and 22 named skill references agree with source; native A2A remains independent of diagnostics. Node Goblin and Goblin Secret Store sources and skill payloads are unchanged. Frontmatter and version metadata are preserved, runtime instruction bodies match, and no skill scripts or application/provider tests were executed. This ordinary static delta does not re-certify unchanged implementation or establish delivery to an installed runtime; the full-review baseline remains 1 November.

## Ordinary maintenance — 5 November 2026

Reviewed all six existing instruction payloads against skill-library `46e26a8242f3f38c59c502391c6a4c4c73f10d12`, Core `6465a9b200bc550697ddfc41959d671eac9abf33` and assembly `1952f88ff182ef465370209f3f1969cbdfbd79e6`. Runtime guidance now covers indexed own-agent session recall, exact original expansion, incomplete readiness, semantic fallback and current-turn shared mod guidance. Source evidence is Core's `session-search.mjs`, `mod-agent-runtime.mjs` and `prompt-assembler.mjs`. Instruction publication receipts: skill library `dd6236f266565f4b0d0e8a4be28ee531ebcbc83c` and Core `8f0a369ab52dd30edb07337e9c16de5295cf8767`.

Backdoor `8fb3fa71beabd0ffd5d13e384c2d5065ca088673` retains all 35 registered tool names and schemas; its 22 skill tool references, API-request example and native A2A separation agree with source. GSS and Node Goblin instruction payloads are unchanged. Non-executing checks cover preserved frontmatter/version metadata, equal runtime instruction bodies and local references. No skill scripts, application tests or operational changes were executed. This ordinary delta does not re-certify unchanged implementation or prove installed-skill delivery; the last full review remains 1 November.

## Ordinary maintenance — 4 November 2026

Re-read all six existing instruction payloads at skill-library `0df0b5429d70fb327ca1875d3fb706cefdeab330`, Core `b62c57ef5e831bacebf2214a31c04147471c1267` and assembly `86f41581cf4feccbd2126db38a6b746db6483080`. Backdoor `939a5969c01242eb5bdb5f953213a67cc682abac` retains the same 35 tool names and argument schemas; all reference headings and 22 skill tool names match. Its skill now distinguishes `modManagementAgentIds` and `coreApiAgentIds`, rather than teaching the obsolete shared administrator list. The three runtime copies now explain active A2A automatic final-reply delivery without a duplicate send; native messaging/discovery remains separate from Backdoor.

GSS and Node Goblin instruction payloads remain unchanged. Static checks verify exact Git-blob source bytes, preserved frontmatter/version metadata, matching runtime bodies and no unresolved local instruction references. Existing source inventories contain only the six reviewed payloads. No skill scripts, application tests, provider calls, permission changes or version changes were made. Unchanged guidance retains its previous dated review; this does not verify delivery to an installed runtime.

## Ordinary maintenance — 3 November 2026

All six existing instruction payloads were re-read at skill-library `f0f033fcd5b795bdc0a5dc8ec548ef82488e8f0e`, Core `32dde3266a231777ddfec6dba141d6b9972a21fd`, and assembly `400ec8f2d0b24478ca2185bf8c38aee2ede4c445`. Recursive inventories of the ten documented component repositories found no additional payloads. The three runtime copies now clarify the native directory's mod-owned peer eligibility and direct-send rechecks: A2A support and a live owning provider are required. This is a narrow existing-tool correction, not full Menagerie documentation.

Backdoor `af17f0feaaa5174780541b814db0d234255c35db` still registers 35 tools; all 35 reference headings and all 22 skill tool names match. Argument tables, discovery and native A2A separation were rechecked. Core's additional scalar context-measurement fields do not invalidate the existing diagnostic instructions. GSS and Node Goblin payloads remain unchanged after schema and updater checks. Frontmatter and versions are unchanged, runtime instruction bodies match, and source hashes are recorded separately from reviewed hashes. No skill scripts, runtime/provider tests, operational changes or external messages were executed. Unchanged guidance retains its prior dated review.

## Ordinary maintenance — 2 November 2026

The six existing payloads were compared with the 1 November full-review receipts. Backdoor `af17f0feaaa5174780541b814db0d234255c35db` and skill-library `95d930c427316963705f5d6e45c5dc28288bb318` retain those documented implementations. Core `69f644aaf9f0060fac7003c22e77f7a3da7c0471` and assembly `d25beccce60830cf4159d91cae9a97dec38eefd2` add saved-photo Forge selection. The three runtime instruction copies are aligned with own-agent, selected-agent and operator reference selectors, including discovery, compatibility, failure behavior and explicit generation authorization. This replaces the older own-photo-only restriction; no version metadata changed.

All 35 Backdoor registrations and the 22 tool names referenced by its skill remain consistent. Native peer messaging/discovery still do not require Backdoor diagnostics. Non-executing checks cover exact skill hashes, YAML frontmatter, runtime-body alignment and local references. Unchanged components retain the dated full-review evidence below; no skill scripts or application/provider tests were executed.

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
