---
name: burrow-backdoor
description: "Inspect the agent's home Burrow and carry out authorized mod lifecycle operations through Backdoor's Core-hosted tools."
---

# Using Burrow Backdoor

Backdoor connects an agent to its **home Burrow**, even when Node Goblin points shell and filesystem tools at a remote machine. The current system mod provides diagnostics and mod administration through Core-owned capabilities. It does not provide an arbitrary shell or unrestricted Core access.

Discover the installed provider and current tool schemas first. Older standalone read-only Backdoor deployments may expose diagnostics only; do not assume an administration tool exists because this skill names it. The current mod uses the existing authenticated agent/mod relationship and does not require a separate external MCP connection or an API token entered by the agent.

## Establish authority and scope

The tools are registered as mod-authorized. Do not request a separate per-tool MCP grant. Core checks trusted caller identity and the applicable scope when tools run:

- Own-scope diagnostics are the default.
- Global diagnostic access permits broader diagnostics; it does not grant administration.
- Mod administration requires the relevant Core capability and an administrative agent assignment.

An `agentId` argument selects diagnostic data; it does not change who is calling. Use actual discovered IDs and accept access denials rather than changing identity or finding a route around them. Availability is capability, not authorization for unrelated work.

## Inspect the relevant evidence

Start with `burrow_health` for runtime health and build identity. Use `burrow_runtime_status` for the relevant agent, `burrow_inventory` for safe counts, and `burrow_postgres_status` when persistence connectivity matters. A health response does not prove shell execution or successful mod operations.

For an agent/session problem:

1. Establish the agent with `burrow_list_agents`.
2. Use `burrow_agent_status`, `burrow_active_runs`, and `burrow_list_sessions` with the narrowest useful scope.
3. Read `burrow_get_session` for a bounded recent tail. It is not the complete conversation; use the runtime's conversation-reading tools when complete history is required.
4. Use `burrow_context_status` or `burrow_get_session_context` for usage/composition. The latter exposes scalar summaries, not the full supplied prompt.
5. List traces, then inspect the relevant run with `burrow_get_trace`; use `burrow_get_trace_authority` for authorization evidence.
6. Use archived run proofs when historical proof is required.

Follow pagination only where the discovered schema supports it. For cursor-based tools, retain the same scope and follow the returned cursor; management inventory instead uses `offset` and `pagination.nextOffset`. Session listing is bounded by `limit` and is not a cursor traversal.

Active-run listings, elapsed time, and counters are observations, not proof of progress. Empty results, denied access, unavailable diagnostics, unsupported tools, and provider errors are distinct states. Sanitized Forge, Brains, and mod summaries do not expose the content Core deliberately omits.

## Complete authorized mod operations

Use these tools only for the operator's requested outcome:

- `burrow_mod_management_inventory`: inspect installed/installable mods and configured source summaries.
- `burrow_refresh_mod_sources`: queue a refresh of already configured sources.
- `burrow_install_mod` / `burrow_update_mod`: queue installation of a discovered mod, optionally at an available version.
- `burrow_enable_mod` / `burrow_disable_mod` / `burrow_uninstall_mod`: queue the specified lifecycle action.
- `burrow_get_mod_operation`: inspect its durable operation record.

Confirm the intended home runtime, mod ID, current state, and requested version from live evidence. A repository name may differ from the manifest ID. These tools do not create a source, change access assignments, edit arbitrary Core settings, or restart Burrow.

A successful submission returns a queued operation receipt, not completion. Retain its operation ID and inspect it until `succeeded`, `failed`, or `interrupted`, or a real blocker prevents verification. Then verify the resulting lifecycle state and any `restartRequired` flag. An interrupted operation or `result.outcome: unknown` can have side effects; inspect the actual installed state before retrying. Do not infer cancellation from a disconnected tool call. Self-update or disabling Backdoor can make its tools unavailable, possibly until an operator re-enables it. If necessary, use an already-authorized operator view to inspect installed state; do not imply that this is a durable operation receipt or claim completion when verification is blocked.

## Protect output and handle denials

Session and trace data may be private. `burrow_get_trace` omits tool output by default; include it only when needed. Summarize relevant evidence rather than publishing raw prompts, sessions, traces, credentials, or private tool output.

For a capability or scope denial, report the exact error and the missing authority. Do not claim a record is absent merely because it is inaccessible. For an unavailable tool, establish installed Core/mod compatibility before recommending configuration changes.

Access-setting authentication depends on Core version: older releases require operator login even with authentication disabled; corrected Core permits the operator UI when authentication is disabled and still requires login when it is enabled. API tokens do not authorize that operator access-setting route. Updating Backdoor alone does not change Core's route behavior.
