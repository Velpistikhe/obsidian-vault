---
title: Project Scope
document_id: TPL-003
template_id: TPL-003
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
tags: ['ai-office', 'templates', 'projects', 'scope']
---

# Project Scope

## 1. Purpose

Dokumen ruang lingkup resmi sebuah proyek: apa yang termasuk dan tidak termasuk, deliverable, batas bisnis, dan kontrol perubahan scope.

Mengikuti [[03-Hermes/Governance/Project-Registration-Standard|Project Registration Standard]] (GOV-007).

- **Seluruh perubahan terhadap approved project scope memerlukan Organizational Owner approval** (GOV-005) — bukan hanya perubahan yang dinilai material.
- Penyesuaian operasional di dalam approved scope (tambahan task, urutan kerja, detail implementasi, jadwal internal) dapat dilakukan berdasarkan delegasi atau assignment yang masih berlaku.
- Scope bukan daftar task; detail teknis berada di GitHub Project Repository sebagai SSOT engineering.

## 2. Usage Instructions

1. Baca master ini berstatus `approved` (untuk penggunaan resmi).
2. Ekstrak Generated Metadata blueprint dan Required Sections.
3. Isi dari fakta aktual — jangan membawa frontmatter master, approval master, Usage Instructions, atau Validation Checklist internal.
4. Isi `source_template_id` dan `source_template_version` dengan master yang benar-benar digunakan.
5. Validasi instance, lalu simpan pada Target SSOT.

**Jangan** mengubah master ini saat menghasilkan instance.

## 3. Target SSOT

`02-Projects/{Project-Name}/Project-Scope.md` (folder proyek di vault).

## 4. Generated Metadata

Blueprint — bukan metadata dokumen siap publikasi.

```yaml
title: null
document_id: null
document_type: project_scope
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
- `approved_by` dan `approved_at` terisi hanya setelah approval Organizational Owner yang sah.

## 5. Required Sections

- **Scope Overview** — ringkasan ruang lingkup dan tujuan dokumen ini.
- **In Scope** — aktivitas, hasil, dan sistem yang tercakup.
- **Out of Scope** — hal yang sengaja tidak dikerjakan beserta alasannya.
- **Deliverables** — hasil proyek yang harus diserahkan beserta kriteria penyampaiannya.
- **Business Boundaries** — batas bisnis, antarorganisasi, dan batasan kepatuhan yang berlaku.
- **Constraints** — batasan waktu, biaya, teknologi, dan sumber daya.
- **Dependencies** — dependensi ke proyek, sistem, tim, atau vendor lain beserta statusnya.
- **Acceptance Criteria** — kriteria penerimaan pada tingkat bisnis yang disepakati.
- **Scope Change Control** — proses pengajuan, persetujuan, dan pencatatan perubahan scope.

## 6. Optional Sections

- **Assumptions** — asumsi yang mendasari scope.
- **Scope Exclusions** — pengecualian yang bersifat sementara atau terbatas waktu.
- **Related Documents** — charter, plan, requirements, dan dokumen terkait.
- **Change Log** — riwayat perubahan scope beserta referensi approval.

## 7. Validation Checklist

Manual sebelum publikasi instance:

- [ ] Sembilan required section terisi dan tidak tumpang tindih.
- [ ] In Scope dan Out of Scope tidak bertentangan.
- [ ] Deliverable selaras dengan charter dan acceptance criteria.
- [ ] Dependencies menyebut status nyata, bukan asumsi.
- [ ] Setiap perubahan scope sejak baseline memiliki referensi approval Organizational Owner.
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
