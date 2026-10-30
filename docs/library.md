# Explore the public skill library

Read the public instruction files before trusting or using them. The runtime skill is provisioned automatically; current Core's managed system also supplies the loaded mods’ declared companions. See [managed skills and release coverage](managed-skills.md).

The public source is:

```text
https://github.com/GoblinKing-Burrow/Burrow-Skills.git
```

The links below open the current public instruction files. Review their Git history and your installed skill version when comparing changes; these live links can advance after this guide is written. The paths also work for optional manual imports on runtimes that need them.

| Skill | Import path | What it teaches |
| --- | --- | --- |
| Burrow runtime | [burrow-runtime/SKILL.md](https://github.com/GoblinKing-Burrow/Burrow-Skills/blob/main/burrow-runtime/SKILL.md) | Conversation, workspace context, tool discovery, memory, delegation, skills, and evidence-based verification |
| Goblin Secret Store | [goblin-secret-store/SKILL.md](https://github.com/GoblinKing-Burrow/Burrow-Skills/blob/main/goblin-secret-store/SKILL.md) | Discovering assigned credentials and using protected references without exposing values |
| Burrow Backdoor | [burrow-backdoor/SKILL.md](https://github.com/GoblinKing-Burrow/Burrow-Skills/blob/main/burrow-backdoor/SKILL.md) | Home-Burrow diagnostics, durable mod administration, and separately authorized full Core API requests |
| Node Goblin operations | [node-goblin-operations/SKILL.md](https://github.com/GoblinKing-Burrow/Burrow-Skills/blob/main/node-goblin-operations/SKILL.md) | Separating service health, pairing, connectivity, assignment, and verified remote execution |

## Start with the integration you actually use

For GSS, review its credential-handling instructions and configure the mod and record access. For Node Goblin, the operations skill provides a troubleshooting sequence; making it available does not pair or approve a host. In the current managed system, these companions come from loaded mods automatically.

The historical 2026.10.19 runtime already provisions `burrow-runtime` and adopts its automatic official Git source by default. Check the installed source before changing anything; manual source setup is only needed when that default does not apply.

## Native peer messaging is separate from diagnostics

Use native `agent_send_message` directly for a known canonical agent ID or unique full display name, including spaces. Exact IDs take precedence; unknown or ambiguous names fail without sending. If discovery or disambiguation is necessary and your runtime exposes `agents_list`, use that native directory rather than loading Backdoor or inspecting health/sessions. The directory lists IDs, names and enabled state, not access to peer data. It supports optional `query`, `includeDisabled`, `limit` and `cursor`; follow `nextCursor` with unchanged filters. Narrow the query or limit if the provider budget omits cards.

For `agent_message_reply_cycle`, return your result as the final reply in the existing exchange rather than requesting a reciprocal reply from the waiting session. Runtime-owned minion depth also limits nested spawning; do not use a reopened child or invented lineage arguments to bypass a leaf.

Ordinary A2A does not require a Backdoor skill/provider or an MCP catalog lookup. On older runtimes without native discovery, use a known accepted recipient or an available directory only when needed. Follow the installed tool schemas: updated skill instructions do not add tools to older runtimes.

## Check compatibility before assignment

The Backdoor skill covers the current system mod’s diagnostics, durable mod-administration tools and full local Core API requests, with compatibility guidance for older deployments. Administrative access is separate from global diagnostics. The full API tool additionally requires its independent `core-api-v1` capability grant; `mod-management-v1` alone does not authorize it. Full API responses are not sanitized diagnostic projections, and generic API requests do not inherit durable lifecycle receipts. Follow the [current Backdoor guide](https://burrow-docs.blissful-psychosis.com/burrow-backdoor/) for setup and discover your installed tool schemas before acting. A queued lifecycle receipt is not a completed installation or update.

Likewise, a tool name in any skill is not proof that your installed version exposes it. Review instructions alongside the version of the application or mod you run. Skills can change independently of those applications.

[Install a skill](installation.md) · [Source revisions](sources.md)
