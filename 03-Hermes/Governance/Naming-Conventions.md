---
title: Naming Conventions
document_id: GOV-008
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
tags: ['ai-office', 'governance', 'draft', 'naming']
---

# Naming Conventions

## Ringkasan

Konvensi penamaan file, ID dokumen, dan tag untuk konsistensi vault AI Office.

## File dan folder

- **Bahasa**: Deskriptif; istilah teknis Inggris diperbolehkan.
- **Format file governance/strategis**: `Pascal-Case-With-Hyphens.md` (contoh: `AI-Office-Charter.md`).
- **Folder proyek**: `02-Projects/<Pascal-Case-Name>/`.
- **Hindari**: spasi pada nama file, tanggal di nama file kecuali artefak sekali pakai di workspace.

## Document ID

| Pola | Penggunaan |
|------|------------|
| `GOV-NNN` | Governance (`GOV-001` …) |
| `TBD` | Kategori lain (ADR org, SOP ID) menunggu persetujuan Owner |

Setiap dokumen governance memuat `document_id` di YAML frontmatter.

## Metadata

Field standar: `title`, `document_id`, `category`, `version`, `status`, `owner`, `author`, `reviewer`, `approved_by`, `approved_at`, `created_at`, `updated_at`, `tags`.

- `owner`: default `owner` untuk fondasi AI Office.
- `author`: `hermes-default` bila dibuat oleh agent default.
- `status`: ikuti [[Document-Lifecycle]].

## Date & Time Conventions

Standar ini merupakan bagian dari dokumen draft dan belum dianggap sebagai kebijakan yang disetujui.

- Zona waktu organisasi: `Asia/Jakarta`.
- Zona waktu server: `UTC`.
- Format tanggal dokumen: `YYYY-MM-DD`.
- Format timestamp: ISO 8601 dengan informasi zona waktu.
- Log eksekusi teknis menggunakan UTC.
- Deadline proyek menggunakan `Asia/Jakarta`.
- Agent wajib menggunakan system clock ketika menghasilkan tanggal atau timestamp aktual; jangan menggunakan tanggal berdasarkan asumsi internal model.
- `created_at` adalah tanggal pembuatan awal dan tidak berubah, kecuali untuk koreksi metadata yang terbukti salah.
- `updated_at` adalah tanggal perubahan terakhir.
- `approved_at` hanya diisi setelah persetujuan aktual.

Contoh command untuk membaca tanggal dan timestamp aktual:

```bash
date -u +'%Y-%m-%dT%H:%M:%SZ'
TZ=Asia/Jakarta date +%F
TZ=Asia/Jakarta date --iso-8601=seconds
```

## Wikilink

- Prefer `[[Judul-Dokumen]]` atau path relatif vault bila judul ambigu.
- Tautkan ke SSOT, jangan duplikasi isi ([[Information-Architecture]]).

## Tag

- Lowercase, hyphenated: `ai-office`, `governance`, `draft`.
- Tambah tag domain: `architecture`, `agents`, `projects`, dll.

## Dokumen terkait

- [[Document-Lifecycle]]
- [[Knowledge-Management-Policy]]
