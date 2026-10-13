# Review checklist and source map

## Source

The source is Permen PANRB Nomor 35 Tahun 2012 tentang Pedoman Penyusunan Standar Operasional Prosedur Administrasi Pemerintahan and its annex, BN 2012 Nomor 649.

- [Official JDIH BPK record](https://peraturan.bpk.go.id/Details/132829/permen-pan-rb-no-35-tahun-2012).
- [Official 63-page PDF](https://peraturan.bpk.go.id/Home/Download/123614/PERMENPAN%20NOMOR%2035%20TAHUN%202012.pdf).
- [Bundled source PDF](permenpanrb-35-2012.pdf), downloaded and checked on 2026-10-09.
- SHA-256: `665a31b3b3773d5a76f703d18c6d7ecad552bc783143db60e93f54bcbdb2baa9`.
- JDIH BPK listed it as "Berlaku" on the verification date. Check official sources again for a request about current status or later amendments.

Use one-based PDF file pages. The annex's printed page number is five lower than its PDF page number. These are source-backed content criteria; app-specific restrictions belong in the separate application reference.

## Identity and authority

Bab II.C.2.a, PDF pages 27-29, printed pages 22-24, defines 13 elements. Check each independently.

| Check | Evidence to examine |
| --- | --- |
| Organization | Correct logo and unit nomenclature; an API may omit the logo |
| SOP number | Confirmed numbering under applicable institutional tata naskah dinas |
| Creation date | Initial completion date, not drafting start date |
| Revision date | Actual revision or stated planned review date; no fabricated revision event |
| Effective date | Confirmed commencement or signing date |
| Approval | Competent official's job title, signature, name, NIP and institutional stamp or separately supplied approval evidence |
| Title | Activity and final output within confirmed duties and functions |
| Legal basis | Applicable supporting regulations and implementing rules, not merely a list copied from a sample |
| Related SOPs | Procedures directly involved in the activity; distinguish an actual dependency from similar subject matter |
| Warnings | Relevant conditional consequences, deadlines and remedies where needed |
| Qualifications | Common competencies needed for the actors' roles, not a person's biography |
| Equipment | Tools and supplies directly required by this procedure |
| Records | Forms, recorded actions and acknowledgments that show performance and handoff |

The number format is delegated to institutional tata naskah dinas; `0001/SOP-BAPENDA/2026` is not a format imposed by this regulation. A typed approver name or effective date is not proof of approval. Digital-signature sufficiency may involve rules and evidence beyond this source; do not equate a displayed QR with a verified signature or declare it invalid from appearance alone.

## Flow format and wording

Bab II.B.2, PDF pages 20-22, printed pages 15-17, requires a vertical branching flowchart, including for procedures with few activities or no decision. A linear path is acceptable within that matrix format when no real decision exists.

Allowed symbols are the capsule for start/end, rectangle for execution, diamond for decision, arrow for flow direction and pentagon for a connection between different pages. Other document, delay, preparation and same-page circle symbols do not belong to this format. Do not confuse the app's saved shape vocabulary with the graphical symbols its renderer derives.

Activity descriptions use active verbs followed by the object and necessary qualifiers, without the actor subject. The actor belongs in the separate column. A named recipient can still clarify a handoff. Actor columns follow the activity sequence rather than organizational hierarchy; the first activity starts in the leftmost actor column. Symbols do not contain the activity descriptions; decision explanations distinguish outcomes.

Figure 1 at PDF page 23 and Figure 4 at PDF page 30 show return paths. Do not flag every backward arrow as a regulatory violation. Check whether the decision criterion and labeled destinations represent a coherent correction route. Do not demand an artificial decision just to make the diagram branch.

For a graphical review, verify visible starts and ends, actual arrows and labels, symbol placement in actor columns, legibility, page continuation and absence of clipping. State when these were not assessed. F4 versus A4, font family, a minimum step count and the app's eight-actor limit are not prescribed by the cited format clauses.

## Activity quality and mutu baku

Bab II.C.2.b, PDF pages 29-30, printed pages 24-25, covers the numbered activity matrix, actors, kelengkapan, waktu, output and keterangan. Figure 4 groups kelengkapan, waktu and output under Mutu Baku, with a separate Keterangan column.

Check that inputs are sufficient, each activity has an accountable actor, times have clear units and a stated basis, and outputs are measurable and usable by subsequent steps. Distinguish confirmed standards, representative observed durations and provisional estimates. A reasonable labeled estimate is acceptable for a draft; recommend filling an empty Waktu with a working estimate when possible. Distinguish a genuinely unestimable time from a verified zero, and flag zero used merely as a placeholder. Do not treat a sum of all row times as service elapsed time when the flow contains alternative branches, correction loops, parallel work or waiting periods. This path analysis is a review method, not a separately prescribed calculation formula.

For estimated values, check that the label and assumptions remain associated with the relevant activities, including in saved or exported material. Separate active work from waiting and normal-case timing from repeated corrections or exceptional cases. Recommend comparing recorded times from actual cases or a trial with the estimates and revising the draft using those observations. Missing perfect measurements alone should not block a draft or cause an estimate to be reported as a regulatory violation. Preserve confirmed service standards and identify proposed changes separately. Filling and revising provisional Waktu is the skill's drafting default, subject to the user's explicit choices; it does not establish institutional approval.

Review `Ket.`/`Keterangan` with activities and connections. Recommend moving missing actions, decisions, handoffs and corrections into appropriate rows and routes with confirmed actors and mutu baku. Fold small qualifiers into an existing activity or decision criterion instead of adding duplicate steps. Keep necessary non-action context brief without repeating visible work or routes. Notes may be empty. Do not require a row for every verb, a fixed step count or a notes quota. Concise notes are the skill's drafting default, subject to the user's explicit choices. Cite regulatory clarity or activity criteria only when a note exposes actual ambiguous instructions, missing work or incomplete flow.

Bab I.E, PDF pages 9-11, printed pages 4-6, supplies the principles of clarity, efficiency, alignment, measurability, adaptability, user orientation, legal compliance and legal certainty. For a qualitative finding, identify the actual ambiguous instruction, redundant handoff, incompatible input or missing performance evidence.

Bab III.C.1, PDF pages 51-53, printed pages 46-48, ties identification to duties, functions, actual activity, final output and activity aspect. A useful title names the activity aspect and final output. Do not infer a unit's legal authority from its title alone.

## Readability and proportionate detail

Review the flow for readers with different levels of education and digital familiarity. Apply these checks to Kegiatan, Pelaksana, inputs, outputs and arrows together:

- Does each activity state a concrete action and object? Phrases such as "Pastikan Penggunaan Email" need an actual criterion, not a more formal synonym.
- Are words familiar and necessary acronyms explained at first use? "Pendaftaran dengan akun Google" is clearer than "Google OAuth". Keep exact menu, button and status labels when the reader needs to find them, with a brief explanation if needed.
- Does a row describe one meaningful task or result? Combine adjacent routine actions by the same actor when they form one task. Split overloaded work only for a real change of responsibility, decision or distinct result. Do not demand one row per click or verb.
- Are supporting data lists in Kelengkapan and concrete results in Output? Retain required actions and routes in the flow. Shortening a row must not conceal work in Keterangan or remove a confirmed requirement, authority or safeguard.
- Can a first-time reader follow the normal route, the documented alternatives and corrections, and identify the final result? Flag the actual missing destination or unclear label. Do not invent generic system failure, approval, recording or referral steps.
- Does each technical detail help the reader perform or decide the task? Internal routes, database names and validation mechanics need not become activities. Retain relevant file limits, identity requirements, menu paths and necessary confirmations. Automatic responses usually belong in Output unless the actor really must check them.

Use a short wording replacement or a targeted merge before recommending added rows or SOPs. Keep real checks and exception handling supported by the evidence. The skill's plain-language default guides the correction, subject to the user's explicit choices; Bab I.E, PDF pages 9-11, supports findings about actual unclear or inefficient instructions. There is no regulatory word count, reading-grade target or step limit here. A desk walkthrough is not evidence of testing by actual users.

## Scope and integration between SOPs

Simplify unclear wording and redundant activities first. Recommend manageable, integrated SOPs when evidence establishes distinct, independently useful services with their own triggers, responsibilities and completion outputs. An intermediate output or different actor alone does not justify a separate SOP. Keep ordinary applicant corrections and simple retries local. Identify the affected rows and propose boundaries with a trigger and completion output for each SOP. Compare reader effort across the whole set. A long diagram or many arrows alone does not prove a regulatory violation, and splitting must not hide necessary work or eliminate real return routes.

For each actual dependency, check the source and target titles or IDs, triggering condition, sending and receiving roles, input and case identifier, expected output, completion evidence, and whether the source ends, waits or resumes at a named activity. These checks do not require a new activity or record when existing content supplies the information. Read relevant target activities within the review scope when accessible. Match the source output to the target input and any returned result to the resuming activity. Trace rejection, unresolved and correction results as well as success. Report circular referrals without a completion condition, incompatible records, duplicate ownership and missing return destinations with their actual locations. Mark proposed, missing or inaccessible targets as unverified.

Bab II.A, PDF pages 12-17, distinguishes macro/micro and final/partial procedures. Bab I.E, PDF pages 9-11, supplies clarity and alignment principles. The Keterkaitan element in Bab II.C.2.a, PDF pages 27-29, identifies directly related procedures. Cite these for the specific issue they support. Smaller scopes and an integration table are skill drafting defaults, subject to the user's explicit choices, not a new prescribed format or step limit.

## Document and readiness scope

Bab II.C.1, PDF pages 24-26, printed pages 19-21, describes a cover, leadership adoption decision, contents list and usage explanation with scope, summary and definitions. Check these when reviewing the complete manual. For a single procedure sheet, identify that the broader manual was not supplied instead of asserting it does not exist.

Bab II.D, PDF pages 31-32, printed pages 26-27, describes hierarchical adoption. Bab III.C.4-5, PDF pages 54-55, printed pages 49-50, distinguishes simulation by the drafting team, trial involving actual actors and approval by leadership. Require evidence for a claim that these actions occurred; an AI walkthrough or clean lint result cannot establish that claim.

Bab III.D, PDF pages 55-57, printed pages 50-52, addresses implementation planning, notification, distribution and accessibility, training and supervision. The app's save action does not perform these actions. Report missing evidence in an implementation review rather than silently assuming readiness.

## Monitoring and evaluation

Bab III.E.1, PDF pages 58-60, printed pages 53-55, calls for regular monitoring every six months as well as monitoring during execution. Table 7 records No., Prosedur, Penilaian Terhadap Penerapan, Catatan Hasil Penilaian, Tindakan yang Harus Diambil and Paraf Penilai. For the implementation result, select the supported "Berjalan dengan baik" or "Tidak berjalan dengan baik" entry. Include evidence, possible causes and corrective action for a poor result. Do not supply assessor initials without evidence.

Bab III.E.2, PDF pages 60-62, printed pages 55-57, calls for regular evaluation within one year and incidental evaluation as needed. Table 8 examines:

1. Performance improvement.
2. Ease of understanding.
3. Ease of execution.
4. Actors' ability to perform their roles.
5. Ability to resolve process problems.
6. Support for organizational performance needs.
7. Consistency with other procedures.

The source permits adapting the evaluation criteria to the actual need. In its Table 8 convention, mark `X` when implementation does not meet the statement, and `-` when it does. Explain any alternative scoring scheme. Missing evidence is not a positive assessment. A proposed six-month review date is not proof of a completed review and does not authorize creating a reminder.
