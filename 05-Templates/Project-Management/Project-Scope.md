---
title: Project Scope
document_id: TPL-003
template_id: TPL-003
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
tags: ['ai-office', 'templates', 'projects', 'scope']
---

# Project Scope

## 1. Purpose

Dokumen ruang lingkup resmi sebuah proyek: apa yang termasuk dan tidak termasuk, deliverable, batas bisnis, dan kontrol perubahan scope.

Mengikuti [[03-Hermes/Governance/Project-Registration-Standard|Project Registration Standard]] (GOV-007).

- **Seluruh perubahan terhadap approved project scope memerlukan Organizational Owner approval** (GOV-005) — bukan hanya perubahan yang dinilai material.
- Penyesuaian operasional di dalam approved scope (tambahan task, urutan kerja, detail implementasi, jadwal internal) dapat dilakukan berdasarkan delegasi atau assignment yang masih berlaku.
- Scope bukan daftar task; detail teknis berada di GitHub Project Repository sebagai SSOT engineering.
- Approved scope yang berlaku **tidak** diturunkan menjadi draft dan baseline **tidak** ditimpa sebelum revision proposal disetujui.

## 2. Usage Instructions

1. Baca master sesuai **Gate 1 — Master Template** pada bagian 7.
2. Ekstrak **Generated Metadata blueprint** (bagian 4), **Required Sections** (bagian 5), dan **applicable optional sections** (bagian 6) yang memang relevan. **Jangan** menyalin seluruh isi master ke instance.
3. Isi metadata dan konten instance dari **fakta aktual** — jangan membawa frontmatter master, approval master, Usage Instructions, atau Validation Checklist internal.
4. Isi `author` dengan **pembuat aktual instance**, `source_template_id` dengan **ID master yang benar-benar digunakan**, `source_template_version` dengan **versi master yang benar-benar digunakan**, serta `created_at` dan `updated_at` dengan **tanggal aktual** (GOV-008).
5. Isi approval metadata (`reviewer`, `approved_by`, `approved_at`) **hanya** bila terdapat keputusan sah sesuai kewenangan; biarkan `null` bila belum ada (GOV-004, GOV-005).
6. Validasi instance terhadap **Gate 2 — Generated Document** pada bagian 7, lalu simpan pada Target SSOT.

**Jangan** mengubah master ini saat menghasilkan instance. **Jangan** mewariskan approval, author, identifier, atau timestamp master ke instance.

## 3. Target SSOT

`02-Projects/{Project-Name}/Project-Scope.md` (folder proyek di vault).

## 4. Generated Metadata

Blueprint — **bukan** metadata dokumen siap publikasi. `document_id` instance mengikuti GOV-008, bukan namespace `TPL`. **Jangan** memasukkan identitas, approval, author, atau timestamp master sebagai nilai aktual instance.

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
approval_references: []
```

- `status` dokumen berbeda dari `project_status`.
- `approved_by` dan `approved_at` terisi hanya setelah approval Organizational Owner yang sah.
- `approval_references` merujuk bukti approval scope itu sendiri — bukan menduplikasi registry otoritatif.
- `project_status` dan `project_owner` **tidak** dicantumkan di sini; sumber tunggalnya adalah Project Profile instance (`02-Projects/{Project-Name}/Project-Profile.md`) sebagai SSOT registrasi proyek (GOV-007).

### Approved scope revision workflow

Seluruh perubahan approved project scope mengikuti urutan berikut:

1. **Approved baseline tetap berlaku** selama proposal diproses — tidak diturunkan menjadi draft dan tidak ditimpa.
2. **Separate revision proposal** — pengajuan perubahan dicatat terpisah dari scope yang berlaku, mengikuti GOV-004 dan GOV-008.
3. **Base version verification** — versi dasar proposal diverifikasi terhadap versi scope approved terakhir.
4. **Analisis dampak** — dampak terhadap deliverable, acceptance criteria, resource, dan komitmen resmi diuraikan.
5. **Review dan Owner approval** — review oleh reviewer yang ditugaskan, kemudian keputusan Organizational Owner.
6. **Authorized publication versi pengganti** — versi baru dipublikasikan hanya setelah approval sah; versi sebelumnya tetap terdokumentasi.

Revision proposal ID **tidak** dialokasikan oleh template ini — mengikuti namespace GOV-008 bila registry tersebut tersedia.
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

- [ ] Sembilan required section terisi dan tidak tumpang tindih.
- [ ] In Scope dan Out of Scope tidak bertentangan.
- [ ] Deliverable selaras dengan charter dan acceptance criteria.
- [ ] Dependencies menyebut status nyata, bukan asumsi.
- [ ] Setiap perubahan scope sejak baseline memiliki referensi approval Organizational Owner.
- [ ] Approved baseline tidak diturunkan menjadi draft dan tidak ditimpa sebelum revision proposal disetujui.
- [ ] Base version proposal diverifikasi terhadap versi approved terakhir.
- [ ] Revisi dokumen approved mengikuti GOV-004 dan GOV-008.
- [ ] `document_id` instance mengikuti GOV-008, bukan namespace `TPL`.
- [ ] Tidak ada kredensial atau raw secret.
## 8. Governance References

- [[03-Hermes/Governance/Project-Registration-Standard|Project Registration Standard]] (GOV-007)
- [[03-Hermes/Governance/Approval-Policy|Approval Policy]] (GOV-005)
- [[03-Hermes/Governance/Information-Architecture|Information Architecture]] (GOV-002)
- [[03-Hermes/Governance/Naming-Conventions|Naming Conventions]] (GOV-008)
- [[03-Hermes/Governance/Document-Lifecycle|Document Lifecycle]] (GOV-004)
- [[03-Hermes/Governance/Authorization-Evidence/README|Authorization Evidence]] — mekanisme bootstrap bukti otorisasi
- [[03-Hermes/Governance/Authorization-Evidence/Template-Phase-1-Authorization-Confirmation|Template Phase 1 Authorization Confirmation]] — bukti keputusan Owner atas approval master ini; path eksplisit: `03-Hermes/Governance/Authorization-Evidence/Template-Phase-1-Authorization-Confirmation.md`
- [[05-Templates/Template-Standard|Template Standard]]
