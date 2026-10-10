# Alur prosedur yang mudah dipahami

Use this guide when drafting or simplifying the procedure matrix. Write for applicants, new employees and responsible officers with different levels of education and familiarity with the application. The aim is enough detail to perform the work correctly without having to decode technical terms. Preserve the format and confirmed requirements in [rules.md](rules.md).

## Write actions the reader can follow

Start Kegiatan with a familiar active verb and a concrete object, such as "Mengisi formulir pendaftaran" or "Memeriksa data pada KTP". Put the responsible actor in Pelaksana. Replace abstract phrases such as "melakukan validasi prasyarat" with the actual check. Avoid vague instructions such as "Pastikan Penggunaan Email" unless the evidence explains what must be checked; identify that missing fact instead of inventing an instruction.

Use the same name for the same thing throughout the flow. Explain necessary acronyms at first use in the relevant identity text or a short definition. Prefer "pendaftaran dengan akun Google" to "Google OAuth" and "menunggu pemeriksaan" to "pending". If a status, menu or button uses a technical label, retain its exact text with a brief explanation where needed. Do not guess application labels or translate them into names the reader cannot find.

Keep sentences short enough to understand in one reading. There is no fixed word limit. A row may contain related actions that the same person completes as one task, for example "Mengisi formulir pendaftaran dan mengirimkannya". Split when a different actor takes over, a real decision changes the route, or the work has a distinct result that needs its own inputs or timing. A long list of checks is a reason to examine the wording, not automatically to create many rows.

## Keep detail where it helps

Kegiatan states the work. Kelengkapan names the data or documents needed. Output states a concrete result such as "Formulir pendaftaran terkirim" rather than "Tahap berikutnya siap". Branch labels and destinations tell the reader what happens after a decision. Avoid repeating these contents in Keterangan.

Retain details that affect successful execution, such as the required identity number, accepted file limits, approval authority or a necessary password confirmation. Put supporting lists and file specifications in Kelengkapan or a short relevant instruction when they make Kegiatan hard to read. Keep required actions and correction routes visible in Kegiatan and the flow. Keterangan may hold a brief menu location, definition or estimate label; it must not conceal missing work.

Use a menu path when it helps the reader find a screen. Raw application routes, database field names, API behavior, internal status codes and validation algorithms belong in a technical work instruction when the task actually needs them. Do not add a separate instruction document merely to shorten a row. State the human task, such as checking that the drawn land sections do not overlap, while retaining any confirmed criterion needed to decide the result.

## Make the route clear without adding work

Draft the normal route first. Include real alternatives and correction routes, with labels such as "Lengkap" and "Belum lengkap" and a clear destination. Do not add a decision for every screen, a row for every click, or generic failure and retry branches without process evidence. An automatic system response usually belongs in Output; checking that response is a separate action only when the actor really needs to do it.

Keep ordinary corrections with the owning procedure. Reuse a linked SOP for a genuine separate service or prerequisite; explain when the reader follows it and where the procedure continues. Splitting a flow is helpful only when the resulting set is easier to follow. Detailed checks made by the author do not all need to appear as new procedural activities.

## Examples from SOP Studio

The following are wording examples based on content read on 2026-10-10. They are not saved revisions or replacement service requirements. Retain the original inputs, limits, decisions and authority when adapting them.

| Example | Wording to examine | Clearer activity or treatment |
| --- | --- | --- |
| Pendaftaran Akun SAPADA Pegawai | "Masuk ke SAPADA, membuka Pajak Saya, dan memilih Pengajuan Pegawai di /pajak-saya/pegawai." | "Masuk ke SAPADA, lalu memilih 'Pajak Saya' > 'Pengajuan Pegawai'." The menu path is enough to locate the screen. |
| Pendftaran Akun Sistem Administrasi Pajak Daerah (SAPADA) | "Memilih metode pendaftaran awal, lewat Google OAuth atau Email" | "Memilih pendaftaran dengan akun Google atau email." Keep both actual routes. |
| Pembuatan Standar Operasional Prosedur | "Menetapkan pelaksana, menyusun langkah kegiatan, dan mengisi kelengkapan, waktu, output, keterangan, simbol, serta hubungan antar langkah." | "Menyusun alur kegiatan, menetapkan pelaksana, dan melengkapi mutu baku." Explain mutu baku as kelengkapan, waktu and output in the supporting instruction. Keep the necessary symbols and connections in the flow. |
| Pengajuan dan Penelaahan Pemecahan Objek PBB-P2 melalui Pajak di Desa, activity "Menyiapkan data objek dan dasar permohonan pemecahan PBB-P2" | A short preparation activity followed by dense checks of access, active objects, prerequisites and pending requests. | Keep preparation as a meaningful task and name the supplied data in Kelengkapan. A check can read "Memeriksa akses desa, status objek pajak, dan kelengkapan data pemecahan." Explain actual unmet conditions and their route separately; do not hide them or invent extra approvals. |

## Check as a first-time reader

Read Kegiatan, Pelaksana, inputs, outputs and arrows together. Can the reader tell what starts the service, what to prepare, what they must do, what happens if a check fails and what result ends the procedure? If not, revise the specific wording or destination. Do not claim that every kind of reader understands the SOP from this desk check alone; record actual user feedback only when available.
