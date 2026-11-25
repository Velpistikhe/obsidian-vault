---
title: Project Profile
document_id: TPL-001
template_id: TPL-001
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
tags: ['ai-office', 'templates', 'projects', 'registration']
---

# Project Profile

## 1. Purpose

Dokumen registrasi otoritatif sebuah proyek di AI Office. Project Profile adalah **SSOT registrasi proyek** di vault: identitas, ownership, status lifecycle, resource references, dan jejak approval/delegasi terkait proyek.

Mengikuti [[03-Hermes/Governance/Project-Registration-Standard|Project Registration Standard]] (GOV-007).

- Registrasi **tidak** memberi delegasi atau permission otomatis.
- `project_status` (project lifecycle) **berbeda** dari `status` (document lifecycle).
- Aktivasi proyek membutuhkan **explicit Organizational Owner approval**.

## 2. Usage Instructions

1. Baca master ini berstatus `approved` (untuk penggunaan resmi).
2. Ekstrak Generated Metadata blueprint dan Required Sections.
3. Isi metadata dan konten instance dari **fakta aktual** — jangan menyalin frontmatter master, approval master, Usage Instructions, atau Validation Checklist internal.
4. Isi `source_template_id` dan `source_template_version` dengan master yang benar-benar digunakan.
5. Validasi instance, lalu simpan pada Target SSOT.

**Jangan** mengubah master ini saat menghasilkan instance.

## 3. Target SSOT

`02-Projects/{Project-Name}/Project-Profile.md`

Folder proyek dan `project_id` hanya dibuat melalui workflow registrasi GOV-007; template ini tidak mengalokasikan ID.

## 4. Generated Metadata

Blueprint — **bukan** metadata dokumen siap publikasi. `document_id` instance mengikuti GOV-008 (pola `PRJ-NNN-DOC-NNN`), bukan namespace `TPL`.

```yaml
title: null
document_id: null
document_type: project_profile
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
# --- konteks proyek (GOV-007) ---
project_id: null
project_name: null
description: null
project_owner: null
project_manager: null
project_status: null
repository: null
knowledge_location: null
workspace_location: null
kanban_reference: null
assigned_agents: []
approval_references: []
delegation_references: []
```

Aturan pengisian field registrasi:

- Nilai tunggal yang belum tersedia → `null`; koleksi kosong → `[]`.
- Status seperti `pending_verification` atau `not_applicable` dicatat pada field status terpisah bila diperlukan — bukan sebagai nilai ID/path.
- `approval_references` adalah array referensi approval dengan jenis approval yang dapat ditelusuri (charter, scope, activation, perubahan berikutnya).
- `created_at` diisi saat registrasi awal dan tidak diubah kecuali koreksi metadata terbukti salah; `updated_at` diperbarui setiap perubahan.
- Jangan mengisi placeholder seolah-olah resource atau assignment sudah operasional.

## 5. Required Sections

- **Project Identity** — `project_id`, `project_name`, `description`, `knowledge_location`.
- **Ownership** — `project_owner` (tujuan bisnis, relevansi, acceptance) dan `project_manager` (planning, task, milestone, koordinasi sesuai delegasi).
- **Project Status** — `project_status` beserta transisi yang terjadi dan otoritasnya.
- **Resource References** — `repository`, `workspace_location`, `kanban_reference` (jika integrasi tersedia), `assigned_agents`.
- **Approval and Delegation Trail** — `approval_references`, `delegation_references`.
- **Registration Record** — `created_at`, `updated_at`, dan jejak registrasi.

## 6. Optional Sections

- **Activation Checklist Status** — kesiapan terhadap kriteria aktivasi GOV-007.
- **Related Documents** — charter, scope, plan, dan dokumen proyek lain.
- **Change Log** — perubahan registrasi beserta referensi approval.
- **Blockers and Risks** — catatan risiko registrasi.

## 7. Validation Checklist

Manual sebelum publikasi instance:

- [ ] Semua field registrasi GOV-007 ada.
- [ ] `null`/`[]` dipakai sesuai tipe field.
- [ ] `project_status` tidak tertukar dengan `status` dokumen.
- [ ] `approval_references` dan `delegation_references` hanya berisi referensi yang benar-benar ada.
- [ ] Tidak ada delegasi/assignment yang diklaim tanpa dasar.
- [ ] Resource yang belum tersedia tidak dipakai sebagai dasar pekerjaan yang bergantung padanya.
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
- [[03-Hermes/Governance/Knowledge-Management-Policy|Knowledge Management Policy]] (GOV-003)
- [[05-Templates/Template-Standard|Template Standard]]
