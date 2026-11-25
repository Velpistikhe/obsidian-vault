---
title: UAT Criteria
document_id: TPL-009
template_id: TPL-009
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

1. Baca master sesuai **Gate 1 — Master Template** pada bagian 7.
2. Ekstrak **Generated Metadata blueprint** (bagian 4), **Required Sections** (bagian 5), dan **applicable optional sections** (bagian 6) yang memang relevan. **Jangan** menyalin seluruh isi master ke instance.
3. Isi metadata dan konten instance dari **fakta aktual** — jangan membawa frontmatter master, approval master, Usage Instructions, atau Validation Checklist internal.
4. Isi `author` dengan **pembuat aktual instance**, `source_template_id` dengan **ID master yang benar-benar digunakan**, `source_template_version` dengan **versi master yang benar-benar digunakan**, serta `created_at` dan `updated_at` dengan **tanggal aktual** (GOV-008).
5. Isi approval metadata (`reviewer`, `approved_by`, `approved_at`) **hanya** bila terdapat keputusan sah sesuai kewenangan; biarkan `null` bila belum ada (GOV-004, GOV-005).
6. Validasi instance terhadap **Gate 2 — Generated Document** pada bagian 7, lalu simpan pada Target SSOT.

**Jangan** mengubah master ini saat menghasilkan instance. **Jangan** mewariskan approval, author, identifier, atau timestamp master ke instance.

## 3. Target SSOT

`02-Projects/{Project-Name}/UAT-Criteria.md` (folder proyek di vault).

## 4. Generated Metadata

Blueprint — **bukan** metadata dokumen siap publikasi. `document_id` instance mengikuti GOV-008, bukan namespace `TPL`. **Jangan** memasukkan identitas, approval, author, atau timestamp master sebagai nilai aktual instance.

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
acceptance_decision: null
approval_references: []
```

- `status` dokumen berbeda dari `project_status`.
- `project_status` dan `project_owner` **tidak** dicantumkan di sini; sumber tunggalnya adalah Project Profile instance (`02-Projects/{Project-Name}/Project-Profile.md`) sebagai SSOT registrasi proyek (GOV-007).
- `acceptance_decision` adalah nilai terpisah dari `status` dan `decision` pada Approval-Record.
- `approval_references` merujuk bukti approval dokumen kriteria UAT itu sendiri — bukan menduplikasi registry otoritatif.

### Tujuh tingkat pemisahan

| Tingkat | Isi | Kapan diisi |
|---------|-----|-------------|
| **Proposed acceptance criteria** | Usulan kriteria yang belum disepakati | Draft dokumen. |
| **Agreed acceptance criteria** | Kriteria yang telah disepakati sesuai kewenangan | Setelah review dan persetujuan kriteria. |
| **Expected outcomes** | Hasil yang diharapkan per skenario, jelas dan dapat diuji | Sebelum eksekusi. |
| **Actual execution results** | Hasil eksekusi aktual | **Hanya** setelah eksekusi terjadi. |
| **Defects and retesting** | Klasifikasi defect, eskalasi, dan hasil retesting | **Hanya** setelah defect teridentifikasi dan diuji ulang. |
| **Authorized acceptance decision** | Keputusan acceptance oleh pihak berwenang | **Hanya** setelah keputusan sah. |
| **Sign-off evidence** | Bukti persetujuan yang sah dan dapat ditelusuri | **Hanya** setelah penandatanganan aktual. |

### Matriks eksekusi UAT

| UAT reference | Requirement reference | Expected result | Actual result | Execution status | Evidence reference |
|---|---|---|---|---|---|
| (contoh ilustratif) | (contoh ilustratif) | (contoh ilustratif) | (kosong sampai eksekusi) | (kosong sampai eksekusi) | (kosong sampai ada bukti) |

Kolom `UAT reference` dan `Requirement reference` memakai **local references** — bukan organizational identifier baru. **Contoh di atas hanya ilustrasi** dan tidak menjadi actual requirement.

### Batas acceptance UAT

**UAT passed tidak otomatis berarti**:

- **Project completion** — transisi `completed` mengikuti [[03-Hermes/Governance/Project-Registration-Standard|GOV-007]].
- **Production approval** — mengikuti kewenangan pada [[03-Hermes/Governance/Approval-Policy|GOV-005]].
- **Deployment authorization** — mengikuti [[03-Hermes/Governance/Approval-Policy|GOV-005]].

Approval **dokumen kriteria UAT** berbeda dari **acceptance decision atas hasil pengujian**.

Dokumen kriteria dapat **approved sebelum execution** tanpa mengklaim UAT passed atau acceptance. Technical testing details tetap berada pada GitHub Project Repository (GOV-002).

Bila pengisian actual results akan mengubah dokumen criteria yang sudah approved, ikuti GOV-004 — **boleh** menggunakan separate linked execution evidence tanpa menimpa approved criteria baseline.
## 5. Required Sections

- **UAT Objectives** — tujuan UAT dan pertanyaan yang dijawabnya.
- **Scope** — apa yang termasuk dan tidak termasuk dalam UAT.
- **Prerequisites** — prasyarat lingkungan, data, dan akses sebelum UAT dijalankan.
- **Acceptance Criteria** — kriteria yang harus terpenuhi agar UAT dianggap berhasil, dengan statusnya (proposed atau agreed).
- **Test Scenarios** — skenario uji beserta langkah, data uji, dan sistem yang diuji.
- **Expected Outcomes** — hasil yang diharapkan untuk setiap skenario; jelas dan dapat diuji.
- **Requirements Traceability** — keterlacakan skenario ke kebutuhan dan acceptance criteria.
- **Defect Handling** — klasifikasi defect dan alur eskalasinya, termasuk retesting.
- **Acceptance Decision** — **kondisional**: keputusan acceptance aktual beserta pihak yang mengambilnya; `null` bila belum ada keputusan sah.
- **Sign-Off Evidence** — **kondisional**: bukti persetujuan yang sah dan dapat ditelusuri.
## 6. Optional Sections

- **Test Environment and Data** — lingkungan dan data uji.
- **Out of Scope Scenarios** — skenario yang sengaja tidak diuji beserta alasannya.
- **Regression Notes** — catatan keterlacakan regresi dan hasil retesting bila relevan.
- **Execution Evidence** — **kondisional**: linked execution evidence terpisah bila actual results dicatat tanpa menimpa approved criteria baseline.
- **Related Documents** — requirements, scope, test plan, dan dokumen terkait.
- **Change Log** — perubahan kriteria beserta dasar pertanggungjawabannya.
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

- [ ] Seluruh required section terisi.
- [ ] Acceptance Criteria, execution result, dan Acceptance Decision tidak tercampur.
- [ ] Status acceptance criteria jelas: proposed atau agreed.
- [ ] Skenario tertaut ke requirements dan acceptance criteria yang benar-benar ada.
- [ ] Expected Outcomes bersifat terverifikasi, bukan placeholder, dan dapat diuji.
- [ ] Actual result, execution status, defect, retest, dan sign-off hanya diisi berdasarkan kejadian aktual.
- [ ] Acceptance Decision tetap `null` bila belum ada keputusan sah.
- [ ] Tidak ada klaim UAT passed pada instance yang baru dibuat.
- [ ] Dokumen approved sebelum execution tidak mengklaim UAT passed atau acceptance.
- [ ] UAT passed tidak diperlakukan sebagai project completion, production approval, atau deployment authorization.
- [ ] Approval dokumen kriteria dipisahkan dari acceptance decision atas hasil pengujian.
- [ ] Matriks eksekusi memakai local references; contoh ilustratif tidak terbawa sebagai actual data.
- [ ] Technical testing details tidak diduplikasi ke vault.
- [ ] Pengisian actual results pada dokumen approved mengikuti GOV-004 dan tidak menimpa approved criteria baseline.
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
