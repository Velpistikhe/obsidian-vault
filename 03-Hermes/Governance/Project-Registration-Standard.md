---
title: Project Registration Standard
document_id: GOV-007
category: governance
version: 0.2.0
status: draft
owner: owner
author: hermes-default
reviewer: null
approved_by: null
approved_at: null
created_at: 2026-11-24
updated_at: 2026-11-25
tags: ['ai-office', 'governance', 'draft', 'projects']
---

# Project Registration Standard

## Ringkasan

Standar registrasi proyek di AI Office: arsitektur registry, informasi registrasi, alur kerja, siklus hidup proyek, kriteria aktivasi, dokumentasi wajib, penanganan proyek existing, serta monitoring dan penutupan. Dokumen ini **draft**; publikasi Git bukan approval kebijakan ([[Document-Lifecycle]]).

Registrasi proyek **tidak** memberikan delegasi atau permission otomatis. Delegasi mengikuti [[Approval-Policy]] dan harus diberikan secara eksplisit serta dapat ditelusuri.

Proyek **Akura** tidak didaftarkan atau diubah oleh tugas revisi ini; penanganan Akura memerlukan tugas terpisah yang diotorisasi.

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

Pembuatan atau aktivasi file registry aktual (Project-Registry.md, folder proyek) memerlukan otorisasi terpisah; tugas revisi ini **tidak** membuat registry atau template operasional.

## Registration Information

Field registrasi proyek (konseptual; skema final dapat diperkaya pada template terpisah setelah disetujui):

| Field | Keterangan | Nullabilitas |
|-------|------------|--------------|
| `project_id` | Identitas organisasi unik (format `PRJ-NNN` mengikuti [[Naming-Conventions]]). | Wajib setelah alokasi ID. |
| `project_name` | Nama proyek; selaras dengan folder vault. | Wajib. |
| `description` | Ringkasan tujuan dan konteks (1–3 paragraf). | Wajib. |
| `project_owner` | Otoritas proyek (default: Owner organisasi kecuali ditetapkan lain). | Wajib. |
| `project_manager` | Penanggung jawab operasional proyek (target role; **belum aktif** tanpa assignment). | `null` / `pending` jika belum ditetapkan. |
| `project_status` | Status siklus hidup proyek (lihat bagian Project Lifecycle). | Wajib. |
| `repository` | GitHub Project Repository (org/repo atau URL) — SSOT kode. | `null` / `pending` jika belum ada. |
| `knowledge_location` | Path vault proyek (biasanya `02-Projects/{Project-Name}/`). | Wajib setelah folder dibuat. |
| `workspace_location` | Hermes workspace atau path kerja yang ditetapkan. | `null` / `pending` jika belum dialokasikan. |
| `kanban_reference` | Referensi native Kanban (board/project ID) bila integrasi tersedia. | `null` / `pending` — integrasi Kanban **Pending Verification** (GOV-002). |
| `assigned_agents` | Daftar agent yang di-assign (setelah aktivasi role/agent). | `null` / `pending` jika belum ada assignment. |
| `approval_reference` | Referensi approval registrasi/charter (`APR-NNNNNN` bila dialokasikan). | `null` sampai approval sah. |
| `delegation_references` | Daftar `DEL-NNNNNN` delegasi aktif terkait proyek. | `null` / kosong jika tidak ada delegasi. |
| `created_at` | Tanggal registrasi awal (`YYYY-MM-DD`, Asia/Jakarta). | Wajib; tidak diubah kecuali koreksi metadata terbukti salah. |
| `updated_at` | Tanggal pembaruan registrasi terakhir. | Wajib diperbarui saat perubahan. |

Resource atau assignment yang belum tersedia harus ditandai **`null`**, **`pending`**, atau nilai setara yang eksplisit — jangan mengisi placeholder seolah-olah sudah operasional.

Alokasi `project_id` dan ID terkait mengikuti mekanisme terpusat [[Naming-Conventions]]; periksa namespace sebelum alokasi. Tugas ini **tidak** mengalokasikan ID aktual.

## Registration Workflow

Alur registrasi proyek (organisasi):

```text
Initiation → Assessment → Identity Allocation → Resource Registration →
Documentation → Review → Owner Approval → Authorized Assignment →
Activation → Monitoring
```

| Tahap | Kegiatan utama | Otoritas / catatan |
|-------|----------------|--------------------|
| Initiation | Permintaan atau identifikasi proyek baru. | Inisiator / Owner. |
| Assessment | Kelayakan, risiko awal, ketergantungan, kesesuaian AI Office. | Document owner / Owner. |
| Identity Allocation | Alokasi `project_id`, penamaan folder, entri registry (setelah otorisasi). | Pihak berwenang alokasi ID. |
| Resource Registration | Repository, workspace, referensi Kanban (jika perlu dan tersedia). | Sesuai assignment; tidak otomatis. |
| Documentation | Project Profile, charter, scope, plan, dan dokumen wajib lain. | Author terotorisasi. |
| Review | Kelengkapan, konsistensi SSOT, gap dokumen. | Reviewer ditugaskan. |
| Owner Approval | Persetujuan registrasi, charter, dan scope resmi. | **Owner** — wajib sebelum aktivasi. |
| Authorized Assignment | Assignment agent, delegasi eksplisit (bukan implisit dari registrasi). | [[Approval-Policy]]. |
| Activation | Proyek memasuki status `active` bila memenuhi kriteria aktivasi. | Owner / project owner. |
| Monitoring | Pelaporan, penerimaan, penutupan, arsip. | Sesuai kewenangan di bawah. |

**Kanban initialization** dilakukan apabila integrasinya tersedia, diverifikasi, dan diperlukan untuk koordinasi operasional; bukan prasyarat mutlak setiap proyek. Status integrasi: **Pending Verification** ([[Information-Architecture]]).

## Project Lifecycle

Status siklus hidup **proyek** (terpisah dari document lifecycle [[Document-Lifecycle]] dan status task Kanban):

| Status | Makna |
|--------|--------|
| `proposed` | Ide atau inisiatif proyek; belum assessment formal. |
| `planning` | Assessment dan perencanaan; dokumentasi disiapkan. |
| `pending_approval` | Menunggu keputusan Owner untuk charter/scope/aktivasi; tetap berlaku sampai ada keputusan. |
| `active` | Proyek diotorisasi dan berjalan sesuai scope approved. |
| `on_hold` | Sementara dihentikan (jalur **opsional**); pekerjaan utama ditangguhkan dengan otorisasi. |
| `completed` | Deliverable diterima; pekerjaan proyek selesai. |
| `archived` | Proyek tidak aktif; dokumentasi dipertahankan untuk referensi. |

### Transisi dan otoritas (ringkas)

| Dari | Ke | Otoritas tipikal |
|------|-----|------------------|
| `proposed` | `planning` | Project owner / Owner. |
| `planning` | `pending_approval` | Author / project owner. |
| `pending_approval` | `active` | **Owner** setelah memenuhi kriteria aktivasi. |
| `pending_approval` | `planning` | Owner menolak atau meminta revisi. |
| `active` | `on_hold` | Owner atau project owner dengan otorisasi. |
| `on_hold` | `active` | Owner atau project owner. |
| `active` | `completed` | Owner / project owner setelah acceptance. |
| `completed` | `archived` | Owner atau otorisasi pengarsipan. |
| `*` | `archived` | Owner untuk penghentian permanen sesuai kebijakan. |

**Pemisahan lifecycle:**

- **Project lifecycle** — status proyek di atas.
- **Document lifecycle** — `draft` → `approved` dll. untuk dokumen kebijakan/proyek ([[Document-Lifecycle]]).
- **Kanban task status** — SSOT operasional task setelah integrasi tersedia; bukan pengganti status proyek.

## Activation Criteria

Aktivasi proyek (`pending_approval` → `active`) memerlukan **semua** persyaratan berikut kecuali yang secara eksplisit ditandai opsional:

1. **Project identity** — `project_id` dialokasikan dan tercatat.
2. **Project Profile** — profil registrasi otoritatif tersedia di vault.
3. **Approved project charter** — disetujui Owner.
4. **Approved project scope** — disetujui Owner.
5. **Resource references** — repository, knowledge location, dan referensi relevan (workspace, Kanban jika dipakai) terdokumentasi; field boleh `pending` hanya bila eksplisit ditunda **tanpa** mengaktifkan pekerjaan yang bergantung pada resource tersebut.
6. **Risk/blocker assessment** — risiko dan blocker awal terdokumentasi.
7. **Delegasi yang diperlukan** — jika pekerjaan membutuhkan delegated authority, delegasi harus **eksplisit** dan aktif ([[Approval-Policy]]); registrasi saja tidak mencukupi.
8. **Explicit Owner approval** — persetujuan aktivasi tercatat (`approval_reference` bila menggunakan skema approval).

**Bukan prasyarat mutlak** untuk semua proyek:

- Inisialisasi Kanban.
- Pembentukan atau aktivasi Specialist Agents.
- Delegasi proyek otomatis akibat registrasi.

## Required Documentation

### Obsidian Vault

| Dokumen | Keterangan |
|---------|------------|
| Project Profile | Registrasi otoritatif proyek. |
| Project Charter | Otoritas dan tujuan proyek; Owner approval. |
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
- **Authorization** — Owner menyetujui pendekatan.
- **Registration** — Project Profile dan entri registry setelah otorisasi.
- **Activation** — Status lifecycle diselaraskan; memenuhi kriteria aktivasi.

Aturan:

- Periksa dokumen dan **approval existing** sebelum membuat dokumen baru duplikat.
- **Jangan** melakukan migrasi otomatis atau menghapus dokumen lama.
- Approval existing yang sah dapat **dipertahankan** setelah bukti dan relevansi diverifikasi.
- Proyek Akura: di luar scope revisi ini.

## Scope and Monitoring

### Perubahan scope

**Seluruh perubahan terhadap approved project scope** memerlukan Owner approval sesuai [[Approval-Policy]] — bukan hanya perubahan yang dinilai material.

Penyesuaian operasional **dalam** approved scope (task tambahan, urutan kerja, detail implementasi, jadwal internal) dapat dilakukan berdasarkan delegasi atau assignment yang masih berlaku, tanpa mengubah dokumen scope resmi.

### Monitoring, reporting, acceptance, completion, archiving

| Aktivitas | Panduan |
|-----------|---------|
| Monitoring | Progress terhadap plan dan milestone; status proyek diperbarui di Project Profile dan laporan berkala. |
| Reporting | Snapshot bertanggal di vault boleh merangkum status; live task status targetnya Kanban setelah integrasi ([[Knowledge-Management-Policy]]). |
| Acceptance | Kriteria UAT/acceptance disepakati dalam scope; Owner atau penerima yang berwenang. |
| Completion | Transisi ke `completed` setelah acceptance; dokumentasi penutupan. |
| Archiving | Transisi ke `archived` dengan otorisasi; mengikuti [[Document-Lifecycle]] untuk dokumen proyek. |

Delegasi operasional **tidak** menggantikan Owner approval untuk scope, charter, atau aktivasi agent/permission.

## Dokumen terkait

- [[Information-Architecture]]
- [[Naming-Conventions]]
- [[Approval-Policy]]
- [[Document-Lifecycle]]
- [[Knowledge-Management-Policy]]
- [[AI-Office-Charter]]
