---
title: Revision Proposal
document_id: TPL-010
template_id: TPL-010
document_type: template
category: knowledge-management
version: "1.0.0"
status: approved
owner: owner
author: hermes-default
reviewer: owner
approved_by: owner
approved_at: 2026-11-26T06:59:35+07:00
created_at: 2026-11-25
updated_at: 2026-11-26
tags: ['ai-office', 'templates', 'knowledge-management', 'revision', 'proposal']
---

# Revision Proposal

## 1. Purpose

Revision Proposal mendokumentasikan **usulan perubahan terhadap approved organizational documents** tanpa menimpa baseline resmi.

Mengikuti [[03-Hermes/Governance/Naming-Conventions|Naming Conventions]] (GOV-008) dan [[03-Hermes/Governance/Document-Lifecycle|Document Lifecycle]] (GOV-004).

- **Proposal bukan dokumen pengganti resmi.** Usulan revisi dokumen approved bukan kebijakan otoritatif; versi approved sebelumnya **tetap berlaku** sampai pengganti disetujui dan dipublikasikan secara resmi.
- **Approval proposal tidak otomatis berarti publication atau activation versi pengganti telah terjadi.** Approval, implementation, dan publication adalah tiga tahap terpisah.
- Proposal **tidak** memberi kewenangan baru, delegasi, atau permission.
- Identitas proposal memakai `proposal_id` namespace `REV-NNNNNN` — nama file **bukan** pengganti `proposal_id` (GOV-008).

### Target document identity (penggunaan resmi)

- `proposal_id` adalah identitas proposal (`REV-NNNNNN`).
- `document_id` adalah **organizational ID** dokumen resmi yang menjadi target revisi — **bukan** path, nama file, atau identitas proposal.
- `target_document_path` adalah lokasi aktual dokumen target di vault (atau referensi eksternal yang ditetapkan governance).

**Penggunaan resmi master ini saat ini terbatas** pada dokumen target yang memiliki organizational ID. Untuk approved supporting artifacts **tanpa** organizational ID:

- **Jangan** mengisi `document_id` menggunakan path.
- **Jangan** mengalokasikan organizational ID hanya agar dokumen dapat direvisi.
- **Hentikan** pembuatan proposal resmi menggunakan template ini dan laporkan pending governance improvement.

Perluasan dukungan path identity memerlukan perubahan GOV-008 yang disetujui dan dipublikasikan secara resmi, kemudian revisi master template yang terotorisasi. Rincian pending improvement: [[03-Hermes/Governance/Authorization-Evidence/Template-Phase-2-Approval|Template Phase 2 Approval]].

### Revision proposal bootstrap

- GOV-008 memiliki organizational ID dan secara prinsip **dapat** menjadi target Revision Proposal melalui workflow yang sah.
- Alokasi `REV-NNNNNN` aktual membutuhkan otorisasi eksplisit, verifikasi namespace, dan pencatatan sesuai GOV-008 — tidak ada infrastruktur otomatis yang dianggap operational pada fase ini.
- **REV Registry** di vault belum tersedia secara terverifikasi; master ini **tidak** mengalokasikan identifier secara otomatis.
- Pending governance improvement terkait path identity dan `document_id` dicatat pada [[03-Hermes/Governance/Authorization-Evidence/Template-Phase-2-Approval|Template Phase 2 Approval]]; **bukan** governance yang sudah berlaku.

## 2. Usage Instructions

1. Baca master sesuai **Gate 1 — Master Template** pada bagian 8.
2. Ekstrak **Generated Metadata blueprint** (bagian 4), **Required Sections** (bagian 5), dan **applicable optional sections** (bagian 6) yang memang relevan. **Jangan** menyalin seluruh isi master ke instance.
3. Isi metadata dan konten instance dari **fakta aktual** — jangan membawa frontmatter master, approval master, Usage Instructions, atau Validation Checklist internal.
4. Isi `author` dengan **pembuat aktual instance**, `source_template_id` dengan **ID master yang benar-benar digunakan** (`TPL-010`), `source_template_version` dengan **versi master yang benar-benar digunakan**, serta `created_at` dan `updated_at` dengan **tanggal aktual** (GOV-008).
5. Pastikan dokumen target memiliki **organizational ID** sebelum memulai proposal resmi. Bila tidak, hentikan dan eskalasi pending governance improvement (bagian 1).
6. Isi `proposal_id` dengan identifier `REV-NNNNNN` yang **benar-benar dialokasikan** pada proposal aktual yang terotorisasi. **Jangan** mengarang atau menebak identifier.
7. Isi `document_id` dengan **organizational ID dokumen resmi target** (misalnya `GOV-007`), bukan identitas proposal. Isi `base_version`, `base_revision_reference`, `base_verified_at`, dan `target_version` sesuai definisi bagian 4; `version` adalah versi dokumen proposal.
8. Isi `implementation_status` dan `implementation_references` hanya untuk pelacakan eksekusi pasca-approval — bukan sebagai pengganti lifecycle GOV-004.
9. Isi approval metadata (`reviewer`, `approved_by`, `approved_at`) **hanya** bila terdapat keputusan sah sesuai kewenangan; biarkan `null` bila belum ada (GOV-004, GOV-005).
10. Validasi instance terhadap **Gate 2 — Generated Document** dan **Execution gates** pada bagian 8, lalu simpan pada Target SSOT (bagian 3).

**Jangan** mengubah master ini saat menghasilkan instance. **Jangan** mewariskan approval, author, identifier, atau timestamp master ke instance.

## 3. Target SSOT

Lokasi penyimpanan proposal **mengikuti SSOT dokumen target** dan governance yang berlaku. **Jangan** memindahkan engineering SSOT ke vault.

| Kelas dokumen target | Lokasi proposal (SSOT) |
|----------------------|-------------------------|
| Governance (`GOV-*`) | Lokasi proposal yang ditetapkan GOV-008 (`03-Hermes/Governance/Proposals/` bila telah diotorisasi dan tersedia) |
| Project management | SSOT proyek di `02-Projects/{Project-Name}/` dan lokasi proposal proyek yang terotorisasi |
| Master template (`TPL-*`) | Lokasi proposal template yang ditetapkan secara terpisah melalui otorisasi Owner |
| Shared knowledge | Knowledge base vault sesuai [[03-Hermes/Governance/Knowledge-Management-Policy|Knowledge Management Policy]] (GOV-003) |
| Engineering / source code | Mekanisme perubahan di **GitHub Project Repository** — bukan duplikasi SSOT teknis ke vault |

**Jika lokasi proposal belum ditetapkan** untuk kelas target, hentikan publikasi proposal resmi dan laporkan kebutuhan keputusan Owner. **Jangan** membuat folder atau lokasi baru tanpa otorisasi.

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
base_revision_reference: null
base_verified_at: null
target_version: null
status: draft
implementation_status: null
implementation_references: []
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
- `document_id` — **organizational ID** dokumen resmi target; **bukan** path, nama file, atau identitas proposal. Placeholder `null` pada blueprint diperbolehkan; pada instance resmi **wajib** terisi untuk target yang memiliki organizational ID.
- `version` — versi dokumen **proposal**.
- `base_version` — versi resmi dokumen target pada saat baseline diverifikasi.
- `base_revision_reference` — commit Git atau referensi revisi yang memungkinkan **isi** baseline target diperiksa kembali.
- `base_verified_at` — timestamp aktual (ISO 8601, Asia/Jakarta) saat baseline diverifikasi.
- `target_version` — versi pengganti yang diusulkan; harus lebih tinggi dari `base_version` bila mengikuti konvensi semver dokumen target.
- `implementation_status` — metadata eksekusi: `not_started`, `in_progress`, `blocked`, `implemented`, `published`, `verified`. **Bukan** status lifecycle GOV-004.
- `implementation_references` — array referensi tertaut ke bukti pelaksanaan (path, commit, catatan verifikasi); `[]` bila belum ada.
- `target_document_path` — path relatif dokumen resmi target di vault (wajib untuk menavigasi ke SSOT).
- `approval_references` — array referensi approval yang dapat ditelusuri; `[]` bila belum ada approval sah.
- Nilai tunggal yang belum tersedia → `null`; koleksi kosong → `[]`.

### Baseline integrity verification

Verifikasi **identitas**, **versi**, dan **isi** dokumen target saat proposal disiapkan dan **verifikasi ulang** sebelum implementation. Perubahan HEAD repository secara umum **tidak otomatis** berarti baseline target berubah — yang relevan adalah perubahan pada dokumen target itu sendiri.

Jika isi target berubah setelah approval, hentikan implementation, lakukan reassessment, dan dapatkan approval baru apabila diperlukan (GOV-004, GOV-005, GOV-008).

### Implementation status separation

- Status pada proposal `approved` mencerminkan kondisi **keputusan** saat versi tersebut dicatat — bukan otomatis status pelaksanaan.
- **Jangan** menyimpulkan status eksekusi dari `status: approved` proposal.
- Approval proposal **tidak** otomatis memberikan implementation authority, delegasi, atau permission.

## 5. Required Sections

1. **Proposal Summary** — ringkasan usulan perubahan, dokumen target, dan alasan pengusulannya.
2. **Target Document and Baseline** — organizational ID, path, `base_version`, `base_revision_reference`, `base_verified_at`, sumber aktual, dan hasil verifikasi.
3. **Background and Justification** — konteks, temuan, atau kebutuhan yang memunculkan usulan.
4. **Proposed Changes** — daftar perubahan yang diusulkan, dirinci pada Proposed Changes Matrix.
5. **Impact Analysis** — dampak terhadap governance, workflow, dokumen lain, metadata, dan consumer downstream.
6. **Risk and Mitigation** — risiko penerapan, risiko tidak menerapkan, dan mitigasi masing-masing.
7. **Governance and Authority Review** — dokumen governance yang relevan, kewenangan yang diperlukan, dan kelompok approval yang berwenang.
8. **Implementation and Validation Plan** — rencana penerapan dalam scope otorisasi, urutan langkah, dan cara validasi.
9. **Review Findings** — **kondisional**: temuan review aktual beserta tindak lanjutnya; diisi sesuai tahap instance.
10. **Approval Decision** — **kondisional**: keputusan aktual (approved/rejected/revise), approver, timestamp, dan evidence reference; `null` bila belum ada keputusan sah.
11. **Publication and Verification** — **kondisional**: hasil publikasi versi pengganti dan verifikasi hasil publikasi; diisi hanya bila publication benar-benar terjadi atau tahap terkait telah dicapai.
12. **Post-approval Execution Evidence** — **kondisional**: catatan realisasi tertaut yang memisahkan baseline keputusan approved dari bukti pelaksanaan aktual.

Section 9–12 **tidak** mewajibkan bukti kejadian yang belum terjadi. Instance pada tahap `draft` mencatat bagian tersebut sebagai belum terisi beserta penjelasan.

### Proposed Changes Matrix

Matriks berikut dapat dipakai ulang pada instance. Kolom `Change reference` memakai **local references** — bukan organizational identifier baru.

| Change reference | Action | Target | Existing content | Proposed change | Justification | Impact |
|---|---|---|---|---|---|---|
| (contoh ilustratif) | modify | (contoh ilustratif) | (contoh ilustratif) | (contoh ilustratif) | (contoh ilustratif) | (contoh ilustratif) |

**Action** yang didukung: `add`, `modify`, `remove`.

- Untuk `add`, kolom **Target** dapat berupa lokasi penyisipan yang jelas — tidak harus section yang sudah ada.
- Untuk `modify` dan `remove`, identifikasi **Existing content** yang relevan.
- Usulan `remove` **tidak** memberikan otorisasi penghapusan konten atau file; eksekusi tetap memerlukan kewenangan terpisah.

**Contoh di atas hanya ilustrasi** dan tidak boleh terbawa sebagai actual change pada instance. Template ini **tidak** memuat actual governance change maupun actual proposal untuk dokumen existing.

### Post-approval execution evidence

Pisahkan dua lapisan:

1. **Approved proposal** sebagai baseline keputusan (tetap pada versi approved; jangan ditimpa untuk mencatat hasil pelaksanaan).
2. **Linked execution evidence** sebagai catatan realisasi (dapat berisi proposal reference, authorized executor, actual implementation, publication commit atau revision reference, verification results, outstanding issues, dan actual execution timestamps).

Isi **Publication and Verification** berdasarkan tahap yang **benar-benar** dicapai. Bila proposal sudah `approved`, gunakan execution evidence tertaut atau ikuti authorized revision workflow untuk memperbarui catatan pelaksanaan. Status pelaksanaan terkini berasal dari execution evidence atau sistem operasional yang berwenang — bukan dari asumsi otomatis atas approval proposal.

## 6. Optional Sections

- **Alternative Solutions** — alternatif yang dipertimbangkan beserta alasan tidak dipilih.
- **Migration Considerations** — dampak migrasi, urutan transisi, dan hal yang harus dipertahankan saat penggantian versi.
- **Compatibility Assessment** — dampak terhadap consumer, tooling, dan dokumen turunan.
- **Supporting Evidence** — referensi bukti pendukung yang benar-benar tersedia.
- **Related Revision Proposals** — proposal lain yang berkaitan.

## 7. Revision Workflow

Sesuai GOV-004, GOV-005, dan GOV-008:

1. **Identify approved target document** — tentukan dokumen approved dengan organizational ID yang akan direvisi.
2. **Verify baseline version, revision reference, dan sumber aktual** — pastikan `base_version` cocok dengan versi resmi terakhir; catat `base_revision_reference`, `base_verified_at`, dan sumber aktualnya.
3. **Create separate revision proposal** — buat proposal terpisah melalui workflow terotorisasi; **jangan** mengubah dokumen resmi dari `approved` menjadi `draft` untuk memulai revisi.
4. **Document proposed changes dan impact** — isi Proposed Changes Matrix dan Impact Analysis.
5. **Review sesuai kewenangan** — reviewer yang ditugaskan memeriksa kelengkapan dan konsistensi.
6. **Submit kepada authorized approver** — ajukan keputusan; status berpindah ke `pending_approval`.
7. **Record actual decision dan evidence** — catat keputusan, approver, timestamp, dan evidence reference.
8. **Verify baseline kembali sebelum implementation** — verifikasi ulang `base_version` dan isi target terhadap versi resmi terakhir.
9. **Implement approved changes hanya dalam scope otorisasi** — terapkan hanya bagian yang disetujui; perbarui `implementation_status` dan `implementation_references` tanpa menimpa baseline approved proposal.
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

### Gate 1 — Master Template

- [ ] Master `approved` → penggunaan resmi sesuai batasan target organizational ID.
- [ ] Master `draft` → hanya untuk review atau simulasi terotorisasi.
- [ ] Master `archived` → hanya referensi historis, bukan penggunaan resmi baru.

### Gate 2 — Generated Document

- [ ] `draft` — target dan usulan teridentifikasi; gap dijelaskan pada bagian yang belum terisi.
- [ ] `in_review` — substansi dan impact analysis siap diperiksa.
- [ ] `pending_approval` — temuan review telah ditangani dan proposal siap diputuskan.
- [ ] `approved` — metadata lengkap, keputusan sah, dan evidence tersedia.
- [ ] `archived` — pengarsipan terotorisasi.

### Execution gates (bukan status lifecycle GOV-004)

- [ ] **Implementation** — baseline diverifikasi ulang dan executor terotorisasi sebelum pekerjaan dimulai.
- [ ] **Publication** — versi pengganti benar-benar dipublikasikan melalui mekanisme yang berwenang.
- [ ] **Verification** — hasil aktual dan riwayat perubahan dapat ditelusuri; bukti tidak ditulis langsung menimpa approved proposal baseline.

### Target identity dan baseline verification

- [ ] `proposal_id` terisi dan benar-benar dialokasikan; nama file bukan pengganti `proposal_id`.
- [ ] `document_id` adalah organizational ID dokumen resmi target, bukan path atau identitas proposal.
- [ ] Target tanpa organizational ID **tidak** menggunakan template ini untuk proposal resmi.
- [ ] `base_version` diverifikasi terhadap versi resmi terakhir; `base_revision_reference` dan `base_verified_at` tercatat.
- [ ] `target_version` diisi dan lebih tinggi dari `base_version` bila konvensi target mewajibkan.
- [ ] `target_document_path` menunjuk dokumen target yang benar-benar ada.

### Change scope dan impact

- [ ] Proposed Changes Matrix memakai tujuh kolom dan local references; setiap baris memiliki `Action` (`add` / `modify` / `remove`).
- [ ] Contoh ilustratif tidak terbawa sebagai actual change.
- [ ] Setiap proposed change menunjuk target yang dapat dilokalisasi pada dokumen target.
- [ ] Impact Analysis mencakup dampak ke dokumen lain dan consumer downstream.
- [ ] Usulan tidak melampaui ruang lingkup dokumen target.

### Approval authority dan evidence

- [ ] Approver yang diperlukan teridentifikasi sesuai GOV-005.
- [ ] `reviewer` dicatat hanya ketika penugasan review sah telah diberikan.
- [ ] Approval Decision diisi hanya atas keputusan aktual, dengan approver, timestamp, dan evidence reference.
- [ ] `approved_by` dan `approved_at` tetap `null` sebelum keputusan sah.
- [ ] Keputusan rejected atau revise tidak mengubah approved target baseline.
- [ ] Tidak ada klaim autentikasi independen identitas Owner.

### Implementation authorization dan execution metadata

- [ ] Penerapan tidak dimulai sebelum proposal disetujui dan baseline diverifikasi ulang.
- [ ] Penerapan hanya mencakup bagian yang disetujui.
- [ ] `implementation_status` dan `implementation_references` tidak disimpulkan dari `status: approved` proposal.
- [ ] Perubahan pada approved governance memerlukan kewenangan yang sesuai; template ini tidak memberi kewenangan baru.

### Post-publication verification

- [ ] Publication and Verification diisi hanya bila publication atau tahap terkait benar-benar terjadi.
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
- [[03-Hermes/Governance/Authorization-Evidence/Template-Phase-2-Authorization|Template Phase 2 Authorization]] — bukti otorisasi pembuatan draft master; path eksplisit: `03-Hermes/Governance/Authorization-Evidence/Template-Phase-2-Authorization.md`
- [[03-Hermes/Governance/Authorization-Evidence/Template-Phase-2-Approval|Template Phase 2 Approval]] — bukti keputusan Owner atas approval master ini; path eksplisit: `03-Hermes/Governance/Authorization-Evidence/Template-Phase-2-Approval.md`
