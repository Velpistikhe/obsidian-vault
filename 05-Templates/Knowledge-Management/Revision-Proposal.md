---
title: Revision Proposal
document_id: TPL-010
template_id: TPL-010
document_type: template
category: knowledge-management
version: "0.1.0"
status: draft
owner: owner
author: hermes-default
reviewer: null
approved_by: null
approved_at: null
created_at: 2026-11-25
updated_at: 2026-11-25
tags: ['ai-office', 'templates', 'knowledge-management', 'revision', 'proposal']
---

# Revision Proposal

## 1. Purpose

Revision Proposal mendokumentasikan **usulan perubahan terhadap approved organizational documents** tanpa menimpa baseline resmi.

Mengikuti [[03-Hermes/Governance/Naming-Conventions|Naming Conventions]] (GOV-008) dan [[03-Hermes/Governance/Document-Lifecycle|Document Lifecycle]] (GOV-004).

- **Proposal bukan dokumen pengganti resmi.** Usulan revisi dokumen approved bukan kebijakan otoritatif; versi approved sebelumnya **tetap berlaku** sampai pengganti disetujui dan dipublikasikan secara resmi.
- **Approval proposal tidak otomatis berarti publication atau activation versi pengganti telah terjadi.** Approval, implementation, dan publication adalah tiga tahap terpisah.
- Proposal **tidak** memberi kewenangan baru, delegasi, atau permission.
- Identitas proposal memakai `proposal_id` namespace `REV-NNNNNN` — nama file **bukan** pengganti `proposal_id` (GOV-008). Namespace `REV` belum memiliki registry di vault, sehingga alokasi ID hanya dilakukan pada proposal aktual yang terotorisasi.

## 2. Usage Instructions

1. Baca master sesuai **Gate 1 — Master Template** pada bagian 7.
2. Ekstrak **Generated Metadata blueprint** (bagian 4), **Required Sections** (bagian 5), dan **applicable optional sections** (bagian 6) yang memang relevan. **Jangan** menyalin seluruh isi master ke instance.
3. Isi metadata dan konten instance dari **fakta aktual** — jangan membawa frontmatter master, approval master, Usage Instructions, atau Validation Checklist internal.
4. Isi `author` dengan **pembuat aktual instance**, `source_template_id` dengan **ID master yang benar-benar digunakan** (`TPL-010`), `source_template_version` dengan **versi master yang benar-benar digunakan**, serta `created_at` dan `updated_at` dengan **tanggal aktual** (GOV-008).
5. Isi `proposal_id` dengan identifier `REV-NNNNNN` yang **benar-benar dialokasikan** pada proposal aktual yang terotorisasi. **Jangan** mengarang, menebak, atau mengagak identifier.
6. Isi `document_id` dengan **referensi dokumen resmi yang direvisi** (misalnya `GOV-007`), bukan identitas proposal. Isi `base_version` dan `target_version` sebagai versi dokumen resmi, sedangkan `version` adalah versi dokumen proposal.
7. Isi approval metadata (`reviewer`, `approved_by`, `approved_at`) **hanya** bila terdapat keputusan sah sesuai kewenangan; biarkan `null` bila belum ada (GOV-004, GOV-005).
8. Validasi instance terhadap **Gate 2 — Generated Document** pada bagian 7, lalu simpan pada Target SSOT.

**Jangan** mengubah master ini saat menghasilkan instance. **Jangan** mewariskan approval, author, identifier, atau timestamp master ke instance.

## 3. Target SSOT

- **Governance revision proposal:** `03-Hermes/Governance/Proposals/` — lokasi target proposal yang ditetapkan GOV-008. Folder ini **belum dibuat** dan tidak dibuat oleh template ini; pembuatannya memerlukan otorisasi terpisah.
- **Dokumen lain:** lokasi proposal mengikuti SSOT dokumen target dan governance yang berlaku.

**Jangan** membuat actual proposal folder atau actual proposal instance dari template ini tanpa otorisasi.

## 4. Generated Metadata

Blueprint — **bukan** metadata dokumen siap publikasi. **Jangan** memasukkan identitas, approval, author, atau timestamp master sebagai nilai aktual instance.

```yaml
title: null
proposal_id: null
document_id: null
document_type: revision_proposal
category: null
version: "0.1.0"
base_version: null
target_version: null
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
target_document_path: null
approval_references: []
```

Aturan pengisian:

- `proposal_id` — identifier unik proposal (`REV-NNNNNN`), **wajib** pada metadata proposal aktual yang terotorisasi; nama file bukan pengganti.
- `document_id` — **referensi dokumen resmi yang direvisi**, bukan identitas proposal.
- `version` — versi dokumen **proposal**; `base_version` dan `target_version` adalah versi **dokumen resmi** yang direvisi.
- `target_document_path` — path relatif dokumen resmi target di vault.
- `approval_references` — array referensi approval yang dapat ditelusuri; `[]` bila belum ada approval sah.
- Nilai tunggal yang belum tersedia → `null`; koleksi kosong → `[]`.

**Supporting artifact tanpa organizational ID:** untuk dokumen approved yang tidak memiliki organizational identifier (path sebagai identitas), `document_id` diisi dengan **path dokumen target** dan `target_document_path` diisi dengan path yang sama — **tanpa** membuat namespace atau identifier baru. Keterbatasan ini dicatat eksplisit pada instance, bukan diperbaiki dengan membuat ID baru.

## 5. Required Sections

1. **Proposal Summary** — ringkasan usulan perubahan, dokumen target, dan alasan pengusulannya.
2. **Target Document and Baseline** — identitas dokumen target, path, `base_version` yang disyaratkan, sumber aktual, dan waktu verifikasi baseline.
3. **Background and Justification** — konteks, temuan, atau kebutuhan yang memunculkan usulan.
4. **Proposed Changes** — daftar perubahan yang diusulkan, dirinci pada Proposed Changes Matrix.
5. **Impact Analysis** — dampak terhadap governance, workflow, dokumen lain, metadata, dan consumer downstream.
6. **Risk and Mitigation** — risiko penerapan, risiko tidak menerapkan, dan mitigasi masing-masing.
7. **Governance and Authority Review** — dokumen governance yang relevan, kewenangan yang diperlukan, dan kelompok approval yang berwenang.
8. **Implementation and Validation Plan** — rencana penerapan dalam scope otorisasi, urutan langkah, dan cara validasi.
9. **Review Findings** — **kondisional**: temuan review aktual beserta tindak lanjutnya; diisi sesuai tahap instance.
10. **Approval Decision** — **kondisional**: keputusan aktual (approved/rejected/revise), approver, timestamp, dan evidence reference; `null` bila belum ada keputusan sah.
11. **Publication and Verification** — **kondisional**: hasil publikasi versi pengganti dan verifikasi thereof; diisi hanya bila publication benar-benar terjadi.

Section 9–11 **tidak** mewajibkan bukti kejadian yang belum terjadi. Instance pada tahap `draft` mencatat bagian tersebut sebagai belum terisi beserta penjelasan.

### Proposed Changes Matrix

Matriks berikut dapat dipakai ulang pada instance. Kolom `Change reference` memakai **local references** — bukan organizational identifier baru.

| Change reference | Target section | Existing content | Proposed change | Justification | Impact |
|---|---|---|---|---|---|
| (contoh ilustratif) | (contoh ilustratif) | (contoh ilustratif) | (contoh ilustratif) | (contoh ilustratif) | (contoh ilustratif) |

**Contoh di atas hanya ilustrasi** dan tidak boleh terbawa sebagai actual change pada instance. Template ini **tidak** memuat actual governance change maupun actual proposal untuk dokumen existing.

## 6. Optional Sections

- **Alternative Solutions** — alternatif yang dipertimbangkan beserta alasan tidak dipilih.
- **Migration Considerations** — dampak migrasi, urutan transisi, dan hal yang harus dipertahankan saat penggantian versi.
- **Compatibility Assessment** — dampak terhadap consumer, tooling, dan dokumen turunan.
- **Supporting Evidence** — referensi bukti pendukung yang benar-benar tersedia.
- **Related Revision Proposals** — proposal lain yang berkaitan.

## 7. Revision Workflow

Sesuai GOV-004, GOV-005, dan GOV-008:

1. **Identify approved target document** — tentukan dokumen approved yang akan direvisi.
2. **Verify baseline version dan sumber aktual** — pastikan `base_version` cocok dengan versi resmi terakhir dan catat sumber aktualnya.
3. **Create separate revision proposal** — buat proposal terpisah melalui workflow terotorisasi; **jangan** mengubah dokumen resmi dari `approved` menjadi `draft` untuk memulai revisi.
4. **Document proposed changes dan impact** — isi Proposed Changes Matrix dan Impact Analysis.
5. **Review sesuai kewenangan** — reviewer yang ditugaskan memeriksa kelengkapan dan konsistensi.
6. **Submit kepada authorized approver** — ajukan keputusan; status berpindah ke `pending_approval`.
7. **Record actual decision dan evidence** — catat keputusan, approver, timestamp, dan evidence reference.
8. **Verify baseline kembali sebelum implementation** — verifikasi ulang `base_version` terhadap versi resmi terakhir.
9. **Implement approved changes hanya dalam scope otorisasi** — terapkan hanya bagian yang disetujui.
10. **Validate dan publish replacement** — validasi hasil, lalu publikasikan versi pengganti melalui mekanisme yang berlaku.
11. **Verify publication dan pertahankan historical traceability** — pastikan versi baru terbaca kembali dan riwayat versi lama tetap terjaga.

Ketentuan siklus hidup:

- **Approved baseline tetap berlaku** sampai penggantian resmi berhasil.
- **Jika baseline berubah**, hentikan implementasi dan lakukan **reassessment** serta approval baru apabila diperlukan.
- **Rejected proposal tidak mengubah baseline**; permintaan revisi dikembalikan sesuai lifecycle GOV-004 dengan **alasan tercatat**.
- **Publication Git bukan approval** — status `approved` tidak boleh disimpulkan dari commit/push (GOV-004).
- **Jangan** memperluas kewenangan approval atau execution di luar yang diberikan.

## 8. Validation Checklist

Manual sebelum publikasi instance. Pemeriksaan ad-hoc — **bukan** automated governance validation.

### Master template usage gate

- [ ] Master `approved` → penggunaan resmi.
- [ ] Master `draft` → hanya untuk review atau simulasi terotorisasi.
- [ ] Master `archived` → hanya referensi historis, bukan penggunaan resmi baru.

### Generated document lifecycle gate

- [ ] `draft` — boleh belum lengkap, dengan penjelasan pada bagian yang belum terisi.
- [ ] `in_review` — memenuhi persyaratan review.
- [ ] `pending_approval` — memenuhi persyaratan pengajuan keputusan.
- [ ] `approved` — metadata lengkap dan approval sah sesuai kewenangan.
- [ ] `archived` — pengarsipan terotorisasi.

### Target identity dan baseline verification

- [ ] `proposal_id` terisi dan benar-benar dialokasikan; nama file bukan pengganti `proposal_id`.
- [ ] `document_id` merujuk dokumen resmi target, bukan identitas proposal.
- [ ] `base_version` diverifikasi terhadap versi resmi terakhir; sumber aktual tercatat.
- [ ] `target_version` diisi dan lebih tinggi dari `base_version`.
- [ ] `target_document_path` menunjuk dokumen target yang benar-benar ada.
- [ ] Dokumen target yang tidak memiliki organizational ID ditangani sesuai catatan pada bagian 4, tanpa identifier baru.

### Change scope dan impact

- [ ] Proposed Changes Matrix memakai local references; contoh ilustratif tidak terbawa sebagai actual change.
- [ ] Setiap proposed change menunjuk target section yang benar-benar ada pada dokumen target.
- [ ] Impact Analysis mencakup dampak ke dokumen lain dan consumer downstream.
- [ ] Usulan tidak melampaui ruang lingkup dokumen target.

### Approval authority dan evidence

- [ ] Approver yang diperlukan teridentifikasi sesuai GOV-005.
- [ ] Approval Decision diisi hanya atas keputusan aktual, dengan approver, timestamp, dan evidence reference.
- [ ] `approved_by` dan `approved_at` tetap `null` sebelum keputusan sah.
- [ ] Tidak ada klaim autentikasi independen identitas Owner.

### Implementation authorization

- [ ] Penerapan tidak dimulai sebelum proposal disetujui dan baseline diverifikasi ulang.
- [ ] Penerapan hanya mencakup bagian yang disetujui.
- [ ] Perubahan pada approved governance memerlukan kewenangan yang sesuai; template ini tidak memberi kewenangan baru.

### Post-publication verification

- [ ] Publication and Verification diisi hanya bila publication benar-benar terjadi.
- [ ] Versi pengganti terbaca kembali setelah publikasi.
- [ ] Versi approved sebelumnya tetap terdokumentasi sebagai riwayat.
- [ ] Status `approved` tidak disimpulkan dari commit/push.

### Author, timestamps dan provenance

- [ ] `author` = pembuat aktual instance.
- [ ] `created_at` dan `updated_at` = tanggal aktual (Asia/Jakarta; GOV-008).
- [ ] `source_template_id` = ID master yang benar-benar digunakan.
- [ ] `source_template_version` = versi master yang benar-benar digunakan.
- [ ] Approval metadata hanya terisi atas keputusan sah; `created_at` instance dipertahankan pada revisi normal.

### SSOT consistency

- [ ] Instance disimpan pada lokasi proposal sesuai bagian 3 dan SSOT dokumen target.
- [ ] Tidak ada duplikasi dokumen resmi kedua yang ambigu.

### Secret handling

- [ ] Tidak ada kredensial atau raw secret.

## 9. Governance References

- [[03-Hermes/Governance/Naming-Conventions|Naming Conventions]] (GOV-008) — namespace `REV-NNNNNN`, metadata proposal, dan lokasi target proposal
- [[03-Hermes/Governance/Document-Lifecycle|Document Lifecycle]] (GOV-004) — lifecycle, otorisasi transisi status, dan revisi dokumen approved
- [[03-Hermes/Governance/Approval-Policy|Approval Policy]] (GOV-005) — Approval Evidence and Traceability
- [[03-Hermes/Governance/Information-Architecture|Information Architecture]] (GOV-002) — SSOT dan lokasi dokumen
- [[03-Hermes/Governance/Knowledge-Management-Policy|Knowledge Management Policy]] (GOV-003)
- [[03-Hermes/Governance/AI-Office-Charter|AI Office Charter]] (GOV-001)
- [[03-Hermes/Governance/Authorization-Evidence/README|Authorization Evidence]] — mekanisme bootstrap bukti otorisasi
- [[05-Templates/Template-Standard|Template Standard]]

## Dokumen terkait

- [[05-Templates/Template-Registry|Template Registry]] — alokasi `TPL-010`
- [[03-Hermes/Governance/Authorization-Evidence/Template-Phase-2-Authorization|Template Phase 2 Authorization]] — bukti otorisasi pembuatan master ini; path eksplisit: `03-Hermes/Governance/Authorization-Evidence/Template-Phase-2-Authorization.md`
