---
name: node-goblin-operations
version: 2026.10.31
description: "Operate and troubleshoot Node Goblin controller and execution hosts without confusing service health, pairing, connectivity, and execution evidence."
---

# Operating Node Goblin

Node Goblin connects Burrow agents to remote execution hosts. The controller mod runs inside Burrow; Mini Node Goblin runs as a systemd service on each Linux execution host.

For home-Burrow diagnostics and authorized mod administration while execution is remote, use the Backdoor companion in the home runtime when available. Remote shell access does not move Burrow Core onto that execution host.

Treat these as separate layers. A running service does not prove controller reachability, pairing approval, agent assignment, workspace access, or successful command execution.

## Inspect before changing

For a connectivity or execution problem, establish each layer in order:

1. Confirm the Node Goblin mod is installed and enabled in the intended Burrow runtime.
2. Confirm the controller listener is enabled, Burrow was restarted after configuration, and the bind address/port is reachable from the host.
3. On the execution host, run `sudo node-goblin status`.
4. Inspect `sudo journalctl -u burrow-host-gateway.service -n 100 --no-pager` when service or connection detail is needed.
5. Confirm the current host ID and trust/pairing state.
6. Confirm the host appears approved and connected in Burrow.
7. Confirm the intended agent is assigned to that host and an absolute workspace path accessible to the `burrow` service account.
8. Verify actual execution with a harmless command or file read in a disposable workspace on a new turn.

Do not substitute one layer's evidence for another.

## Pair safely

For first-time pairing:

- obtain the current pairing code from `sudo node-goblin pairing-code`;
- compare the host and controller views through a trusted channel;
- confirm the exact current code on the host;
- approve only the intended host in Burrow;
- reject unexpected requests.

Reconnects can create a new pairing transcript. Use the current code. If a certificate or identity changes unexpectedly, investigate and follow the documented re-pairing procedure rather than bypassing trust checks.

Pairing grants Burrow process and filesystem access as the host's `burrow` account. A configured workspace is a working directory, not a sandbox. Use least privilege at the host OS boundary.

## Apply configuration deliberately

`node-goblin configure` saves settings but does not restart an already running daemon. After draining active work, apply saved changes with:

```sh
sudo node-goblin apply --restart
```

`node-goblin connect` starts/enables the service but does not restart an already-running daemon. Verify the resulting connection and a real operation rather than stopping at systemd's active state.

Keep credentials and enrollment material in protected configuration, never in command arguments, URLs, chat, or logs. Treat `/etc/burrow-host-gateway/gateway.env`, `/var/lib/burrow-host-gateway`, backups, and journals as sensitive.

## Update and recover without duplicating side effects

Before an update:

1. Drain active work.
2. Check the outcome of any interrupted operation before retrying it.
3. Back up protected configuration and persistent state.
4. Install a selected release package.
5. Start the service and verify controller connection, trust, assignment, and actual execution.

A dropped connection does not prove the host operation stopped. Determine its outcome before retrying commands with side effects.

The supported uninstall preserves the `burrow` account, configuration, identity/trust state, and operation journal. Do not claim it purges credentials or removes the controller mod.

## Respect the execution boundary

When an agent is assigned to Node Goblin, use the runtime-provided execution target and filesystem boundary. Do not invent host IDs, workspace paths, or controller addresses. Verify mutable host state before acting.

For destructive, privileged, or externally impactful commands, authorization still comes from the operator's request. Node Goblin access does not broaden scope. Use the minimum required privilege and verify the final remote outcome.
