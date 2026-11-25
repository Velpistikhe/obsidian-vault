---
title: Business Requirements
document_id: TPL-005
template_id: TPL-005
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
tags: ['ai-office', 'templates', 'projects', 'requirements']
---

# Business Requirements

## 1. Purpose

Dokumen kebutuhan bisnis sebuah proyek: konteks, kebutuhan, aturan bisnis, prioritas, dan keterlacakan ke kriteria acceptance.

Mengikuti [[03-Hermes/Governance/Project-Registration-Standard|Project Registration Standard]] (GOV-007).

- **Bedakan kebutuhan bisnis dari detail technical implementation** yang menjadi SSOT GitHub Project Repository (GOV-002).
- Business requirements mencakup **functional dan non-functional requirements pada tingkat bisnis**, tanpa menentukan detail implementasi teknis. Technical specifications tetap berada pada GitHub Project Repository.
- Template ini bersifat kondisional — digunakan bila proyek memang memiliki kebutuhan bisnis yang perlu didokumentasikan.
- Requirements **bukan** jalur untuk mengubah approved scope secara tidak langsung.

## 2. Usage Instructions

1. Baca master sesuai **Gate 1 — Master Template** pada bagian 7.
2. Ekstrak **Generated Metadata blueprint** (bagian 4), **Required Sections** (bagian 5), dan **applicable optional sections** (bagian 6) yang memang relevan. **Jangan** menyalin seluruh isi master ke instance.
3. Isi metadata dan konten instance dari **fakta aktual** — jangan membawa frontmatter master, approval master, Usage Instructions, atau Validation Checklist internal.
4. Isi `author` dengan **pembuat aktual instance**, `source_template_id` dengan **ID master yang benar-benar digunakan**, `source_template_version` dengan **versi master yang benar-benar digunakan**, serta `created_at` dan `updated_at` dengan **tanggal aktual** (GOV-008).
5. Isi approval metadata (`reviewer`, `approved_by`, `approved_at`) **hanya** bila terdapat keputusan sah sesuai kewenangan; biarkan `null` bila belum ada (GOV-004, GOV-005).
6. Validasi instance terhadap **Gate 2 — Generated Document** pada bagian 7, lalu simpan pada Target SSOT.

**Jangan** mengubah master ini saat menghasilkan instance. **Jangan** mewariskan approval, author, identifier, atau timestamp master ke instance.

## 3. Target SSOT

`02-Projects/{Project-Name}/Business-Requirements.md` (folder proyek di vault).

## 4. Generated Metadata

Blueprint — **bukan** metadata dokumen siap publikasi. `document_id` instance mengikuti GOV-008, bukan namespace `TPL`. **Jangan** memasukkan identitas, approval, author, atau timestamp master sebagai nilai aktual instance.

```yaml
title: null
document_id: null
document_type: business_requirements
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
approval_references: []
```

- `status` dokumen berbeda dari `project_status`.
- `project_status` dan `project_owner` **tidak** dicantumkan di sini; sumber tunggalnya adalah Project Profile instance (`02-Projects/{Project-Name}/Project-Profile.md`) sebagai SSOT registrasi proyek (GOV-007).
- `approval_references` merujuk bukti approval requirements itu sendiri — bukan menduplikasi registry otoritatif.

### Matriks keterlacakan requirements

Gunakan matriks berikut pada instance. Kolom `Requirement reference` memakai **local requirement references** — bukan organizational identifier baru. MoSCoW boleh digunakan bila relevan, tetapi **bukan kewajiban governance**.

| Requirement reference | Description | Priority | Scope reference | Acceptance reference |
|---|---|---|---|---|
| (contoh ilustratif) | (contoh ilustratif) | (contoh ilustratif) | (contoh ilustratif) | (contoh ilustratif) |

**Contoh di atas hanya ilustrasi** dan **tidak** menjadi actual requirement. Draft boleh memiliki traceability yang belum lengkap dengan penjelasan pada bagian yang belum terisi.

### Proposed dan approved requirements

| Tingkat | Makna |
|---------|-------|
| **Proposed requirements** | Usulan kebutuhan yang belum disetujui; boleh didokumentasikan pada dokumen `draft`. |
| **Approved requirements** | Kebutuhan yang telah disetujui sesuai kewenangan; tercatat pada dokumen `approved` beserta evidence reference. |

Perubahan requirements yang **memengaruhi approved project scope** memerlukan **Organizational Owner approval**. Perubahan di dalam approved scope mengikuti kewenangan dan delegasi yang berlaku. Revisi dokumen approved mengikuti GOV-004 dan GOV-008.
## 5. Required Sections

- **Business Context** — situasi bisnis, pasar, atau kondisi kerja yang melandasi kebutuhan.
- **Stakeholders** — pihak yang membutuhkan, terpengaruh, atau memiliki kepentingan.
- **Business Needs** — masalah dan kebutuhan bisnis yang harus dijawab.
- **Functional Requirements** — kapabilitas dan perilaku yang dibutuhkan bisnis, dirumuskan pada level bisnis.
- **Non-Functional Business Requirements** — kebutuhan bisnis non-fungsional seperti kepatuhan, waktu layanan, atau kebijakan organisasi.
- **Business Rules** — aturan yang mengikat proses dan keputusan.
- **Priority** — prioritas tiap kebutuhan beserta justifikasinya.
- **Acceptance References** — rujukan ke kriteria acceptance pada scope atau UAT.
- **Requirements Traceability** — matriks keterlacakan kebutuhan ke scope, deliverable, dan acceptance criteria.
## 6. Optional Sections

- **Assumptions and Open Questions** — asumsi dan pertanyaan yang belum terjawab.
- **Out of Scope Requirements** — kebutuhan yang sengaja tidak ditangani pada fase ini.
- **Related Documents** — charter, scope, business process, dan dokumen terkait.
- **Change Log** — perubahan kebutuhan beserta referensi approval.
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

- [ ] Sembilan required section terisi.
- [ ] Functional dan non-functional requirements dibedakan dan tetap pada level bisnis.
- [ ] Tidak ada detail teknis, kode, atau pilihan desain dalam requirements; technical specifications mengikuti GitHub Project Repository.
- [ ] Setiap kebutuhan unik, dapat diuji, dan memiliki prioritas.
- [ ] Matriks keterlacakan memakai local requirement references dan kolom Priority, Scope reference, serta Acceptance reference terisi.
- [ ] Contoh ilustratif pada master **tidak** terbawa sebagai actual requirement pada instance.
- [ ] Traceability yang belum lengkap pada draft disertai penjelasan.
- [ ] Business Rules konsisten dengan Business Process bila keduanya ada.
- [ ] Requirements Traceability menunjuk acceptance criteria yang benar-benar ada.
- [ ] Perubahan yang memengaruhi approved scope memiliki referensi approval Organizational Owner.
- [ ] `document_id` instance mengikuti GOV-008, bukan namespace `TPL`.
- [ ] Tidak ada kredensial atau raw secret.
## 8. Governance References

- [[03-Hermes/Governance/Project-Registration-Standard|Project Registration Standard]] (GOV-007)
- [[03-Hermes/Governance/Information-Architecture|Information Architecture]] (GOV-002)
- [[03-Hermes/Governance/Approval-Policy|Approval Policy]] (GOV-005)
- [[03-Hermes/Governance/Naming-Conventions|Naming Conventions]] (GOV-008)
- [[03-Hermes/Governance/Document-Lifecycle|Document Lifecycle]] (GOV-004)
- [[03-Hermes/Governance/Authorization-Evidence/README|Authorization Evidence]] — mekanisme bootstrap bukti otorisasi
- [[03-Hermes/Governance/Authorization-Evidence/Template-Phase-1-Authorization-Confirmation|Template Phase 1 Authorization Confirmation]] — bukti keputusan Owner atas approval master ini; path eksplisit: `03-Hermes/Governance/Authorization-Evidence/Template-Phase-1-Authorization-Confirmation.md`
- [[05-Templates/Template-Standard|Template Standard]]
