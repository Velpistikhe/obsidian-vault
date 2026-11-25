---
title: Project Plan
document_id: TPL-004
template_id: TPL-004
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
tags: ['ai-office', 'templates', 'projects', 'planning']
---

# Project Plan

## 1. Purpose

Dokumen perencanaan tingkat proyek: baseline planning, strategi pengerjaan, struktur pekerjaan, milestone, kebutuhan resource, dan kontrol pemantauan.

Mengikuti [[03-Hermes/Governance/Project-Registration-Standard|Project Registration Standard]] (GOV-007).

- **Planning tidak memberikan assignment atau delegasi otomatis.**
- Penyesuaian operasional tidak boleh mengubah approved scope atau komitmen resmi.
- Project Plan mengikuti review/approval operasional sesuai GOV-005; review tersebut bukan persetujuan scope.
- Kanban menjadi target live task SSOT **setelah integrasi diverifikasi**; saat ini integrasi berstatus Pending Verification (GOV-002).

## 2. Usage Instructions

1. Baca master ini berstatus `approved` (untuk penggunaan resmi).
2. Ekstrak Generated Metadata blueprint dan Required Sections.
3. Isi dari fakta aktual — jangan membawa frontmatter master, approval master, Usage Instructions, atau Validation Checklist internal.
4. Isi `source_template_id` dan `source_template_version` dengan master yang benar-benar digunakan.
5. Validasi instance, lalu simpan pada Target SSOT.

**Jangan** mengubah master ini saat menghasilkan instance.

## 3. Target SSOT

`02-Projects/{Project-Name}/Project-Plan.md` (folder proyek di vault).

## 4. Generated Metadata

Blueprint — bukan metadata dokumen siap publikasi.

```yaml
title: null
document_id: null
document_type: project_plan
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
project_manager: null
project_status: null
delegation_references: []
```

- `status` dokumen berbeda dari `project_status`.
- `delegation_references` hanya berisi delegasi yang benar-benar aktif.

## 5. Required Sections

- **Planning Baseline** — versi rencana, tanggal baseline, dan dokumen acuan (charter dan scope approved).
- **Delivery Strategy** — pendekatan pengerjaan, fase, dan tingkat integrasi.
- **Work Breakdown Structure** — hierarki pekerjaan dan hasil kerja utama.
- **Milestones and Schedule** — milestone, target waktu, dan ketergantungan antar milestone.
- **Resource Requirements** — sumber daya, peran, dan kebutuhan kapasitas yang diperlukan.
- **Dependencies** — dependensi eksternal dan internal beserta dampak bila terlambat.
- **Risks and Mitigation** — risiko rencana, mitigasi, dan pemilik tindakan.
- **Communication Plan** — forum, laporan berkala, dan penerima informasi.
- **Monitoring and Control** — cara kemajuan dipantau, metrik, dan ambang penyimpangan.

## 6. Optional Sections

- **Assumptions and Constraints** — asumsi dan batasan yang memengaruhi rencana.
- **Budget and Cost Plan** — bila ada commitment biaya; setiap commitment biaya baru memerlukan Organizational Owner approval (GOV-005).
- **Quality Plan** — pendekatan jaminan mutu dan review.
- **Related Documents** — charter, scope, requirements, dan dokumen terkait.
- **Change Log** — perubahan rencana beserta dasar pertanggungjawabannya.

## 7. Validation Checklist

Manual sebelum publikasi instance:

- [ ] Sembilan required section terisi.
- [ ] Rencana tidak mencerminkan atau mengubah scope dan komitmen resmi.
- [ ] Milestone memiliki target waktu yang jelas.
- [ ] Resource requirements tidak mengklaim assignment atau delegasi yang tidak ada.
- [ ] Klaim status Kanban tidak menyatakan integrasi sebagai operational.
- [ ] `document_id` instance mengikuti GOV-008, bukan namespace `TPL`.
- [ ] `source_template_id` dan `source_template_version` sesuai master yang digunakan.
- [ ] Tanggal mengikuti system clock aktual (Asia/Jakarta).
- [ ] Tidak ada kredensial atau raw secret.

## 8. Governance References

- [[03-Hermes/Governance/Project-Registration-Standard|Project Registration Standard]] (GOV-007)
- [[03-Hermes/Governance/Approval-Policy|Approval Policy]] (GOV-005)
- [[03-Hermes/Governance/Information-Architecture|Information Architecture]] (GOV-002)
- [[03-Hermes/Governance/Naming-Conventions|Naming Conventions]] (GOV-008)
- [[03-Hermes/Governance/Document-Lifecycle|Document Lifecycle]] (GOV-004)
- [[05-Templates/Template-Standard|Template Standard]]
