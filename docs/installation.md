# Add optional text or Git skills

This page covers optional user-created or imported library skills. Core and mod-managed skills follow their own [automatic provisioning and ownership](managed-skills.md); do not import duplicates or use these controls to override managed IDs.

Open **Settings → Skills** in Burrow. Choose repository import when you want a maintained upstream source, or a text skill for instructions you control yourself.

## Import from the public library

1. Open **Import from repository**.
2. Set **Repository** to `https://github.com/GoblinKing-Burrow/Burrow-Skills.git`.
3. Set **Skill path** to the chosen path, for example `goblin-secret-store/SKILL.md`.
4. Expand **Ref & automatic updates**. Set **Ref** to `main`, or use a full commit ID for a fixed version. `HEAD` selects the repository default. Automatic sync is off initially.
5. Click **Preview skill**. Read the actual instruction text, previewed revision, storage type, and **Included files**.
6. Review **Install ID & availability**. Keep a meaningful unique ID, choose a lifecycle, and decide whether to **Assign globally**.
7. Click **Install skill**, then [assign it to the intended agents](using-skills.md).

Import does not overwrite an existing ID. If Burrow says that the ID already exists, select its installed entry and configure its source, or deliberately choose a different ID for a separate copy.

If upstream changed after preview, Burrow rejects that installation request and asks you to preview again. If the install response times out, reload the library and check whether it completed before retrying.

## File or directory?

Choose `SKILL.md` for text alone. Choose its containing directory when the skill needs companion files such as reference documents or scripts. The directory must contain `SKILL.md` directly.

A selection containing only `SKILL.md` uses PostgreSQL. A selection with companion files uses published filesystem package storage. Importing the file alone does not bring those companions along. The whole Burrow-Skills repository is not one skill: select one of its skill directories or files.

Import and sync read Git objects and install files. They do **not** execute included scripts or Git hooks. Later use of a script is a separate execution action with its own access and authorization requirements.

## Create your own text skill

1. Open **New text skill**.
2. Enter **ID**, **Name**, **Description**, and **Content**.
3. Alternatively, click **Choose text file** and select a `.md`, `.markdown`, or `.txt` file. Burrow loads the complete file for review and suggests an ID and name from the filename. Check those fields and add a useful description yourself.
4. Choose **Lifecycle** and whether to **Assign globally**.
5. Click **Create skill**.

Choosing a file only fills the form. It does not save the skill or establish a link to the file on your computer. Later edits to that local file will not update the saved copy automatically.

IDs use letters, digits, periods, underscores, or hyphens, start with a letter or digit, and are at most 128 characters. Pick the ID carefully: it is not editable after creation.

## Other Git sources

The importer also accepts HTTPS, SSH, and absolute local Git repository paths. A local path is on the **Burrow runtime's filesystem**, not a file picker on your browser computer. Private HTTPS credentials are not configured in this form; do not embed passwords or tokens in repository URLs.

Use repository-relative skill paths without leading slashes or `..`. Symlinks, submodules/gitlinks, and unmaterialized Git LFS pointers are rejected. See [troubleshooting](troubleshooting.md) for recovery.
