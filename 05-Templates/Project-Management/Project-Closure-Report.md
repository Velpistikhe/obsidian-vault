---
title: Project Closure Report
document_id: TPL-007
template_id: TPL-007
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
tags: ['ai-office', 'templates', 'projects', 'closure']
---

# Project Closure Report

## 1. Purpose

Dokumentasi penutupan sebuah proyek: alasan penutupan, hasil deliverable, bukti acceptance, item yang belum tuntas, serah terima operasional, pelajaran, dan otorisasi pengarsipan.

Mengikuti [[03-Hermes/Governance/Project-Registration-Standard|Project Registration Standard]] (GOV-007).

- **Bedakan** successful completion, permanent termination, temporary suspension, dan permanent rejection.
- **`archived` tidak otomatis berarti successful completion.**
- **Mengisi laporan ini bukan otorisasi archiving.** Transisi ke `archived` memerlukan otorisasi tersendiri (GOV-007, GOV-005).
- Perubahan terhadap approved project scope tetap memerlukan Organizational Owner approval.

## 2. Usage Instructions

1. Baca master sesuai **Gate 1 — Master Template** pada bagian 7.
2. Ekstrak **Generated Metadata blueprint** (bagian 4), **Required Sections** (bagian 5), dan **applicable optional sections** (bagian 6) yang memang relevan. **Jangan** menyalin seluruh isi master ke instance.
3. Isi metadata dan konten instance dari **fakta aktual** — jangan membawa frontmatter master, approval master, Usage Instructions, atau Validation Checklist internal.
4. Isi `author` dengan **pembuat aktual instance**, `source_template_id` dengan **ID master yang benar-benar digunakan**, `source_template_version` dengan **versi master yang benar-benar digunakan**, serta `created_at` dan `updated_at` dengan **tanggal aktual** (GOV-008).
5. Isi approval metadata (`reviewer`, `approved_by`, `approved_at`) **hanya** bila terdapat keputusan sah sesuai kewenangan; biarkan `null` bila belum ada (GOV-004, GOV-005).
6. Validasi instance terhadap **Gate 2 — Generated Document** pada bagian 7, lalu simpan pada Target SSOT.

**Jangan** mengubah master ini saat menghasilkan instance. **Jangan** mewariskan approval, author, identifier, atau timestamp master ke instance.

## 3. Target SSOT

`02-Projects/{Project-Name}/Project-Closure-Report.md` (folder proyek di vault).

## 4. Generated Metadata

Blueprint — **bukan** metadata dokumen siap publikasi. `document_id` instance mengikuti GOV-008, bukan namespace `TPL`. **Jangan** memasukkan identitas, approval, author, atau timestamp master sebagai nilai aktual instance.

```yaml
title: null
document_id: null
document_type: project_closure_report
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
closure_path: null
approval_references: []
```

- `status` dokumen berbeda dari `project_status`.
- Status lifecycle proyek **tidak** dicantumkan sebagai SSOT di sini. Bila dicatat, gunakan nilai **sebelum dan sesudah** keputusan lifecycle dengan sumber dan waktu efektif yang jelas — sumber tunggalnya tetap Project Profile instance (`02-Projects/{Project-Name}/Project-Profile.md`).
- `closure_path` mencerminkan jalur penutupan: `successful_completion`, `permanent_termination`, `temporary_suspension`, atau `permanent_rejection`.

### Closure path dan bukti yang bersyarat

| `closure_path` | Hasil lifecycle | Bukti yang bersyarat |
|----------------|-----------------|----------------------|
| `successful_completion` | `completed` | Acceptance evidence dan authorized completion decision. |
| `permanent_termination` | `archived` sesuai keputusan yang berwenang | Alasan penghentian dan keputusan yang berwenang. |
| `permanent_rejection` | `archived` sesuai keputusan yang berwenang | Referensi keputusan penolakan. |
| `temporary_suspension` | `on_hold` | **Bukan** permanent closure — proyek dapat kembali `active` melalui aktivasi oleh Organizational Owner. |

**Archiving References wajib** hanya bila archiving benar-benar dilakukan. Jalur yang tidak membutuhkan acceptance atau archiving evidence **tidak** boleh dipaksa memiliki bukti tersebut.

**Closure authorization** (keputusan penutupan) **dan** **archiving authorization** (keputusan pengarsipan) adalah dua hal berbeda. Laporan ini **tidak** menjadi otorisasi perubahan lifecycle.
## 5. Required Sections

- **Closure Reason** — jalur penutupan yang terjadi dan otoritas yang mengambil keputusan.
- **Project Summary** — ringkasan proyek, tujuan, dan rentang pengerjaannya.
- **Deliverable Outcomes** — hasil deliverable terhadap kebutuhan bisnis dan scope.
- **Acceptance Evidence** — bukti acceptance yang sah beserta referensinya — **kondisional** sesuai `closure_path`.
- **Assignment and Delegation Disposition** — status penyelesaian assignment dan delegasi, pemilik tindak lanjut, serta referensi bukti tindakan yang benar-benar dilakukan.
- **Unresolved Items** — item yang belum tuntas, alasannya, dan tindak lanjut yang dimiliki.
- **Operational Handover** — serah terima operasional: apa yang diserahkan, ke siapa, dan tindak lanjut rutin.
- **Lessons Learned** — pelajaran yang dapat dipakai untuk proyek berikutnya.
- **Closure Authorization** — referensi otorisasi penutupan yang sah dan dapat ditelusuri.
- **Archiving References** — rujukan pengarsipan, termasuk dokumen yang diarsipkan dan lokasinya — **wajib** bila archiving benar-benar dilakukan.
## 6. Optional Sections

- **Rejected Alternatives** — alternatif yang dipertimbangkan dan alasannya.
- **Post-closure Actions** — tindakan setelah penutupan beserta pemiliknya.
- **Technical Access Review** — **kondisional**: apakah diperlukan review akses teknis, dan hasilnya. Pencabutan akses dilaksanakan **terpisah** sesuai kewenangan.
- **Related Documents** — charter, scope, plan, status report, dan dokumen terkait.
- **Change Log** — revisi laporan beserta dasar pertanggungjawabannya.
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

- [ ] `closure_path` sesuai dengan jalur penutupan yang benar (GOV-007).
- [ ] Tidak ada klaim keberhasilan bila `closure_path` bukan `successful_completion`.
- [ ] Temporary suspension dicatat sebagai `on_hold`, bukan permanent closure.
- [ ] Acceptance Evidence dan Archiving References hanya diisi bila jalur penutupan memang membutuhkannya.
- [ ] Pengisian laporan tidak diperlakukan sebagai otorisasi archiving maupun perubahan lifecycle.
- [ ] Closure authorization dan archiving authorization dibedakan.
- [ ] Assignment dan delegasi disposition tercatat: completed, cancelled, handed over, atau outstanding; delegasi expired, revoked, atau retained sesuai kewenangan; pemilik tindak lanjut disebutkan.
- [ ] Technical access revocation **tidak** diklaim tanpa execution dan verification evidence.
- [ ] Unresolved Items memiliki tindak lanjut yang jelas.
- [ ] `document_id` instance mengikuti GOV-008, bukan namespace `TPL`.
- [ ] Tidak ada kredensial atau raw secret.
## 8. Governance References

- [[03-Hermes/Governance/Project-Registration-Standard|Project Registration Standard]] (GOV-007)
- [[03-Hermes/Governance/Approval-Policy|Approval Policy]] (GOV-005)
- [[03-Hermes/Governance/Document-Lifecycle|Document Lifecycle]] (GOV-004)
- [[03-Hermes/Governance/Naming-Conventions|Naming Conventions]] (GOV-008)
- [[03-Hermes/Governance/Knowledge-Management-Policy|Knowledge Management Policy]] (GOV-003)
- [[03-Hermes/Governance/Authorization-Evidence/README|Authorization Evidence]] — mekanisme bootstrap bukti otorisasi
- [[03-Hermes/Governance/Authorization-Evidence/Template-Phase-1-Authorization-Confirmation|Template Phase 1 Authorization Confirmation]] — bukti keputusan Owner atas approval master ini; path eksplisit: `03-Hermes/Governance/Authorization-Evidence/Template-Phase-1-Authorization-Confirmation.md`
- [[05-Templates/Template-Standard|Template Standard]]
