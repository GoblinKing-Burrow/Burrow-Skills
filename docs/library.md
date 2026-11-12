# Explore the public skill library

Read the public instruction files before trusting or using them. The runtime skill is provisioned automatically; current Core's managed system also supplies the loaded mods’ declared companions. See [managed skills and release coverage](managed-skills.md).

The public source is:

```text
https://github.com/GoblinKing-Burrow/Burrow-Skills.git
```

The links below open the current public instruction files. Review their Git history and your installed skill version when comparing changes; these live links can advance after this guide is written. These are source paths, not an instruction to import managed operating skills. Manual import applies only to older compatible runtimes lacking the automatic mechanism; check installed capabilities first.

| Skill | Source path | What it teaches |
| --- | --- | --- |
| Burrow runtime | [burrow-runtime/SKILL.md](https://github.com/GoblinKing-Burrow/Burrow-Skills/blob/main/burrow-runtime/SKILL.md) | Conversation, workspace context, tool discovery, memory, delegation, skills, and evidence-based verification |
| Goblin Secret Store | [goblin-secret-store/SKILL.md](https://github.com/GoblinKing-Burrow/Burrow-Skills/blob/main/goblin-secret-store/SKILL.md) | Discovering assigned credentials and using protected references without exposing values |
| Burrow Backdoor | [burrow-backdoor/SKILL.md](https://github.com/GoblinKing-Burrow/Burrow-Skills/blob/main/burrow-backdoor/SKILL.md) | Home-Burrow diagnostics, durable mod administration, and separately authorized full Core API requests |
| Node Goblin operations | [node-goblin-operations/SKILL.md](https://github.com/GoblinKing-Burrow/Burrow-Skills/blob/main/node-goblin-operations/SKILL.md) | Separating service health, pairing, connectivity, assignment, and verified remote execution |
| Menagerie companion visits | [burrow-menagerie/SKILL.md](https://github.com/GoblinKing-Burrow/Burrow-Skills/blob/main/burrow-menagerie/SKILL.md) | Native A2A visits, the visitor journal, assigned-parent inventory scope and avoiding duplicate gift records |

### Menagerie companion visits

The fifth public instruction, `burrow-menagerie/SKILL.md`, is declared by loaded Menagerie for ordinary agents visiting their assigned resident. It does not supply resident identity or operator instructions. The public path was verified at the **10 November** snapshot; its instruction body matches the reviewed development copy apart from the public version label. Earlier reviews' 404 results describe the old publication state. Check installed managed metadata before assuming your runtime has pulled this snapshot.

The canonical ID is now `burrow-menagerie`; `menagerie-companion-visits` is the former ID. Do not manually import a duplicate or rename installed managed files. A successful managed reconciliation follows the current declaration and removes no-longer-declared managed copies.

Use native `agent_send_message`, with `messageMode: "request_reply"` while a visit unfolds and `request_reply_complete` only for a final exchange. The guidance does not require a fixed reply count or authorize repeated visits. Before actual visits, `menagerie_visit_log` can read the visitor's own recent journal; afterward it records one compact factual recap with a stable retry key. This is separate from resident notebooks, shared interactions and Brains, and is not preloaded into ordinary work context.

The saved assigned parent can target their resident's inventory with `agentId`; this does not grant another resident's inventory, notebook or Dream access. Discover the current schema and preserve concurrency tokens and provenance. For accepted **untracked** gifts, the recipient alone adds the holding then records supplied acquisition provenance. Tracked gifts use the existing `itemId` through exchange, without a second recipient copy. No gift or inventory entry is required merely to visit. See the [source receipt](sources.md).

## Start with the integration you actually use

For GSS, review its credential-handling instructions and configure the mod and record access. For Node Goblin, the operations skill provides a troubleshooting sequence; making it available does not pair or approve a host. In the current managed system, these companions come from loaded mods automatically.

The historical 2026.10.19 runtime already provisions `burrow-runtime` and adopts its automatic official Git source by default. That historical library-source setup is not the current managed catalog. On current Core, inspect the managed metadata and effective catalog; connecting a legacy library source does not update the authoritative managed copy.

## Native peer messaging is separate from diagnostics

Use native `agent_send_message` directly for a known canonical agent ID or unique full display name, including spaces. Exact IDs take precedence; unknown or ambiguous names fail without sending. If discovery or disambiguation is necessary and your runtime exposes `agents_list`, use that native directory rather than loading Backdoor or inspecting health/sessions. The directory lists IDs, names and enabled state, not access to peer data. On runtimes with mod-owned agents, those peers appear only when they support A2A and their owning provider is live. Direct sends recheck both mod-owned participants, so a known ID cannot bypass provider unavailability or disabled A2A. It supports optional `query`, `includeDisabled`, `limit` and `cursor`; follow `nextCursor` with unchanged filters. Narrow the query or limit if the provider budget omits cards.

Incoming A2A respects the receiving agent's inbox preference. With `a2aInDefault: false`, default-session routes, including an explicit `targetSessionId: "default"` and mirrored final replies, use that receiver's per-sender inbox. Explicit nondefault targets remain addressable. Check the routing receipt rather than assuming delivery to the operator's current chat. Inspect reply `ok`, `decision` and error fields; failed or partial answers are not completion, and a blocked reply reports a boundary.

For an active incoming `request_reply` or `request_reply_complete` exchange, your final response is automatically delivered to the attributed sending agent. Answer as yourself and do not send the same answer separately with `agent_send_message`. Distinct progress updates, deliberate follow-up questions and other-peer messages remain available; historical peer content does not activate these reply mechanics.

For `agent_message_reply_cycle`, return your result as the final reply in the existing exchange rather than requesting a reciprocal reply from the waiting session. Runtime-owned minion depth also limits nested spawning; do not use a reopened child or invented lineage arguments to bypass a leaf.

Ordinary A2A does not require a Backdoor skill/provider or an MCP catalog lookup. On older runtimes without native discovery, use a known accepted recipient or an available directory only when needed. Follow the installed tool schemas: updated skill instructions do not add tools to older runtimes.

## Recall and shared mod guidance

The runtime skill distinguishes explicit `session_search` evidence from current instructions. Returned `sourceId` and `sourceSessionId` identify the original entry and session for exact expansion. `session_recall_not_ready` means indexing is unfinished, not that history is empty; exact expansion can remain available while neighbor windows are unavailable. Optional semantic ranking can fall back to lexical hits if its provider is unavailable.

Enabled, available mods can supply separately attributed current-turn shared guidance. This does not replace an agent profile or grant tools. Current replay excludes runtime-marked prior turn-support snapshots and supplies fresh support once, while retaining original dispatch evidence. Model-facing profile and context sections use readable record headings; original names and `mod://` provenance remain in receipts, not editable local files. Check installed runtime capabilities; publishing new skill text does not add these implementation features to older releases.

## Saved photos in Forge

The runtime skill now explains saved-photo discovery and selection for supported image or video generation: your own photo, selected registered agents and the operator photo. Inspect `forge_catalog` and the installed `forge_create_job` schema before using `useAgentReferenceImage`, `referenceAgentIds` or `useOperatorReferenceImage`; older runtimes may expose only the own-photo flag. Uploading a photo does not start generation or authorize it. Unsupported models and missing photos fail without silently reverting to text-only generation.


In current Core, native `forge_create_job` waits for completion and automatically delivers succeeded artifacts as agent messages in the current chat. A successful response does not require another `forge_attach_artifact` call. Older installed schemas may instead return a queued job that requires inspection and attachment. After an interrupted wait, inspect the existing job and its separate delivery status before retrying: generation can continue after the waiter disconnects, and `forge_delivery_failed` does not mean the paid generation failed. Do not generate a second image merely to repair delivery.
### GIF, video references and repeat delivery

Current `forge_catalog` advertises model-specific `imageOptions`, including supported output formats, sizes and GIF controls. `forge_create_job` accepts typed image settings only for compatible image models; do not infer GIF support from a model name. GIF defaults are nine frames at 200 ms and auto size. Explicit frame count is 2–16, duration 20–2000 ms rounded to 10 ms, with advertised dimension limits.

Supported native Google video models accept saved portraits and ordered prior Forge image references. Discover the model’s `referenceArtifacts` support, then pass `{jobId, artifactId}` pairs from existing Forge records. Saved portraits come first, followed by these artifacts, with at most six references total. Artifact inputs must be succeeded PNG/JPEG/WebP images up to 20 MiB each; GIF and private mod artifacts are excluded. Missing or invalid sources fail without generation or fallback; arbitrary uploads, URLs and file paths remain unsupported.

Explicit `forge_attach_artifact` is idempotent within one assistant turn. A later authorized turn can resend an existing artifact without regenerating it. Automatic successful generation already delivers its attachments; do not attach them again merely because they appear in the result.

### Reopen an existing Forge image across chats

Current Core also accepts `[forge:JOB_ID:ARTIFACT_ID]` (or the same literal without brackets) as `attachment_view`'s `attachmentId`. Obtain both UUIDs from the existing job/artifact record. This operator-scoped, read-only lookup opens the original PNG/JPEG/GIF/WebP in another chat without generation or copying it into that chat. Missing/deleted artifacts, unsupported media and images over 20 MiB fail explicitly. Older runtimes may lack this reference format.

### Parked board tasks

Current native task tools accept `status: "parked"`. Parked tasks remain retrievable but cannot execute or be scheduled until moved out of Parked. The runtime instructions distinguish that holding state from active work; a tool being available is not authorization to resume it.

## Check compatibility before assignment

The Backdoor skill covers the current system mod’s diagnostics, durable mod-administration tools and full local Core API requests, with compatibility guidance for older deployments. Administrative access is separate from global diagnostics. Mod management requires `mod-management-v1` and membership in `modManagementAgentIds`; full API requires its independent `core-api-v1` grant and membership in `coreApiAgentIds`. The two agent assignments are independent, so management approval or assignment alone does not authorize API access. Full API responses are not sanitized diagnostic projections, and generic API requests do not inherit durable lifecycle receipts. Follow the [current Backdoor guide](https://docs.goblin-kingdom.com/burrow-backdoor/) for setup and discover your installed tool schemas before acting. A queued lifecycle receipt is not a completed installation or update. Optional install/update `version` must match the inspected source's latest version; it is a guard against a changed source, not a historical-release selector.

Likewise, a tool name in any skill is not proof that your installed version exposes it. Review instructions alongside the version of the application or mod you run. Skills can change independently of those applications.

[Add an optional skill](installation.md) · [Source revisions](sources.md)
