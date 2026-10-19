---
name: burrow-backdoor
description: "Investigate a Burrow runtime through Backdoor's read-only MCP diagnostics while preserving evidence boundaries and sensitive data."
---

# Diagnosing Burrow through Backdoor

Burrow Backdoor is a read-only MCP view into a running Burrow Core. Use it to inspect health, runtime configuration, agents, sessions, runs, traces, mods, Forge, Brains, and PostgreSQL diagnostics.

Backdoor observes; it does not repair, cancel, restart, reconfigure, or mutate work. Do not describe a diagnostic read as a corrective action.

## Establish the path first

Discover the installed Backdoor provider and current tool schemas through the MCP catalog. Tool availability depends on both the Backdoor version and matching Core diagnostic endpoints.

Start with:

1. `burrow_health` to verify the full client → Backdoor → Core path.
2. `burrow_runtime_status` for release, model-selection, policy, retention, and trace-observability state.
3. `burrow_inventory` when MCP/mod counts or installed mod state matters.
4. `burrow_postgres_status` only when persistence connectivity or pgvector availability is relevant.

The Backdoor process `/healthz` is not equivalent to `burrow_health`: process health alone does not verify Core reachability, token validity, or diagnostic authorization.

## Follow the subject, not every endpoint

For an agent/session problem:

1. Use `burrow_list_agents` to establish the agent ID.
2. Use `burrow_agent_status`, `burrow_active_runs`, and `burrow_list_sessions` with the narrowest useful scope.
3. Inspect the relevant session with `burrow_get_session`.
4. Use `burrow_context_status` or `burrow_get_session_context` when context pressure, composition, or compression is implicated.
5. List traces, then inspect the specific run with `burrow_get_trace`.
6. Use `burrow_get_trace_authority` when the question concerns authorization or why an action was selected.
7. Use archived run proofs only when current traces are absent or historical proof is required.

Do not dump every diagnostic surface into the answer. Build a supported conclusion from the smallest relevant evidence set.

## Preserve diagnostic semantics

- An active-run listing is an observation at read time, not proof that work is still progressing.
- Elapsed time, counters, and pending operations do not prove a worker is alive.
- Empty results, unsupported diagnostics, unavailable diagnostics, and provider errors are different states.
- Session, trace, and proof records describe different forms of evidence; do not silently substitute one for another.
- Global Brains counts and agent-scoped listings are different scopes.
- Paginated results are not one atomic snapshot while concurrent work changes.

Follow `nextCursor` with the same route and scope until the needed result is found or pagination ends. Restart pagination when changing scope.

## Protect sensitive output

Sessions and traces may contain private operational material. `burrow_get_trace` omits tool output by default. Keep it omitted unless the investigation genuinely requires it.

- Do not publish raw sessions, traces, prompts, credentials, private file content, or sensitive tool output.
- Summarize the evidence needed for the conclusion.
- Treat read-only access as sensitive access, not safe-to-share access.
- Preserve exact error codes when they matter, but redact private payloads.

Forge and mod diagnostic summaries are deliberately sanitized. Do not infer hidden prompts, artifacts, provider errors, or arbitrary mod state from fields Core intentionally excludes.

## Handle failures cleanly

- **`403 api_token_forbidden`:** check Core compatibility and the `diagnostics:read` allowlist; do not widen the token casually.
- **Backdoor health succeeds but tools fail:** inspect Core reachability, token expiry, and endpoint support.
- **Mod diagnostics unavailable:** verify the mod is enabled and supports diagnostic adapters; do not claim it has no work.
- **Timeout or gateway failure:** report the failed diagnostic path, not a conclusion about the underlying runtime state.

When the evidence identifies a repair, use the correct authorized operational tool or owner outside Backdoor. Backdoor itself remains read-only.
