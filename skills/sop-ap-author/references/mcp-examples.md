# MCP payload examples

Read [sop-studio.md](sop-studio.md) and the connected `sop_guide` before using these examples. They show the upgraded contract. An older connector can reject `sections`, `connections`, `set_outgoing` or backward destinations. Replace example facts and IDs with the user's procedure; these examples do not establish institutional requirements, legal bases or service standards.

## Create a complete branching draft

This illustrative request submits or corrects a file, checks it, registers an accepted request and returns its receipt. The completeness decision returns incomplete files to the applicant's first activity. The first real decision follows the initiating activity so its diamond is visible. All durations are provisional estimates for one file, not approved standards.

```json
{
  "action": "create",
  "title": "Penerimaan Permohonan",
  "metadata": {
    "government": "",
    "agency": "",
    "division": "",
    "number": "",
    "createdDate": "",
    "revisedDate": "",
    "effectiveDate": "",
    "approverTitle": "",
    "approverName": "",
    "approverNip": ""
  },
  "sections": {
    "legal": [],
    "qualifications": ["Mampu memeriksa berkas sesuai daftar persyaratan layanan"],
    "equipment": ["Daftar persyaratan layanan", "Berkas permohonan", "Register permohonan"],
    "warnings": ["Berkas yang belum lengkap dikembalikan untuk diperbaiki sebelum dicatat"],
    "records": ["Register permohonan", "Tanda terima permohonan"]
  },
  "lanes": [
    {"id": "pemohon", "name": "Pemohon"},
    {"id": "petugas", "name": "Petugas layanan"}
  ],
  "steps": [
    {
      "id": "ajukan",
      "laneId": "pemohon",
      "description": "Mengajukan atau memperbaiki berkas permohonan sesuai daftar persyaratan",
      "equipment": "Daftar persyaratan dan berkas permohonan",
      "shape": "process",
      "durationValue": 5,
      "durationUnit": "menit",
      "output": "Berkas permohonan untuk diperiksa",
      "notes": "Estimasi awal untuk satu berkas; waktu menyiapkan dokumen di luar layanan belum dihitung"
    },
    {
      "id": "periksa",
      "laneId": "petugas",
      "description": "Memeriksa kelengkapan berkas berdasarkan daftar persyaratan dan mengembalikan berkas yang belum lengkap kepada pemohon",
      "equipment": "Berkas permohonan dan daftar persyaratan",
      "shape": "decision",
      "durationValue": 3,
      "durationUnit": "menit",
      "output": "Hasil pemeriksaan dan berkas beserta daftar kekurangan disampaikan kepada pemohon jika belum lengkap",
      "notes": "Estimasi awal untuk satu berkas"
    },
    {
      "id": "catat",
      "laneId": "petugas",
      "description": "Mencatat permohonan yang lengkap dan menyiapkan tanda terima",
      "equipment": "Berkas lengkap dan register permohonan",
      "shape": "process",
      "durationValue": 4,
      "durationUnit": "menit",
      "output": "Nomor register dan tanda terima permohonan",
      "notes": "Estimasi awal untuk satu berkas lengkap"
    },
    {
      "id": "terima",
      "laneId": "pemohon",
      "description": "Menerima tanda terima permohonan",
      "equipment": "Tanda terima permohonan",
      "shape": "process",
      "durationValue": 1,
      "durationUnit": "menit",
      "output": "Tanda terima diterima pemohon",
      "notes": "Estimasi awal untuk satu berkas lengkap"
    }
  ],
  "connections": [
    {"from": "ajukan", "to": "periksa"},
    {"from": "periksa", "to": "catat", "label": "Lengkap"},
    {"from": "periksa", "to": "ajukan", "label": "Belum lengkap"},
    {"from": "catat", "to": "terima"}
  ]
}
```

Unknown identity fields and legal basis remain empty and produce content warnings to resolve or report. The connection list is complete: it includes ordinary paths as well as decision outcomes. Inspect the preview's root `changes[].after` and `canApply`, apply the returned plan once, and read/lint the saved SOP. Replace empty official fields only with verified facts; do not fill them from a sample.

## Replace decision outcomes in an existing SOP

Read all pages of the real SOP first. The following is a payload fragment: substitute the actual SOP ID, 64-character revision and stable step IDs from that read.

```json
{
  "action": "update",
  "sopId": "actual-sop-id",
  "expectedRevision": "0123456789abcdef0123456789abcdef0123456789abcdef0123456789abcdef",
  "operations": [
    {
      "type": "set_outgoing",
      "from": "periksa",
      "destinations": [
        {"to": "catat", "label": "Lengkap"},
        {"to": "ajukan", "label": "Belum lengkap"}
      ]
    }
  ]
}
```

`set_outgoing` replaces all paths from `periksa`; it leaves other sources unchanged. The source must already be a decision for multiple or backward destinations. Change its shape first if appropriate to the actual procedure. An empty `destinations` list deliberately makes the source a finish. When changing a decision to a process, first set at most one forward destination, then update the shape.

For insertion between two existing activities, the update normally contains `add_step`, `set_outgoing` for the previous activity pointing to the inserted ID, and `set_outgoing` for the inserted step pointing to the next ID. Read the effective graph: an edited source can retain its old destination after row insertion.

## Legacy branch update

When `set_outgoing` is absent, use `remove_branch` for each unwanted existing path followed by `set_branch` for the desired paths. `set_branch` with an existing `(from, to)` updates that edge's label. Do not remove an edge that is absent; inspect the current connections first. A process's existing outgoing path must be removed before adding a different destination. Operations execute sequentially, and a backward process destination remains unsupported.

A legacy connector that only permits forward paths cannot encode the return in the creation example. Preserve the actual correction loop in the accompanying draft and identify that capability gap. Do not invent another procedure or a fake decision to work around it.
