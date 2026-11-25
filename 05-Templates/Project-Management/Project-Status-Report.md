---
title: Project Status Report
document_id: TPL-006
template_id: TPL-006
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
tags: ['ai-office', 'templates', 'projects', 'reporting']
---

# Project Status Report

## 1. Purpose

Laporan berkala (snapshot) kondisi sebuah proyek pada satu periode: kemajuan, risiko dan isu, blocker, keputusan yang dibutuhkan, dan rekomendasi.

Mengikuti [[03-Hermes/Governance/Knowledge-Management-Policy|Knowledge Management Policy]] (GOV-003).

- **Snapshot ini bukan live task SSOT.** Live task status menjadi target Hermes Kanban setelah integrasi tersedia dan diverifikasi; saat ini integrasi berstatus Pending Verification (GOV-002).
- **Jangan mengarang** progress, percentage, task status, atau milestone. Isi hanya dari fakta yang tersedia.
- Nama file boleh bertanggal bila tanggal merupakan bagian identitas artefak (GOV-008).

## 2. Usage Instructions

1. Baca master ini berstatus `approved` (untuk penggunaan resmi).
2. Ekstrak Generated Metadata blueprint dan Required Sections.
3. Isi dari fakta aktual — jangan membawa frontmatter master, approval master, Usage Instructions, atau Validation Checklist internal.
4. Isi `source_template_id` dan `source_template_version` dengan master yang benar-benar digunakan.
5. Validasi instance, lalu simpan pada Target SSOT dengan nama file bertanggal.

**Jangan** mengubah master ini saat menghasilkan instance.

## 3. Target SSOT

`02-Projects/{Project-Name}/Project-Status-Report-{YYYY-MM-DD}.md` (folder proyek di vault, sebagai dated report).

## 4. Generated Metadata

Blueprint — bukan metadata dokumen siap publikasi.

```yaml
title: null
document_id: null
document_type: project_status_report
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
# --- konteks laporan ---
reporting_period: null
snapshot_timestamp: null
```

- `status` dokumen berbeda dari `project_status`.
- `snapshot_timestamp` memakai ISO 8601 dengan timezone dari system clock aktual (GOV-008).

## 5. Required Sections

- **Reporting Period and Snapshot Timestamp** — periode laporan dan waktu pengambilan snapshot.
- **Executive Summary** — ringkasan kondisi proyek dalam beberapa kalimat.
- **Progress and Milestones** — kemajuan terhadap rencana dan status milestone yang terverifikasi.
- **Completed Activities** — aktivitas yang benar-benar selesai pada periode ini.
- **Upcoming Activities** — aktivitas yang direncanakan pada periode berikutnya.
- **Risks and Issues** — risiko dan isu beserta dampak dan aksi mitigasi.
- **Blockers** — hambatan yang memerlukan resolusi beserta pemilik aksinya.
- **Decisions Required** — keputusan yang dibutuhkan beserta pihak yang berwenang mengambilnya.
- **Recommendations** — rekomendasi tindakan lanjutan.
- **Source References** — sumber data laporan (rencana, dokumen terkait, sistem yang digunakan).

## 6. Optional Sections

- **Resource and Delegation Status** — status resource yang dirujuk beserta delegasi aktif yang relevan.
- **Changes Since Previous Report** — delta terhadap laporan sebelumnya.
- **Attached Artefact References** — rujukan ke dokumen atau artefak pendukung.

## 7. Validation Checklist

Manual sebelum publikasi instance:

- [ ] Periode laporan dan snapshot timestamp terisi.
- [ ] Tidak ada angka progress, percentage, atau status task yang tidak bersumber dari fakta.
- [ ] Milestone yang dilaporkan sesuai rencana yang berlaku.
- [ ] Blocker dan keputusan yang dibutuhkan menyebut pihak berwenang.
- [ ] Source References menunjukkan asal data.
- [ ] Tidak ada klaim bahwa integrasi Kanban sudah operational.
- [ ] `document_id` instance mengikuti GOV-008, bukan namespace `TPL`.
- [ ] `source_template_id` dan `source_template_version` sesuai master yang digunakan.
- [ ] Tanggal mengikuti system clock aktual (Asia/Jakarta).
- [ ] Tidak ada kredensial atau raw secret.

## 8. Governance References

- [[03-Hermes/Governance/Knowledge-Management-Policy|Knowledge Management Policy]] (GOV-003)
- [[03-Hermes/Governance/Project-Registration-Standard|Project Registration Standard]] (GOV-007)
- [[03-Hermes/Governance/Information-Architecture|Information Architecture]] (GOV-002)
- [[03-Hermes/Governance/Naming-Conventions|Naming Conventions]] (GOV-008)
- [[03-Hermes/Governance/Document-Lifecycle|Document Lifecycle]] (GOV-004)
- [[05-Templates/Template-Standard|Template Standard]]
