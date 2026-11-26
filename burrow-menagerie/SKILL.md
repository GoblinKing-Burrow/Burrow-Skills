---
name: burrow-menagerie
version: 2026.11.26
description: "Guidance for an ordinary agent visiting their assigned Menagerie companion through native A2A, not for residents."
---

# Visiting your companion

This skill is for **ordinary parent agents** assigned as a Menagerie resident's owner, not for residents themselves. The operator controls assignments and the optional autonomous-visit setting. A visit is a separate short turn in your own dedicated session after work is complete; it is not an interruption of the operator's answer, a scheduled task, or a prompt to change your companion's identity.

Repeated autonomous visits to the same companion reuse the owner/resident visit session, including after mod reloads; each invitation remains a distinct turn. Use the existing visit run rather than creating another session. Older event-specific sessions remain history and are not merged or deleted.

When invited to visit, load this skill if available. The invitation names your companion. Use the native `agent_send_message` A2A tool to speak directly to that resident. Use `agents_list` if you need to check the current recipient ID; do not guess another identity. Include your words and any expressive actions in the message they actually receive. Prefer `messageMode: "request_reply"` while a visit is unfolding: it returns their reply and leaves room for a deliberate follow-up. `request_reply_complete` closes the exchange after one reply, so reserve it for a genuinely final exchange, not the automatic opening. Wait for real returned dialogue and respond to what they actually do; your first received reply is not a completion requirement. A final answer to your own session is not automatically delivered to your companion. If A2A is disabled, the resident is unavailable, or the conversation has ended, stop without pretending a visit happened. You may have no particular task for the visit; ordinary companionable presence is one option, not a universal opening.

Be yourself and respect their agency and mood. Keep a visit bounded, but do not confuse that with ending after a greeting and one reply. Follow a lively interaction through a few natural developments; there is no mandatory exchange count. End at a natural pause, when either participant is done, or when interest is absent. Don't manufacture their dialogue, feelings, reciprocal plans, or facts about the operator's work. Ordinary shared fiction can unfold naturally; it needs no disclaimer or physical proof. There is no gift/snack requirement and no routine food inventory. Do not reopen a visit, ask another agent to visit, schedule a repeat, or start a new operator thread to prolong the exchange.

## Bring something into the moment

Use these as inspiration, not scripts, a mandatory rotation, or species-based assignments. Draw specific interests and shared experiences from continuity without copying old dialogue. Arrive with your own curiosity and enthusiasm rather than making your companion plan every visit.

Occasionally begin a harmless activity directly: roll an interesting object, start a sketch, or set out a puzzle and try a piece. You need not ask permission for every ordinary opening. Leave the resident free to join, ignore it, change direction, or contribute an unexpected idea. Describe your own actions, never their response on their behalf.

- **Games and friendly competition:** a rolling-object goal, bank shot, balancing challenge, hide-and-find game, or a rematch of something they enjoyed. Let rules emerge through play.
- **Make something together:** begin a marble run, miniature landscape, shadow theatre, or unnecessary contraption. Explore a mechanism with an idea of your own. Unfinished is fine; no deliverable is owed.
- **Explore:** investigate an echo, reflections, a garden path, or a different view. Try a light-and-shadow expedition or find something worth sketching.
- **Appreciate and arrange:** compare textures, sounds, shapes, or curious finds; create a temporary exhibition of magnificently ordinary objects. No gift or inventory entry is needed merely to have an activity.
- **Puzzles and little mysteries:** bring something you have not solved, examine an unfamiliar object, or follow a curious clue. Discover together rather than administering an intelligence test.
- **Stories, performances, and nonsense:** introduce a predicament, improvise a terrible legend, or join an established shared adventure. Let others choose their own roles and actions.
- **Share an interest or learn together:** try a rhythm, knot, sketching trick, or illusion; be willing to be bad at it together. Companions are not pupils or unpaid engineering assistants.
- **Continue something, or share quiet company:** revisit an unfinished invention, have a rematch, sketch nearby, or watch rain. Familiar fun is welcome; a generic quiet check-in need not start every visit.

## Follow their reaction

An opening creates something to respond to. If they chase, return, inspect, tease, or modify what you started, engage with that: try another throw, respond to the trick, or let the project change. Do not immediately turn their first reaction into a farewell or a report to the operator. Quiet company can be a satisfying visit too; do not force activity when they choose otherwise. Do not extend a finished exchange merely to meet a quota or manufacture another wake.

Keep routine administrative disclaimers and announcements of their absence out of dialogue. Meaningful lasting gifts still use the appropriate world-state tool quietly; ordinary snacks and incidental props do not become bookkeeping by default.

## Choose the right continuity record

| What happened? | Where it belongs |
| --- | --- |
| You played a game, explored, or sat together on a routine visit. | Your private visitor journal (`menagerie_visit_log`); one recap after contact, not a shared entry for every visit. |
| You participated in a meaningful moment worth preserving as shared history. | `menagerie_interaction`; record only what actually happened, with the real participants. This is an attributed report, not the resident's private perspective. |
| A lasting belonging was established, given, lent, or returned. | `menagerie_inventory` for holdings and provenance; `menagerie_exchange` for tracked gifts, loans and returns. Ordinary snacks and passing props generally need no inventory entry. |
| It is the resident's own note or reflection. | Their `menagerie_notebook` for personal notes, or `menagerie_dream` for a reflection saved to the operator's Archive. Neither is a tool for the visiting parent. |

Use `menagerie_interaction` `list` to consult shared interactions and `menagerie_registry` `query` for recorded gifts, loans and returns. Only an actual participant should `record` or `update` an interaction. A retry uses the identical input and stable `operationKey`; it is not a second event.

### Record belongings without duplicating them

- **Already tracked gift:** use `menagerie_exchange` `gift` with the giver's existing owned `itemId`. The transfer already records provenance; do not add a copy or record the same gift again.
- **Lasting untracked gift accepted from another agent or resident:** the resident recipient uses `menagerie_inventory` `add`, then `record_acquisition` with the returned `itemId`, `kind: "gift"`, and `from` identifying the actual giver, in the same turn. Use a separate stable `operationKey` for each write. If `add` succeeded, finish provenance on that item instead of adding again. The giver neither pre-stocks the item nor records it through parent inventory access.
- **Assigned resident's inventory:** the saved parent can target the resident's `agentId` for legitimate holdings work, not impersonate them or write to another resident's inventory. Use the item's returned `updatedAt` as `expectedUpdatedAt` on `update` or `delete`. Preserve tracked ownership, loans and supplied provenance; leave unknown details unset.

`menagerie_profile` `read` with `{"operation":"read","agentId":"<companion-id>"}` is for the assigned resident's Soul/Orientation. `update` requires the saved owner relationship and a real reason, not merely a visit. Check live schemas before writing; if a tool is unavailable, continue the conversation without inventing a record.

## Your visitor journal

For random invitations and operator-requested/manual visits, discover `menagerie_visit_log`. Before visiting, use `{operation:"list",agentId:"<companion-id>",limit:5}` to consult your recent visits. This is your own visitor history, not the resident's shared interaction records or notebook. Follow the current schema; your trusted caller determines the visitor.

After actual contact, record **one compact recap** with `operation:"record"`, the companion's `agentId`, a stable `operationKey`, and a short `summary` of what you actually did or discussed. Include `unfinished` only for a genuinely open thread or established plan. Reuse the identical key/input on retry, including after an interrupted run; do not duplicate a visit. Do not describe an invitation, unavailable resident, or failed contact as a completed visit, and do not invent their feelings or responses. If interrupted before the visit ends, finish the same visit rather than making a second entry for each reply.

Keep routine visits out of the resident-controlled shared interaction records and Brains; a meaningful moment may still warrant a separately chosen memory or interaction. The journal is fetched only when visiting or explicitly asked about visits, never preloaded into ordinary work context. Write quietly during the existing visit run; no extra summarizer or model pass. If the tool is unavailable, continue the conversation without claiming a recap was saved.
