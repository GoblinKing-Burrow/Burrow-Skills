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

## Start with the integration you actually use

For GSS, review its credential-handling instructions and configure the mod and record access. For Node Goblin, the operations skill provides a troubleshooting sequence; making it available does not pair or approve a host. In the current managed system, these companions come from loaded mods automatically.

The historical 2026.10.19 runtime already provisions `burrow-runtime` and adopts its automatic official Git source by default. That historical library-source setup is not the current managed catalog. On current Core, inspect the managed metadata and effective catalog; connecting a legacy library source does not update the authoritative managed copy.

## Native peer messaging is separate from diagnostics

Use native `agent_send_message` directly for a known canonical agent ID or unique full display name, including spaces. Exact IDs take precedence; unknown or ambiguous names fail without sending. If discovery or disambiguation is necessary and your runtime exposes `agents_list`, use that native directory rather than loading Backdoor or inspecting health/sessions. The directory lists IDs, names and enabled state, not access to peer data. On runtimes with mod-owned agents, those peers appear only when they support A2A and their owning provider is live. Direct sends recheck both mod-owned participants, so a known ID cannot bypass provider unavailability or disabled A2A. It supports optional `query`, `includeDisabled`, `limit` and `cursor`; follow `nextCursor` with unchanged filters. Narrow the query or limit if the provider budget omits cards.

For an active incoming `request_reply` or `request_reply_complete` exchange, your final response is automatically delivered to the attributed sending agent. Answer as yourself and do not send the same answer separately with `agent_send_message`. Distinct progress updates, deliberate follow-up questions and other-peer messages remain available; historical peer content does not activate these reply mechanics.

For `agent_message_reply_cycle`, return your result as the final reply in the existing exchange rather than requesting a reciprocal reply from the waiting session. Runtime-owned minion depth also limits nested spawning; do not use a reopened child or invented lineage arguments to bypass a leaf.

Ordinary A2A does not require a Backdoor skill/provider or an MCP catalog lookup. On older runtimes without native discovery, use a known accepted recipient or an available directory only when needed. Follow the installed tool schemas: updated skill instructions do not add tools to older runtimes.

## Recall and shared mod guidance

The runtime skill distinguishes explicit `session_search` evidence from current instructions. Returned `sourceId` and `sourceSessionId` identify the original entry and session for exact expansion. `session_recall_not_ready` means indexing is unfinished, not that history is empty; exact expansion can remain available while neighbor windows are unavailable. Optional semantic ranking can fall back to lexical hits if its provider is unavailable.

Enabled, available mods can supply separately attributed current-turn shared guidance. This does not replace an agent profile or grant tools. Current replay excludes runtime-marked prior turn-support snapshots and supplies fresh support once, while retaining original dispatch evidence. Model-facing profile and context sections use readable record headings; original names and `mod://` provenance remain in receipts, not editable local files. Check installed runtime capabilities; publishing new skill text does not add these implementation features to older releases.

## Saved photos in Forge

The runtime skill now explains saved-photo discovery and selection for supported image generation: your own photo, selected registered agents and the operator photo. Inspect `forge_catalog` and the installed `forge_create_job` schema before using `useAgentReferenceImage`, `referenceAgentIds` or `useOperatorReferenceImage`; older runtimes may expose only the own-photo flag. Uploading a photo does not start generation or authorize it. Unsupported models and missing photos fail without silently reverting to text-only generation.


In current Core, native `forge_create_job` waits for completion and automatically delivers succeeded artifacts as agent messages in the current chat. A successful response does not require another `forge_attach_artifact` call. Older installed schemas may instead return a queued job that requires inspection and attachment. After an interrupted wait, inspect the existing job and its separate delivery status before retrying: generation can continue after the waiter disconnects, and `forge_delivery_failed` does not mean the paid generation failed. Do not generate a second image merely to repair delivery.
## Check compatibility before assignment

The Backdoor skill covers the current system mod’s diagnostics, durable mod-administration tools and full local Core API requests, with compatibility guidance for older deployments. Administrative access is separate from global diagnostics. Mod management requires `mod-management-v1` and membership in `modManagementAgentIds`; full API requires its independent `core-api-v1` grant and membership in `coreApiAgentIds`. The two agent assignments are independent, so management approval or assignment alone does not authorize API access. Full API responses are not sanitized diagnostic projections, and generic API requests do not inherit durable lifecycle receipts. Follow the [current Backdoor guide](https://docs.goblin-kingdom.com/burrow-backdoor/) for setup and discover your installed tool schemas before acting. A queued lifecycle receipt is not a completed installation or update.

Likewise, a tool name in any skill is not proof that your installed version exposes it. Review instructions alongside the version of the application or mod you run. Skills can change independently of those applications.

[Add an optional skill](installation.md) · [Source revisions](sources.md)
