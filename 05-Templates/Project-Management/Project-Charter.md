---
title: Project Charter
document_id: TPL-002
template_id: TPL-002
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
tags: ['ai-office', 'templates', 'projects', 'charter']
---

# Project Charter

## 1. Purpose

Dokumen otoritas dan tujuan resmi sebuah proyek: dasar Business Value, tujuan, batas tinggi, dan komitmen yang disetujui Organizational Owner.

Mengikuti [[03-Hermes/Governance/Project-Registration-Standard|Project Registration Standard]] (GOV-007).

- Charter memerlukan **Organizational Owner approval** sebelum dianggap sah.
- Charter bukan pengganti Project Scope; detail ruang lingkup ada di scope terpisah.

## 2. Usage Instructions

1. Baca master ini berstatus `approved` (untuk penggunaan resmi).
2. Ekstrak Generated Metadata blueprint dan Required Sections.
3. Isi dari **fakta aktual** — jangan membawa frontmatter master, approval master, Usage Instructions, atau Validation Checklist internal.
4. Isi `source_template_id` dan `source_template_version` dengan master yang benar-benar digunakan.
5. Validasi instance, lalu simpan pada Target SSOT.

**Jangan** mengubah master ini saat menghasilkan instance.

## 3. Target SSOT

`02-Projects/{Project-Name}/Project-Charter.md` (folder proyek di vault).

## 4. Generated Metadata

Blueprint — **bukan** metadata dokumen siap publikasi.

```yaml
title: null
document_id: null
document_type: project_charter
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
- `approved_by`/`approved_at` terisi hanya setelah approval sah; `approval_references` mencatat jejak approval yang dapat ditelusuri.

## 5. Required Sections

- **Executive Summary** — ringkasan singkat proyek, tujuan, dan nilai bisnisnya.
- **Background** — konteks, pemicu, dan alasan proyek dimulai.
- **Project Objectives** — tujuan yang terukur dan prioritasnya.
- **Business Value** — manfaat yang diharapkan bagi organisasi.
- **Stakeholders** — pihak yang berkepentingan, promosi, serta peran mereka dalam proyek.
- **High-Level Scope** — batasan umum; detail lengkap pada scope terpisah.
- **Constraints and Assumptions** — batasan dan asumsi yang melandasi charter.
- **Strategic Risks** — risiko strategis yang dapat menimpa proyek.
- **Success Criteria** — kriteria keberhasilan proyek pada tingkat bisnis.
- **Approval Evidence** — referensi approval Organizational Owner yang sah dan dapat ditelusuri.

## 6. Optional Sections

- **Initiative Origin** — pemicu dan pemohon awal.
- **Related Documents** — Project Scope, Project Plan, dan dokumen terkait.
- **Revision History** — perubahan charter beserta referensi approval.

## 7. Validation Checklist

Manual sebelum publikasi instance:

- [ ] Seluruh 10 required section terisi.
- [ ] Tidak ada detail implementasi teknis di luar tingkat bisnis.
- [ ] Objektif dan success criteria dapat diverifikasi.
- [ ] Approval Evidence merujuk approval Organizational Owner yang sah — **bukan** placeholder.
- [ ] `approved_by`/`approved_at` kosong bila belum ada approval.
- [ ] `document_id` instance mengikuti GOV-008, bukan namespace `TPL`.
- [ ] `source_template_id` dan `source_template_version` sesuai master yang digunakan.
- [ ] Tanggal mengikuti system clock aktual (Asia/Jakarta).
- [ ] Tidak ada kredensial atau raw secret.

## 8. Governance References

- [[03-Hermes/Governance/Project-Registration-Standard|Project Registration Standard]] (GOV-007)
- [[03-Hermes/Governance/Approval-Policy|Approval Policy]] (GOV-005)
- [[03-Hermes/Governance/AI-Office-Charter|AI Office Charter]] (GOV-001)
- [[03-Hermes/Governance/Naming-Conventions|Naming Conventions]] (GOV-008)
- [[03-Hermes/Governance/Document-Lifecycle|Document Lifecycle]] (GOV-004)
- [[05-Templates/Template-Standard|Template Standard]]
