<p align="center">
  <img src="docs/assets/hero.png" width="720" alt="Burrow Skills library for reusable agent operating instructions" />
</p>

# Burrow Skills

Public operating skills for Burrow and its integrations, updated independently of application releases.

## Available

- `burrow-runtime/SKILL.md`: native runtime, tools, continuity, delegation, skills, and verification.
- `goblin-secret-store/SKILL.md`: safe credential discovery and protected-reference use through Goblin Secret Store.
- `burrow-backdoor/SKILL.md`: evidence-driven, read-only Burrow diagnostics through Backdoor.
- `node-goblin-operations/SKILL.md`: pairing, health, updates, recovery, and remote-execution boundaries for Node Goblin.

## Install and update

In **Settings → Skills**, import repository `https://github.com/GoblinKing-Burrow/Burrow-Skills.git`, ref `main`, and the path to the wanted skill, such as `goblin-secret-store/SKILL.md`. Preview, inspect, then install and enable automatic synchronization with your preferred schedule. Tags and commits pin content instead of following updates.

Import never overwrites an existing ID. For an existing bundled `burrow-runtime`, configure its Git source instead. Synchronization preserves assignments; bundled startup publication defers to a configured Git source.

Text-only skills use PostgreSQL. Select a directory for skills with artifacts so supporting files stay together in runtime filesystem storage. Import and sync do not execute scripts.

## Contributions

Each skill has its own directory with `SKILL.md` and name/description frontmatter. Supporting files belong alongside it. Keep instructions matched to current capabilities and document minimum runtime requirements where needed. Runtime tool schemas remain authoritative: skills cannot grant tools, access, or authorization.

Review contributions for secrets, private infrastructure details, and operator-specific data before publishing. Do not include runtime exports, credentials, conversations, caches, or mirrored application source.
