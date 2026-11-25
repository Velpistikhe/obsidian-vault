---
title: Project Plan
document_id: TPL-004
template_id: TPL-004
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
tags: ['ai-office', 'templates', 'projects', 'planning']
---

# Project Plan

## 1. Purpose

Dokumen perencanaan tingkat proyek: baseline planning, strategi pengerjaan, struktur pekerjaan, milestone, kebutuhan resource, dan kontrol pemantauan.

Mengikuti [[03-Hermes/Governance/Project-Registration-Standard|Project Registration Standard]] (GOV-007).

- **Planning tidak memberikan assignment atau delegasi otomatis.**
- Rencana harus **selaras dengan baseline scope yang berlaku**. Penyesuaian operasional **tidak boleh** mengubah approved scope atau komitmen resmi; perubahan tersebut memerlukan proses persetujuan terpisah oleh Organizational Owner.
- Project Plan mengikuti review/approval operasional sesuai GOV-005; review tersebut bukan persetujuan scope.
- Kanban menjadi target live task SSOT **setelah integrasi diverifikasi**; saat ini integrasi berstatus Pending Verification (GOV-002).

### Pemisahan tingkat commitment

| Tingkat | Makna |
|---------|-------|
| **Proposed plan** | Usulan perencanaan awal; belum direview dan belum menjadi komitmen. |
| **Reviewed operational plan** | Sudah direview sesuai kewenangan; boleh menjadi dasar kerja operasional, tetapi belum mengikat organisasi. |
| **Official commitment** | Milestone dan commitment biaya yang telah menjadi komitmen resmi — memerlukan Organizational Owner authority (GOV-005). |
| **Actual execution** | Pelaksanaan aktual; dicatat pada laporan status, bukan pada rencana. |

Target internal (target angka, target sprint, asumsi kapasitas) **tidak** otomatis menjadi komitmen resmi. Charter atau scope berstatus draft boleh dirujuk dalam proposed planning **dengan status yang jelas**, tetapi **tidak** menjadi dasar pekerjaan yang memerlukan aktivasi proyek. Planning baseline untuk activation mengikuti GOV-007.

### Work packages versus live task board

Project Plan menyimpan **work packages, deliverables, milestone, dan dependencies pada tingkat proyek**. Operational tasks, assignment, dan live task status menjadi SSOT Kanban setelah integrasi diverifikasi — Project Plan **tidak** menjadi duplikasi live task board. Integrasi Kanban tetap **Pending Verification**.

## 2. Usage Instructions

1. Baca master sesuai **Gate 1 — Master Template** pada bagian 7.
2. Ekstrak **Generated Metadata blueprint** (bagian 4), **Required Sections** (bagian 5), dan **applicable optional sections** (bagian 6) yang memang relevan. **Jangan** menyalin seluruh isi master ke instance.
3. Isi metadata dan konten instance dari **fakta aktual** — jangan membawa frontmatter master, approval master, Usage Instructions, atau Validation Checklist internal.
4. Isi `author` dengan **pembuat aktual instance**, `source_template_id` dengan **ID master yang benar-benar digunakan**, `source_template_version` dengan **versi master yang benar-benar digunakan**, serta `created_at` dan `updated_at` dengan **tanggal aktual** (GOV-008).
5. Isi approval metadata (`reviewer`, `approved_by`, `approved_at`) **hanya** bila terdapat keputusan sah sesuai kewenangan; biarkan `null` bila belum ada (GOV-004, GOV-005).
6. Validasi instance terhadap **Gate 2 — Generated Document** pada bagian 7, lalu simpan pada Target SSOT.

**Jangan** mengubah master ini saat menghasilkan instance. **Jangan** mewariskan approval, author, identifier, atau timestamp master ke instance.

## 3. Target SSOT

`02-Projects/{Project-Name}/Project-Plan.md` (folder proyek di vault).

## 4. Generated Metadata

Blueprint — **bukan** metadata dokumen siap publikasi. `document_id` instance mengikuti GOV-008, bukan namespace `TPL`. **Jangan** memasukkan identitas, approval, author, atau timestamp master sebagai nilai aktual instance.

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
delegation_references: []
```

- `status` dokumen berbeda dari `project_status`.
- `project_status` **tidak** dicantumkan di sini; sumber tunggalnya adalah Project Profile instance (`02-Projects/{Project-Name}/Project-Profile.md`) sebagai SSOT registrasi proyek (GOV-007).
- `delegation_references` hanya berisi delegasi yang benar-benar aktif dan relevan bagi dokumen ini.
- `approval_references` pada dokumen ini merujuk bukti approval yang relevan dengan plan — bukan menduplikasi registry otoritatif.
## 5. Required Sections

- **Planning Baseline** — versi rencana, tanggal baseline, dan dokumen acuan (charter dan scope approved) beserta statusnya.
- **Delivery Strategy** — pendekatan pengerjaan, fase, dan tingkat integrasi.
- **Work Breakdown Structure** — hierarki work package, deliverable, dan milestone pada tingkat proyek.
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
- [ ] Rencana **selaras dengan baseline scope yang berlaku**; penyesuaian operasional tidak mengubah approved scope atau komitmen resmi, dan perubahan tersebut melalui proses persetujuan terpisah oleh Organizational Owner.
- [ ] Tingkat commitment pada setiap item jelas: proposed, reviewed operational plan, official commitment, atau actual execution.
- [ ] Target internal tidak diperlakukan sebagai komitmen resmi tanpa Organizational Owner authority.
- [ ] Milestone memiliki target waktu yang jelas.
- [ ] Resource requirements tidak mengklaim assignment atau delegasi yang tidak ada.
- [ ] Project Plan tidak menduplikasi operational task board; live task status tetap SSOT Kanban.
- [ ] Klaim status Kanban tidak menyatakan integrasi sebagai operational.
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
