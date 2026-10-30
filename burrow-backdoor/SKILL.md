---
name: burrow-backdoor
version: 2026.10.29.1
description: "Inspect and administer the home Burrow, including full local API requests, through trusted Core-hosted Backdoor tools."
---

# Using Burrow Backdoor

Backdoor connects an agent to its **home Burrow**, even when Node Goblin points shell and filesystem tools at a remote machine. The current system mod provides scoped diagnostics, durable mod administration, and explicitly authorized full local Core API requests. It does not provide an arbitrary host shell or a network HTTP proxy.

Discover the installed provider and current tool schemas first. Older standalone read-only Backdoor deployments may expose diagnostics only; do not assume an administration tool exists because this skill names it. The current mod uses the existing authenticated agent/mod relationship and does not require a separate external MCP connection or an API token entered by the agent.

## Native A2A is not a diagnostic operation

For ordinary peer messages use native `agent_send_message` directly with a known
canonical ID or unique display name. If recipient discovery/disambiguation is
needed and `agents_list` is available, use that native directory. Do not load
Backdoor, run health checks or inspect sessions just to send a message. The
`burrow_list_agents` steps below are for diagnostics and older runtimes lacking
native discovery, not a prerequisite for A2A. Follow the currently supplied tool
schemas; this skill does not add tools to an older runtime.

## Establish authority and scope

The tools are registered as mod-authorized. Do not request a separate per-tool MCP grant. Core checks trusted caller identity and the applicable scope when tools run:

- Own-scope diagnostics are the default.
- Global diagnostic access permits broader diagnostics; it does not grant administration.
- Mod administration requires `mod-management-v1` and an administrative agent assignment.
- Full Core API access requires the independent `core-api-v1` grant and that same Core-owned `adminAgentIds` assignment. Global diagnostics or mod-management approval alone does not grant full API access.

An `agentId` argument selects diagnostic data; it does not change who is calling. Use actual discovered IDs and accept access denials rather than changing identity or finding a route around them. Availability is capability, not authorization for unrelated work.

## Inspect the relevant evidence

Start with `burrow_health` for runtime health and build identity. Use `burrow_runtime_status` for the relevant agent, `burrow_inventory` for safe counts, and `burrow_postgres_status` when persistence connectivity matters. A health response does not prove shell execution or successful mod operations.

For an agent/session problem:

1. Establish the agent with `burrow_list_agents`.
2. Use `burrow_agent_status`, `burrow_active_runs`, and `burrow_list_sessions` with the narrowest useful scope.
3. Read `burrow_get_session` for a bounded recent tail. Valid stored delegation markers such as `metadata.kind` and `metadata.parentAgentId` are retained; user-role delegated tasks are not necessarily operator messages. It is not the complete conversation; use the runtime's conversation-reading tools when complete history is required.
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

## Full local Core API requests

Discover `burrow_api_request` in the installed Backdoor catalog before relying on it. Older Core/mod versions may expose only the earlier diagnostics and lifecycle tools. This tool invokes the **same home-Core API router in-process**, using the trusted active caller. It does not need the browser's OIDC/Basic session, an API token, a loopback URL, or the selected Node Goblin host. External HTTP authentication remains enabled and unchanged.

Use it within the operator's current authorization, for example:

```json
{"method":"GET","path":"/api/openapi.json"}
```

The returned running OpenAPI document is discovery, not an endpoint admission list. Supply a local `/api/...` path including any URL-encoded query; absolute URLs and non-API targets are not supported. All valid HTTP methods route normally, including writes. Existing Archive Dream group/detail, Workflow Events/calendar and mod API routes are available without new named-tool wrappers.

Inputs are `path`, optional `method` (default `GET`), optional string/string-array `headers`, and at most one of `body` (any JSON value), `bodyText`, or `bodyBase64`. Core returns `{ok,status,headers,body,encoding,byteLength}`. `encoding` is `json`, `utf8`, or `base64`; finite NDJSON is complete aggregate text, not a live tool stream. Binary downloads are base64 with their headers and exact byte count. Follow the underlying route's pagination. HTTP errors such as 400/404/409 are response data, not missing tools; a 2xx acceptance still does not prove asynchronous work finished.

The full API result is not a sanitized diagnostic subset. It can contain complete transcripts, metadata, exports, and credentials returned by the actual route. Request only what is needed and never publish sensitive responses. Core's technical allocation/body validation still applies; oversize aggregate responses fail explicitly rather than silently truncating. Transport cancellation can leave an already admitted route running, just as browser disconnect can; reconcile durable state before retrying a mutation.

Full API authority is deliberately powerful: it can modify settings, sources, retention and access. That is capability, **not permission to expand the operator's task**. Do not change your own grants or disable authentication merely to avoid a denial. Grants and assignments remain operator-owned. Prefer the existing durable mod-management tools for Backdoor self-update/disable/uninstall: their operation receipts and caller-settlement handling are designed for host replacement.

## Protect output and handle denials

Session and trace data may be private. `burrow_get_trace` omits tool output by default; include it only when needed. Summarize relevant evidence rather than publishing raw prompts, sessions, traces, credentials, or private tool output.

For a capability or scope denial, report the exact error and the missing authority. Do not claim a record is absent merely because it is inaccessible. For an unavailable tool, establish installed Core/mod compatibility before recommending configuration changes.

Access-setting authentication depends on Core version: older releases require operator login even with authentication disabled; corrected Core permits the operator UI when authentication is disabled and still requires login when it is enabled. API tokens do not authorize that operator access-setting route. Updating Backdoor alone does not change Core's route behavior.
