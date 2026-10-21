# Explore the public skill library

Read the public instruction files before trusting or using them. The runtime skill is provisioned automatically in the current public runtime; the forthcoming managed system also supplies the loaded mods’ companions. See [managed skills and release coverage](managed-skills.md).

The public source is:

```text
https://github.com/GoblinKing-Burrow/Burrow-Skills.git
```

The links below open the current public instruction files. Review their Git history and your installed skill version when comparing changes; these live links can advance after this guide is written. The paths also work for optional manual imports on runtimes that need them.

| Skill | Import path | What it teaches |
| --- | --- | --- |
| Burrow runtime | [burrow-runtime/SKILL.md](https://github.com/GoblinKing-Burrow/Burrow-Skills/blob/main/burrow-runtime/SKILL.md) | Conversation, workspace context, tool discovery, memory, delegation, skills, and evidence-based verification |
| Goblin Secret Store | [goblin-secret-store/SKILL.md](https://github.com/GoblinKing-Burrow/Burrow-Skills/blob/main/goblin-secret-store/SKILL.md) | Discovering assigned credentials and using protected references without exposing values |
| Burrow Backdoor | [burrow-backdoor/SKILL.md](https://github.com/GoblinKing-Burrow/Burrow-Skills/blob/main/burrow-backdoor/SKILL.md) | Home-Burrow diagnostics, scoped mod administration, and durable operation verification |
| Node Goblin operations | [node-goblin-operations/SKILL.md](https://github.com/GoblinKing-Burrow/Burrow-Skills/blob/main/node-goblin-operations/SKILL.md) | Separating service health, pairing, connectivity, assignment, and verified remote execution |

## Start with the integration you actually use

For GSS, review its credential-handling instructions and configure the mod and record access. For Node Goblin, the operations skill provides a troubleshooting sequence; making it available does not pair or approve a host. In the forthcoming managed system, these companions come from loaded mods automatically.

The current public runtime already provisions `burrow-runtime` and adopts its automatic official Git source by default. Check the installed source before changing anything; manual source setup is only needed when that default does not apply.

## Check compatibility before assignment

The Backdoor skill covers the current system mod’s diagnostics and mod-administration tools, with compatibility guidance for older diagnostic-only deployments. Administrative access is separate from global diagnostics. Follow the [current Backdoor guide](https://burrow-docs.blissful-psychosis.com/burrow-backdoor/) for setup and discover your installed tool schemas before acting. A queued lifecycle receipt is not a completed installation or update.

Likewise, a tool name in any skill is not proof that your installed version exposes it. Review instructions alongside the version of the application or mod you run. Skills can change independently of those applications.

[Install a skill](installation.md) · [Source revisions](sources.md)
