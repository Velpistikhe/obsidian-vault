---
title: Project Status Report
document_id: TPL-006
template_id: TPL-006
document_type: template
category: project-management
version: "1.0.0"
status: approved
owner: owner
author: hermes-default
reviewer: owner
approved_by: owner
approved_at: 2026-11-25T19:25:47+07:00
created_at: 2026-11-25
updated_at: 2026-11-25
tags: ['ai-office', 'templates', 'projects', 'reporting']
---

# Project Status Report

## 1. Purpose

Laporan berkala (snapshot) kondisi sebuah proyek pada satu periode: kemajuan, risiko dan isu, blocker, keputusan yang dibutuhkan, dan rekomendasi.

Mengikuti [[03-Hermes/Governance/Knowledge-Management-Policy|Knowledge Management Policy]] (GOV-003).

- **Snapshot ini bukan live task SSOT** dan **bukan live project lifecycle SSOT.** Live task status menjadi target Hermes Kanban setelah integrasi tersedia dan diverifikasi; saat ini integrasi berstatus Pending Verification (GOV-002).
- **Jangan mengarang** progress, percentage, task status, atau milestone. Isi hanya dari fakta yang tersedia.
- Nama file bertanggal karena tanggal merupakan bagian identitas artefak (GOV-008).

## 2. Usage Instructions

1. Baca master sesuai **Gate 1 — Master Template** pada bagian 7.
2. Ekstrak **Generated Metadata blueprint** (bagian 4), **Required Sections** (bagian 5), dan **applicable optional sections** (bagian 6) yang memang relevan. **Jangan** menyalin seluruh isi master ke instance.
3. Isi metadata dan konten instance dari **fakta aktual** — jangan membawa frontmatter master, approval master, Usage Instructions, atau Validation Checklist internal.
4. Isi `author` dengan **pembuat aktual instance**, `source_template_id` dengan **ID master yang benar-benar digunakan**, `source_template_version` dengan **versi master yang benar-benar digunakan**, serta `created_at` dan `updated_at` dengan **tanggal aktual** (GOV-008).
5. Isi approval metadata (`reviewer`, `approved_by`, `approved_at`) **hanya** bila terdapat keputusan sah sesuai kewenangan; biarkan `null` bila belum ada (GOV-004, GOV-005).
6. Validasi instance terhadap **Gate 2 — Generated Document** pada bagian 7, lalu simpan pada Target SSOT.

**Jangan** mengubah master ini saat menghasilkan instance. **Jangan** mewariskan approval, author, identifier, atau timestamp master ke instance.

## 3. Target SSOT

`02-Projects/{Project-Name}/Project-Status-Report-YYYY-MM-DD.md` (folder proyek di vault, sebagai dated report).

Bila terdapat lebih dari satu laporan pada tanggal yang sama, tambahkan suffix waktu (`-HHMM`) atau document identifier pada nama file. **Jangan menimpa laporan sebelumnya secara otomatis.**

## 4. Generated Metadata

Blueprint — **bukan** metadata dokumen siap publikasi. `document_id` instance mengikuti GOV-008, bukan namespace `TPL`. **Jangan** memasukkan identitas, approval, author, atau timestamp master sebagai nilai aktual instance.

```yaml
title: null
document_id: null
document_type: project_status_report
category: project-management
version: "0.1.0"
status: draft
owner: null
author: null
reviewer: null
approved_by: null
approved_at: null
created_at: null
updated_at: null
tags: []
source_template_id: null
source_template_version: null
# --- konteks proyek ---
project_id: null
# --- konteks laporan ---
reporting_period_start: null
reporting_period_end: null
snapshot_timestamp: null
project_status_at_snapshot: null
approval_references: []
delegation_references: []
```

- `status` dokumen berbeda dari `project_status`.
- `project_status_at_snapshot` adalah nilai **snapshot**: dicatat dari Project Profile instance (`02-Projects/{Project-Name}/Project-Profile.md`) pada **waktu efektif** yang relevan, dengan sumber dan waktu dicatat eksplisit. Status ini **bukan** SSOT project lifecycle — pembaruan lifecycle tetap dilakukan pada Project Profile.
- `snapshot_timestamp` memakai ISO 8601 dengan timezone dari system clock aktual (GOV-008).
- Bedakan **waktu pembuatan laporan**, **snapshot timestamp**, dan **waktu efektif data** apabila berbeda.
- Progress yang belum dapat diverifikasi ditandai `unknown` atau `pending verification` — **bukan** angka nol atau estimasi tanpa dasar.

### Decisions Required versus Decisions Made

| Section | Sifat | Isi |
|---------|--------|-----|
| **Decisions Required** | Selalu ada bila ada keputusan yang dibutuhkan | Request, authorized decision maker, required date, dan impact if delayed. |
| **Decisions Made** | **Kondisional** — hanya bila keputusan benar-benar diberikan | Actual decision, decision maker, timestamp, dan evidence reference. |

Status report **bukan** pengganti approval record. Keputusan yang diberikan dicatat sebagai bukti yang dapat ditelusuri, bukan sebagai metadata approval dokumen.
## 5. Required Sections

- **Reporting Period and Snapshot Timestamp** — periode laporan dan waktu pengambilan snapshot.
- **Executive Summary** — ringkasan kondisi proyek dalam beberapa kalimat.
- **Progress and Milestones** — kemajuan terhadap rencana dan status milestone yang terverifikasi.
- **Completed Activities** — aktivitas yang benar-benar selesai pada periode ini.
- **Upcoming Activities** — aktivitas yang direncanakan pada periode berikutnya.
- **Risks and Issues** — risiko dan isu beserta dampak dan aksi mitigasi.
- **Blockers** — hambatan yang memerlukan resolusi beserta pemilik aksinya.
- **Decisions Required** — keputusan yang dibutuhkan beserta request, pihak berwenang, required date, dan dampak bila tertunda.
- **Recommendations** — rekomendasi tindakan lanjutan.
- **Source References** — sumber data laporan (rencana, dokumen terkait, sistem yang digunakan).
## 6. Optional Sections

- **Decisions Made** — **kondisional**: keputusan yang benar-benar diberikan pada periode ini, beserta decision maker, timestamp, dan evidence reference. Tidak ada keputusan sah → section dikosongkan dengan penjelasan.
- **Resource and Delegation Status** — status resource yang dirujuk beserta delegasi aktif yang relevan.
- **Changes Since Previous Report** — delta terhadap laporan sebelumnya.
- **Attached Artefact References** — rujukan ke dokumen atau artefak pendukung.
## 7. Validation Checklist

Manual sebelum publikasi instance. Pemeriksaan ad-hoc — **bukan** automated governance validation.

### Gate 1 — Master Template

- [ ] Master `approved` → penggunaan resmi.
- [ ] Master `draft` → hanya untuk review atau simulasi terotorisasi.
- [ ] Master `archived` → hanya referensi historis, bukan penggunaan resmi baru.

### Gate 2 — Generated Document

- [ ] `draft` — boleh belum lengkap, dengan penjelasan pada bagian yang belum terisi.
- [ ] `in_review` — memenuhi persyaratan review.
- [ ] `pending_approval` — memenuhi persyaratan pengajuan keputusan.
- [ ] `approved` — metadata lengkap dan approval sah sesuai kewenangan.
- [ ] `archived` — pengarsipan terotorisasi.

### Provenance dan metadata

- [ ] `author` = pembuat aktual instance.
- [ ] `created_at` dan `updated_at` = tanggal aktual (Asia/Jakarta; GOV-008).
- [ ] `source_template_id` = ID master yang benar-benar digunakan.
- [ ] `source_template_version` = versi master yang benar-benar digunakan.
- [ ] Approval metadata hanya terisi atas keputusan sah; `created_at` instance dipertahankan pada revisi normal.

### Pemeriksaan instance

- [ ] Periode laporan dan snapshot timestamp terisi.
- [ ] Nama file bertanggal `Project-Status-Report-YYYY-MM-DD.md`; suffix waktu atau document identifier ditambahkan bila ada lebih dari satu laporan pada tanggal yang sama.
- [ ] Laporan sebelumnya tidak ditimpa secara otomatis.
- [ ] Waktu pembuatan laporan, snapshot timestamp, dan waktu efektif data dibedakan bila berbeda.
- [ ] Tidak ada angka progress, percentage, atau status task yang tidak bersumber dari fakta.
- [ ] Progress yang belum terverifikasi ditandai `unknown` atau `pending verification`, bukan nol atau estimasi.
- [ ] Milestone yang dilaporkan sesuai rencana yang berlaku.
- [ ] `project_status_at_snapshot` dicatat dari Project Profile dengan sumber dan waktu efektif yang jelas; status report bukan SSOT project lifecycle.
- [ ] Blocker dan keputusan yang dibutuhkan menyebut pihak berwenang, required date, dan dampak bila tertunda.
- [ ] Decisions Made hanya diisi atas keputusan aktual beserta decision maker, timestamp, dan evidence reference.
- [ ] Source References menunjukkan asal data.
- [ ] Tidak ada klaim bahwa integrasi Kanban sudah operational.
- [ ] `document_id` instance mengikuti GOV-008, bukan namespace `TPL`.
- [ ] Tidak ada kredensial atau raw secret.
## 8. Governance References

- [[03-Hermes/Governance/Knowledge-Management-Policy|Knowledge Management Policy]] (GOV-003)
- [[03-Hermes/Governance/Project-Registration-Standard|Project Registration Standard]] (GOV-007)
- [[03-Hermes/Governance/Information-Architecture|Information Architecture]] (GOV-002)
- [[03-Hermes/Governance/Approval-Policy|Approval Policy]] (GOV-005)
- [[03-Hermes/Governance/Naming-Conventions|Naming Conventions]] (GOV-008)
- [[03-Hermes/Governance/Document-Lifecycle|Document Lifecycle]] (GOV-004)
- [[03-Hermes/Governance/Authorization-Evidence/README|Authorization Evidence]] — mekanisme bootstrap bukti otorisasi
- [[03-Hermes/Governance/Authorization-Evidence/Template-Phase-1-Authorization-Confirmation|Template Phase 1 Authorization Confirmation]] — bukti keputusan Owner atas approval master ini; path eksplisit: `03-Hermes/Governance/Authorization-Evidence/Template-Phase-1-Authorization-Confirmation.md`
- [[05-Templates/Template-Standard|Template Standard]]
