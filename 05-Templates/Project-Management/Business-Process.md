---
title: Business Process
document_id: TPL-008
template_id: TPL-008
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
tags: ['ai-office', 'templates', 'projects', 'process']
---

# Business Process

## 1. Purpose

Dokumentasi alur kerja bisnis sebuah proyek atau unit: tujuan proses, aktor, pemicu, input/output, kondisi saat ini dan target, aturan, penanganan pengecualian, serta validasi.

Mengikuti [[03-Hermes/Governance/Project-Registration-Standard|Project Registration Standard]] (GOV-007).

- Template ini bersifat **kondisional** — digunakan bila proses bisnis memang perlu didokumentasikan terpisah.
- Diagram bersifat opsional: dapat memakai Mermaid atau representasi terstruktur (tabel/langkah).
- Proses yang sudah otomatis di sistem tetap memiliki SSOT teknis di GitHub Project Repository (GOV-002); vault memuat deskripsi bisnisnya.
- **Seluruh perubahan business process yang mengubah approved project scope memerlukan Organizational Owner approval** (GOV-005, GOV-007). Revisi dokumen business process yang approved mengikuti GOV-004 dan GOV-008.

## 2. Usage Instructions

1. Baca master sesuai **Gate 1 — Master Template** pada bagian 7.
2. Ekstrak **Generated Metadata blueprint** (bagian 4), **Required Sections** (bagian 5), dan **applicable optional sections** (bagian 6) yang memang relevan. **Jangan** menyalin seluruh isi master ke instance.
3. Isi metadata dan konten instance dari **fakta aktual** — jangan membawa frontmatter master, approval master, Usage Instructions, atau Validation Checklist internal.
4. Isi `author` dengan **pembuat aktual instance**, `source_template_id` dengan **ID master yang benar-benar digunakan**, `source_template_version` dengan **versi master yang benar-benar digunakan**, serta `created_at` dan `updated_at` dengan **tanggal aktual** (GOV-008).
5. Isi approval metadata (`reviewer`, `approved_by`, `approved_at`) **hanya** bila terdapat keputusan sah sesuai kewenangan; biarkan `null` bila belum ada (GOV-004, GOV-005).
6. Validasi instance terhadap **Gate 2 — Generated Document** pada bagian 7, lalu simpan pada Target SSOT.

**Jangan** mengubah master ini saat menghasilkan instance. **Jangan** mewariskan approval, author, identifier, atau timestamp master ke instance.

## 3. Target SSOT

`02-Projects/{Project-Name}/Business-Process.md` (folder proyek di vault).

## 4. Generated Metadata

Blueprint — **bukan** metadata dokumen siap publikasi. `document_id` instance mengikuti GOV-008, bukan namespace `TPL`. **Jangan** memasukkan identitas, approval, author, atau timestamp master sebagai nilai aktual instance.

```yaml
title: null
document_id: null
document_type: business_process
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
```

- `status` dokumen berbeda dari `project_status`.
- `project_status` **tidak** dicantumkan di sini; sumber tunggalnya adalah Project Profile instance (`02-Projects/{Project-Name}/Project-Profile.md`) sebagai SSOT registrasi proyek (GOV-007).
- `approval_references` merujuk bukti approval business process itu sendiri — bukan menduplikasi registry otoritatif.

### Empat tingkat status proses

| Tingkat | Makna |
|---------|-------|
| **Actual As-Is process** | Proses yang benar-benar berjalan saat ini. |
| **Proposed To-Be process** | Proses target yang **diajukan**; belum disetujui dan belum diimplementasikan. |
| **Approved To-Be process** | Proses target yang **telah disetujui** sesuai kewenangan, dengan evidence reference. |
| **Implemented and verified process** | Proses target yang telah diimplementasikan **dan** diverifikasi; pembuktian dilakukan lewat mekanisme validasi. |

**Approval atas To-Be process tidak otomatis membuktikan implementasi telah selesai.**
## 5. Required Sections

- **Process Overview** — deskripsi proses, ruang lingkupnya, dan keterkaitannya dengan proyek.
- **Process Objectives** — hasil yang ingin dicapai proses.
- **Actors and Responsibilities** — aktor yang terlibat, tanggung jawab, dan **authorization boundary** masing-masing; dibedakan pihak yang mengusulkan, meninjau, menyetujui, dan menjalankan proses.
- **Triggers** — peristiwa atau kondisi yang memulai proses.
- **Inputs and Outputs** — data dan dokumen masuk serta keluaran proses.
- **As-Is Process** — kondisi aktual saat ini bila relevan.
- **To-Be Process** — kondisi target beserta gap terhadap kondisi aktual, dan statusnya (proposed atau approved).
- **Business Rules** — aturan yang berlaku di sepanjang proses.
- **Exception Handling** — skenario pengecualian dan penanganannya.
- **Process Validation** — cara proses diverifikasi, diukur, dan ditinjau ulang.
## 6. Optional Sections

- **Alternative Flows** — **kondisional**: alur alternatif yang applicable beserta trigger dan outcome-nya. Dibedakan dari normal flow dan exception flow.
- **Process Diagram** — diagram Mermaid atau representasi terstruktur.
- **Process Metrics** — indikator kinerja proses dan targetnya.
- **Known Issues** — isu proses yang diketahui.
- **Related Documents** — requirements, scope, dan dokumen terkait.
- **Change Log** — perubahan proses beserta dasar pertanggungjawabannya.
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

- [ ] Seluruh required section terisi; As-Is diisi bila relevan.
- [ ] Alur dapat ditelusuri dari trigger sampai output.
- [ ] Aktor dan tanggung jawabnya konsisten dengan kebutuhan bisnis.
- [ ] Authorization boundary tiap aktor jelas; pihak yang mengusulkan, meninjau, menyetujui, dan menjalankan dibedakan.
- [ ] Template tidak menyatakan role, kewenangan, atau permission baru yang tidak berlaku.
- [ ] Aturan dan exception handling tidak bertentangan.
- [ ] Alternative flows (bila ada) memuat trigger dan outcome, dan dibedakan dari normal flow serta exception flow.
- [ ] To-Be Process mencantumkan statusnya (proposed atau approved) dan tidak mengklaim implementasi telah selesai.
- [ ] Perubahan yang mengubah approved project scope memiliki referensi approval Organizational Owner.
- [ ] Revisi dokumen approved mengikuti GOV-004 dan GOV-008.
- [ ] Diagram (bila ada) sesuai dengan deskripsi tertulis.
- [ ] `document_id` instance mengikuti GOV-008, bukan namespace `TPL`.
- [ ] Tidak ada kredensial atau raw secret.
## 8. Governance References

- [[03-Hermes/Governance/Project-Registration-Standard|Project Registration Standard]] (GOV-007)
- [[03-Hermes/Governance/Approval-Policy|Approval Policy]] (GOV-005)
- [[03-Hermes/Governance/Information-Architecture|Information Architecture]] (GOV-002)
- [[03-Hermes/Governance/Knowledge-Management-Policy|Knowledge Management Policy]] (GOV-003)
- [[03-Hermes/Governance/Naming-Conventions|Naming Conventions]] (GOV-008)
- [[03-Hermes/Governance/Document-Lifecycle|Document Lifecycle]] (GOV-004)
- [[03-Hermes/Governance/Authorization-Evidence/README|Authorization Evidence]] — mekanisme bootstrap bukti otorisasi
- [[03-Hermes/Governance/Authorization-Evidence/Template-Phase-1-Authorization-Confirmation|Template Phase 1 Authorization Confirmation]] — bukti keputusan Owner atas approval master ini; path eksplisit: `03-Hermes/Governance/Authorization-Evidence/Template-Phase-1-Authorization-Confirmation.md`
- [[05-Templates/Template-Standard|Template Standard]]
