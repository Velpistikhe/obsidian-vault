---
title: Documentation Templates
category: templates
version: 0.1.0
status: draft
owner: owner
author: hermes-default
reviewer: null
approved_by: null
approved_at: null
created_at: 2026-11-25
updated_at: 2026-11-25
tags: ['ai-office', 'templates']
---

# Documentation Templates

> **Catatan frontmatter:** tiga dokumen foundation di folder ini (`README.md`, `Template-Registry.md`, `Template-Standard.md`) **tidak** memiliki `document_id` maupun `template_id`. Menurut [[Naming-Conventions]], `document_id` wajib untuk dokumen terkelola yang **menggunakan organizational identifier**; dokumen foundation tidak memakai namespace tersebut dan tidak boleh menerima ID `TPL` (khusus master template). Namespace identitas untuk dokumen foundation belum ditetapkan — jangan membuat namespace baru tanpa keputusan Owner.

## Fungsi folder

`05-Templates/` menyimpan **master template** serta artefak pendukung navigasi dan registry. Isi instance dokumen hasil pengisian template **tidak** berada di folder ini; lokasi instance mengikuti Target SSOT pada [[Template-Standard]] dan [[Information-Architecture]].

Artefak foundation:

| Berkas | Fungsi |
|--------|--------|
| `05-Templates/README.md` | Navigasi, katalog rancangan 29 template, aturan penggunaan. |
| `05-Templates/Template-Registry.md` | SSOT alokasi identifier namespace `TPL`. |
| `05-Templates/Template-Standard.md` | Standar turunan: metadata, struktur, lifecycle, penggunaan master. |

Keempat README subfolder (`Project-Management`, `Agent-Management`, `Software-Development`, `Knowledge-Management`) tetap menjadi pembaca per kategori.

## Status

Seluruh **29 master template masih Planned dan belum dibuat**. Daftar di bawah adalah **katalog rancangan yang telah disetujui Owner**, bukan berkas yang tersedia. Jangan membuat wikilink seolah-olah file template sudah ada — gunakan nama atau path rencana seperti pada tabel.

Master template yang kelak dibuat akan dicatat alokasi ID-nya pada [[Template-Registry]]; katalog ini tidak mencatat alokasi.

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
| **Opsional** | Dikecualikan secara eksplisit oleh rancangan katalog. |

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

Master disimpan di vault sebagai **master template**; **instance engineering lengkap tetap berada di GitHub Project Repository** sebagai SSOT ([[Information-Architecture]]). Vault hanya menyimpan master, ringkasan, atau referensi.

| # | Template (rencana) | Kebutuhan | Catatan governance |
|---|--------------------|-----------|--------------------|
| 1 | `Software-Development/Technical-Architecture.md` | Kondisional | Detail engineering → GitHub Project Repository (GOV-002). |
| 2 | `Software-Development/Technical-ADR.md` | Kondisional | ADR detail → repo; review rutin mengikuti delegasi yang aktif (GOV-005). |
| 3 | `Software-Development/API-Specification.md` | Kondisional | Spesifikasi lengkap → repo (GOV-002). |
| 4 | `Software-Development/Test-Plan.md` | Kondisional | Strategi/bukti pengujian (GOV-007). |
| 5 | `Software-Development/Code-Review-Report.md` | Opsional | Dikecualikan secara eksplisit oleh rancangan katalog. |
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

1. Salin master ke lokasi instance; **jangan** mengedit master saat mengisi instance.
2. Gunakan master berstatus `approved` untuk penggunaan resmi; master `draft` hanya untuk review atau simulasi terotorisasi.
3. Pengisian template **tidak** memberikan approval, assignment, delegasi, atau permission apa pun.
4. Pengisian template **tidak** mengalokasikan ID; ID hanya dialokasikan melalui workflow terotorisasi pada [[Template-Registry]] (GOV-008).
5. Approval pada master **tidak** diwariskan ke instance yang dihasilkan.
6. Jangan menyimpan kredensial atau raw secret.
7. Validation checklist dilakukan **manual** sampai automated validation terverifikasi.
8. Detail metadata, struktur universal, dan pemisahan lifecycle: [[Template-Standard]].

## Governance references

- [[AI-Office-Charter]] (GOV-001)
- [[Information-Architecture]] (GOV-002) — SSOT instance dan repository
- [[Knowledge-Management-Policy]] (GOV-003)
- [[Document-Lifecycle]] (GOV-004) — status dokumen, revisi, approval
- [[Approval-Policy]] (GOV-005) — kewenangan approval dan delegasi
- [[Agent-Access-Policy]] (GOV-006) — akses dan larangan agent
- [[Project-Registration-Standard]] (GOV-007) — field registrasi dan aktivasi proyek
- [[Naming-Conventions]] (GOV-008) — identifier, metadata, penamaan, date & time

## Status implementasi

| Kemampuan | Status |
|-----------|--------|
| Dokumen foundation (README, Registry, Standard) | Dibuat pada Phase 0 — draft. |
| 29 master template | **Planned** — belum dibuat. |
| Alokasi ID `TPL-*` | **Belum ada** — lihat [[Template-Registry]]. |
| Automatic allocation / collision prevention | **Planned** atau belum terverifikasi (GOV-002, GOV-008). |
| Metadata schema validation otomatis | **Planned** (GOV-002). |
