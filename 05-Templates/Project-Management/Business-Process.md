---
title: Business Process
document_id: TPL-008
template_id: TPL-008
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
tags: ['ai-office', 'templates', 'projects', 'process']
---

# Business Process

## 1. Purpose

Dokumentasi alur kerja bisnis sebuah proyek atau unit: tujuan proses, aktor, pemicu, input/output, kondisi saat ini dan target, aturan, penanganan pengecualian, serta validasi.

Mengikuti [[03-Hermes/Governance/Project-Registration-Standard|Project Registration Standard]] (GOV-007).

- Template ini bersifat **kondisional** — digunakan bila proses bisnis memang perlu didokumentasikan terpisah.
- Diagram bersifat opsional: dapat memakai Mermaid atau representasi terstruktur (tabel/langkah).
- Proses yang sudah otomatis di sistem tetap memiliki SSOT teknis di GitHub Project Repository (GOV-002); vault memuat deskripsi bisnisnya.

## 2. Usage Instructions

1. Baca master ini berstatus `approved` (untuk penggunaan resmi).
2. Ekstrak Generated Metadata blueprint dan Required Sections.
3. Isi dari fakta aktual — jangan membawa frontmatter master, approval master, Usage Instructions, atau Validation Checklist internal.
4. Isi `source_template_id` dan `source_template_version` dengan master yang benar-benar digunakan.
5. Validasi instance, lalu simpan pada Target SSOT.

**Jangan** mengubah master ini saat menghasilkan instance.

## 3. Target SSOT

`02-Projects/{Project-Name}/Business-Process.md` (folder proyek di vault).

## 4. Generated Metadata

Blueprint — bukan metadata dokumen siap publikasi.

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
project_status: null
```

- `status` dokumen berbeda dari `project_status`.

## 5. Required Sections

- **Process Overview** — deskripsi proses, ruang lingkupnya, dan terkaitannya dengan proyek.
- **Process Objectives** — hasil yang ingin dicapai proses.
- **Actors and Responsibilities** — aktor yang terlibat beserta tanggung jawabnya.
- **Triggers** — peristiwa atau kondisi yang memulai proses.
- **Inputs and Outputs** — data dan dokumen masuk serta keluaran proses.
- **As-Is Process** — kondisi saat ini bila relevan.
- **To-Be Process** — kondisi target beserta gap terhadap kondisi saat ini.
- **Business Rules** — aturan yang berlaku di sepanjang proses.
- **Exception Handling** — skenario pengecualian dan penanganannya.
- **Process Validation** — cara proses diverifikasi, diukur, dan ditinjau ulang.

## 6. Optional Sections

- **Process Diagram** — diagram Mermaid atau representasi terstruktur.
- **Process Metrics** — indikator kinerja proses dan targetnya.
- **Known Issues** — isu proses yang diketahui.
- **Related Documents** — requirements, scope, dan dokumen terkait.
- **Change Log** — perubahan proses beserta dasar pertanggungjawabannya.

## 7. Validation Checklist

Manual sebelum publikasi instance:

- [ ] Seluruh required section terisi; As-Is diisi bila relevan.
- [ ] Alur dapat ditelusuri dari trigger sampai output.
- [ ] Aktor dan tanggung jawabnya konsisten dengan kebutuhan bisnis.
- [ ] Aturan dan exception handling tidak bertentangan.
- [ ] Diagram (bila ada) sesuai dengan deskripsi tertulis.
- [ ] `document_id` instance mengikuti GOV-008, bukan namespace `TPL`.
- [ ] `source_template_id` dan `source_template_version` sesuai master yang digunakan.
- [ ] Tanggal mengikuti system clock aktual (Asia/Jakarta).
- [ ] Tidak ada kredensial atau raw secret.

## 8. Governance References

- [[03-Hermes/Governance/Project-Registration-Standard|Project Registration Standard]] (GOV-007)
- [[03-Hermes/Governance/Information-Architecture|Information Architecture]] (GOV-002)
- [[03-Hermes/Governance/Knowledge-Management-Policy|Knowledge Management Policy]] (GOV-003)
- [[03-Hermes/Governance/Naming-Conventions|Naming Conventions]] (GOV-008)
- [[03-Hermes/Governance/Document-Lifecycle|Document Lifecycle]] (GOV-004)
- [[05-Templates/Template-Standard|Template Standard]]
