---
name: goblin-secret-store
version: 2026.10.31
description: "Safely discover and use credentials assigned through Goblin Secret Store without exposing protected values."
---

# Using Goblin Secret Store

Use Goblin Secret Store (GSS) when an authorized operation needs a credential assigned to the active agent. GSS protects values at rest and returns managed references instead of plaintext.

This skill does not grant access. The live mod, verified caller identity, record ACL, and current record version remain authoritative.

## Discover before using

Discover the installed GSS provider and its current schemas through the MCP catalog. Do not assume the provider is installed, enabled, or available merely because this skill exists.

Use the normal sequence:

1. Call `gss_list` to see records assigned to the active agent.
2. Identify the correct record from its public metadata. Do not guess an ID when discovery can establish it.
3. Call `gss_read {id}` when additional public fields are needed to confirm the record.
4. Call `gss_use {id, field}` only for the protected field required by the authorized operation.
5. Pass the returned `protected://` reference through the receiving tool's protected-binding mechanism.

Never place a protected reference or secret value directly in command text, source, logs, chat, memory, documentation, or a tool argument that does not explicitly support protected bindings.

## Respect the access boundary

Agent identity comes from Burrow's verified caller context, not from a tool argument. GSS tools are mod-authorized: the record ACL controls access without a separate per-agent MCP grant.

- A listed record is not permission to use every field for every purpose.
- Retrieve a protected field only when the current requested operation needs it.
- Do not use another credential source to bypass a GSS denial.
- Do not administer records, sharing, or ACLs through agent tools.
- Revoke access by changing the record ACL or disabling the provider; removing an unrelated MCP grant is not revocation.

Managed references are caller-, session-, conversation-, record-version-, and field-bound. Expiry, record edits, restore, ACL changes, provider disablement, or restart can invalidate them. If consumption is rejected, handle the current denial rather than caching plaintext or repeatedly retrying a stale reference.

## Understand what protection means

Protected bindings keep plaintext out of normal model-visible tool results and command text. They do not sandbox the receiving process or prevent an authorized destination from observing the value.

Before use:

- verify the destination and operation;
- use the narrowest credential field needed;
- avoid commands or applications that echo environment variables;
- avoid debug modes, process dumps, rendered configuration, or logs that expose secrets;
- clean up temporary helpers and sessions created for the operation.

Never put secrets in GSS record names, public fields, or other metadata. Those are intentionally visible to authorized discovery.

## Failure handling

Distinguish the actual failure:

- **Provider absent or disabled:** do not claim the credential does not exist; report that GSS is unavailable.
- **Record not listed or access denied:** do not bypass the ACL. Ask the operator only if access is required to complete the authorized task.
- **Protected reference expired or revoked:** obtain a fresh reference only if the operation remains authorized.
- **Receiving tool lacks protected bindings:** do not resolve the secret manually. Use a compatible execution path or report the blocker.

Report operational outcomes without reproducing credentials, protected references, private metadata, or sensitive destination responses.
