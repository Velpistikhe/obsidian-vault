---
title: Project Charter
document_id: TPL-002
template_id: TPL-002
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
tags: ['ai-office', 'templates', 'projects', 'charter']
---

# Project Charter

## 1. Purpose

Dokumen otoritas dan tujuan resmi sebuah proyek: dasar Business Value, tujuan, batas tinggi, dan komitmen yang disetujui Organizational Owner.

Mengikuti [[03-Hermes/Governance/Project-Registration-Standard|Project Registration Standard]] (GOV-007).

- Charter memerlukan **Organizational Owner approval** sebelum dianggap sah.
- Charter bukan pengganti Project Scope; detail ruang lingkup ada di scope terpisah.
- Draft charter dapat dipublikasikan untuk review tanpa approval evidence yang belum tersedia, tetapi **tidak boleh mengklaim approval**.

## 2. Usage Instructions

1. Baca master sesuai **Gate 1 — Master Template** pada bagian 7.
2. Ekstrak **Generated Metadata blueprint** (bagian 4), **Required Sections** (bagian 5), dan **applicable optional sections** (bagian 6) yang memang relevan. **Jangan** menyalin seluruh isi master ke instance.
3. Isi metadata dan konten instance dari **fakta aktual** — jangan membawa frontmatter master, approval master, Usage Instructions, atau Validation Checklist internal.
4. Isi `author` dengan **pembuat aktual instance**, `source_template_id` dengan **ID master yang benar-benar digunakan**, `source_template_version` dengan **versi master yang benar-benar digunakan**, serta `created_at` dan `updated_at` dengan **tanggal aktual** (GOV-008).
5. Isi approval metadata (`reviewer`, `approved_by`, `approved_at`) **hanya** bila terdapat keputusan sah sesuai kewenangan; biarkan `null` bila belum ada (GOV-004, GOV-005).
6. Validasi instance terhadap **Gate 2 — Generated Document** pada bagian 7, lalu simpan pada Target SSOT.

**Jangan** mengubah master ini saat menghasilkan instance. **Jangan** mewariskan approval, author, identifier, atau timestamp master ke instance.

## 3. Target SSOT

`02-Projects/{Project-Name}/Project-Charter.md` (folder proyek di vault).

## 4. Generated Metadata

Blueprint — **bukan** metadata dokumen siap publikasi. `document_id` instance mengikuti GOV-008, bukan namespace `TPL`. **Jangan** memasukkan identitas, approval, author, atau timestamp master sebagai nilai aktual instance.

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
approval_references: []
```

- `status` dokumen berbeda dari `project_status`.
- `approved_by` dan `approved_at` terisi hanya setelah Organizational Owner approval yang sah.
- `approval_references` merujuk bukti approval charter itu sendiri — bukan menduplikasi registry otoritatif.
- `project_status` dan `project_owner` **tidak** dicantumkan di sini; sumber tunggalnya adalah Project Profile instance (`02-Projects/{Project-Name}/Project-Profile.md`) sebagai SSOT registrasi proyek (GOV-007).

### Pemisahan draft publication dan approved publication

| Situasi | Yang dicatat |
|---------|-------------|
| Draft charter untuk review | `status: draft`; `approved_by`/`approved_at` = `null`; alasan belum disetujui dicatat eksplisit. |
| Charter approved | `status: approved`; keputusan Organizational Owner yang sah; `approved_by` dan `approved_at` aktual; `approval_references` menunjuk evidence reference keputusan tersebut. |

Draft charter **tidak boleh** menampilkan klaim approval, dan published draft **tidak sama** dengan approved charter.
## 5. Required Sections

- **Executive Summary** — ringkasan singkat proyek, tujuan, dan nilai bisnisnya.
- **Background** — konteks, pemicu, dan alasan proyek dimulai.
- **Project Objectives** — tujuan yang terukur dan prioritasnya.
- **Business Value** — manfaat yang diharapkan bagi organisasi.
- **Stakeholders** — pihak yang berkepentingan, tanggung jawab, kewenangan, dan peran masing-masing dalam proyek.
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

- [ ] Seluruh 10 required section terisi.
- [ ] Tujuan strategis dan success criteria dapat diverifikasi.
- [ ] Draft tidak mengklaim approval; `approved_by`/`approved_at` tetap `null` bila belum ada keputusan sah.
- [ ] Charter approved memuat keputusan Organizational Owner yang sah, evidence reference, `approved_by`, dan `approved_at` aktual.
- [ ] Detail implementasi teknis tidak masuk di luar tingkat bisnis.
- [ ] `document_id` instance mengikuti GOV-008, bukan namespace `TPL`.
- [ ] Tidak ada kredensial atau raw secret.
## 8. Governance References

- [[03-Hermes/Governance/Project-Registration-Standard|Project Registration Standard]] (GOV-007)
- [[03-Hermes/Governance/Approval-Policy|Approval Policy]] (GOV-005)
- [[03-Hermes/Governance/AI-Office-Charter|AI Office Charter]] (GOV-001)
- [[03-Hermes/Governance/Naming-Conventions|Naming Conventions]] (GOV-008)
- [[03-Hermes/Governance/Document-Lifecycle|Document Lifecycle]] (GOV-004)
- [[03-Hermes/Governance/Authorization-Evidence/README|Authorization Evidence]] — mekanisme bootstrap bukti otorisasi
- [[03-Hermes/Governance/Authorization-Evidence/Template-Phase-1-Authorization-Confirmation|Template Phase 1 Authorization Confirmation]] — bukti keputusan Owner atas approval master ini; path eksplisit: `03-Hermes/Governance/Authorization-Evidence/Template-Phase-1-Authorization-Confirmation.md`
- [[05-Templates/Template-Standard|Template Standard]]
