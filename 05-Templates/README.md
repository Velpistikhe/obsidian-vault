---
title: Documentation Templates
category: templates
version: 1.0.0
status: approved
owner: owner
author: hermes-default
reviewer: owner
approved_by: owner
approved_at: 2026-11-25T16:22:31+07:00
created_at: 2026-11-25
updated_at: 2026-11-25
tags: ['ai-office', 'templates']
---

# Documentation Templates

> **Identitas artefak:** ketiga dokumen foundation (`05-Templates/README.md`, `05-Templates/Template-Registry.md`, `05-Templates/Template-Standard.md`) menggunakan **path vault** sebagai identitas otoritatif. Mereka **tidak** memiliki `document_id` maupun `template_id`. Menurut [[03-Hermes/Governance/Naming-Conventions|Naming Conventions]], `document_id` wajib untuk dokumen terkelola yang menggunakan organizational identifier; namespace `TPL` khusus master template. Persetujuan foundation ini **bukan** persetujuan terhadap master template yang belum dibuat.

## Fungsi folder

`05-Templates/` menyimpan **master template** serta artefak pendukung navigasi dan registry. Isi instance dokumen hasil generate dari template **tidak** berada di folder ini; lokasi instance mengikuti Target SSOT pada [[05-Templates/Template-Standard|Template Standard]] dan [[03-Hermes/Governance/Information-Architecture|Information Architecture]].

Artefak foundation:

| Berkas | Fungsi |
|--------|--------|
| `05-Templates/README.md` | Navigasi, katalog rancangan 29 template, aturan penggunaan. |
| `05-Templates/Template-Registry.md` | SSOT alokasi identifier namespace `TPL`. |
| `05-Templates/Template-Standard.md` | Standar turunan: metadata, struktur, lifecycle, penggunaan master. |

Keempat README subfolder (`Project-Management`, `Agent-Management`, `Software-Development`, `Knowledge-Management`) tetap menjadi pembaca per kategori.

## Status

Seluruh **29 master template masih Planned dan belum dibuat**. Daftar di bawah adalah **katalog rancangan yang telah disetujui Owner**, bukan berkas yang tersedia. Jangan membuat wikilink seolah-olah file template sudah ada — gunakan nama atau path rencana seperti pada tabel.

Master template yang kelak dibuat akan dicatat alokasi ID-nya pada [[05-Templates/Template-Registry|Template Registry]]; katalog ini tidak mencatat alokasi.

[[05-Templates/Template-Registry|Template Registry]] **hanya** mengelola namespace `TPL`. Identifier `PRJ`, `AGT`, `DEL`, `APR`, `REV`, dan namespace lain mengikuti [[03-Hermes/Governance/Naming-Conventions|Naming Conventions]] serta registry atau allocation record yang relevan — **belum tersedia** untuk semua namespace. Jangan menggunakan Template Registry sebagai registry seluruh organizational identifiers.

## Navigation

| Kategori | Jumlah | Rencana lokasi master |
|----------|--------|-----------------------|
| Project Management | 9 | `05-Templates/Project-Management/` |
| Agent Management | 7 | `05-Templates/Agent-Management/` |
| Software Development | 6 | `05-Templates/Software-Development/` |
| Knowledge Management | 7 | `05-Templates/Knowledge-Management/` |
| **Total** | **29** | |

## Kategori kebutuhan

| Kategori | Makna |
|----------|--------|
| **Wajib** | Dipersyaratkan governance untuk jenis dokumen atau proyek tertentu. |
| **Kondisional** | Wajib hanya bila kondisi penggunaannya terpenuhi. |
| **Pendukung** | Membantu operasi; tidak dipersyaratkan governance. |
| **Opsional** | Tersedia dalam katalog dan dapat digunakan sesuai kebutuhan pekerjaan; **bukan** persyaratan wajib governance. |

## Katalog — Project Management (9)

| # | Template (rencana) | Kebutuhan | Catatan governance |
|---|--------------------|-----------|--------------------|
| 1 | `Project-Management/Project-Profile.md` | Wajib | Registrasi otoritatif proyek; prasyarat aktivasi (GOV-007). |
| 2 | `Project-Management/Project-Charter.md` | Wajib | Organizational Owner approval (GOV-007). |
| 3 | `Project-Management/Project-Scope.md` | Wajib | Setiap perubahan approved scope → Organizational Owner (GOV-005). |
| 4 | `Project-Management/Project-Plan.md` | Wajib | Review operasional; tidak mengubah scope/komitmen resmi (GOV-007). |
| 5 | `Project-Management/Business-Requirements.md` | Kondisional | Jika relevan dengan jenis proyek (GOV-007). |
| 6 | `Project-Management/Project-Status-Report.md` | Pendukung | Snapshot bertanggal; live task status tetap Kanban — integrasi Pending Verification (GOV-002). |
| 7 | `Project-Management/Project-Closure-Report.md` | Pendukung | Dokumentasi penutupan; `archived` ≠ otomatis sukses (GOV-007). |
| 8 | `Project-Management/Business-Process.md` | Kondisional | Jika relevan dengan jenis proyek (GOV-007). |
| 9 | `Project-Management/UAT-Criteria.md` | Kondisional | Jika relevan; dasar acceptance (GOV-007). |

## Katalog — Agent Management (7)

| # | Template (rencana) | Kebutuhan | Catatan governance |
|---|--------------------|-----------|--------------------|
| 1 | `Agent-Management/Agent-Profile.md` | Kondisional | Wajib bila agent terdaftar; pola `AGT-NNN` (GOV-008). |
| 2 | `Agent-Management/Agent-Assignment.md` | Kondisional | Assignment ≠ delegasi atau permission otomatis (GOV-005). |
| 3 | `Agent-Management/Delegation-Record.md` | Kondisional | Pola `DEL-NNNNNN`; validity ISO 8601 (GOV-005, GOV-008). |
| 4 | `Agent-Management/Approval-Record.md` | Kondisional | Pola `APR-NNNNNN`; traceability approval (GOV-005). |
| 5 | `Agent-Management/Agent-Execution-Report.md` | Opsional | Ringkasan aman; bukan raw execution log (GOV-003, GOV-006). |
| 6 | `Agent-Management/Agent-Change-Request.md` | Kondisional | Wajib merujuk dampak pada knowledge base (README Agent-Management). |
| 7 | `Agent-Management/Agent-Onboarding-Checklist.md` | Pendukung | Checklist onboarding; bukan bukti aktivasi agent. |

## Katalog — Software Development (6)

Master disimpan di vault sebagai **master template**; **instance engineering lengkap tetap berada di GitHub Project Repository** sebagai SSOT ([[03-Hermes/Governance/Information-Architecture|Information Architecture]]). Vault hanya menyimpan master, ringkasan, atau referensi.

| # | Template (rencana) | Kebutuhan | Catatan governance |
|---|--------------------|-----------|--------------------|
| 1 | `Software-Development/Technical-Architecture.md` | Kondisional | Detail engineering → GitHub Project Repository (GOV-002). |
| 2 | `Software-Development/Technical-ADR.md` | Kondisional | ADR detail → repo; review rutin mengikuti delegasi yang aktif (GOV-005). |
| 3 | `Software-Development/API-Specification.md` | Kondisional | Spesifikasi lengkap → repo (GOV-002). |
| 4 | `Software-Development/Test-Plan.md` | Kondisional | Strategi/bukti pengujian (GOV-007). |
| 5 | `Software-Development/Code-Review-Report.md` | Opsional | Dapat digunakan bila dibutuhkan; tidak wajib governance. |
| 6 | `Software-Development/Deployment-Plan.md` | Kondisional | Production deployment → Owner approval (GOV-005). |

## Katalog — Knowledge Management (7)

| # | Template (rencana) | Kebutuhan | Catatan governance |
|---|--------------------|-----------|--------------------|
| 1 | `Knowledge-Management/Knowledge-Note.md` | Pendukung | Reusable knowledge; catat provenance (GOV-003). |
| 2 | `Knowledge-Management/Troubleshooting-Note.md` | Pendukung | Solusi teknis terverifikasi (GOV-003). |
| 3 | `Knowledge-Management/Research-Report.md` | Pendukung | Research knowledge dengan sumber (GOV-003). |
| 4 | `Knowledge-Management/Standard-Operating-Procedure.md` | Kondisional | Pola `SOP-NNN` (GOV-008). |
| 5 | `Knowledge-Management/Workflow-Definition.md` | Kondisional | Pola `WF-NNN` (GOV-008). |
| 6 | `Knowledge-Management/Revision-Proposal.md` | Kondisional | Wajib pada setiap revisi dokumen approved; `proposal_id` `REV-NNNNNN` (GOV-004, GOV-008). |
| 7 | `Knowledge-Management/Organizational-Decision-Record.md` | Pendukung | Decision record organisasi (README Knowledge-Management). |

## Usage instructions

### Generate from template (bukan salin seluruh master)

1. Baca master template berstatus `approved`.
2. Ekstrak **generated metadata blueprint** dari body master.
3. Ekstrak **Required Sections** dan **Optional Sections** yang berlaku.
4. Isi metadata dan konten instance berdasarkan **fakta aktual** — jangan menyalin frontmatter master, approval master, Usage Instructions, atau Validation Checklist internal master.
5. Validasi instance sebelum publikasi (checklist manual).
6. Simpan instance pada **Target SSOT** yang ditetapkan master.

**Jangan** mengubah master ketika menghasilkan instance.

### Aturan umum

1. Gunakan master `approved` untuk penggunaan resmi; master `draft` hanya untuk review atau simulasi terotorisasi.
2. Generate dari template **tidak** memberikan approval, assignment, delegasi, atau permission.
3. Generate **tidak** mengalokasikan ID; ID hanya melalui workflow terotorisasi ([[05-Templates/Template-Registry|Template Registry]] untuk `TPL`; namespace lain sesuai GOV-008).
4. Approval master **tidak** diwariskan ke instance.
5. Jangan menyimpan kredensial atau raw secret.
6. Validation checklist **manual** sampai automated validation terverifikasi.
7. Detail struktur, metadata, lifecycle: [[05-Templates/Template-Standard|Template Standard]].

## Governance references

- [[03-Hermes/Governance/AI-Office-Charter|AI Office Charter]] (GOV-001)
- [[03-Hermes/Governance/Information-Architecture|Information Architecture]] (GOV-002)
- [[03-Hermes/Governance/Knowledge-Management-Policy|Knowledge Management Policy]] (GOV-003)
- [[03-Hermes/Governance/Document-Lifecycle|Document Lifecycle]] (GOV-004)
- [[03-Hermes/Governance/Approval-Policy|Approval Policy]] (GOV-005)
- [[03-Hermes/Governance/Agent-Access-Policy|Agent Access Policy]] (GOV-006)
- [[03-Hermes/Governance/Project-Registration-Standard|Project Registration Standard]] (GOV-007)
- [[03-Hermes/Governance/Naming-Conventions|Naming Conventions]] (GOV-008)

## Status implementasi

| Kemampuan | Status |
|-----------|--------|
| Dokumen foundation (README, Registry, Standard) | **Approved** v1.0.0. |
| 29 master template | **Planned** — belum dibuat. |
| Alokasi ID `TPL-*` | **Belum ada** — lihat [[05-Templates/Template-Registry|Template Registry]]. |
| Automatic allocation / collision prevention | **Planned** atau belum terverifikasi (GOV-002, GOV-008). |
| Metadata schema validation otomatis | **Planned** (GOV-002). |
