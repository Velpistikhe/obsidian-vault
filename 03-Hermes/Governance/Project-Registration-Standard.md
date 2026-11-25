---
title: Project Registration Standard
document_id: GOV-007
category: governance
version: 0.1.0
status: draft
owner: owner
author: hermes-default
reviewer: null
approved_by: null
approved_at: null
created_at: 2026-11-24
updated_at: 2026-11-25
tags: ['ai-office', 'governance', 'draft', 'projects']
---

# Project Registration Standard

## Ringkasan

Standar minimal untuk mendaftarkan proyek di AI Office vault sebelum dokumentasi substantif menyebar.

## Kapan registrasi diperlukan

- Proyek baru yang memiliki dokumentasi di `02-Projects/`, kanban aktif, atau repository GitHub terpisah.
- Proyek existing (contoh: Akura) tidak diubah oleh standar ini tanpa tugas terpisah yang diotorisasi.

## Lokasi vault

```
02-Projects/<Nama-Proyek>/
```

Gunakan [[Naming-Conventions]] untuk `<Nama-Proyek>`.

## Informasi minimum (proposed)

| Field | Keterangan |
|-------|------------|
| Nama proyek | Sesuai folder |
| Ringkasan tujuan | 1–3 paragraf |
| Owner proyek | Default: Owner organisasi kecuali didelegasikan (**delegasi formal: TBD**) |
| Repository GitHub | URL atau org/repo — SSOT kode |
| Status | active / paused / archived |
| Tanggal registrasi | ISO date |

Template detail dapat ditambahkan di [[05-Templates/Project-Management]] tanpa mengubah standar ini.

## Setelah registrasi

- Charter dan keputusan bisnis di vault; detail teknis di GitHub ([[Information-Architecture]]).
- Perubahan scope material: persetujuan Owner ([[Approval-Policy]]).

## Dokumen terkait

- [[Information-Architecture]]
- [[Naming-Conventions]]
- [[AI-Office-Charter]]
