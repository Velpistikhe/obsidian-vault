---
title: Template Registry
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
tags: ['ai-office', 'templates', 'registry']
---

# Template Registry

> **Catatan frontmatter:** berkas ini adalah registry artifact, bukan master template, sehingga **tidak** menerima `template_id` maupun `document_id` (lihat [[README|05-Templates README]]). `document_id` hanya diwajibkan untuk dokumen terkelola yang menggunakan organizational identifier.

## Tujuan

Single source of truth untuk **alokasi identifier namespace `TPL`** pada master template: mencatat status alokasi, waktu, dan referensi otorisasi yang benar-benar terjadi.

Katalog rancangan 29 template berada di [[README|05-Templates README]]. **Katalog ≠ registry**: README menyimpan rencana, registry hanya menyimpan riwayat alokasi yang benar-benar terjadi.

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
| `category` | `Project-Management`, `Agent-Management`, `Software-Development`, `Knowledge-Management`. |
| `path` | Path relatif master di vault. |
| `allocation_status` | Identifier lifecycle: `reserved`, `allocated`, `retired` (lihat bawah). |
| `reserved_at` | Tanggal `reserved` dicatat (`YYYY-MM-DD`, Asia/Jakarta); `null` bila belum. |
| `allocated_at` | Tanggal `allocated` tercatat; `null` bila belum. |
| `retired_at` | Tanggal `retired` tercatat; `null` bila belum. |
| `authorization_reference` | Referensi otorisasi alokasi (`APR-NNNNNN` bila dialokasikan); `null` bila belum ada. |

Field waktu dan referensi mengikuti GOV-008: `null` untuk nilai tunggal yang belum tersedia, system clock aktual untuk tanggal yang terjadi.

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

## Riwayat alokasi

**Belum ada entri alokasi.** Tabel berikut sengaja dikosongkan — tidak ada ID yang reserved, allocated, atau retired pada Phase 0.

| template_id | title | category | path | allocation_status | reserved_at | allocated_at | retired_at | authorization_reference |
|-------------|-------|----------|------|-------------------|-------------|--------------|------------|-------------------------|

Entri akan ditambahkan hanya setelah alokasi aktual melalui workflow di atas dan mendapat otorisasi terpisah.

## Status implementasi

| Komponen | Status |
|----------|--------|
| Registry initialization (tanpa entri ID) | Dilakukan pada Phase 0. |
| Alokasi `TPL-*` aktual | **Belum ada.** |
| Automatic allocation | **Planned** — belum terverifikasi (GOV-002, GOV-008). |
| Collision prevention otomatis | **Planned** — belum terverifikasi (GOV-008). |
| Full-cycle locking / concurrency control | **Planned** — belum diimplementasikan (GOV-002). |

## Dokumen terkait

- [[README|05-Templates README]] — katalog rancangan 29 template
- [[Template-Standard]] — standar metadata, struktur, dan penggunaan master
- [[Naming-Conventions]] (GOV-008) — identifier lifecycle dan alokasi terpusat
- [[Document-Lifecycle]] (GOV-004) — status dan version master
- [[Knowledge-Management-Policy]] (GOV-003) — sinkronisasi dan publikasi
