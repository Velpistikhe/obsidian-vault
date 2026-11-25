---
title: Document Lifecycle
document_id: GOV-004
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
tags: ['ai-office', 'governance', 'draft', 'lifecycle']
---

# Document Lifecycle

## Ringkasan

Siklus hidup dokumen kebijakan dan pengetahuan di vault.

## Status

```
Draft → In Review → Pending Approval → Approved → Archived
```

| Status | Makna |
|--------|--------|
| **Draft** | Konten awal atau revisi; boleh dipublish ke Git untuk kolaborasi review |
| **In Review** | Reviewer ditugaskan; komentar dan perbaikan |
| **Pending Approval** | Siap keputusan Owner (kebijakan strategis) atau delegasi yang disetujui Owner |
| **Approved** | Berlaku operasional sesuai versi pada metadata |
| **Archived** | Tidak aktif; disimpan untuk referensi historis di `99-Archive` bila dipindahkan |

## Aturan versi

- Gunakan semantic versioning pada field `version` di frontmatter (contoh awal: `0.1.0` untuk draft fondasi).
- Perubahan material setelah Approved memerlukan versi baru dan kembali ke alur review ([[Approval-Policy]]).
- Update `updated_at` pada setiap perubahan substantif.

## Metadata wajib

Lihat standar di dokumen governance (`title`, `document_id`, `status`, `owner`, `author`, dll.). ID governance: `GOV-001`–`GOV-008`.

## Pemisahan publish vs approval

Commit dan push dokumen berstatus **Draft** atau **In Review** **tidak** berarti dokumen disetujui sebagai kebijakan organisasi.

## Dokumen terkait

- [[Approval-Policy]]
- [[Naming-Conventions]]
- [[Knowledge-Management-Policy]]
