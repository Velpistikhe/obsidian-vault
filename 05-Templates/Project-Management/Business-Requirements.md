---
title: Business Requirements
document_id: TPL-005
template_id: TPL-005
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
tags: ['ai-office', 'templates', 'projects', 'requirements']
---

# Business Requirements

## 1. Purpose

Dokumen kebutuhan bisnis sebuah proyek: konteks, kebutuhan, aturan bisnis, prioritas, dan keterlacakan ke kriteria acceptance.

Mengikuti [[03-Hermes/Governance/Project-Registration-Standard|Project Registration Standard]] (GOV-007).

- **Bedakan kebutuhan bisnis dari detail technical implementation** yang menjadi SSOT GitHub Project Repository (GOV-002).
- Kebutuhan bisnis bersifat non-functional dari sisi sistem: fokus pada nilai, aturan, dan proses, bukan pilihan desain.
- Template ini bersifat kondisional — digunakan bila proyek memang memiliki kebutuhan bisnis yang perlu didokumentasikan.

## 2. Usage Instructions

1. Baca master ini berstatus `approved` (untuk penggunaan resmi).
2. Ekstrak Generated Metadata blueprint dan Required Sections.
3. Isi dari fakta aktual — jangan membawa frontmatter master, approval master, Usage Instructions, atau Validation Checklist internal.
4. Isi `source_template_id` dan `source_template_version` dengan master yang benar-benar digunakan.
5. Validasi instance, lalu simpan pada Target SSOT.

**Jangan** mengubah master ini saat menghasilkan instance.

## 3. Target SSOT

`02-Projects/{Project-Name}/Business-Requirements.md` (folder proyek di vault).

## 4. Generated Metadata

Blueprint — bukan metadata dokumen siap publikasi.

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
project_owner: null
project_status: null
approval_references: []
```

- `status` dokumen berbeda dari `project_status`.

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

Manual sebelum publikasi instance:

- [ ] Sembilan required section terisi.
- [ ] Tidak ada detail teknis, kode, atau pilihan desain dalam requirements.
- [ ] Setiap kebutuhan unik, dapat diuji, dan memiliki prioritas.
- [ ] Business Rules konsisten dengan Business Process bila keduanya ada.
- [ ] Requirements Traceability menunjuk acceptance criteria yang benar-benar ada.
- [ ] `document_id` instance mengikuti GOV-008, bukan namespace `TPL`.
- [ ] `source_template_id` dan `source_template_version` sesuai master yang digunakan.
- [ ] Tanggal mengikuti system clock aktual (Asia/Jakarta).
- [ ] Tidak ada kredensial atau raw secret.

## 8. Governance References

- [[03-Hermes/Governance/Project-Registration-Standard|Project Registration Standard]] (GOV-007)
- [[03-Hermes/Governance/Information-Architecture|Information Architecture]] (GOV-002)
- [[03-Hermes/Governance/Approval-Policy|Approval Policy]] (GOV-005)
- [[03-Hermes/Governance/Naming-Conventions|Naming Conventions]] (GOV-008)
- [[03-Hermes/Governance/Document-Lifecycle|Document Lifecycle]] (GOV-004)
- [[05-Templates/Template-Standard|Template Standard]]
