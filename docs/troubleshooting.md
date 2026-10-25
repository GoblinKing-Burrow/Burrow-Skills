# Troubleshoot skills

## An automatic companion is missing

First check [release coverage](managed-skills.md). The historical 2026.10.19 snapshot lacks the dedicated mod-managed catalog; current Core implements it. On a compatible installed runtime, verify the relevant mod actually loaded, declares its companion, and the managed refresh succeeded. A failed first fetch can leave the companion pending; an existing copy can remain older after a fetch failure. Do not use an import under the same ID as a supposed override.

## The agent cannot see an optional skill

Check the exact agent, installed ID, assignment, global flag, lifecycle, and library filters. Disabled entries are unavailable. A skill installed without global assignment still needs an individual assignment. Ask the agent to list its current skills before assuming it has loaded one.

If the ID exists but the text is unexpected, check filesystem overrides with the same ID. See [assignment and loading](using-skills.md).

## A tool mentioned in the skill is missing

Skills supply instructions, not integrations. Confirm the corresponding mod is installed and enabled, the agent has the required access, and the installed version exposes the tool. Use its live schema. For Backdoor in particular, read the [library compatibility note](library.md#check-compatibility-before-assignment).

## Repository preview fails

Check repository reachability from the Burrow runtime, the ref, and the repository-relative path. The selected directory must have its own `SKILL.md`; a file selection must be a regular file named exactly `SKILL.md`.

The importer rejects invalid paths, symlinks, submodules/gitlinks, non-UTF-8 instruction text, and Git LFS pointer-only artifacts. Use ordinary committed files or materialize the real artifacts upstream. For a slow network or large legitimate package, review **Fetch timeout (ms)**; the timeout covers both fetching and object extraction.

Do not put credentials in the repository URL. Private HTTPS login is not configured in this screen.

## The ID already exists

Burrow deliberately refuses to overwrite it during import. Select the existing skill to manage its source, or choose a distinct ID for a separate skill. For bundled `burrow-runtime`, use [Connect the existing runtime skill](updates.md#connect-the-existing-runtime-skill).

## The repository changed after preview

Preview again and inspect the new revision before installing. The rejected request did not install the changed content. Pin a full commit ID when you want to review and install an exact revision.

## Import or sync timed out

An install response timeout does not prove installation failed. Reload the library before trying again. For synchronization, use **Refresh status** and wait for its recorded outcome. Do not repeatedly click while it is in progress.

A recorded sync failure retains the previous installed content. Check repository/ref/path and the reported error before retrying. An upstream observation is not proof that the new content was installed.

## Sync reports local changes

`skill_local_changes` means the installed Git-managed content no longer matches its recorded hash. Preserve any intentional local edits, investigate how the published files changed, and reconcile the source deliberately. Do not delete or overwrite files blindly to make the error disappear.

## Instructions are read-only, or Remove source is disabled

Bundled and Git-managed content is upstream-controlled. Change lifecycle or assignments in Burrow, edit the maintained source, or create a separate text skill. Text-only Git sources can be removed while keeping the text. Packages with companion files cannot be detached through this control; turn off automatic sync if you only need to freeze updates.

## An update did not change behavior

Confirm you clicked **Sync now** after saving the source and that the update succeeded. Check whether the ref is pinned and whether an overriding filesystem skill exists. Then verify the agent loads the intended skill on the relevant turn. Assignment alone does not guarantee use, and an already loaded instruction is not a live subscription to upstream text.
