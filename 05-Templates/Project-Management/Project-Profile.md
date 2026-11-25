---
title: Project Profile
document_id: TPL-001
template_id: TPL-001
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
tags: ['ai-office', 'templates', 'projects', 'registration']
---

# Project Profile

## 1. Purpose

Dokumen registrasi otoritatif sebuah proyek di AI Office. Project Profile adalah **authoritative living registration record** dan **SSOT registrasi proyek** di vault: identitas, ownership, status lifecycle, resource references, dan jejak approval/delegasi terkait proyek.

Mengikuti [[03-Hermes/Governance/Project-Registration-Standard|Project Registration Standard]] (GOV-007).

- Registrasi **tidak** memberi delegasi atau permission otomatis.
- `project_status` (project lifecycle) **berbeda** dari `status` (document lifecycle).
- Aktivasi proyek membutuhkan **explicit Organizational Owner approval**.
- **Living record:** pembaruan lifecycle, resource references, assignment, dan approval references dicatat **hanya** berdasarkan kejadian aktual yang terotorisasi. Pembaruan record **tidak** memberikan kewenangan baru.

### Peran dan kewenangan

| Peran | Kewenangan |
|-------|------------|
| **Organizational Owner** | Otoritas strategis: charter, scope, aktivasi, komitmen resmi, dan keputusan yang mengikat organisasi. |
| **Project Owner** | Penanggung jawab tujuan bisnis, relevansi proyek, dan acceptance **sesuai kewenangan** yang diberikan. **Tidak** otomatis memiliki strategic approval authority. |
| **Project Manager** | Planning, task, milestone, dan koordinasi **sesuai delegasi** yang berlaku. |

### Activation readiness

Kesiapan aktivasi mengikuti kriteria aktivasi [[03-Hermes/Governance/Project-Registration-Standard|Project Registration Standard]] (GOV-007) dan dicatat pada instance dengan evidence reference terhadap criteria yang relevan.

| Status proyek | Activation readiness |
|---|---|
| `proposed` | Opsional — belum memerlukan criteria aktivasi lengkap. |
| `planning` | Mulai dipersiapkan — kelengkapan criteria aktivasi sedang dikumpulkan. |
| `pending_approval` | **Wajib tersedia** — criteria aktivasi lengkap dan pengajuan keputusan aktivasi siap diajukan. |
| `active` | **Wajib tersedia** — bukti pemenuhan seluruh criteria aktivasi GOV-007 dan Owner activation approval tercatat. |

Resource yang berstatus pending verification atau unavailable **tidak boleh** menjadi dasar pekerjaan yang bergantung padanya.

## 2. Usage Instructions

1. Baca master sesuai **Gate 1 — Master Template** pada bagian 7.
2. Ekstrak **Generated Metadata blueprint** (bagian 4), **Required Sections** (bagian 5), dan **applicable optional sections** (bagian 6) yang memang relevan. **Jangan** menyalin seluruh isi master ke instance.
3. Isi metadata dan konten instance dari **fakta aktual** — jangan membawa frontmatter master, approval master, Usage Instructions, atau Validation Checklist internal.
4. Isi `author` dengan **pembuat aktual instance**, `source_template_id` dengan **ID master yang benar-benar digunakan**, `source_template_version` dengan **versi master yang benar-benar digunakan**, serta `created_at` dan `updated_at` dengan **tanggal aktual** (GOV-008).
5. Isi approval metadata (`reviewer`, `approved_by`, `approved_at`) **hanya** bila terdapat keputusan sah sesuai kewenangan; biarkan `null` bila belum ada (GOV-004, GOV-005).
6. Validasi instance terhadap **Gate 2 — Generated Document** pada bagian 7, lalu simpan pada Target SSOT.

**Jangan** mengubah master ini saat menghasilkan instance. **Jangan** mewariskan approval, author, identifier, atau timestamp master ke instance.

## 3. Target SSOT

`02-Projects/{Project-Name}/Project-Profile.md`

Folder proyek dan `project_id` hanya dibuat melalui workflow registrasi GOV-007; template ini tidak mengalokasikan ID.

## 4. Generated Metadata

Blueprint — **bukan** metadata dokumen siap publikasi. `document_id` instance mengikuti GOV-008, bukan namespace `TPL`. **Jangan** memasukkan identitas, approval, author, atau timestamp master sebagai nilai aktual instance.

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
- **Ownership** — Organizational Owner, Project Owner, dan Project Manager beserta kewenangan masing-masing; Project Owner tidak diasumsikan memiliki strategic approval authority.
- **Project Status** — `project_status` beserta transisi yang terjadi dan otoritasnya.
- **Resource References** — `repository`, `workspace_location`, `kanban_reference` (jika integrasi tersedia), `assigned_agents`.
- **Approval and Delegation Trail** — `approval_references`, `delegation_references`.
- **Registration Record** — `created_at`, `updated_at`, dan jejak registrasi.

## 6. Optional Sections

- **Activation Readiness** — kesiapan terhadap kriteria aktivasi GOV-007 per status proyek, beserta evidence reference tiap criteria yang relevan. **Wajib** untuk status `pending_approval` dan `active`; opsional untuk `proposed` dan `planning`.
- **Related Documents** — charter, scope, plan, dan dokumen proyek lain.
- **Change Log** — perubahan registrasi beserta referensi approval.
- **Blockers and Risks** — catatan risiko registrasi.

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

- [ ] Seluruh field registrasi GOV-007 ada dan `null`/`[]` dipakai sesuai tipe field.
- [ ] `project_status` tidak tertukar dengan `status` dokumen.
- [ ] `approval_references` dan `delegation_references` hanya berisi referensi yang benar-benar ada.
- [ ] Tidak ada delegasi/assignment yang diklaim tanpa dasar.
- [ ] Resource yang belum tersedia tidak dipakai sebagai dasar pekerjaan yang bergantung padanya.
- [ ] Activation readiness konsisten dengan status proyek dan memuat evidence reference criteria aktivasi.
- [ ] Kewenangan Organizational Owner, Project Owner, dan Project Manager tidak tertukar.
- [ ] Pembaruan living record hanya memuat kejadian aktual yang terotorisasi.
- [ ] `document_id` instance mengikuti GOV-008, bukan namespace `TPL`.
- [ ] Tidak ada kredensial atau raw secret.

## 8. Governance References

- [[03-Hermes/Governance/Project-Registration-Standard|Project Registration Standard]] (GOV-007)
- [[03-Hermes/Governance/Approval-Policy|Approval Policy]] (GOV-005)
- [[03-Hermes/Governance/Information-Architecture|Information Architecture]] (GOV-002)
- [[03-Hermes/Governance/Naming-Conventions|Naming Conventions]] (GOV-008)
- [[03-Hermes/Governance/Document-Lifecycle|Document Lifecycle]] (GOV-004)
- [[03-Hermes/Governance/Knowledge-Management-Policy|Knowledge Management Policy]] (GOV-003)
- [[03-Hermes/Governance/Authorization-Evidence/README|Authorization Evidence]] — mekanisme bootstrap bukti otorisasi
- [[03-Hermes/Governance/Authorization-Evidence/Template-Phase-1-Authorization-Confirmation|Template Phase 1 Authorization Confirmation]] — bukti keputusan Owner atas approval master ini; path eksplisit: `03-Hermes/Governance/Authorization-Evidence/Template-Phase-1-Authorization-Confirmation.md`
- [[05-Templates/Template-Standard|Template Standard]]
