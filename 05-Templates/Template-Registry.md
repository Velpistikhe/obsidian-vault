---
title: Template Registry
category: templates
version: 1.0.0
status: approved
owner: owner
author: hermes-default
reviewer: owner
approved_by: owner
approved_at: 2026-11-25T16:22:31+07:00
created_at: 2026-11-25
updated_at: 2026-11-26
tags: ['ai-office', 'templates', 'registry']
---

# Template Registry

> **Identitas artefak:** berkas ini adalah registry artifact, bukan master template; identitas otoritatif = path `05-Templates/Template-Registry.md`. **Tidak** memiliki `template_id` maupun `document_id`. Lihat [[05-Templates/README|Documentation Templates]].

## Tujuan

Single source of truth untuk **alokasi identifier namespace `TPL`** pada master template: mencatat status alokasi, waktu, dan referensi otorisasi yang benar-benar terjadi.

Katalog rancangan 29 template berada di [[05-Templates/README|Documentation Templates]]. **Katalog ≠ registry**: README menyimpan rencana; registry hanya riwayat alokasi yang benar-benar terjadi.

Registry ini **hanya** mengelola namespace `TPL`. Project (`PRJ`), Agent (`AGT`), Delegation (`DEL`), Approval (`APR`), Revision Proposal (`REV`), dan identifier lain mengikuti [[03-Hermes/Governance/Naming-Conventions|Naming Conventions]] serta registry atau allocation record yang relevan — **belum tersedia** untuk semua namespace. Jangan menggunakan registry ini sebagai registry seluruh organizational identifiers.

## Ruang lingkup

- Alokasi `TPL-NNN` untuk master template di `05-Templates/`.
- Riwayat identifier: reserved, allocated, retired (GOV-008).

Registry **tidak**:

- Memberikan approval authority atau permission apa pun.
- Mendaftarkan proyek, agent, delegasi, atau approval.
- Menyimpan metadata dokumen instance hasil pengisian template.
- Menggantikan document lifecycle master (status dan version master bersumber dari master template itu sendiri, GOV-004).

## Field registry

| Field | Keterangan |
|-------|------------|
| `template_id` | Identifier master template (`TPL-NNN`, GOV-008). |
| `title` | Judul master template. |
| `category` | `project-management`, `agent-management`, `software-development`, `knowledge-management` — selaras dengan nilai `category` pada frontmatter master (GOV-008). Folder vault tetap `Project-Management/`, dll. |
| `path` | Path relatif master di vault. |
| `allocation_status` | Identifier lifecycle: `reserved`, `allocated`, `retired` (lihat bawah). |
| `reserved_at` | Timestamp kejadian `reserved` — ISO 8601 dengan timezone (Asia/Jakarta); `null` bila belum terjadi. |
| `allocated_at` | Timestamp kejadian `allocated` — ISO 8601 dengan timezone; `null` bila belum terjadi. |
| `retired_at` | Timestamp kejadian `retired` — ISO 8601 dengan timezone; `null` bila belum terjadi. |
| `authorization_reference` | Referensi otorisasi reservation/allocation; wajib untuk setiap reservation atau allocation aktual; `null` bila belum ada. |

Field waktu mengikuti [[03-Hermes/Governance/Naming-Conventions|Naming Conventions]]: kejadian alokasi memakai ISO 8601 + timezone dari system clock aktual; `created_at`/`updated_at` dokumen foundation memakai `YYYY-MM-DD`. Field kejadian yang belum terjadi tetap `null`.

## Identifier lifecycle

Terpisah dari document lifecycle, project lifecycle, dan agent lifecycle (GOV-008):

| Status | Makna |
|--------|--------|
| `reserved` | ID dicadangkan; pembuatan master belum selesai. |
| `allocated` | ID diberikan kepada master template sah dan tercatat. |
| `retired` | ID tidak aktif; **tidak boleh** digunakan kembali. |

- Reservation yang dibatalkan **tetap dipertahankan** sebagai riwayat `retired`.
- Riwayat identifier tidak dihapus atau ditimpa sehingga jejak kewenangan hilang.

## Aturan alokasi

1. **Manual dan serial** oleh pihak berwenang (Owner atau delegate yang ditetapkan); tidak ada automatic allocation yang dianggap operasional.
2. **Sinkronisasi sebelum alokasi** — jalankan knowledge-sync (pull) agar registry berbasis keadaan terkini.
3. **Periksa namespace, registry, dan riwayat identitas** sebelum memilih nomor berikutnya: status `reserved`, `allocated`, dan `retired`.
4. ID **unik**, **immutable**, dan **non-reusable** dalam namespace (GOV-008).
5. ID **tidak dianggap selesai dialokasikan** sampai master **dan** registry berhasil dipublikasikan serta diverifikasi (local HEAD = remote HEAD).
6. Jika terjadi **duplicate ID**, **konflik Git**, atau **ketidakpastian registry**: hentikan proses alokasi/registrasi dan laporkan.
7. Jika terjadi **push failure**: pertahankan local changes atau commit yang belum terpublikasi; **jangan discard** perubahan, **jangan force push**. Selesaikan konflik sebelum melanjutkan.
8. Dokumen foundation ini **tidak** menerima ID `TPL`.

### Bootstrap authorization

- `authorization_reference` **wajib** untuk setiap reservation atau allocation aktual.
- Pada fase bootstrap, `authorization_reference` dapat merujuk **bukti persetujuan eksplisit Owner yang dapat ditelusuri**, walaupun Approval Registry atau `APR-NNNNNN` belum tersedia.
- Gunakan referensi bukti yang **benar-benar tersedia** dan dapat diperiksa kembali.
- **Jangan** membuat Approval ID, conversation ID, evidence reference, atau timestamp fiktif.
- Jika bukti otorisasi tidak tersedia atau tidak dapat ditelusuri, **hentikan** alokasi.
- Ketentuan ini **tidak** memberikan otorisasi alokasi ID dalam tugas finalisasi foundation; tugas alokasi memerlukan otorisasi terpisah.

## Riwayat alokasi

Entri hanya ditambahkan setelah alokasi aktual melalui workflow di atas dan mendapat otorisasi terpisah. Tabel tunggal berikut menjadi riwayat lengkap namespace `TPL`.

### Project Management (Phase 1)

Reservation dilakukan manual dan serial oleh pihak berwenang pada 2026-11-25, setelah sinkronisasi dan pemeriksaan namespace `TPL` (riwayat kosong pada saat itu).

`authorization_reference` merujuk bukti otorisasi Owner yang dapat ditelusuri: **Approval Owner atas "AI Office — Documentation Templates Phase 1"**, dan baseline review `edf37a9dcb29bdd464c92e1a11d5e442a8bb11d1` (approved Template Foundation v1.0.0). Approval Registry dan `APR-NNNNNN` belum tersedia pada fase bootstrap, sehingga tidak ada approval ID yang dibuat.

Status `allocated` ditetapkan setelah sembilan master template lolos validasi dan berhasil dipublikasikan bersama registry ini; `reserved_at` (reservation) dan `authorization_reference` dipertahankan.

Pada 2026-11-25, `authorization_reference` ke-9 entri diperkaya dengan rujukan konfirmasi retrospektif tanpa menghapus original reference (transaksi audit record yang diotorisasi; aturan alokasi tidak berubah).

| template_id | title | category | path | allocation_status | reserved_at | allocated_at | retired_at | authorization_reference |
|-------------|-------|----------|------|-------------------|-------------|--------------|------------|-------------------------|
| TPL-001 | Project Profile | project-management | 05-Templates/Project-Management/Project-Profile.md | allocated | 2026-11-25T16:27:54+07:00 | 2026-11-25T16:34:01+07:00 | null | [original @ allocation] Owner approval "AI Office — Documentation Templates Phase 1"; baseline edf37a9dcb29bdd464c92e1a11d5e442a8bb11d1; [retrospective confirmation @ 2026-11-25T17:51:52+07:00] 03-Hermes/Governance/Authorization-Evidence/Template-Phase-1-Authorization-Confirmation.md (recorded_at 2026-11-25T17:51:52+07:00; historical evidence limitation tetap berlaku) |
| TPL-002 | Project Charter | project-management | 05-Templates/Project-Management/Project-Charter.md | allocated | 2026-11-25T16:27:54+07:00 | 2026-11-25T16:34:01+07:00 | null | [original @ allocation] Owner approval "AI Office — Documentation Templates Phase 1"; baseline edf37a9dcb29bdd464c92e1a11d5e442a8bb11d1; [retrospective confirmation @ 2026-11-25T17:51:52+07:00] 03-Hermes/Governance/Authorization-Evidence/Template-Phase-1-Authorization-Confirmation.md (recorded_at 2026-11-25T17:51:52+07:00; historical evidence limitation tetap berlaku) |
| TPL-003 | Project Scope | project-management | 05-Templates/Project-Management/Project-Scope.md | allocated | 2026-11-25T16:27:54+07:00 | 2026-11-25T16:34:01+07:00 | null | [original @ allocation] Owner approval "AI Office — Documentation Templates Phase 1"; baseline edf37a9dcb29bdd464c92e1a11d5e442a8bb11d1; [retrospective confirmation @ 2026-11-25T17:51:52+07:00] 03-Hermes/Governance/Authorization-Evidence/Template-Phase-1-Authorization-Confirmation.md (recorded_at 2026-11-25T17:51:52+07:00; historical evidence limitation tetap berlaku) |
| TPL-004 | Project Plan | project-management | 05-Templates/Project-Management/Project-Plan.md | allocated | 2026-11-25T16:27:54+07:00 | 2026-11-25T16:34:01+07:00 | null | [original @ allocation] Owner approval "AI Office — Documentation Templates Phase 1"; baseline edf37a9dcb29bdd464c92e1a11d5e442a8bb11d1; [retrospective confirmation @ 2026-11-25T17:51:52+07:00] 03-Hermes/Governance/Authorization-Evidence/Template-Phase-1-Authorization-Confirmation.md (recorded_at 2026-11-25T17:51:52+07:00; historical evidence limitation tetap berlaku) |
| TPL-005 | Business Requirements | project-management | 05-Templates/Project-Management/Business-Requirements.md | allocated | 2026-11-25T16:27:54+07:00 | 2026-11-25T16:34:01+07:00 | null | [original @ allocation] Owner approval "AI Office — Documentation Templates Phase 1"; baseline edf37a9dcb29bdd464c92e1a11d5e442a8bb11d1; [retrospective confirmation @ 2026-11-25T17:51:52+07:00] 03-Hermes/Governance/Authorization-Evidence/Template-Phase-1-Authorization-Confirmation.md (recorded_at 2026-11-25T17:51:52+07:00; historical evidence limitation tetap berlaku) |
| TPL-006 | Project Status Report | project-management | 05-Templates/Project-Management/Project-Status-Report.md | allocated | 2026-11-25T16:27:54+07:00 | 2026-11-25T16:34:01+07:00 | null | [original @ allocation] Owner approval "AI Office — Documentation Templates Phase 1"; baseline edf37a9dcb29bdd464c92e1a11d5e442a8bb11d1; [retrospective confirmation @ 2026-11-25T17:51:52+07:00] 03-Hermes/Governance/Authorization-Evidence/Template-Phase-1-Authorization-Confirmation.md (recorded_at 2026-11-25T17:51:52+07:00; historical evidence limitation tetap berlaku) |
| TPL-007 | Project Closure Report | project-management | 05-Templates/Project-Management/Project-Closure-Report.md | allocated | 2026-11-25T16:27:54+07:00 | 2026-11-25T16:34:01+07:00 | null | [original @ allocation] Owner approval "AI Office — Documentation Templates Phase 1"; baseline edf37a9dcb29bdd464c92e1a11d5e442a8bb11d1; [retrospective confirmation @ 2026-11-25T17:51:52+07:00] 03-Hermes/Governance/Authorization-Evidence/Template-Phase-1-Authorization-Confirmation.md (recorded_at 2026-11-25T17:51:52+07:00; historical evidence limitation tetap berlaku) |
| TPL-008 | Business Process | project-management | 05-Templates/Project-Management/Business-Process.md | allocated | 2026-11-25T16:27:54+07:00 | 2026-11-25T16:34:01+07:00 | null | [original @ allocation] Owner approval "AI Office — Documentation Templates Phase 1"; baseline edf37a9dcb29bdd464c92e1a11d5e442a8bb11d1; [retrospective confirmation @ 2026-11-25T17:51:52+07:00] 03-Hermes/Governance/Authorization-Evidence/Template-Phase-1-Authorization-Confirmation.md (recorded_at 2026-11-25T17:51:52+07:00; historical evidence limitation tetap berlaku) |
| TPL-009 | UAT Criteria | project-management | 05-Templates/Project-Management/UAT-Criteria.md | allocated | 2026-11-25T16:27:54+07:00 | 2026-11-25T16:34:01+07:00 | null | [original @ allocation] Owner approval "AI Office — Documentation Templates Phase 1"; baseline edf37a9dcb29bdd464c92e1a11d5e442a8bb11d1; [retrospective confirmation @ 2026-11-25T17:51:52+07:00] 03-Hermes/Governance/Authorization-Evidence/Template-Phase-1-Authorization-Confirmation.md (recorded_at 2026-11-25T17:51:52+07:00; historical evidence limitation tetap berlaku) |

### Knowledge Management (Phase 2)

Reservation dilakukan manual dan serial oleh pihak berwenang pada 2026-11-25, setelah sinkronisasi dan pemeriksaan namespace `TPL` (terisi `TPL-001`–`TPL-009` pada saat itu; `TPL-010` tidak ditemukan di repository, registry, maupun riwayat Git).

`authorization_reference` merujuk bukti otorisasi Owner Phase 2 yang telah dipublikasikan: `03-Hermes/Governance/Authorization-Evidence/Template-Phase-2-Authorization.md` (recorded_at 2026-11-25T21:40:15+07:00; baseline `9510257493e78f0e107449e6d069f4b2e5f2358a`). Approval Registry dan `APR-NNNNNN` belum tersedia pada fase bootstrap, sehingga tidak ada approval ID yang dibuat.

| template_id | title | category | path | allocation_status | reserved_at | allocated_at | retired_at | authorization_reference |
|-------------|-------|----------|------|-------------------|-------------|--------------|------------|-------------------------|
| TPL-010 | Revision Proposal | knowledge-management | 05-Templates/Knowledge-Management/Revision-Proposal.md | allocated | 2026-11-25T21:41:07+07:00 | 2026-11-25T21:43:29+07:00 | null | 03-Hermes/Governance/Authorization-Evidence/Template-Phase-2-Authorization.md (recorded_at 2026-11-25T21:40:15+07:00; baseline 9510257493e78f0e107449e6d069f4b2e5f2358a) |

### Agent Management (Phase 3)

Reservation dilakukan manual dan serial oleh pihak berwenang pada 2026-11-26, setelah sinkronisasi dan pemeriksaan namespace `TPL` (terisi `TPL-001`–`TPL-010` pada saat itu; `TPL-011`–`TPL-017` tidak ditemukan di repository, registry, maupun riwayat Git).

`authorization_reference` merujuk bukti otorisasi Owner Phase 3 yang telah dipublikasikan: `03-Hermes/Governance/Authorization-Evidence/Template-Phase-3-Authorization.md` (recorded_at 2026-11-26T12:15:05+07:00; baseline `8be443fd4a9f0390a458514f4f0e6b5f53ebbd3f`). Approval Registry dan `APR-NNNNNN` belum tersedia pada fase bootstrap, sehingga tidak ada approval ID yang dibuat.

| template_id | title | category | path | allocation_status | reserved_at | allocated_at | retired_at | authorization_reference |
|-------------|-------|----------|------|-------------------|-------------|--------------|------------|-------------------------|
| TPL-011 | Agent Profile | agent-management | 05-Templates/Agent-Management/Agent-Profile.md | reserved | 2026-11-26T12:15:33+07:00 | null | null | 03-Hermes/Governance/Authorization-Evidence/Template-Phase-3-Authorization.md (recorded_at 2026-11-26T12:15:05+07:00; baseline 8be443fd4a9f0390a458514f4f0e6b5f53ebbd3f) |
| TPL-012 | Agent Assignment | agent-management | 05-Templates/Agent-Management/Agent-Assignment.md | reserved | 2026-11-26T12:15:33+07:00 | null | null | 03-Hermes/Governance/Authorization-Evidence/Template-Phase-3-Authorization.md (recorded_at 2026-11-26T12:15:05+07:00; baseline 8be443fd4a9f0390a458514f4f0e6b5f53ebbd3f) |
| TPL-013 | Delegation Record | agent-management | 05-Templates/Agent-Management/Delegation-Record.md | reserved | 2026-11-26T12:15:33+07:00 | null | null | 03-Hermes/Governance/Authorization-Evidence/Template-Phase-3-Authorization.md (recorded_at 2026-11-26T12:15:05+07:00; baseline 8be443fd4a9f0390a458514f4f0e6b5f53ebbd3f) |
| TPL-014 | Approval Record | agent-management | 05-Templates/Agent-Management/Approval-Record.md | reserved | 2026-11-26T12:15:33+07:00 | null | null | 03-Hermes/Governance/Authorization-Evidence/Template-Phase-3-Authorization.md (recorded_at 2026-11-26T12:15:05+07:00; baseline 8be443fd4a9f0390a458514f4f0e6b5f53ebbd3f) |
| TPL-015 | Agent Execution Report | agent-management | 05-Templates/Agent-Management/Agent-Execution-Report.md | reserved | 2026-11-26T12:15:33+07:00 | null | null | 03-Hermes/Governance/Authorization-Evidence/Template-Phase-3-Authorization.md (recorded_at 2026-11-26T12:15:05+07:00; baseline 8be443fd4a9f0390a458514f4f0e6b5f53ebbd3f) |
| TPL-016 | Agent Change Request | agent-management | 05-Templates/Agent-Management/Agent-Change-Request.md | reserved | 2026-11-26T12:15:33+07:00 | null | null | 03-Hermes/Governance/Authorization-Evidence/Template-Phase-3-Authorization.md (recorded_at 2026-11-26T12:15:05+07:00; baseline 8be443fd4a9f0390a458514f4f0e6b5f53ebbd3f) |
| TPL-017 | Agent Onboarding Checklist | agent-management | 05-Templates/Agent-Management/Agent-Onboarding-Checklist.md | reserved | 2026-11-26T12:15:33+07:00 | null | null | 03-Hermes/Governance/Authorization-Evidence/Template-Phase-3-Authorization.md (recorded_at 2026-11-26T12:15:05+07:00; baseline 8be443fd4a9f0390a458514f4f0e6b5f53ebbd3f) |

### Namespace lain

Namespace `PRJ`, `AGT`, `DEL`, `APR`, `REV`, dan lainnya **belum** punya entri di registry ini; registry ini hanya mengelola namespace `TPL`.

## Status implementasi

| Komponen | Status |
|----------|--------|
| Registry initialization (tanpa entri ID) | **Operational** untuk struktur field dan aturan; belum ada entri alokasi. |
| Alokasi `TPL-*` aktual | 10 master (`TPL-001`–`TPL-010`) berstatus **allocated** — 9 Project Management (Phase 1) dan 1 Knowledge Management (Phase 2). |
| Automatic allocation | **Planned** — belum terverifikasi (GOV-002, GOV-008). |
| Collision prevention otomatis | **Planned** — belum terverifikasi (GOV-008). |
| Full-cycle locking / concurrency control | **Planned** — belum diimplementasikan (GOV-002). |

## Dokumen terkait

- [[05-Templates/README|Documentation Templates]] — katalog rancangan 29 template
- [[05-Templates/Template-Standard|Template Standard]] — standar metadata, struktur, dan penggunaan master
- [[03-Hermes/Governance/Naming-Conventions|Naming Conventions]] (GOV-008)
- [[03-Hermes/Governance/Document-Lifecycle|Document Lifecycle]] (GOV-004)
- [[03-Hermes/Governance/Knowledge-Management-Policy|Knowledge Management Policy]] (GOV-003)
