---
title: Project Closure Report
document_id: TPL-007
template_id: TPL-007
document_type: template
category: project-management
version: "0.1.0"
status: draft
owner: owner
author: hermes-default
reviewer: null
approved_by: null
approved_at: null
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

1. Baca master ini berstatus `approved` (untuk penggunaan resmi).
2. Ekstrak Generated Metadata blueprint dan Required Sections.
3. Isi dari fakta aktual — jangan membawa frontmatter master, approval master, Usage Instructions, atau Validation Checklist internal.
4. Isi `source_template_id` dan `source_template_version` dengan master yang benar-benar digunakan.
5. Validasi instance, lalu simpan pada Target SSOT.

**Jangan** mengubah master ini saat menghasilkan instance.

## 3. Target SSOT

`02-Projects/{Project-Name}/Project-Closure-Report.md` (folder proyek di vault).

## 4. Generated Metadata

Blueprint — bukan metadata dokumen siap publikasi.

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
project_status: null
closure_path: null
approval_references: []
```

- `status` dokumen berbeda dari `project_status`.
- `closure_path` mencerminkan jalur penutupan: `successful_completion`, `permanent_termination`, `temporary_suspension`, atau `permanent_rejection`.

## 5. Required Sections

- **Closure Reason** — jalur penutupan yang terjadi dan otoritas yang mengambil keputusan.
- **Project Summary** — ringkasan proyek, tujuan, dan rentang pengerjaannya.
- **Deliverable Outcomes** — hasil deliverable terhadap kebutuhan bisnis dan scope.
- **Acceptance Evidence** — bukti acceptance yang sah beserta referensinya.
- **Unresolved Items** — item yang belum tuntas, alasannya, dan tindak lanjut yang dimiliki.
- **Operational Handover** — serah terima operasional: apa yang diserahkan, ke siapa, dan tindak lanjut rutin.
- **Lessons Learned** — pelajaran yang dapat dipakai untuk proyek berikutnya.
- **Closure Authorization** — referensi otorisasi penutupan yang sah dan dapat ditelusuri.
- **Archiving References** — rujukan pengarsipan, termasuk dokumen yang diarsipkan dan lokasinya.

## 6. Optional Sections

- **Rejected Alternatives** — alternatif yang dipertimbangkan dan alasannya.
- **Post-closure Actions** — tindakan setelah penutupan beserta pemiliknya.
- **Related Documents** — charter, scope, plan, status report, dan dokumen terkait.
- **Change Log** — revisi laporan beserta dasar pertanggungjawabannya.

## 7. Validation Checklist

Manual sebelum publikasi instance:

- [ ] Closure Reason sesuai dengan jalur penutupan yang benar.
- [ ] Acceptance Evidence menunjuk bukti yang benar-benar ada.
- [ ] Tidak ada klaim keberhasilan bila closure_path bukan successful completion.
- [ ] Pengisian laporan tidak diperlakukan sebagai otorisasi archiving.
- [ ] Unresolved Items memiliki tindak lanjut yang jelas.
- [ ] `document_id` instance mengikuti GOV-008, bukan namespace `TPL`.
- [ ] `source_template_id` dan `source_template_version` sesuai master yang digunakan.
- [ ] Tanggal mengikuti system clock aktual (Asia/Jakarta).
- [ ] Tidak ada kredensial atau raw secret.

## 8. Governance References

- [[03-Hermes/Governance/Project-Registration-Standard|Project Registration Standard]] (GOV-007)
- [[03-Hermes/Governance/Approval-Policy|Approval Policy]] (GOV-005)
- [[03-Hermes/Governance/Document-Lifecycle|Document Lifecycle]] (GOV-004)
- [[03-Hermes/Governance/Naming-Conventions|Naming Conventions]] (GOV-008)
- [[03-Hermes/Governance/Knowledge-Management-Policy|Knowledge Management Policy]] (GOV-003)
- [[05-Templates/Template-Standard|Template Standard]]
