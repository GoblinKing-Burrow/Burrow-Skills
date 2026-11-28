---
name: burrow-auditor
version: 2026.11.28
description: "Use Burrow Auditor for independent inspections: report requested audits and use internal acceptance audits to finish the work."
---

# Use Burrow Auditor

Auditor provides an independent verdict on work, not another implementation helper. Use it when the operator asks for an audit or when the applicable acceptance workflow calls for one. When Auditor is the agreed review gate, submit the candidate **before** publishing or handing it off as accepted. Your own tests, a generic Minion review, green CI, and publication verification answer different questions; none is an Auditor verdict. An audit does not replace any separately required check or authorize publication, changes, or deployment.

## Submit the right subject

1. Discover the live **Mod: Auditor** tool catalog. Use `auditor_projects` to find the exact configured project and see its runners' eligibility. Use those runners; don't choose a friendlier reviewer or change project settings to make a submission pass. If the project or necessary capabilities are missing, report the actual blocker. Auditor's mod-authorized tools do not need individual MCP grants on compatible installations.
2. Preserve the operator's original request, clarifications, and applicable constraints with accessible references. Put the question in `objective`, name the subject clearly, and supply the references needed for the runners to reach the **same** target. For source, use full commits and actual repository locations; for a release, supply the exact artifact and authoritative source pins. For a UI or live-behavior audit, identify the actual interface or instance, relevant version and authorized access. A release source audit does not imply a live deployment check. If a pre-publication candidate isn't accessible to the configured runner host, resolve that or report it before claiming the review ran.
3. Preserve independence: give runners the objective, operator requirements, and discovery starting points, not the implementer's verdict or a checklist that excludes other applicable contracts. They choose their own investigation and evidence. Inspect and report within the authorized scope; do not ask the runners to edit the target or bypass access controls. Test results can be evidence, not acceptance authority. Share only relevant context and do not put secrets in audit inputs or evidence.
4. Use `auditor_submit` with `projectId`, `subject`, `objective`, `references` when needed, and a stable `requestId`. Preserve the audit ID. On an uncertain submission, reconcile the existing record with `auditor_list` or retry with the same request ID **and identical input**; use a new ID for a genuinely different candidate or objective. A running or completed job is not a verdict. Retain whether the operator asked for the audit itself or you submitted it as an internal check, and the next step in the original work; distinguish those when the audit returns.

## Close the loop

On compatible versions, leave `wake` unset for an internal acceptance gate. Call the native `mod_wait` tool **by itself**, using the exact `waitReceiptId` from `auditor_submit` in this run and a credential-free checkpoint of the original scope, candidate pins, remaining work and gate rules. Let Core suspend that work without blocking chat. On return, only **Pass** clears the gate. Fix a material **Fail** and wait on a new audit of the changed candidate; **Split** and **Inconclusive** need resolution and are not passes. A standalone audit the operator asked to receive uses **`wake: true`** instead. Manual Settings runs stay Archive-only. If the necessary path is unavailable, reconcile the original audit and keep the gate unresolved until there is a formal verdict. Do not create a task, standing poll, fake message, or duplicate audit to retrieve it.

On return, use `auditor_read` with the exact audit ID and read the original runner reports and any comparison. Never turn a missing verdict, a failed investigation, or a derived comparison into your own pass. If the runners inspected different subjects, the results aren't comparable even if the displayed verdicts differ.

- **Operator-requested audit:** The audit is the deliverable. Report Auditor's recorded **Pass**, **Fail**, **Inconclusive**, or **Split**, with the exact subject reviewed, material findings or blockers, and the originals in **Archive → Mods → Auditor**. If the comparison failed but original reports exist, distinguish the two. Don't make the operator ask again for the result.
- **Internal quality check:** The work is the deliverable. Keep routine audit submissions, returns, and verdicts out of chat. Act on the findings and continue the original work; a pass is a cue to proceed, not a status announcement or completion. Report the requested outcome once, or surface a material blocker or decision you cannot resolve within the authorized scope. If an audit finding is material to that outcome, include it there without forwarding routine audit chatter.

Do not filter away a runner's finding. If it reveals an actionable defect within authorized scope, resolve it and submit the changed revision for another independent verdict. A disposition on an earlier revision doesn't carry over automatically. Original reports remain available in Archive in either case.
