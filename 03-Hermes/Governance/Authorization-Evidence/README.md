---
title: Authorization Evidence
category: governance
version: 1.0.0
status: approved
owner: owner
author: hermes-default
reviewer: owner
approved_by: owner
approved_at: 2026-11-25T17:49:57+07:00
created_at: 2026-11-25
updated_at: 2026-11-25
tags: ['ai-office', 'governance', 'authorization-evidence']
---

# Authorization Evidence

> **Identitas artefak:** dokumen ini adalah **supporting operational guidance**, bukan governance policy baru. Identitas otoritatif = path `03-Hermes/Governance/Authorization-Evidence/README.md`. Tidak memiliki `document_id`, `template_id`, atau APR identifier. Panduan ini mengikuti [[03-Hermes/Governance/Document-Lifecycle|Document Lifecycle]] (GOV-004), [[03-Hermes/Governance/Approval-Policy|Approval Policy]] (GOV-005), [[03-Hermes/Governance/Agent-Access-Policy|Agent Access Policy]] (GOV-006), dan [[03-Hermes/Governance/Naming-Conventions|Naming Conventions]] (GOV-008); bila bertentangan, governance yang berlaku.

## 1. Purpose dan scope

Folder ini menyimpan **catatan bukti otorisasi** untuk tindakan yang memerlukan persetujuan Owner tetapi belum tercatat pada Approval Record infrastructure.

**Dalam scope:**

- Mekanisme **bootstrap** untuk mencatat dan memverifikasi bukti otorisasi.
- Catatan konfirmasi retrospektif atas tindakan yang sudah terjadi.
- Rujukan bukti pada registry terkait.

**Di luar scope:**

- Menggantikan [[03-Hermes/Governance/Approval-Policy|Approval Policy]] (GOV-005) atau approval matrix.
- Membuat APR ID, Approval Record, atau namespace identifier baru.
- Menyimpan raw secret, kredensial, atau transcript lengkap.
- Membuktikan autentikasi identitas pembuat keputusan.

**Status mekanisme:** mekanisme bootstrap ini berlaku **selama Approval Record infrastructure belum tersedia**. Saat infrastructure tersedia dan diverifikasi, pencatatan berpindah ke mekanisme tersebut dan bootstrap dicatat sebagai historis.

## 2. Explicit Owner authorization

Mekanisme dalam dokumen ini diotorisasi eksplisit oleh Owner melalui keputusan:

> 1. Project Management Templates: Setujui sembilan master menjadi v1.0.0 dengan seluruh koreksi C01–C26.
> 2. Authorization Confirmation: Konfirmasi secara retrospektif bahwa reservation dan allocation TPL-001–009 telah diotorisasi Owner, dengan tetap mencatat keterbatasan bukti historis.
> 3. Bootstrap Authorization Evidence: Setujui seluruh mekanisme yang direkomendasikan.

Otorisasi ini mencakup pencatatan bukti dan pembaruan registry yang disebutkan. **Tidak** mencakup alokasi ID baru, pembuatan APR record, atau finalisasi master template pada tugas yang sama.

## 3. Retrospective confirmation

Konfirmasi retrospektif adalah **pengakuan Owner atas tindakan yang sudah terjadi**, dicatat setelah kejadian.

Sifatnya:

- **Tidak** memulihkan bukti historis yang hilang.
- **Tidak** mengubah timestamp reservation atau allocation yang sudah tercatat.
- **Tidak** menghapus keterbatasan bukti historis.
- **Tidak** memberikan otorisasi untuk alokasi ID berikutnya.
- **Tidak** memberikan delegasi atau permission baru.

Catatan konfirmasi retrospektif tersimpan terpisah per kejadian, contohnya: [[03-Hermes/Governance/Authorization-Evidence/Template-Phase-1-Authorization-Confirmation|Template Phase 1 Authorization Confirmation]].

## 4. Historical evidence limitation

Keterbatasan ini **wajib dicatat** dan tidak boleh dihapus:

- Instruksi persetujuan awal **tidak dapat ditemukan kembali** dalam store yang diperiksa saat Review A (pencarian isi vault, filesystem di luar vault, dan session history).
- Baseline commit yang dirujuk **membuktikan keadaan repository**, **bukan** bukti approval independen. Keberadaan commit hanya menunjukkan bahwa perubahan terjadi dan terpublikasi — bukan bahwa Owner menyetujuinya.
- Reference otorisasi asli pada registry bootstrap hanya menunjuk judul persetujuan dan baseline; keduanya **tidak** membuktikan keputusan secara independen.

Jika source reference asli tidak tersedia, **nyatakan keterbatasannya secara eksplisit** pada catatan. Jangan menggantinya dengan reference yang terkesan lebih kuat tanpa dasar.

## 5. Evidence recording dan verification

### Alur otorisasi berikutnya

Untuk alokasi atau tindakan yang memerlukan bukti otorisasi, gunakan urutan berikut:

```text
Request → Explicit Owner Authorization → Record Evidence → Publish Evidence →
Verify Evidence → Synchronize → Namespace Check → Reserve → Allocate →
Publish → Verify
```

**Bukti otorisasi wajib tersedia, terpublikasi, dan dapat dibaca kembali sebelum reservation dilakukan.** Reservation tanpa bukti yang sudah terpublikasi tidak boleh dimulai.

Urutan ini memperluas alur alokasi terpusat GOV-008 dengan tahap pencatatan dan verifikasi bukti di depan; tahap `Synchronize`, `Namespace Check`, `Allocate`, `Publish`, dan `Verify` tetap mengikuti GOV-008.

### Evidence minimal

Setiap catatan bukti minimal memuat:

| Elemen | Keterangan |
|--------|------------|
| Owner decision | Keputusan Owner yang **benar-benar diterima**, dikutip apa adanya |
| Authorized action | Tindakan yang diotorisasi |
| Authorized resource | Resource yang dicakup otorisasi |
| Scope dan constraints | Batasan yang berlaku |
| `recorded_at` | Timestamp **aktual** pencatatan (ISO 8601 + timezone) |
| Baseline / version | Baseline atau versi dokumen yang relevan |
| Validity dan kondisi | Masa berlaku dan syarat, bila ada |
| Evidence source dan keterbatasannya | Asal bukti dan batasannya |

### Original decision time vs recorded_at

- **`recorded_at`** = kapan catatan ini ditulis, selalu dari system clock aktual.
- **Original decision time** = kapan keputusan Owner benar-benar dibuat.

Jika waktu keputusan asli **tidak diketahui**, **jangan mengarang timestamp**. Tulis `unknown` beserta alasannya, dan jangan menyamakannya dengan `recorded_at`.

### Batasan klaim identitas

Catatan instruksi yang diterima **tidak boleh diklaim** sebagai bukti autentikasi independen identitas Owner. Pencatatan membuktikan bahwa instruksi diterima dan dicatat — bukan bahwa identitas pembuatnya diverifikasi secara kriptografis atau oleh pihak ketiga.

Jangan mengklaim tanda tangan digital, sertifikat, atau mekanisme autentikasi yang tidak tersedia.

## 6. Safe handling dan traceability

- **Jangan** menyimpan seluruh transcript percakapan — cukup kutipan keputusan yang relevan.
- **Jangan** menyimpan raw secret, kredensial, token, atau informasi sensitif yang tidak relevan (GOV-003, GOV-006).
- **Jangan** menyimpan data pribadi atau konteks percakapan yang tidak diperlukan untuk menelusuri keputusan.
- Setiap catatan harus dapat ditelusuri: keputusan → resource → tindakan → dampak pada registry.
- Registry merujuk ke catatan bukti melalui path eksplisit vault; catatan merujuk kembali ke baseline, commit, dan registry.
- Gunakan system clock aktual (Asia/Jakarta untuk tanggal; ISO 8601 dengan timezone untuk timestamp) — GOV-008.

## 7. Registry reference

[[05-Templates/Template-Registry|Template Registry]] menyimpan `authorization_reference` per entri alokasi. Field tersebut memuat:

- **Original reference** — referensi yang ada saat alokasi bootstrap, dipertahankan apa adanya.
- **Retrospective confirmation reference** — path eksplisit ke catatan konfirmasi, ditambahkan tanpa menghapus original reference.

Kedua referensi dibedakan secara eksplisit agar pembaca dapat membedakan bukti yang tersedia saat alokasi dari konfirmasi yang diberikan belakangan.

Registry tetap menggunakan schema, approval metadata, dan `version: 1.0.0` yang approved. Pembaruan `authorization_reference` adalah **transaksi audit record yang diotorisasi**, bukan revisi aturan alokasi (GOV-008).

## 8. Future authorization workflow

Saat Approval Record infrastructure tersedia:

1. Verifikasi infrastructure tersedia dan berfungsi (GOV-002 — status aktual, bukan asumsi).
2. Migrasikan pencatatan ke mekanisme tersebut sesuai GOV-005 (Approval Evidence and Traceability).
3. Catat dokumen bootstrap ini sebagai historis; jangan menghapusnya.
4. Terapkan standar ID approval (`APR-NNNNNN`) hanya setelah infrastructure tersedia dan otorisasi terpisah diberikan.

Sampai saat itu, bootstrap tetap berlaku dengan batasan yang dinyatakan di bagian 4 dan 5.

## Dokumen terkait

- [[03-Hermes/Governance/Authorization-Evidence/Template-Phase-1-Authorization-Confirmation|Template Phase 1 Authorization Confirmation]]
- [[05-Templates/Template-Registry|Template Registry]]
- [[03-Hermes/Governance/Approval-Policy|Approval Policy]] (GOV-005)
- [[03-Hermes/Governance/Document-Lifecycle|Document Lifecycle]] (GOV-004)
- [[03-Hermes/Governance/Agent-Access-Policy|Agent Access Policy]] (GOV-006)
- [[03-Hermes/Governance/Naming-Conventions|Naming Conventions]] (GOV-008)
- [[03-Hermes/Governance/Knowledge-Management-Policy|Knowledge Management Policy]] (GOV-003)
