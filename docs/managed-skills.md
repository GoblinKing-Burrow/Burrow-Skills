# How managed skills work

Burrow's own operating guidance should be available without making you copy and maintain it by hand. Current Core provides the managed catalog below; the older adoption path is retained for compatibility.

## Historical runtime: 2026.10.19

The public runtime at the [verified revision](sources.md) automatically provisions `burrow-runtime`. On first adoption, it creates the bundled fallback as a global skill and connects the official public Git source with automatic sync enabled, using `0 */6 * * *` in the operator timezone.

This is not a requirement to import `burrow-runtime` manually. Look at what is already installed first. Existing operator-owned content with that ID is not silently converted; existing configured sources, including disabled schedules, are preserved. Adoption is recorded once, so removing the source deliberately is not silently undone on reboot.

Bundled and Git-managed instruction text is read-only in the operator editor. Availability and assignments are separate controls. The [optional source-management guide](updates.md) describes this public runtime's library controls.

## Current implementation: Core and mod-managed skills

The dedicated managed catalog is implemented in current Core, rechecked **25 October 2026**. It is absent from the historical runtime revision above; verify installed capabilities rather than interpreting that older snapshot as the current release. See [source pins](sources.md).

- Core declares `burrow-runtime`.
- Loaded Goblin Secret Store declares `goblin-secret-store`.
- Loaded Burrow Backdoor declares `burrow-backdoor`.
- Loaded Node Goblin declares `node-goblin-operations`.

Burrow fetches these declarations from the official public skill repository and makes their managed copies available in agents' effective catalogs. You do not import and assign separate copies to activate this mechanism. A mod must actually load and declare the companion; merely having an old mod checkout does not establish that support.

### Automatic refresh

Burrow reconciles the desired managed set at startup, after mod lifecycle changes, and periodically. The default refresh interval is six hours; runtime configuration can change it. The implementation fetches the source's default revision. It records the fetched revision and content hash with the installed copy.

All desired packages are fetched and staged before replacement begins. A fetch or staging failure leaves the existing installed set in place. Do not treat this as a promise of transactional recovery from every possible disk failure during replacement. If refresh fails, inspect the runtime error and installed state instead of assuming the latest instructions arrived.

When a mod is no longer loaded, a successful reconciliation removes its no-longer-declared managed copy. That does not delete a separately created user skill with another ID.

### Managed means upstream-owned

Managed files are published read-only, and catalog entries identify managed ownership. They are not ordinary editable text skills or independently assignable database copies. A managed ID takes precedence over a user or agent skill with the same ID, so creating a look-alike does not override it.

These are ownership controls in Burrow, not a claim that a host administrator can never alter files. Keep custom procedures under distinct IDs rather than modifying runtime-managed copies.

### Available is not automatically loaded

Managed provisioning makes instructions discoverable. The agent still explicitly loads the relevant skill; neither provisioning nor assignment injects every complete skill into every prompt. The skill does not grant access to tools, credentials, or hosts.

## Inspect before trusting

Review the [exact public instruction files](library.md) before enabling the integration that supplies them. Revisit changes when skills refresh. An instruction file can be stale or unsuitable for your setup even when it is readable and automatically maintained. Live tool schemas and your permission boundaries remain authoritative.

For your own instructions, continue to [optional text and Git skills](installation.md).
