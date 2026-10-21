# Assign and use optional skills

This page covers optional user-created or imported library skills. Core and mod-managed skills follow their own [automatic provisioning and ownership](managed-skills.md); do not import duplicates or use these controls to override managed IDs.

Installing a skill adds it to the shared library. Assignment makes it available to an agent; loading brings its instructions into the agent's work.

## Assign the shared copy

1. Open **Settings → Skills → Installed skills**.
2. Select the skill. Search by name, ID, or description if needed; check the lifecycle and assignment filters if it is hidden.
3. In **Assignments**, select the agents that need it. Alternatively, enable **Assign globally** and click **Save skill** for every agent.

You can also open **Settings → Agents → [agent] → Skills** to change individual assignments. A global skill cannot be individually unchecked there. Remove its global assignment first if you want only selected agents to have it.

Assignments point to the same shared skill. They are not independent copies, so an upstream update or operator edit affects every agent assigned that ID.

## Understand lifecycle

- **available**: normal availability.
- **experimental**: available, with an experimental label.
- **deprecated**: available, with a deprecated label.
- **disabled**: unavailable for discovery/use through the effective skill catalog.

Experimental and deprecated do not disable a skill. To stop offering it, use disabled or remove the relevant assignment. Neither action revokes permissions previously granted to a mod, host, or credential.

## Ask for a small first use

After assignment, try a bounded request such as:

> List your available skills, load `goblin-secret-store`, and explain its credential-handling boundaries without retrieving a credential.

The agent can use `list_skills` to discover available entries and `load_skill` to read a selected ID. Assignment does not inject the full skill text into every prompt or guarantee use on a particular turn. The planner does not automatically select full skill bodies.

For a real task, name the skill if you want to be explicit, state the desired result, and keep the task's authorization clear. Loading operating instructions is not evidence that the requested work succeeded; verify the actual operation separately.

## Skills, profiles, and memory

Use skills for reusable task procedures. Use agent profile documents for agent-specific behavior and orientation. Use Brains for explicit saved facts. None of those replaces live evidence when a service, repository, or permission may have changed.

## Advanced: a different skill with the same ID

For ordinary, non-managed IDs, Burrow also discovers filesystem skills. An agent-owned filesystem skill shadows a shared filesystem skill with the same ID, and shared filesystem entries shadow assigned database-backed entries. If an agent loads unexpected text, inspect its effective catalog and source location rather than repeatedly reassigning the library entry. Give unrelated skills distinct IDs. In the forthcoming managed system, managed IDs take precedence over all of these ordinary entries.

See [source coverage](sources.md) for the catalog and explicit-loading implementation.
