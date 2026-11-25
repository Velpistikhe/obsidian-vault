---
title: UAT Criteria
document_id: TPL-009
template_id: TPL-009
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
tags: ['ai-office', 'templates', 'projects', 'uat', 'acceptance']
---

# UAT Criteria

## 1. Purpose

Dokumen kriteria User Acceptance Testing: tujuan, cakupan, prasyarat, kriteria acceptance, skenario uji, hasil yang diharapkan, keterlacakan ke requirements, penanganan defect, dan keputusan acceptance.

Mengikuti [[03-Hermes/Governance/Project-Registration-Standard|Project Registration Standard]] (GOV-007).

- **Bedakan** proposed acceptance criteria, execution result, dan actual acceptance decision.
- **Template kosong tidak boleh menunjukkan UAT passed atau approved.**
- Detail testing teknis tetap mengikuti SSOT GitHub Project Repository (GOV-002).
- Acceptance decision memerlukan pihak yang berwenang; pelaporan hasil UAT bukan wewenang acceptance.

## 2. Usage Instructions

1. Baca master ini berstatus `approved` (untuk penggunaan resmi).
2. Ekstrak Generated Metadata blueprint dan Required Sections.
3. Isi dari fakta aktual — jangan membawa frontmatter master, approval master, Usage Instructions, atau Validation Checklist internal.
4. Isi `source_template_id` dan `source_template_version` dengan master yang benar-benar digunakan.
5. Validasi instance, lalu simpan pada Target SSOT.

**Jangan** mengubah master ini saat menghasilkan instance.

## 3. Target SSOT

`02-Projects/{Project-Name}/UAT-Criteria.md` (folder proyek di vault).

## 4. Generated Metadata

Blueprint — bukan metadata dokumen siap publikasi.

```yaml
title: null
document_id: null
document_type: uat_criteria
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
acceptance_decision: null
approval_references: []
```

- `status` dokumen berbeda dari `project_status`.
- `acceptance_decision` adalah nilai terpisah dari `status` dan `decision` pada Approval-Record.

## 5. Required Sections

- **UAT Objectives** — tujuan UAT dan pertanyaan yang dijawabnya.
- **Scope** — apa yang termasuk dan tidak termasuk dalam UAT.
- **Prerequisites** — prasyarat lingkungan, data, dan akses sebelum UAT dijalankan.
- **Acceptance Criteria** — kriteria yang harus terpenuhi agar UAT dianggap berhasil.
- **Test Scenarios** — skenario uji beserta langkah, data uji, dan sistem yang diuji.
- **Expected Outcomes** — hasil yang diharapkan untuk setiap skenario.
- **Requirements Traceability** — keterlacakan skenario ke kebutuhan dan acceptance criteria.
- **Defect Handling** — klasifikasi defect dan alur eskalasinya.
- **Acceptance Decision** — keputusan acceptance aktual beserta pihak yang mengambilnya.
- **Sign-Off Evidence** — bukti persetujuan yang sah dan dapat ditelusuri.

## 6. Optional Sections

- **Test Environment and Data** — lingkungan dan data uji.
- **Out of Scope Scenarios** — skenario yang sengaja tidak diuji beserta alasannya.
- **Regression Notes** — catatan keterlacakan regresi bila relevan.
- **Related Documents** — requirements, scope, test plan, dan dokumen terkait.
- **Change Log** — perubahan kriteria beserta dasar pertanggungjawabannya.

## 7. Validation Checklist

Manual sebelum publikasi instance:

- [ ] Seluruh required section terisi.
- [ ] Acceptance Criteria, execution result, dan Acceptance Decision tidak tercampur.
- [ ] Skenario tertaut ke requirements dan acceptance criteria yang benar-benar ada.
- [ ] Expected Outcomes bersifat terverifikasi, bukan placeholder.
- [ ] Acceptance Decision tetap `null` bila belum ada keputusan sah.
- [ ] Tidak ada klaim UAT passed pada instance yang baru dibuat.
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
