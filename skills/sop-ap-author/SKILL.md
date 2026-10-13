---
name: sop-ap-author
description: "Create, edit or simplify Indonesian government SOP AP, including saving complete drafts through SOP Studio MCP, with plain-language activities, clear routes and mutu baku under Permen PANRB 35/2012. Use for SOP content, not application development."
---

# Draft SOP AP

Create an Indonesian SOP AP draft grounded in the user's actual procedure and Permen PANRB Nomor 35 Tahun 2012. A saved draft is not an institutional approval.

This skill defaults to plain language, labeled provisional Waktu estimates, concise Keterangan and manageable SOP scopes. Follow the user's explicit drafting choices when they differ, while preserving confirmed requirements and authority. These defaults do not add regulatory requirements.

## Read the relevant references

- Read [references/rules.md](references/rules.md) for the drafting requirements and exact PDF page references. The original regulation and annex are included at [references/permenpanrb-35-2012.pdf](references/permenpanrb-35-2012.pdf).
- Read [references/plain-language.md](references/plain-language.md) when writing or simplifying alur prosedur. It covers activity wording, useful detail and examples from SOP Studio.
- For a request to create or change a SOP in SOP Studio, also read [references/sop-studio.md](references/sop-studio.md). Discover `sop_guide` when available to obtain the connected version's input schemas; read [references/mcp-examples.md](references/mcp-examples.md) when constructing a creation or branch payload. The connected schema determines supported fields.

SOP Studio is an optional integration. If its connector is unavailable, draft from supplied PDFs, JSON or process notes. For a requested app edit, deliver the proposed content and report that app reads and saves are unavailable; do not claim that the document was changed.

## Establish the procedure

Use the supplied SOP, process notes, service standard, organizational duties and regulations. Identify the responsible unit, trigger, final output, actors, inputs, decisions, exceptions and evidence of completion. For a revision, preserve the existing scope and confirmed facts unless the user requests changes.

Ask only for missing information that changes the procedure or authority. Continue drafting the parts supported by the evidence. Record unknown SOP numbers, dates, approver identities, official service-time standards and legal references as unresolved; do not manufacture official facts. Missing measured times need not block a draft; fill Waktu with working estimates as described below. User-supplied legal citations can be retained with their verification status. Verify new legal citations against official sources before treating them as established. Do not copy officials or regulations from the app's sample SOP into a different procedure.

For an inventory request, trace tugas, fungsi, uraian tugas, kegiatan, final output and activity aspect before proposing titles. For a single SOP, derive the title from the activity aspect and final output. Keep the procedure inside the unit's confirmed duties.

## Choose manageable, integrated SOPs

Choose the simplest complete procedure within the requested scope. Simplify wording and combine redundant activities before proposing more SOPs. Use several directly related SOPs when evidence establishes independently useful services with distinct triggers, responsibilities and completion outputs. Check that the set reduces reader effort rather than adding referrals. Keep ordinary completeness checks, applicant corrections and simple retries within their owning SOP. Do not create a separate SOP for every branch or impose a fixed activity, branch or page limit. For a limited revision, recommend a scope change separately unless restructuring is already authorized.

Reuse an existing related SOP when its scope and output fit. Keep the referring SOP's decision, handoff and continuation, and leave the target's internal activities in the target SOP. Record genuine dependencies in Keterkaitan. For each actual handoff, check the target, triggering condition, sending and receiving roles, required input, expected output, completion evidence and whether the source ends, waits or resumes at a named activity. These are drafting checks, not a requirement to add a row or record for each item. Preserve real rejection and correction routes across the SOPs.

Read [references/linked-sops.md](references/linked-sops.md) when proposing boundaries or drafting an integrated set. It includes a Pendaftaran Wajib Pajak Orang Pribadi example. This drafting default supports manageable procedures; it is not an additional regulatory requirement or permission to create unrequested app documents.

## Write the draft

Write the identity sheet and procedure matrix in Bahasa Indonesia unless the user requests another language. Follow the source rules for each part:

Make alur prosedur understandable to applicants, new employees and officers with different levels of education and digital familiarity. Use familiar Indonesian words and concrete actions. Explain necessary acronyms at first use and retain exact menu or button names when they help the reader. Keep implementation details and speculative system failures out of the activity text. Plain language must preserve confirmed requirements, authority and safeguards.

- Fill the identity elements from known facts. Separate common actor competencies from per-step inputs and equipment. State concrete conditional warnings and the records needed to demonstrate completion.
- Order actor columns by their first participation in the activity sequence. The first activity starts in the leftmost actor column. Preserve lane IDs when reordering an existing document.
- Write each activity with an active verb, object and needed qualifier, without the actor as its grammatical subject. For example, use "Memeriksa kelengkapan berkas permohonan" and assign its actor separately.
- Give each row one meaningful task or result. Combine adjacent routine actions by the same actor when they form one task; separate them when responsibility, a real decision or a distinct result requires it. Do not turn every click, automatic response or verb into another row.
- Use the vertical branching flowchart format even for a short linear procedure. Add decision branches only when the process contains a real decision. Give each decision its criterion, labeled outcomes and a defined destination.
- Supply kelengkapan, Waktu with a numeric duration and unit, and a verifiable output for each activity. Preserve confirmed durations and use applicable confirmed standards first. Otherwise use representative observed durations or propose a reasonable initial estimate in Waktu. Mark estimates clearly as "Estimasi awal" and state their normal-case assumptions. Add keterangan only when necessary.
- Use terminator, process, decision, arrow and off-page connector according to their meanings. Put activity descriptions in the activity column, not inside the symbols. A separate document symbol is not part of this SOP AP format.

Prefer a filled, revisable Waktu over an empty field merely because no measurement or official standard is available. Base estimates on the activity, actor, inputs, workload and expected system response; use rounded values rather than false precision. Identify estimated rows in a brief note or an associated estimate table that stays with the draft. Keep a time unresolved only when a meaningful estimate is not possible, and never use zero as a placeholder. After actual cases or a trial, compare recorded times with the estimates and revise them with the observed basis. Distinguish active work, waiting and repeated corrections. Do not present estimates as approved standards or silently replace established institutional or regulatory limits. This is the skill's drafting default, not an additional regulatory requirement.

Put the work in Kegiatan. When `Ket.` / Keterangan describes an action, decision, handoff or correction, incorporate it into the appropriate activity or create a distinct step when it has its own actor, output or place in the flow. Keep small qualifiers with the existing activity and avoid unnecessary splits. Reserve Keterangan for brief, essential context; leave it empty when unnecessary and avoid repeating activities, mutu baku or branch labels. Apply this as the skill's drafting default, not an additional regulatory requirement.

Trace the normal route and each exception route supported by the procedure or evidence. Do not invent approval, logging, retry or referral work for hypothetical failures. Check that outputs support the next activity's inputs and that returned work has a stated correction route. Do not replace a real return loop with a different process to satisfy a tool limitation.

Before delivery, read the flow as a first-time user. Can the reader identify what to prepare, what to do, which branch to follow, who receives the result and when the procedure ends? Revise any wording or route that requires guessing. This desk check does not establish that actual users have tested the SOP.

When an actor has no activity, verify whether the procedure is incomplete or that column is unnecessary. Keep genuine related procedures even if the current app cannot encode every relationship.

## Deliver or apply

For a complete SOP draft, return the identity sheet, a matrix with No., Kegiatan, Pelaksana, Kelengkapan, Waktu, Output and Keterangan, and explicit branch destinations. For wording examples or limited revisions, return the affected content and any needed routes. Match the deliverable to the request. List unresolved facts and any material implementation limits that affect it. A table alone does not establish that the graphical flowchart was verified.

For multiple integrated SOPs, also return a short integration table showing their boundaries and handoffs. Walk the normal route and relevant exceptions across the set, including any return to the source SOP. Identify proposed targets separately from existing verified SOPs and name any missing dependency or unsupported continuation.

For an authorized SOP Studio creation, prefer one complete preview containing the identity, sections, steps and explicit connections when the connected schema supports them. For an edit, read the current document and all its step pages and preserve stable IDs. Inspect the preview's actual candidate, changes and lint, apply only with `canApply: true`, then read and lint the saved result. A preview is not a saved change. If the connected version requires staged creation, finish the sections and routes before calling the SOP complete. Check the candidate SOP ID before retrying an apply whose outcome is unknown so a saved draft is not duplicated. Existing authorization for the edit is sufficient; do not add an approval round for routine reversible edits.

For a complete institutional SOP manual, include or identify the cover, adoption decision, table of contents and usage explanation. Do not invent the adoption decision, signature or stamp. If these are outside the editor's fields, provide them separately or identify the gap.

Finish with what was drafted or saved, what evidence was checked and what remains unresolved. Distinguish content review, visual verification, simulation with the drafting team, trial with actual actors and formal approval. Report a simulation or trial as completed only when there is evidence it occurred.
