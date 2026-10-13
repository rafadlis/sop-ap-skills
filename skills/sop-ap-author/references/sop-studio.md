# SOP Studio field and transaction guide

This is an application mapping, not additional regulation. It reflects the SOP Studio project inspected on 2026-10-13. The connected tool schema and returned permissions govern execution; a deployed connector can be older than the repository. Report an unsupported operation rather than bypassing the connector through direct storage, SQL or production requests.

## Discover the connected contract

Use the optional SOP Studio connector when available for requested app work. If it is unavailable, draft the proposed content from supplied material and report that app reads and saves are unavailable. Discover the connector's `sop_guide`, `sop_list`, `sop_get`, `sop_lint`, `sop_plan` and `sop_apply` tools. Names can have a connector prefix. If `sop_guide` exists, use the relevant topic (`create`, `update` or `workflow`) to obtain current input JSON schemas and examples. Its output is useful when the client's tool signature shows `Array<unknown>` for lanes, steps or operations. If it is absent, inspect the actual tool schema and use the compatibility path below. Do not call an unavailable guide or send new fields to an older connector.

For a file-only or chat-only draft, no connector access is needed. Do not request broader storage permissions or move local SOPs to another storage system merely to use this skill.

`sop_list` returns permitted documents and permissions. Use search, status and pagination only if the active schema offers them; otherwise call the available form and filter its result. Do not select a target by title alone when several results match. Inspect separate `create` and `write` permissions; a legacy staged creation needs both to finish its sections and routes.

For an existing document, read `sop_get` pages using `pagination.nextOffset` until it is `null`. Collect all steps, ordered lanes and the complete effective connection list. Revisions across reads must match. If a revision changes, read a consistent set again. Preserve existing SOP, lane and step IDs. For a new document, choose short unique lane and step IDs, and use them consistently in lane assignments and connections; the server assigns the SOP ID.

## Field mapping

| Source element | App field or behavior |
| --- | --- |
| SOP title | `title` |
| Organization and unit | `metadata.government`, `agency`, `division`; `service` is additional app context |
| SOP number and dates | `metadata.number`, `createdDate`, `revisedDate`, `effectiveDate` |
| Approver identity | `metadata.approverTitle`, `approverName`, `approverNip` |
| Cover contact | `metadata.address`, `phone`, `city` |
| Dasar hukum | Create `sections.legal`; update `set_section` with `field: "legal"` |
| Kualifikasi pelaksana | Create `sections.qualifications`; update `field: "qualifications"` |
| Peralatan / perlengkapan | Create `sections.equipment`; update `field: "equipment"` |
| Peringatan | Create `sections.warnings`; update `field: "warnings"` |
| Pencatatan / pendataan | Create `sections.records`; update `field: "records"` |
| Keterkaitan | Derived from linked SOPs; `related` is not a writable section |
| Actor columns | `lanes`, each with an `id` and `name` |
| Activity and actor | `steps[].description`, `steps[].laneId` |
| Step mutu baku | `steps[].equipment`, `durationValue`, `durationUnit`, `output` |
| Keterangan | `steps[].notes` |
| Decisions and paths | `steps[].shape`, create `connections` and update typed branch operations |

Create `sections` and `connections` are supported by the upgraded schema. Older versions require typed updates after creating the initial draft. Do not place section lists in `metadata`: it only accepts its documented scalar keys. Section arrays contain plain strings without manual list numbers. Setting a section replaces its complete list, so retain existing items outside the requested edit. An empty array deliberately clears a section; omit its `set_section` operation to preserve it in an update.

Use `description` and paths for procedure actions. Keep `notes` brief and use an empty string when no essential note remains. Added ordinary steps need a unique `id`, valid `laneId` and nonempty `description`; supported defaults fill other fields, but supply equipment, numeric timing, output and estimate status for a useful SOP. Do not copy the entire read object into a strict input payload: normalized fields such as `manualRouting` or `linkedSopTitle` are not writable. Use the connected schema to distinguish writable aliases from returned fields.

Dates use valid `YYYY-MM-DD` strings. Unknown dates remain empty. Numeric `durationValue` must be finite and nonnegative, with `durationUnit` one of `detik`, `menit`, `jam` or `hari`. Use confirmed durations or reasonable working estimates; `null` is for a time that cannot meaningfully be estimated, and zero is not an unknown-time placeholder. Do not store "5 menit" in a numeric field. `hari` converts to 86,400 seconds; working days and business hours are not modeled by that conversion.

The upgraded schema also accepts optional `duration` text on create, `add_step` and `update_step`. Recognized text such as "5 menit" normalizes to numeric fields; unmeasured text such as "Sesuai kebutuhan" remains text with `durationValue: null`. Conflicting text and numeric timing is rejected. Prefer numeric `durationValue` and `durationUnit` for a predictable estimate or confirmed duration, and use the text alias only when the connected schema offers it. On an older strict schema, translate "5 menit" to `durationValue: 5, durationUnit: "menit"` and omit `duration`. Do not discard useful timing or abandon MCP merely because this alias was rejected.

There is no estimate-status field. Keep estimates visible with a brief durable `notes` label such as "Estimasi awal untuk satu berkas lengkap" and provide fuller assumptions separately when needed. Preserve confirmed timings and do not manually change derived linked-SOP timings.

Hosted SAPADA numbering and signing dates can be managed by its formal workflow. Preserve managed fields and use returned permissions and lock information. A sample number or official's name is not evidence of the institution's current standard or approver.

## Construct a complete create preview

When supported, submit `action: "create"`, `title`, `lanes`, `steps`, known scalar `metadata`, all relevant `sections`, and the complete intended `connections`. Each connection is `{from, to, label?}` using existing step IDs; do not assign a connection ID. Labels are at most 80 characters and distinguish outcomes from the same decision. A branching example is in [mcp-examples.md](mcp-examples.md).

Omitting `connections` asks the app to generate adjacent row-to-row paths. Supplying `connections` replaces that automatic flow with exactly the supplied graph. Include every intended process path and decision outcome, not just the exceptional branches. An explicit empty array means no outgoing paths; it can make later rows unreachable. Use an explicit graph for decisions, correction loops, jumps and multiple finishes so row order cannot silently add a route.

Inspect the actual candidate in the preview's changes. For creation, the full new document is returned as the `after` value of the root change. Verify its ordered lanes, steps, effective connections and section text, including fields the host normalizes. Check lint and blocking issues, apply, then read and lint the saved result. Do not call a SOP complete when sections or required branches remain unfinished.

For a connector whose create schema lacks `sections` or `connections`, create the initial draft using only accepted fields, then read it and use typed updates for complete section lists and the intended connections. Inspect generated paths before changing them. Keep the same SOP ID and latest revision across stages. If required write permission is missing, identify the limitation before creating an incomplete draft. If a later stage fails, report the partial draft's ID and remaining work; do not recreate or delete it to hide the partial result.

## Flow behavior and limitations

- Editable shapes are `process`, `decision` and `off-page`. The renderer derives start/end capsules. Do not submit `start`, `end` or `document`, or add empty "Mulai"/"Selesai" rows just to force those symbols.
- The first step always renders as the start, and a non-off-page step without an outgoing connection renders as a finish. Place the first real decision after an initiating activity when its diamond and branches must be visible. Inspect a terminal decision in the rendered output.
- A process has at most one forward outgoing path. A decision may have multiple paths and, in the upgraded version, backward paths. Every non-first step needs an incoming path from an earlier step. A backward edge alone does not establish its reachability. Self-loops are prohibited. Older connected versions may permit only forward destinations; preserve the required correction route in the draft and report the limitation.
- Existing documents can have automatic adjacent paths. Inspect effective connections before editing. Remove an unwanted process path before setting its replacement. Remove extra branches before changing a decision into a process. Operations execute in array order, so a later removal cannot repair an earlier invalid operation. Recheck routes after reordering or removing steps.
- `off-page` requires an accessible, active, different SOP via `linkedSopId` and derives description, equipment, timing and related metadata from the target. It can retain one forward local outgoing path in the current model. Do not patch those derived fields. Inspect each target's actual trigger, inputs and result before linking.
- A forward local path from an app off-page link can represent the source's continuation, but the link does not execute the target SOP or prove call-and-return. If work resumes, preserve the sending, expected result, completion evidence and named continuation activity. Inspect the connected version's capabilities and report any unsupported route. Do not replace a real continuation with a terminal referral merely because an older description says no local exit.
- The regulation's off-page symbol continues a flowchart between pages; an app link to another SOP is a distinct use. Do not create a dummy SOP for pagination. PDF page breaks are renderer behavior. Related procedures without linked steps may remain unrepresented by the derived `related` field; retain them in the accompanying draft.
- Connector reads omit logos and local fonts. Its operations do not expose signatures, stamps, formal TTE submission, adoption decisions, contents pages or a usage chapter. Keep these as evidence or separate deliverables.

## Typed updates

Submit `action: "update"`, the actual `sopId`, current `expectedRevision` from `sop_get` or a confirmed apply, and typed `operations`. Supply only fields for the chosen action even if a client advertises a flattened schema. Do not submit an arbitrary JSON patch, a full normalized document, or an entire read response.

| Operation | Fields besides `type` |
| --- | --- |
| `set_title` | `title` |
| `set_metadata` | `values` with supported scalar keys |
| `set_section` | `field`, complete `items` array |
| `add_lane` / `rename_lane` | `id`, `name` |
| `move_lane` | `id`, `targetId`, `placement: "before" \| "after"` |
| `remove_lane` | `id`, `reassignTo` for affected steps |
| `add_step` | `step`, `afterId`; `null` inserts at the beginning |
| `update_step` | `id`, `values` containing only changed writable fields |
| `move_step` | `id`, `targetId`, `placement` |
| `remove_step` | `id` |
| `set_outgoing` | `from`, complete `destinations: [{to, label?}]`; `[]` makes a finish |
| `set_branch` | `from`, `to`, optional `label` |
| `remove_branch` | `from`, `to` |

Prefer `set_outgoing` when supported to replace all paths from one source without remove/add sequencing. After inserting a step, set the previous source's destination and the inserted step's destination explicitly; automatic row routing may not join it into an edited graph. Preserve other sources' routes. Legacy `set_branch` changes one edge, so remove an unwanted edge first where required. See [mcp-examples.md](mcp-examples.md) for a focused update.

The repository limits are 8 lanes, 400 steps and 50 operations per update. Split a larger update at meaningful boundaries that each leave a valid graph, and re-read the saved revision between transactions. If an atomic change cannot fit, report that limitation rather than leaving an invalid intermediate procedure.

## Apply and recover

1. Preview only authorized changes and inspect the candidate, `changes`, `lint`, `blocking` and `canApply`. Existing errors or content warnings can survive a preview that is allowed to save; resolve or report them according to scope.
2. Apply only with `canApply: true`. A plan lasts five minutes and is single-use. Save its `planId` and candidate `sopId` so an uncertain result can be checked.
3. Confirm `applied: true`, the actual SOP ID and saved revision. Read every saved step page and run lint at that revision, checking required sections and each decision route. A save alone does not prove legal accuracy, graphical conformity or formal approval.
4. On a schema or argument error, inspect its field path and `sop_guide`, repair only the incompatible fields, then retry the preview. Planning does not save a document. A rejected `duration` field or malformed nested step is not evidence that the MCP integration is unusable. Keep the remaining valid content and use the typed tools; browser fallback is relevant only when a required operation is actually unavailable.
5. If an apply response is lost or unclear, read the candidate SOP ID and compare the intended changes before issuing another create. When a save is confirmed, continue from it. A preview or an error alone is not success.
6. On a revision conflict or expired plan, read current state and create a fresh preview; do not reuse a rejected plan. On a link-target change, refresh that target too. Stop blind retries when the same blocker persists. An edit lease, access expiry, permission or workflow lock needs the indicated user or host action, not repeated write attempts.

Existing authorization to create or edit is sufficient for routine reversible changes. No new cloud services, analytics, storage migrations, direct database writes or unrelated deployment work belong to this workflow. Lint checks application structure and selected content conditions; legal applicability and official authorization require evidence.
