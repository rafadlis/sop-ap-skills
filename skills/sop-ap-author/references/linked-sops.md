# Manageable, integrated SOPs

Use this guide when one flowchart combines distinct services or extensive exception handling. This skill defaults to keeping each SOP understandable and connecting related procedures explicitly, subject to the user's explicit drafting choices. The regulation's macro/micro and final/partial distinctions, clarity and alignment principles, and Keterkaitan element support assessing these boundaries. See [rules.md](rules.md) for their source pages. They do not prescribe a maximum number of rows or require a separate SOP for each exception.

## Choose the boundaries

Define the requested service's trigger and completion output first. Start with one understandable procedure for that scope and simplify its wording and redundant activities. Separate work when evidence establishes an independently useful service with its own trigger, responsibility and completion output. An intermediate output or a different actor alone is not a reason for another SOP. A macro SOP may coordinate several micro SOPs when that serves the requested scope. Avoid a coordinator that repeats every micro SOP's activities.

Many crossing arrows, repeated remote return paths or branches for unrelated services are reasons to examine the scope. They are not sufficient reasons to remove real decisions. Keep ordinary missing-document corrections and short retries in the owning SOP. Split substantial data maintenance or incident resolution only when it is a distinct responsibility supported by the evidence. Compare the whole set from the reader's perspective; extra titles and referrals must not make the service harder to follow. Confirm the actual titles and duties; a proposed procedure is not an existing institutional SOP.

## Define the integration

Use a short table with these fields when an actual handoff needs explanation. The fields are drafting checks; existing inputs, outputs and routes may already supply the information. Do not create an activity, approval or record for every check:

| Field | What to specify |
| --- | --- |
| Source and target | SOP titles and confirmed IDs or numbers when available; mark proposed or unread targets |
| Trigger and roles | Decision outcome or condition, sending role and receiving role |
| Input | Data or documents transferred, including the case identifier needed to match the result |
| Output and evidence | Usable result, responsible role and record of completion or referral |
| Continuation | Source ends with a stated result, waits, or resumes at a named activity after an explicit condition |
| Unsuccessful result | Rejection, unresolved issue or correction route, including its owner and return destination |

Match the source output to the target input and the target result to any resuming activity's requirements. Keep the routing decision and actual transfer in Kegiatan and the flow. Keterkaitan records the relationship; it does not replace procedural work. Fill Waktu with confirmed timings or clearly labeled working estimates, including waiting assumptions, without double-counting a linked procedure's duration. Revise estimates from actual cases across the set. Trace a case across the set to find missing work, incompatible data, circular referrals and lost correction routes.

For SOP Studio, follow [sop-studio.md](sop-studio.md). A linked off-page node refers to another SOP and can have one forward local continuation in the current model. It does not execute the target or implement an automatic return. Document the handoff, expected result and completion condition at named activities. Inspect the connected version and report any unsupported route rather than changing the real procedure.

## Example: Pendaftaran Wajib Pajak Orang Pribadi

These are candidate boundaries for a registration flow that also contains existing NIK/NOP cases, PBB-P2 object work and SIP-PBB failures. They are illustrative drafts. Use only the institution's confirmed authority, outputs and related procedures; do not invent SOP numbers, official service-time standards or legal bases. When drafting the activities, propose labeled Waktu estimates where no confirmed timing exists.

| Candidate SOP | Work and completion output | Integration with registration |
| --- | --- | --- |
| SOP Pendaftaran Wajib Pajak Orang Pribadi | Receive the request, check requirements, handle ordinary applicant corrections, register the taxpayer and communicate the recorded result. Use NPWPD as an output only when confirmed for this service. | Keep the registration route here. If NIK is already registered, verify the existing record and communicate the result or refer the requested change to its owning service. |
| SOP Pengelolaan Data Wajib Pajak | Handle taxpayer data changes or duplicate-record issues within the responsible service's duties; return the verified record or resolution status. | Transfer the identified record and requested correction. Resume registration only if it is still required and the stated readiness condition is met. |
| SOP Pengelolaan Data Objek PBB-P2 | Handle NOP, existing objects or changes in the taxpayer-object relationship when these belong to a separate service; return the confirmed object data or disposition. | Transfer the NOP and case details. State whether this ends the registration referral or supplies data needed at a named verification activity. |
| SOP Penanganan Kendala Verifikasi atau Penyimpanan | Resolve sustained data or system failures when a separate service owns the work; return a recorded resolution or unresolved status. | Keep simple retries in registration. For a separate referral, send the failed operation and relevant evidence, then define the readiness check and resume point or unresolved outcome. |

Each target may have its own branches and correction loops. Keep those inside the target and retain only the relevant decision, handoff and result handling in registration. Where an existing SOP already covers the work, reuse it instead of creating a competing procedure. In a single-SOP request, identify the needed related SOPs and their handoffs without expanding into an unrequested manual.
