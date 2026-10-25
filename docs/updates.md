# Manage optional skill sources

This page covers optional user-created or imported library skills. Core and mod-managed skills follow their own [automatic provisioning and ownership](managed-skills.md); do not import duplicates or use these controls to override managed IDs.

Select a skill under **Settings → Skills → Installed skills**. Its **Source** section controls the repository, ref, path, sync schedule, and fetch timeout.

## Update on demand

1. Review the configured repository, ref, and skill path.
2. If you changed them, click **Save source** (or **Connect Git source** for the first connection).
3. Click **Sync now** to fetch and install the upstream instructions.
4. Read the result. Use **Refresh status** if the response is uncertain or synchronization is still running.

Saving source settings does not itself install new content. Synchronization preserves lifecycle and assignments. A failed update retains the previously installed content; do not tell agents they are using the new version merely because a fetch started.

## Follow updates or pin a revision

Enable **Automatic sync**, set **Sync schedule**, and save the source to check periodically. Schedules use the operator timezone. The default form suggests `0 */6 * * *`, meaning every six hours at minute zero.

A branch such as `main` follows that branch on subsequent syncs. A full commit ID selects a fixed version. The interface also accepts tags as pinned references; a commit ID is the clearest way to identify immutable content if the upstream might move a tag.

Disabling automatic sync keeps the installed content. It does not remove the source or make its content editable, and **Sync now** remains the deliberate way to update it.

## Connect the existing runtime skill

The historical 2026.10.19 runtime normally connects this source automatically. These steps are only for an existing non-managed library entry without that source; they do not replace current Core's dedicated managed catalog:

1. Select that entry rather than importing a duplicate.
2. Set its repository to `https://github.com/GoblinKing-Burrow/Burrow-Skills.git`, ref to `main` (or an exact commit), and path to `burrow-runtime/SKILL.md`.
3. Click **Connect Git source**, then **Sync now**.
4. Check the outcome and keep its intended assignments.

Bundled startup publication defers to a configured Git source. This lets the public skill library supply updates without replacing the installed skill's identity.

## Who controls the text?

Operator-managed text can be edited in Burrow. Bundled and Git-managed instructions are read-only in that editor; lifecycle and assignments remain editable. Edit the upstream source if you maintain it, then synchronize, or create a separate operator-managed skill for your own procedure.

For a text-only Git skill, **Remove source** asks for confirmation and keeps the installed text and assignments as operator-managed content. Automatic updates stop. A filesystem package cannot be detached with this control because its companion files need copying; disable automatic sync if you simply want to retain it unchanged.

Do not edit published package files in place. Synchronization detects local content changes and refuses to overwrite them. Preserve any intentional changes before resolving that conflict.

## Remove access or delete?

Unassign a skill from an agent to stop offering that shared entry to that agent; check global assignments too. Disable its lifecycle to make it unavailable across its assignments. **Delete skill** removes the shared library copy and assignments after confirmation. Deleting instructions is not a way to uninstall the integration they describe or revoke its access.
