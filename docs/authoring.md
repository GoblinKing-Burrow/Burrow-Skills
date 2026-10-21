# Write a useful skill

Start with one repeatable job: investigate a service failure, review a document, or use an integration safely. Explain when to use the skill, what evidence to gather, what decisions require the operator, and how to verify the result.

## A small repository package

```text
my-skill/
  SKILL.md
  references/
    checklist.md
```

```markdown
---
name: service-check
description: "Inspect a service and report its observed health without changing it."
---

# Inspect the service

Use this skill when the user asks for a service health check.

1. Establish the intended service and environment.
2. Discover the available tools and read their current schemas.
3. Gather the smallest relevant health and recent-error evidence.
4. Report what was checked, what failed, and what remains unknown.
5. Ask before making changes outside the requested scope.

Read references/checklist.md when a deeper investigation is needed.
```

Use simple `name:` and `description:` frontmatter fields. Give the description enough context for an agent to recognize the skill. The Git importer reads these fields for preview metadata; the install ID is reviewed separately in the UI.

Keep `SKILL.md` directly in the selected package directory. Include referenced companion files there, and import the **directory** to keep them together. Do not use symlinks or submodules as a substitute for included files. Plain text skills need no package build.

## Keep instructions grounded

- State required applications, versions, or capabilities where they matter.
- Discover live tool schemas instead of treating copied examples as permanent contracts.
- Separate observation from changes and describe permission boundaries explicitly.
- Include a recovery path for missing tools, denied access, timeouts, or partial results.
- Explain what proves success; a queued operation or healthy process is not always the final result.
- Avoid secrets, runtime exports, private conversations, and operator-specific infrastructure details in public packages.

A script included in a package is a file, not an automatically registered tool. Import and sync do not run it. Instructions to run it still require an appropriate execution capability and authorization for the action.

## Test the first version

Preview the package and inspect every included file. Install under a distinct test ID with individual assignment, then ask a test agent to list and load it. Check that the loaded instructions and companions match your intent. Try one harmless representative task and one missing-prerequisite case before assigning it more broadly.

For repository changes, pin the tested commit when reproducibility matters. Letting `main` update automatically means trusting later changes from that source as well.
