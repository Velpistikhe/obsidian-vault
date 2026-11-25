---
title: Document Lifecycle
document_id: GOV-004
category: governance
version: 0.2.0
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

Siklus hidup dokumen kebijakan dan pengetahuan di vault. Status mencerminkan kondisi dokumen; publikasi Git sendiri tidak memberikan approval.

## Status dan transisi

```text
draft → in_review → pending_approval → approved → archived
          ↑  ↓             ↓
          └── draft ←───────┘
```

| Status | Makna dan kondisi |
|---|---|
| `draft` | Konten awal atau revisi yang sedang disiapkan. Boleh dipublikasikan untuk review bila diotorisasi; belum disetujui. |
| `in_review` | Reviewer ditugaskan dan memeriksa konten. Reviewer dapat meminta perubahan; dokumen kembali ke `draft`. |
| `pending_approval` | Review selesai dan dokumen diajukan kepada Owner atau delegasi yang secara eksplisit disetujui. Jika approval belum diberikan atau revisi diminta, status kembali ke `draft`. |
| `approved` | Versi yang disetujui oleh pihak berwenang; metadata approval mencatat otoritas dan waktu aktual. Tidak boleh ditetapkan tanpa approval sah. |
| `archived` | Dokumen tidak aktif dan dipertahankan untuk referensi historis; pengarsipan memerlukan otorisasi dan mengikuti aturan arsip di bawah. |

Transisi normal: `draft` → `in_review` → `pending_approval` → `approved`. Reviewer mengembalikan ke `draft` untuk revisi. Approver yang belum memberi approval atau menolak proposal mengembalikannya ke `draft`; versi approved sebelumnya tetap berlaku. Perpindahan ke `archived` dilakukan atas otorisasi yang sesuai. Status `approved` tidak boleh disimpulkan dari commit/push.

Untuk dokumen rutin, lifecycle sederhana dapat digunakan hanya bila jenis dokumen dan delegasinya secara eksplisit disetujui. Tidak ada delegasi yang diasumsikan aktif; detail otoritas mengikuti [[Approval-Policy]].

## Document Versioning

Gunakan pola `MAJOR.MINOR.PATCH` yang diadaptasi untuk dokumentasi:

- `0.1.0`: initial draft.
- `0.2.0`: substantive draft revision.
- `0.2.1`: minor draft correction.
- `1.0.0`: first approved version.
- **PATCH:** non-substantive correction.
- **MINOR:** compatible addition.
- **MAJOR:** fundamental policy change.

Contoh tersebut adalah pedoman versi, bukan hak approval. Kenaikan versi tidak memberikan kewenangan approval. Perubahan pada dokumen approved mengikuti otorisasi dan dampak perubahan; perubahan material kembali melalui review dan approval.

## Revisi dokumen approved

Versi approved terakhir tetap menjadi versi resmi selama revisi berlangsung dan jika revisi ditolak. Jangan mengubah file resmi dari `approved` menjadi `draft` untuk memulai revisi.

Buat usulan perubahan sebagai draft terpisah di workspace, atau sebagai file proposal terpisah di vault jika publikasi review diotorisasi. Proposal mencantumkan `document_id`, `base version`, dan `target version`. Setelah memperoleh approval sah, versi resmi diperbarui melalui publikasi terotorisasi dan mencatat approval. Jika ditolak, proposal tidak menggantikan versi resmi sebelumnya.

## Document Ownership dan peran

- **Organizational Owner:** otoritas strategis organisasi; bukan otomatis pemilik operasional setiap dokumen.
- **Document Owner (`owner`):** bertanggung jawab atas akurasi, relevansi, pemeliharaan, dan pengajuan perubahan dokumen. Status ini tidak otomatis memberi kewenangan strategic approval.
- **Author (`author`):** menyiapkan atau menyusun perubahan.
- **Reviewer (`reviewer`):** mengevaluasi konten dan memberi rekomendasi; tidak otomatis menjadi approver.
- **Approver (`approved_by`):** pihak yang berwenang dan benar-benar memberikan approval.
- **Publisher:** pihak yang menjalankan publikasi terotorisasi sesuai akses dan workflow.
- **Consumer:** pembaca/pengguna dokumen; wajib memperhatikan status dan versi.

## Change History

Git adalah mekanisme utama version history untuk dokumen di repository. Perubahan material harus menyatakan alasan perubahan, versi sebelumnya, versi baru, dan referensi approval apabila diperlukan. Commit/push membantu mencatat perubahan teknis tetapi bukan bukti approval tanpa metadata atau catatan persetujuan yang sah.

## Document Archiving

`archived` berarti dokumen tidak aktif tetapi dipertahankan untuk referensi historis. Gunakan `99-Archive` hanya bila pengarsipan diotorisasi. Jangan membuat salinan semua versi historis jika riwayat Git sudah memadai. Penghapusan dokumen tetap memerlukan otorisasi eksplisit; aturan ini tidak mengotorisasi pemindahan atau penghapusan.

## Metadata Standards

Ikuti [[Naming-Conventions]] (GOV-008) untuk standar metadata; bagian ini tidak menggantikan atau menduplikasi standar tersebut. Secara ringkas:

- `document_id`: identitas dokumen yang stabil.
- `version`: versi dokumen.
- `status`: status lifecycle.
- `owner`: document owner, bukan otomatis approver.
- `author`: penulis dokumen/perubahan.
- `reviewer`: reviewer yang ditugaskan.
- `approved_by`: hanya pihak yang benar-benar memberikan approval sah.
- `approved_at`: hanya diisi setelah approval sah.
- `created_at`: tanggal pembuatan awal; dipertahankan.
- `updated_at`: tanggal perubahan dokumen; diperbarui saat ada perubahan.

Gunakan system clock Asia/Jakarta untuk tanggal metadata dan ISO 8601 dengan zona waktu untuk timestamp. Jangan memperkirakan waktu dari asumsi internal model. Detail format dan konvensi tetap mengikuti GOV-008.

## Pemisahan publikasi dan approval

Commit/push dokumen `draft` atau `in_review` dapat mendukung kolaborasi review, tetapi **tidak** berarti dokumen disetujui sebagai kebijakan organisasi. Hanya approval sah yang dapat menetapkan status `approved`.

## Dokumen terkait

- [[Approval-Policy]]
- [[Naming-Conventions]]
- [[Knowledge-Management-Policy]]
- [[Agent-Access-Policy]]
