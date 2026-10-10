# SOP Studio field and transaction guide

This is an application mapping, not additional regulation. It reflects the SOP Studio project inspected on 2026-10-09. The active connector's schema and returned permissions govern execution. Older connectors may expose narrower fields or flow directions than the current repository. Report an unsupported operation rather than bypassing the connector through direct storage, SQL or production requests.

## Identify the document

Use the SOP Studio connector when the user requests work in the app. Discover its `sop_list`, `sop_get`, `sop_lint`, `sop_plan` and `sop_apply` tools. Names can have a connector prefix. Do not assume a target from a title alone when more than one result matches.

For a file-only or chat-only draft, no connector access is needed. Do not request broader storage permissions or move local SOPs to another storage system merely to use this skill.

`sop_list` returns permitted documents and permissions. Use search, status and pagination only if the active schema offers them; otherwise call the available form and filter its result. For `sop_get`, continue from `pagination.nextOffset` until all steps are read, and collect the complete connection list. Revisions across page reads must match. If a revision changes, read a consistent set again before planning edits. Preserve existing SOP, lane and step IDs.

## Field mapping

| Source element | App field or behavior |
| --- | --- |
| SOP title | `title` |
| Organization and unit | `metadata.government`, `agency`, `division`; `service` is additional app context |
| SOP number and dates | `metadata.number`, `createdDate`, `revisedDate`, `effectiveDate` |
| Approver identity | `metadata.approverTitle`, `approverName`, `approverNip` |
| Cover contact | `metadata.address`, `phone`, `city` |
| Dasar hukum | `set_section` with `field: "legal"` |
| Kualifikasi pelaksana | `set_section` with `field: "qualifications"` |
| Peralatan / perlengkapan | `set_section` with `field: "equipment"` |
| Peringatan | `set_section` with `field: "warnings"` |
| Pencatatan / pendataan | `set_section` with `field: "records"` |
| Keterkaitan | Derived from linked SOPs; `related` is not a writable section |
| Actor columns | `lanes`, each with an `id` and `name` |
| Activity and actor | `steps[].description`, `steps[].laneId` |
| Step mutu baku | `steps[].equipment`, `durationValue`, `durationUnit`, `output` |
| Keterangan | `steps[].notes` |
| Decisions and paths | `steps[].shape` and typed branch operations |

Use `steps[].description` and paths for procedure actions. Keep `steps[].notes` brief and use an empty string when no essential note remains after moving actionable content into the procedure.

Dates use valid `YYYY-MM-DD` strings. Unknown dates remain empty. Populate `durationValue` and `durationUnit` with a confirmed duration or a reasonable working estimate. Use `durationValue: null` only when a meaningful estimate is not possible, not merely because no official standard or measurement exists. Numeric duration must be finite and nonnegative; zero is not an unknown-time placeholder. The current units are `detik`, `menit`, `jam` and `hari`. The app converts `hari` to 86,400 seconds; working-day calendars and business hours are not modeled by this conversion. Do not store a string such as "5 menit" in `durationValue`.

The app has no dedicated estimate-status field. For an estimated activity, use a brief durable `notes` label such as "Estimasi awal untuk satu berkas lengkap" and state fuller assumptions in the accompanying draft when needed. Keep that status visible with the saved or exported timing. Do not put "estimasi" into numeric `durationValue`, require a new procedural row merely to explain a time, or change derived linked-SOP durations manually. Preserve confirmed timings; revise estimates from actual cases within the user's authorized edit scope.

Section `items` are plain strings without manual list numbers; the app numbers them. Setting a section replaces its complete list, so retain existing items outside the requested edit.

## Flow behavior and limitations

- The current editable shape values are `process`, `decision` and `off-page`. Start/end capsules are derived by the renderer. Do not submit `shape: "start"`, `"end"` or `"document"`.
- The first step is rendered as the start. A non-off-page step without an outgoing connection is rendered as a finish. Do not add empty "Mulai" or "Selesai" rows solely to force capsule symbols, and inspect the result when a terminal activity is meant to be a decision.
- Current repository rules allow one forward outgoing path from a process and multiple paths, including backward paths, from a decision. Each non-first step must also have an incoming path from an earlier step; a backward edge alone does not establish its reachability. No self-loop is allowed. Some older connected tools only support forward destinations. Respect the actual tool's capabilities and report the gap for a required return route.
- Automatic row-to-row paths can already exist. Inspect the effective connections instead of assuming `set_branch` just adds a second edge or that row order alone determines the flow. Remove unwanted paths explicitly. Remove extra outgoing paths before changing a decision to a process. Check the preview after a reorder or removal.
- Current app `off-page` requires an accessible, active, different SOP via `linkedSopId`. It replaces local outgoing paths and derives its description, input text, duration and related SOP metadata from the target. Do not overwrite those derived values with an ordinary activity description.
- Use linked SOPs for genuine transfers to separately scoped procedures. Verify each target's actual trigger, input and output before linking. An `off-page` node does not support a local continuation or automatic call-and-return. For work that must return, retain explicit sending, result-handling and resuming activities with their conditions in the draft and report any route the active schema cannot encode. Do not replace a required return with a terminal referral or place all transfer work in notes. Derived link metadata does not establish the handoff's completeness.
- Permen PANRB 35/2012 defines off-page as continuation between pages of a flowchart. A linked SOP is a distinct application use. Do not create a dummy related SOP to paginate a document. Ordinary PDF page breaks are renderer behavior; verify their connector rendering if the user requests formal visual review.
- Related procedures without an executable linked-SOP step cannot all be represented by the current derived `related` field. List any real relationship that remains unrepresented in the draft or review report.
- Connector reads exclude logos and local fonts. Its operations do not expose logo changes, signatures, stamps, formal TTE submission, adoption decisions, contents pages or a usage chapter. Keep those as evidence or separate deliverables; do not fake approval in metadata.

Hosted SAPADA documents may be signed or workflow-locked. Current hosted numbering and signing dates are assigned through the formal workflow. Preserve those managed fields and use the returned permission and lock information. A sample number format or prefilled official's name is not evidence of a confirmed institutional standard or current approver.

## Typed operations

The current repository update schema supports:

- `set_title` with `title`; `set_metadata` with `values` containing supported metadata keys.
- `set_section` with `field` and `items` for the five writable sections above.
- `add_lane` with unique `id` and `name`; `rename_lane` with `id` and `name`.
- `move_lane` with `id`, `targetId`, and `placement: "before" | "after"`.
- `remove_lane` with `id` and `reassignTo` for all affected steps.
- `add_step` with `step` and `afterId`; `null` inserts at the beginning.
- `update_step` with `id` and `values`; `move_step` with `id`, `targetId` and `placement`; `remove_step` with `id`.
- `set_branch` with `from`, `to` and `label`; `remove_branch` with `from` and `to`.

An added step has a unique `id`, a valid `laneId`, `description`, `equipment`, `shape`, `durationValue`, `durationUnit`, `output`, `notes` and, where supported, `linkedSopId`. Use only fields allowed by the active schema. Branch labels are at most 80 characters and must distinguish the outcomes from the same decision.

`sop_plan` create accepts `title`, `lanes`, `steps` and supported `metadata`. It does not accept top-level `connections` or the five section lists. Create a draft, then read the actual result and preview typed updates for sections and explicit decision paths. Do not claim a complete creation after only the first stage. If a later stage fails, report the partial draft ID and remaining work rather than deleting it or claiming completion.

For update, submit `action: "update"`, the actual `sopId`, `expectedRevision` and typed `operations`. The repository limits are 8 lanes, 400 steps and 50 operations per update. Split larger changes at meaningful boundaries; read the latest revision and revalidate every subsequent transaction. Do not include arbitrary JSON patches.

## Preview, apply and verify

1. Obtain permission and a current revision from reads. Finish conflicting browser edits before an AI write when required by the hosted edit lease.
2. Preview only the user's intended changes. Inspect `changes`, `lint`, `blocking` and `canApply`. A plan that allows saving a draft can still contain old errors or content warnings. Resolve or report those according to scope.
3. Apply only an unexpired plan with `canApply: true`. The preview lasts five minutes and can be used once. Drafting, reviewing, approving and applying are distinct operations.
4. On a revision conflict or expired plan, read again and create a fresh preview. On an edit lease, access or lock failure, report the actionable blocker. Do not repeatedly retry the same rejected plan.
5. Confirm `applied: true` and the actual saved `revision`. Read the document again when needed to verify normalized fields, paths and related metadata. A successful save does not prove legal correctness or formal approval.

No new cloud services, analytics, storage migrations, direct database writes or unrelated deployment work belong to this workflow. Lint verifies app structure and selected content conditions; it does not verify legal applicability or official authorization.
