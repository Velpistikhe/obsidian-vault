---
title: Project Registration Standard
document_id: GOV-007
category: governance
version: 1.0.0
status: approved
owner: owner
author: hermes-default
reviewer: owner
approved_by: owner
approved_at: 2026-11-25T08:58:26+07:00
created_at: 2026-11-24
updated_at: 2026-11-25
tags: ['ai-office', 'governance', 'projects']
---

# Project Registration Standard

## Ringkasan

Standar registrasi proyek di AI Office: arsitektur registry, informasi registrasi, alur kerja, siklus hidup proyek, kriteria aktivasi, dokumentasi wajib, penanganan proyek existing, serta monitoring dan penutupan. Publikasi Git bukan approval kebijakan ([[Document-Lifecycle]]).

Registrasi proyek **tidak** memberikan delegasi atau permission otomatis. Delegasi mengikuti [[Approval-Policy]] dan harus diberikan secara eksplisit serta dapat ditelusuri.

Proyek **Akura** tidak didaftarkan atau diubah oleh standar ini; penanganan Akura memerlukan otorisasi terpisah.

## Ownership Roles

Peran berikut dibedakan secara eksplisit; jangan disamakan:

| Peran | Tanggung jawab | Kewenangan |
|-------|----------------|------------|
| **Organizational Owner** | Otoritas strategis organisasi: charter, scope, aktivasi, dan komitmen resmi. | Satu-satunya otoritas aktivasi proyek dan perubahan approved scope. |
| **Project Owner** | Penanggung jawab tujuan bisnis, relevansi proyek, dan acceptance sesuai kewenangan. | Acceptance dan keputusan operasional dalam scope; **tidak** otomatis memiliki strategic approval authority. |
| **Project Manager** | Planning, task, milestone, dan koordinasi sesuai delegasi. | Hanya sejauh delegasi yang aktif; target role, belum aktif tanpa assignment. |

- Project Owner **tidak** otomatis memiliki strategic approval authority; jabatan tersebut bukan pengganti Organizational Owner.
- Aktivasi proyek membutuhkan **explicit Organizational Owner approval**.
- Authorized executor/publisher dapat memperbarui status berdasarkan keputusan sah tanpa memperoleh kewenangan approval (GOV-004, GOV-005).

## Registry Architecture

Struktur registry proyek di vault:

| Lokasi | Fungsi |
|--------|--------|
| `02-Projects/Project-Registry.md` | Indeks proyek: ringkasan, status, dan referensi — bukan duplikasi penuh Project Profile. |
| `02-Projects/{Project-Name}/Project-Profile.md` | Profil registrasi **otoritatif** untuk identitas dan metadata proyek di vault. |
| Folder `02-Projects/{Project-Name}/` | Dokumentasi manajemen proyek lain sesuai kebutuhan (charter, scope, plan, dll.). |

Prinsip:

- Registry memuat **ringkasan dan referensi** (`[[Project-Profile]]`, wikilink, ID), bukan menyalin seluruh isi Project Profile.
- `{Project-Name}` mengikuti [[Naming-Conventions]] (Pascal-Case folder).
- Hubungkan identitas proyek dengan: assigned agents, delegasi, repository, workspace, knowledge location, dan referensi Kanban native (bila tersedia).
- SSOT per jenis informasi mengikuti [[Information-Architecture]]; registrasi vault tidak menggantikan SSOT kode atau engineering di GitHub Project Repository.

Pembuatan atau aktivasi file registry aktual (Project-Registry.md, folder proyek) memerlukan otorisasi terpisah; standar ini tidak membuat registry atau template operasional.

## Registration Information

Field registrasi proyek (konseptual; skema final dapat diperkaya pada template terpisah setelah disetujui):

| Field | Keterangan | Nullabilitas |
|-------|------------|--------------|
| `project_id` | Identitas organisasi unik (format `PRJ-NNN` mengikuti [[Naming-Conventions]]). | `null` sampai alokasi ID. |
| `project_name` | Nama proyek; selaras dengan folder vault. | Wajib. |
| `description` | Ringkasan tujuan dan konteks (1–3 paragraf). | Wajib. |
| `project_owner` | Project Owner: penanggung jawab tujuan bisnis, relevansi proyek, dan acceptance (lihat Ownership Roles). | `null` sampai ditetapkan. |
| `project_manager` | Project Manager: planning, task, milestone, koordinasi sesuai delegasi (target role; **belum aktif** tanpa assignment). | `null` jika belum ditetapkan. |
| `project_status` | Status siklus hidup proyek (lihat bagian Project Lifecycle). | Wajib. |
| `repository` | GitHub Project Repository (org/repo atau URL) — SSOT kode. | `null` jika belum ada. |
| `knowledge_location` | Path vault proyek (biasanya `02-Projects/{Project-Name}/`). | `null` sampai folder dibuat; wajib setelah folder dibuat. |
| `workspace_location` | Hermes workspace atau path kerja yang ditetapkan. | `null` jika belum dialokasikan. |
| `kanban_reference` | Referensi native Kanban (board/project ID) bila integrasi tersedia. | `null` — status integrasi Kanban **Pending Verification** (GOV-008, GOV-002), dicatat terpisah. |
| `assigned_agents` | Daftar agent yang di-assign (setelah aktivasi role/agent). | `[]` jika belum ada assignment. |
| `approval_references` | Daftar referensi approval; tiap entri memuat jenis approval yang dapat ditelusuri untuk charter, scope, activation, dan perubahan berikutnya (`APR-NNNNNN` bila dialokasikan). | `[]` jika belum ada approval sah. |
| `delegation_references` | Daftar `DEL-NNNNNN` delegasi aktif terkait proyek. | `[]` jika tidak ada delegasi. |
| `created_at` | Tanggal registrasi awal (`YYYY-MM-DD`, Asia/Jakarta). | Wajib; tidak diubah kecuali koreksi metadata terbukti salah. |
| `updated_at` | Tanggal pembaruan registrasi terakhir. | Wajib diperbarui saat perubahan. |

Aturan nilai metadata:

- Nilai tunggal yang belum tersedia: **`null`**.
- Koleksi yang belum memiliki anggota: **`[]`**.
- Status seperti `pending_verification` atau `not_applicable` dicatat pada field status terpisah bila diperlukan — **bukan** sebagai nilai ID atau path.
- Jangan mengisi placeholder seolah-olah resource atau assignment sudah operasional.
- `approval_references` berupa **array** referensi approval, dengan jenis approval yang dapat ditelusuri untuk charter, scope, activation, dan perubahan berikutnya.

Contoh ilustratif (bukan skema final dan bukan alokasi aktual):

```yaml
project_id: PRJ-001
project_name: Example Project
project_status: planning
project_manager: null
repository: null
workspace_location: null
kanban_reference: null
assigned_agents: []
approval_references: []
delegation_references: []
```

Alokasi `project_id` dan ID terkait mengikuti mekanisme terpusat [[Naming-Conventions]]; periksa namespace dan registry sebelum alokasi. Standar ini **tidak** mengalokasikan ID aktual.

## Registration Workflow

Alur registrasi proyek (organisasi):

```text
Initiation → Assessment → Identity Allocation → Resource Registration →
Documentation → Review → Owner Approval → Authorized Assignment →
Activation → Monitoring
```

| Tahap | Kegiatan utama | Otoritas / catatan |
|-------|----------------|--------------------|
| Initiation | Permintaan atau identifikasi proyek baru. | Inisiator / Project Owner. |
| Assessment | Kelayakan, risiko awal, ketergantungan, kesesuaian AI Office. | Document owner / Organizational Owner. |
| Identity Allocation | Alokasi `project_id`, penamaan folder, entri registry (setelah otorisasi). | Pihak berwenang alokasi ID. |
| Resource Registration | Repository, workspace, referensi Kanban (jika perlu dan tersedia). | Sesuai assignment; tidak otomatis. |
| Documentation | Project Profile, charter, scope, plan, dan dokumen wajib lain. | Author terotorisasi. |
| Review | Kelengkapan, konsistensi SSOT, gap dokumen. | Reviewer ditugaskan. |
| Owner Approval | Persetujuan registrasi, charter, dan scope resmi. | **Organizational Owner** — wajib sebelum aktivasi. |
| Authorized Assignment | Assignment agent, delegasi eksplisit (bukan implisit dari registrasi). | [[Approval-Policy]]. |
| Activation | Proyek memasuki status `active` bila memenuhi kriteria aktivasi. | **Organizational Owner** — explicit approval; Project Owner tidak memiliki kewenangan ini secara otomatis. |
| Monitoring | Pelaporan, penerimaan, penutupan, arsip. | Sesuai kewenangan di bawah. |

**Kanban initialization** dilakukan apabila integrasinya tersedia, diverifikasi, dan diperlukan untuk koordinasi operasional; bukan prasyarat mutlak setiap proyek. Status integrasi: **Pending Verification** ([[Information-Architecture]]).

## Project Lifecycle

Status siklus hidup **proyek** (terpisah dari document lifecycle [[Document-Lifecycle]] dan status task Kanban):

| Status | Makna |
|--------|--------|
| `proposed` | Ide atau inisiatif proyek; belum assessment formal. |
| `planning` | Assessment dan perencanaan; dokumentasi disiapkan. |
| `pending_approval` | Menunggu keputusan Organizational Owner untuk charter/scope/aktivasi; tetap berlaku sampai ada keputusan. |
| `active` | Proyek diotorisasi dan berjalan sesuai scope approved. |
| `on_hold` | Sementara dihentikan (jalur **opsional**); pekerjaan utama ditangguhkan dengan otorisasi. |
| `completed` | Deliverable diterima; pekerjaan proyek selesai. |
| `archived` | Proyek tidak aktif; dokumentasi dipertahankan untuk referensi. |

### Transisi dan otoritas (ringkas)

| Dari | Ke | Otoritas tipikal |
|------|-----|------------------|
| `proposed` | `planning` | Project Owner / Organizational Owner. |
| `planning` | `pending_approval` | Author / Project Owner. |
| `pending_approval` | `active` | **Organizational Owner** setelah memenuhi kriteria aktivasi. |
| `pending_approval` | `planning` | Organizational Owner menolak atau meminta revisi. |
| `active` | `on_hold` | Organizational Owner, atau Project Owner dengan otorisasi. |
| `on_hold` | `active` | **Organizational Owner** — aktivasi kembali memenuhi kriteria aktivasi. |
| `active` | `completed` | Project Owner / penerima yang berwenang setelah acceptance. |
| `completed` | `archived` | Organizational Owner atau otorisasi pengarsipan. |
| `*` | `archived` | Organizational Owner untuk penghentian permanen sesuai kebijakan. |

Seluruh transisi ke `active` memerlukan **explicit Organizational Owner approval**; Project Owner tidak memiliki kewenangan aktivasi secara otomatis. Authorized executor/publisher dapat memperbarui `project_status` berdasarkan keputusan sah tanpa memperoleh kewenangan approval (GOV-004).

### Jalur penutupan (closure)

Tidak ada status baru; seluruh jalur berikut memakai status yang sudah ada:

| Jalur | Status akhir | Keterangan |
|-------|--------------|------------|
| Successful completion | `completed` → `archived` | `completed` ditetapkan setelah acceptance; `archived` hanya bila diotorisasi. |
| Permanent termination | `archived` | Disertai alasan penghentian. |
| Temporary suspension | `on_hold` | Dapat kembali `active` melalui aktivasi oleh Organizational Owner. |
| Permanent rejection | `archived` | Disertai referensi keputusan penolakan. |

- `archived` **tidak** otomatis berarti proyek berhasil diselesaikan; keadaan tersebut hanya dinyatakan oleh jalur successful completion.
- Seluruh perubahan approved project scope tetap membutuhkan Organizational Owner approval (lihat bagian Scope and Monitoring).

**Pemisahan lifecycle:**

- **Project lifecycle** — status proyek di atas.
- **Document lifecycle** — `draft` → `approved` dll. untuk dokumen kebijakan/proyek ([[Document-Lifecycle]]).
- **Kanban task status** — SSOT operasional task setelah integrasi tersedia; bukan pengganti status proyek.

## Activation Criteria

Aktivasi proyek (`pending_approval` → `active`, termasuk kembali dari `on_hold` → `active`) memerlukan **semua** persyaratan berikut kecuali yang secara eksplisit ditandai opsional:

1. **Project identity** — `project_id` dialokasikan dan tercatat.
2. **Project Profile** — profil registrasi otoritatif tersedia di vault.
3. **Approved project charter** — disetujui Organizational Owner.
4. **Approved project scope** — disetujui Organizational Owner.
5. **Reviewed project plan** — Project Plan telah direview sesuai kewenangan. Project Plan mengikuti review/approval operasional sesuai [[Approval-Policy]]; review tersebut tidak mengubah scope atau komitmen resmi.
6. **Resource references** — repository, knowledge location, dan referensi relevan (workspace, Kanban jika dipakai) terdokumentasi. Resource yang belum tersedia **tidak boleh** dijadikan dasar untuk menjalankan pekerjaan yang bergantung padanya; field yang belum terisi berisi `null` dan keterlambatannya dicatat pada field status terpisah hanya bila eksplisit ditunda.
7. **Risk/blocker assessment** — risiko dan blocker awal terdokumentasi.
8. **Required delegations active** — jika pekerjaan membutuhkan delegated authority, delegasi harus **eksplisit** dan aktif ([[Approval-Policy]]); registrasi saja tidak mencukupi.
9. **Authorized operational workflow** — alur kerja operasional yang diotorisasi untuk proyek tersebut tersedia dan sesuai governance yang berlaku.
10. **Explicit Organizational Owner approval** — persetujuan aktivasi tercatat (`approval_references` bila menggunakan skema approval). Project Owner tidak dapat menggantikan persetujuan ini.

**Bukan prasyarat mutlak** untuk semua proyek:

- Inisialisasi Kanban.
- Pembentukan atau aktivasi Specialist Agents.
- Delegasi proyek otomatis akibat registrasi.

## Required Documentation

### Obsidian Vault

| Dokumen | Keterangan |
|---------|------------|
| Project Profile | Registrasi otoritatif proyek. |
| Project Charter | Otoritas dan tujuan proyek; Organizational Owner approval. |
| Project Scope | Ruang lingkup resmi; perubahan mengikuti [[Approval-Policy]]. |
| Project Plan | Perencanaan tingkat proyek. |
| Business Requirements, Business Process, UAT criteria | Jika relevan dengan jenis proyek. |

### GitHub Project Repository

| Dokumen | Keterangan |
|---------|------------|
| Technical Architecture | Detail engineering (SSOT repo). |
| API Specification | Sesuai jenis sistem. |
| Technical ADR | Keputusan teknis; approval rutin dapat mengikuti delegasi proyek **jika** aktif. |
| Testing Documentation | Strategi dan bukti pengujian. |
| Deployment Documentation | Prosedur deploy; production mengikuti [[Approval-Policy]]. |

Dokumentasi engineering disesuaikan dengan jenis proyek; tidak semua kategori wajib untuk setiap proyek kecil, tetapi gap harus disetujui dalam assessment.

**Kanban** menjadi target SSOT informasi task operasional setelah integrasi tersedia dan diverifikasi; saat ini integrasi **Pending Verification**.

## Existing Project Registration

Untuk proyek yang sudah berjalan sebelum standar ini berlaku:

```text
Discovery → Assessment → Gap Analysis → Migration Proposal →
Authorization → Registration → Activation
```

- **Discovery** — Inventarisasi dokumentasi, repo, dan artefak existing.
- **Assessment** — Kesesuaian dengan AI Office SSOT dan risiko migrasi.
- **Gap analysis** — Bandingkan terhadap field dan dokumen wajib standar ini.
- **Migration proposal** — Rencana tanpa menghapus atau memigrasi otomatis.
- **Authorization** — Organizational Owner menyetujui pendekatan.
- **Registration** — Project Profile dan entri registry setelah otorisasi.
- **Activation** — Status lifecycle diselaraskan; memenuhi kriteria aktivasi.

Aturan:

- Periksa dokumen dan **approval existing** sebelum membuat dokumen baru duplikat.
- **Jangan** melakukan migrasi otomatis atau menghapus dokumen lama.
- Approval existing yang sah dapat **dipertahankan** setelah bukti dan relevansi diverifikasi.
- Proyek Akura: di luar cakupan standar ini; penanganan memerlukan otorisasi terpisah.

## Scope and Monitoring

### Perubahan scope

**Seluruh perubahan terhadap approved project scope** memerlukan Organizational Owner approval sesuai [[Approval-Policy]] — bukan hanya perubahan yang dinilai material.

Penyesuaian operasional **dalam** approved scope (task tambahan, urutan kerja, detail implementasi, jadwal internal) dapat dilakukan berdasarkan delegasi atau assignment yang masih berlaku, tanpa mengubah dokumen scope resmi.

### Monitoring, reporting, acceptance, completion, archiving

| Aktivitas | Panduan |
|-----------|---------|
| Monitoring | Progress terhadap plan dan milestone; status proyek diperbarui di Project Profile dan laporan berkala. |
| Reporting | Snapshot bertanggal di vault boleh merangkum status; live task status targetnya Kanban setelah integrasi ([[Knowledge-Management-Policy]]). |
| Acceptance | Kriteria UAT/acceptance disepakati dalam scope; Project Owner atau penerima yang berwenang. |
| Completion | Transisi ke `completed` setelah acceptance; dokumentasi penutupan. |
| Archiving | Transisi ke `archived` dengan otorisasi; mengikuti [[Document-Lifecycle]] untuk dokumen proyek. |

Delegasi operasional **tidak** menggantikan Organizational Owner approval untuk scope, charter, atau aktivasi agent/permission.

## Dokumen terkait

- [[Information-Architecture]]
- [[Naming-Conventions]]
- [[Approval-Policy]]
- [[Document-Lifecycle]]
- [[Knowledge-Management-Policy]]
- [[AI-Office-Charter]]
