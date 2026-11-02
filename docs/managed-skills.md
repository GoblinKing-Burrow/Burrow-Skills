# How managed skills work

Burrow's own operating guidance should be available without making you copy and maintain it by hand. Current Core provides the managed catalog below; the older adoption path is retained for compatibility.

## Historical runtime: 2026.10.19

The public runtime at the [verified revision](sources.md) automatically provisions `burrow-runtime`. On first adoption, it creates the bundled fallback as a global skill and connects the official public Git source with automatic sync enabled, using `0 */6 * * *` in the operator timezone.

This is not a requirement to import `burrow-runtime` manually. Look at what is already installed first. Existing operator-owned content with that ID is not silently converted; existing configured sources, including disabled schedules, are preserved. Adoption is recorded once, so removing the source deliberately is not silently undone on reboot.

Bundled and Git-managed instruction text is read-only in the operator editor. Availability and assignments are separate controls. The [optional source-management guide](updates.md) describes this public runtime's library controls.

## Current implementation: Core and mod-managed skills

The dedicated managed catalog is implemented in current Core, rechecked **1 November 2026**. It is absent from the historical runtime revision above; verify installed capabilities rather than interpreting that older snapshot as the current release. See [source pins](sources.md).

- Core declares `burrow-runtime`.
- Loaded Goblin Secret Store declares `goblin-secret-store`.
- Loaded Burrow Backdoor declares `burrow-backdoor`.
- Loaded Node Goblin declares `node-goblin-operations`.

Burrow fetches these declarations from the official public skill repository and makes their managed copies available in agents' effective catalogs. You do not import and assign separate copies to activate this mechanism. A mod must actually load and declare the companion; merely having an old mod checkout does not establish that support.

### Automatic refresh

Burrow reconciles the desired managed set at startup, after mod lifecycle changes, and periodically. The default refresh interval is six hours; runtime configuration can change it. The implementation fetches each declaration's repository/path at `HEAD`. Official declarations currently point to the **Public** Burrow-Skills repository, even when the application or mod uses a Development build. Changing the application update channel does not rewrite these declarations. There is no publication push into the running process; the managed synchronizer pulls at its own triggers.

The six-hour interval is a process-local background producer, not the optional library's cron schedule. `BURROW_MANAGED_SKILL_SYNC_INTERVAL_MS` can change it, with a minimum of 60 seconds. Background schedulers must be enabled for periodic checks. No agent/model invocation is needed.

Managed copies live under `<workspaceRoot>/global/managed-skills/<id>/`. Each copy records its fetched revision, package content hash and last successful synchronization time in `.burrow-managed-skill.json`. An empty ordinary Skills library is compatible with all managed operating skills being available.

All desired packages are fetched and staged before replacement begins. A fetch or staging failure leaves the existing installed set in place. Do not treat this as a promise of transactional recovery from every possible disk failure during replacement. If refresh fails, inspect the runtime error and installed state instead of assuming the latest instructions arrived. One failed declaration can prevent the whole staged set from publishing. Periodic failures emit `managed_skill_sync_unavailable`; a later successful interval emits `managed_skill_sync_restored`. These events and metadata describe the managed producer separately from mod-source refresh or ordinary library synchronization.

When a mod is no longer loaded, a successful reconciliation removes its no-longer-declared managed copy. That does not delete a separately created user skill with another ID.

### Managed means upstream-owned

Managed files are published read-only, and catalog entries identify managed ownership. They are not ordinary editable text skills or independently assignable database copies. A managed ID takes precedence over a user or agent skill with the same ID, so creating a look-alike does not override it.

These are ownership controls in Burrow, not a claim that a host administrator can never alter files. Keep custom procedures under distinct IDs rather than modifying runtime-managed copies.

### Available is not automatically loaded

Managed provisioning makes instructions discoverable. The agent still explicitly loads the relevant skill; neither provisioning nor assignment injects every complete skill into every prompt. The skill does not grant access to tools, credentials, or hosts.

## Versions and freshness

A Mods card can show three different versions: **Installed** is the mod package, **Running** is the active host, and **Managed skill** is the installed instruction's frontmatter `version`. None is a last-checked timestamp. An unchanged skill label alone does not prove unchanged text or a failed update.

Current public promotion stamps the four official skills with the snapshot's plain UTC `YYYY.MM.DD` identity and validates it against `PUBLIC_RELEASE.json`. Development authoring may retain `.N` revisions. This describes promotion source behavior, not proof that a particular public snapshot has been published or pulled into your installation. Older immutable snapshots may still have earlier labels.

For read-only verification, inspect `GET /api/agents/<agentId>/skills` and its **`effectiveSkills`** entries, including `owner.scope: "managed"` and `owner.readOnly: true`. The ordinary assignment ID arrays alone do not describe managed availability. Compare the declared upstream revision with the installed metadata's `revision`, `version`, `contentHash` and `synchronizedAt`. The package hash covers paths, modes and bytes; it is different from the instruction-body hash recorded by `load_skill`.

There is no dedicated managed-skill **Sync now** operator route. Ordinary library sync, mod-source refresh, import and assignment control different mechanisms. Do not import duplicates or toggle/restart a working mod just to force a refresh; diagnose the managed producer and its next ordinary interval instead.

## Inspect before trusting

Review the [exact public instruction files](library.md) before enabling the integration that supplies them. Revisit changes when skills refresh. An instruction file can be stale or unsuitable for your setup even when it is readable and automatically maintained. Live tool schemas and your permission boundaries remain authoritative.

For your own instructions, continue to [optional text and Git skills](installation.md).

