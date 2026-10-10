# Reading SOP Studio for a review

Use the connected SOP Studio tools only for a requested review of app documents. The active schema and grants govern access. Do not change permissions, copy private browser storage, write directly to the database or move local data to another system to perform a review.

## Complete and consistent reads

Discover `sop_list`, `sop_get` and `sop_lint` under the connector's actual prefix. Select the intended permitted SOP. Use search, status and list pagination if offered by the active schema; otherwise use the available list form. Read step pages using `pagination.nextOffset` until it is `null`. Collect all lanes and connections and verify that the revisions across pages match. If they change, read again at a consistent revision.

Record the SOP ID, title, revision, supplied approval or workflow evidence and any linked targets that could not be read. Run `sop_lint` at that revision when available. If lint refers to a different revision, refresh the evidence. Tool errors or missing pages limit the conclusions; do not claim a complete review from partial data.

## Evidence mapping

| Review element | Returned data |
| --- | --- |
| Title | `document.title` |
| Organization, number, dates and approver identity | `document.metadata` |
| Legal basis, qualifications, equipment, warnings and records | `metadata.legal`, `qualifications`, `equipment`, `warnings`, `records` |
| Actor columns | Ordered `document.lanes` with stable IDs and names |
| Activities | Ordered `document.steps` with stable IDs and `laneId` |
| Step inputs, time, output and notes | `equipment`, `durationValue`, `durationUnit`, `output`, `notes` |
| Flow logic | `shape`, `linkedSopId` and effective `document.connections` |
| Related SOPs | Linked targets and derived `metadata.related` |

Metadata lists can be stored as newline-separated text. Empty fields may indicate draft gaps. Do not infer a missing date or time from an absent field when an older schema uses a different representation; identify the format before evaluating it.

Estimated Waktu is stored as numeric `durationValue` with `durationUnit`, just like a confirmed duration. The current schema has no estimate-status field, so check a brief `notes` label and any associated draft assumptions. Do not infer an official standard from a populated number. Accept a reasonable marked estimate, recommend one for an empty draft timing when feasible, and check that its provisional status remains visible in exported material. Reserve unresolved timing for a genuinely unestimable activity or dependency. For derived linked-SOP timings, inspect the target's timing basis and any lost estimate labels; an app link does not confirm the estimate.

Read each step's `notes` with its activity and effective connections. A note containing a handoff, correction or other missing action can reveal an incomplete procedure even when lint passes. Apply the checklist's guidance on activities; an empty `notes` field alone is not a gap.

## Application behavior to account for

The current repository exposes editable `process`, `decision` and `off-page` shapes. Its renderer derives the first step and non-off-page steps without outgoing connections as start/end capsules. A missing literal `start` or `end` value in JSON is not a missing symbol finding. Check the rendered PDF for a graphical conclusion. An unlabeled decision with no outgoing path still needs content review even if the app renders it as a finish.

Current process paths move forward and allow one destination. Decision paths may include return paths, although an older connector may restrict destinations to later steps. Each non-first step needs an incoming edge from an earlier step; a backward edge alone is insufficient for app reachability. Distinguish app validation from the regulation, whose illustrated examples show return paths.

The current `off-page` node refers to an accessible, active, different SOP. It replaces local outgoing paths and derives description, equipment text, duration and related metadata from the target. The regulation's off-page symbol instead denotes a connection between different pages. Report any material representation gap. Do not recommend fake SOP links for ordinary pagination. Genuine related procedures may be omitted by the current app's derived relationship field even if the user has documented them elsewhere.

Review each linked target's trigger, input, result and completion evidence against the source handoff. An off-page link is terminal within the source graph; it does not prove that work automatically returns. If the real service resumes, check its documented return condition and named activity, and report any unsupported route. Separate an application representation gap from a missing procedural handoff. A populated derived Keterkaitan field or clean link lint cannot establish integration across the SOPs.

The connector omits logos and local fonts and does not return every form of signature or adoption evidence. Treat these as unassessed when the PDF or workflow evidence is unavailable. A declared name, an effective date, a QR or a completed workflow label alone does not establish all approval facts.

The app's `hari` duration converts to 86,400 seconds and has no working-day calendar. Review business-hour or working-day standards against the actual service policy rather than inferring them from that numeric conversion.

Lint identifies structural and selected content conditions. Warnings can allow draft saving, and old errors can remain while a change introduces none. The reported `legalReferencesVerified: false` means that legal references were not checked by lint. A clean report does not establish legal accuracy, actor authority, visual conformity or formal approval.

The app's sample legal references, initial organization and official's identity are examples. Preserve confirmed user data and identify unknown provenance instead of treating defaults as evidence.

## Corrections if also requested

A review alone uses reads. If the user explicitly requests corrections too, inspect the active `sop_plan` and `sop_apply` schema, preserve stable IDs and existing facts, preview against the actual current revision, inspect the changes and lint, and apply only with `canApply: true`. Plans expire after five minutes and are single-use. Re-read and re-plan on conflict; report a lock or permission failure. Never claim a save after a preview or a failed apply.

Section changes replace their full list. Keep unaffected items. `related` is derived rather than a writable section in the current schema. Reorder lanes by first participation without assigning new IDs. Do not request a new approval round for reversible corrections already authorized by the user, and do not submit formal TTE or impersonate an approver.
