---
title: Template Standard
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
tags: ['ai-office', 'templates', 'standard']
---

# Template Standard

> **Catatan frontmatter:** dokumen ini adalah supporting operational standard, bukan master template, sehingga **tidak** menerima `template_id` maupun `document_id` (lihat [[README|05-Templates README]]).

## Tujuan

Panduan turunan untuk membuat dan menggunakan master template di `05-Templates/`. Dokumen ini **bukan governance policy baru**; seluruh aturannya menurunkan dan mengacu ke GOV-001 sampai GOV-008 yang berstatus approved. Bila terjadi konflik, governance yang berlaku.

**Status: draft sampai review Owner.**

## Master Template Metadata

Setiap master template memiliki **satu YAML frontmatter aktual** dengan field berikut:

| Field | Keterangan |
|-------|------------|
| `title` | Judul manusia. |
| `document_id` | Nilai TPL — **sama** dengan `template_id`. |
| `template_id` | Nilai TPL — **sama** dengan `document_id`. |
| `document_type` | Selalu `template`. |
| `category` | Salah satu dari empat kategori folder. |
| `version` | Semver (GOV-004). |
| `status` | Document lifecycle (GOV-004). |
| `owner` | Document owner. |
| `author` | Pembuat. |
| `reviewer` | Reviewer; `null` bila belum ditetapkan. |
| `approved_by` | `null` sampai approval sah. |
| `approved_at` | `null` sampai approval sah; ISO 8601 + timezone setelah approval. |
| `created_at` | `YYYY-MM-DD` dari system clock. |
| `updated_at` | `YYYY-MM-DD` dari system clock. |
| `tags` | Array lowercase-hyphenated. |

Aturan:

- **`document_id` dan `template_id` memakai nilai TPL yang sama** — tidak ada dua ID berbeda untuk satu master.
- **Master baru:** `version: 0.1.0`, `status: draft`, `reviewer: null` bila belum ditetapkan, `approved_by: null`, `approved_at: null`, `created_at` dan `updated_at` dari system clock aktual.
- **Tidak mengalokasikan ID aktual dalam Phase 0** — alokasi mengikuti [[Template-Registry]] dan GOV-008.

## Generated Document Metadata

Contoh metadata instance diletakkan sebagai **fenced YAML di dalam body template**, bukan frontmatter kedua:

```yaml
# Contoh pola — bukan alokasi aktual
document_id: TPL-INSTANCE-ID
document_type: <jenis-dokumen>
title: <Judul Dokumen>
category: <project|agent|software|knowledge>
version: 0.1.0
status: draft
owner: <document-owner>
author: hermes-default
reviewer: null
approved_by: null
approved_at: null
created_at: YYYY-MM-DD
updated_at: YYYY-MM-DD
tags: []
# --- field entity bila relevan (GOV-007, GOV-008) ---
project_id: null            # pola PRJ-NNN; null sampai dialokasikan
project_status: null        # lifecycle proyek — BUKAN status dokumen
delegation_status: null     # bila dokumen adalah Delegation-Record
decision: null              # bila dokumen adalah Approval-Record
activation_status: null     # bila dokumen adalah Agent-Profile
allocation_status: null     # identifier lifecycle — lihat Template-Registry
# --- provenance ---
source_template_id: <template-id>
source_template_version: 0.1.0
```

Aturan instance:

- Metadata instance mengikuti GOV-004, GOV-007, GOV-008 dan jenis dokumennya.
- `source_template_id` dan `source_template_version` mereferensikan master yang digunakan (provenance).
- Instance **tidak mewarisi** `document_id`, status approval, metadata approval, `author`, atau timestamp master.
- Instance memperoleh identitas dan metadata aktual melalui workflow yang terotorisasi.
- Gunakan `null` untuk nilai tunggal yang belum tersedia dan `[]` untuk koleksi kosong (GOV-008).

## Universal Template Structure

Setiap master template memiliki:

1. **Template Metadata** — frontmatter master.
2. **Purpose** — tujuan dan ruang lingkup template.
3. **Usage Instructions** — cara mengisi dan di mana menyimpan instance.
4. **Target SSOT** — lokasi otoritatif instance yang dihasilkan.
5. **Generated Metadata** — contoh fenced YAML metadata instance.
6. **Required Sections** — bagian wajib instance.
7. **Optional Sections** — bagian opsional instance.
8. **Validation Checklist** — pemeriksaan manual sebelum publish.
9. **Governance References** — wikilink GOV terkait.

Struktur disesuaikan berdasarkan jenis dokumen. **Instruksi penggunaan template dipisahkan dari konten instance** — panduan tidak boleh terbaca sebagai isi dokumen aktual.

## Lifecycle Separation

Jangan mencampur dimensi status berikut:

| Dimensi | Field | Berlaku pada |
|---------|-------|--------------|
| Document lifecycle | `status` | Dokumen vault dan master template (GOV-004) |
| Project lifecycle | `project_status` | Project Profile dan registrasi proyek (GOV-007) |
| Agent activation | `activation_status` | Agent Profile / registry agent |
| Delegation | `delegation_status` | Delegation-Record (GOV-005) |
| Approval decision | `decision` | Approval-Record (GOV-005) |
| Identifier lifecycle | `allocation_status` | Registry alokasi ID, mis. `TPL` (GOV-008) |

- Jangan memaksakan seluruh core document metadata pada native system resources atau entity records bila tidak relevan (GOV-008).
- **Pertahankan native IDs** (Kanban, GitHub, Git, ADR repo) — organizational ID melengkapi, tidak menggantikan (GOV-008).

## Usage Rules

- Jangan mengedit master saat mengisi instance.
- Gunakan master `approved` untuk penggunaan resmi.
- Master `draft` dapat digunakan untuk review atau simulasi terotorisasi.
- Approval master **tidak diwariskan** kepada instance.
- Pengisian template **tidak** memberikan approval, assignment, delegasi, atau permission.
- Project, agent, approval, dan delegation IDs hanya dialokasikan melalui workflow terotorisasi (GOV-008, [[Template-Registry]]).
- Jangan menyimpan raw secrets.
- SSOT instance mengikuti [[Information-Architecture]] (GOV-002).
- Metadata waktu mengikuti [[Naming-Conventions]] (GOV-008) dan system clock aktual.
- Revisi master approved mengikuti [[Document-Lifecycle]] (GOV-004) dan GOV-008 — siapkan proposal terpisah, jangan menurunkan status master resmi ke draft.
- Validation checklist dilakukan **manual** sampai automated validation terverifikasi.

## Foundation Document Metadata

| Berkas | Sifat | `template_id` |
|--------|-------|---------------|
| `05-Templates/README.md` | Supporting navigation artifact — bukan master template. | Tidak diberikan |
| `05-Templates/Template-Registry.md` | Supporting registry artifact — bukan master template. | Tidak diberikan |
| `05-Templates/Template-Standard.md` | Supporting operational standard — bukan master template. | Tidak diberikan |

- Jangan memberikan ID `TPL` kepada ketiga file foundation.
- Bila suatu field identitas belum memiliki namespace yang sesuai, **jangan** menciptakan ID fiktif atau namespace baru; laporkan kebutuhan metadata tambahan kepada Owner.
- `document_id` ketiga file foundation sengaja dikosongkan karena tidak ada namespace yang sesuai — bukan kelalaian.

## Validation Checklist

Manual, per master template, sebelum publikasi:

- [ ] Frontmatter master memuat seluruh field wajib; `document_id` == `template_id`.
- [ ] `version` mulai `0.1.0`, `status: draft`, `approved_by`/`approved_at` `null`.
- [ ] Tanggal dari system clock aktual (Asia/Jakarta; ISO 8601 + timezone untuk timestamp).
- [ ] Contoh metadata instance berada di fenced YAML body, bukan frontmatter kedua.
- [ ] Instance tidak mewarisi `document_id`/approval/author/timestamp master.
- [ ] Field entity (`project_status`, `delegation_status`, `decision`, `activation_status`, `allocation_status`) tidak tertukar dengan `status`.
- [ ] Sembilan bagian struktur universal tersedia atau disesuaikan secara eksplisit.
- [ ] Target SSOT instance konsisten dengan GOV-002.
- [ ] Tidak ada ID aktual dialokasikan lewat pengisian template.
- [ ] Tidak ada kredensial atau raw secret.
- [ ] Wikilink hanya menunjuk berkas yang benar-benar ada.
- [ ] Master tercatat pada [[Template-Registry]] setelah alokasi dan verifikasi.

## Governance References

- [[AI-Office-Charter]] (GOV-001)
- [[Information-Architecture]] (GOV-002)
- [[Knowledge-Management-Policy]] (GOV-003)
- [[Document-Lifecycle]] (GOV-004)
- [[Approval-Policy]] (GOV-005)
- [[Agent-Access-Policy]] (GOV-006)
- [[Project-Registration-Standard]] (GOV-007)
- [[Naming-Conventions]] (GOV-008)

## Dokumen terkait

- [[README|05-Templates README]] — katalog rancangan 29 template
- [[Template-Registry]] — SSOT alokasi namespace `TPL`
