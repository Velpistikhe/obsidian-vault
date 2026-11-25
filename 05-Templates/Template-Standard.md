---
title: Template Standard
category: templates
version: 1.0.0
status: approved
owner: owner
author: hermes-default
reviewer: owner
approved_by: owner
approved_at: 2026-11-25T16:22:31+07:00
created_at: 2026-11-25
updated_at: 2026-11-25
tags: ['ai-office', 'templates', 'standard']
---

# Template Standard

> **Identitas artefak:** supporting operational standard; identitas otoritatif = path `05-Templates/Template-Standard.md`. **Tidak** memiliki `template_id` maupun `document_id`. Lihat [[05-Templates/README|Documentation Templates]].

## Tujuan

Panduan turunan untuk membuat dan menggunakan master template di `05-Templates/`. Dokumen ini **bukan governance policy baru**; seluruh aturannya menurunkan dan mengacu ke GOV-001 sampai GOV-008 yang berstatus approved. Bila terjadi konflik, governance yang berlaku.

## Master Template Metadata

Setiap master template memiliki **satu YAML frontmatter aktual** dengan field berikut:

| Field | Keterangan |
|-------|------------|
| `title` | Judul manusia. |
| `document_id` | Nilai TPL — **sama** dengan `template_id`. |
| `template_id` | Nilai TPL — **sama** dengan `document_id`. |
| `document_type` | Selalu `template`. |
| `category` | `project-management`, `agent-management`, `software-development`, atau `knowledge-management` — selaras dengan [[05-Templates/Template-Registry|Template Registry]]. Folder vault tetap `Project-Management/`, dll. |
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
- Alokasi `TPL-*` mengikuti [[05-Templates/Template-Registry|Template Registry]] dan GOV-008 — hanya melalui workflow terotorisasi.

## Generated Document Metadata

Contoh metadata instance diletakkan sebagai **fenced YAML di dalam body template**, bukan frontmatter kedua:

```yaml
title: null
document_id: null
document_type: null
category: null
version: "0.1.0"
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
```

Blueprint di atas merupakan **contoh pola** di body master — **bukan** metadata dokumen yang siap dipublikasikan.

- Namespace `TPL` **hanya** untuk master template, bukan untuk instance.
- Instance memperoleh `document_id` dan identifier lain sesuai GOV-008 dan jenis entitas (`PRJ-NNN-DOC-NNN`, `KNW-NNN`, `proposal_id`, dll.).
- Pertahankan context-specific metadata bila relevan; entity records dan native system resources mengikuti schema masing-masing.

Aturan instance:

- Metadata instance mengikuti GOV-004, GOV-007, GOV-008 dan jenis dokumennya.
- Saat instance **dibuat**, isi: `author` = pembuat aktual; `source_template_id` = ID master aktual; `source_template_version` = versi master yang benar-benar digunakan; `created_at`/`updated_at` = system clock aktual.
- Instance **tidak mewarisi** approval, author, identifier, atau timestamp master.
- Gunakan `null` dan `[]` sesuai tipe field (GOV-008).

## Universal Template Structure

Setiap master template memiliki:

1. **Template Metadata** — frontmatter master.
2. **Purpose** — tujuan dan ruang lingkup template.
3. **Usage Instructions** — cara **generate** instance dari master (bukan salin seluruh master) dan di mana menyimpan instance.
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

### Generate from template

1. Baca master `approved`.
2. Ekstrak generated metadata blueprint dan section yang berlaku.
3. Isi metadata/konten instance dari fakta aktual.
4. Validasi, lalu simpan pada Target SSOT.

**Jangan** membawa master frontmatter, master approval, Usage Instructions, atau Validation Checklist ke instance. **Jangan** mengubah master saat generate instance.

### Aturan umum

- Gunakan master `approved` untuk penggunaan resmi; master `draft` hanya untuk review/simulasi terotorisasi.
- Approval master **tidak diwariskan** kepada instance.
- Generate **tidak** memberikan approval, assignment, delegasi, atau permission.
- `TPL-*` hanya melalui [[05-Templates/Template-Registry|Template Registry]]; `PRJ`, `AGT`, `DEL`, `APR`, `REV`, dan lainnya sesuai GOV-008 — registry namespace lain **belum tersedia** untuk semua jenis.
- Jangan menyimpan raw secrets.
- SSOT instance mengikuti [[03-Hermes/Governance/Information-Architecture|Information Architecture]] (GOV-002).
- Metadata waktu mengikuti [[03-Hermes/Governance/Naming-Conventions|Naming Conventions]] dan system clock aktual.
- Revisi master approved mengikuti GOV-004/GOV-008 — proposal terpisah.
- Validation checklist **manual** sampai automated validation terverifikasi.

## Foundation Document Metadata

| Berkas | Sifat | `template_id` |
|--------|-------|---------------|
| `05-Templates/README.md` | Supporting navigation artifact — bukan master template. | Tidak diberikan |
| `05-Templates/Template-Registry.md` | Supporting registry artifact — bukan master template. | Tidak diberikan |
| `05-Templates/Template-Standard.md` | Supporting operational standard — bukan master template. | Tidak diberikan |

- Jangan memberikan ID `TPL` kepada ketiga file foundation.
- Ketiga foundation menggunakan **path vault** sebagai identitas; tidak memiliki `document_id` atau `template_id`.
- Jangan menciptakan namespace identifier baru untuk foundation.

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
- [ ] Tidak ada ID aktual dialokasikan lewat generate instance.
- [ ] Tidak ada kredensial atau raw secret.
- [ ] Wikilink hanya menunjuk berkas yang benar-benar ada.
- [ ] Master tercatat pada [[05-Templates/Template-Registry|Template Registry]] setelah alokasi dan verifikasi.
- [ ] Blueprint instance tidak memakai namespace `TPL` untuk `document_id`.

## Governance References

- [[03-Hermes/Governance/AI-Office-Charter|AI Office Charter]] (GOV-001)
- [[03-Hermes/Governance/Information-Architecture|Information Architecture]] (GOV-002)
- [[03-Hermes/Governance/Knowledge-Management-Policy|Knowledge Management Policy]] (GOV-003)
- [[03-Hermes/Governance/Document-Lifecycle|Document Lifecycle]] (GOV-004)
- [[03-Hermes/Governance/Approval-Policy|Approval Policy]] (GOV-005)
- [[03-Hermes/Governance/Agent-Access-Policy|Agent Access Policy]] (GOV-006)
- [[03-Hermes/Governance/Project-Registration-Standard|Project Registration Standard]] (GOV-007)
- [[03-Hermes/Governance/Naming-Conventions|Naming Conventions]] (GOV-008)

## Dokumen terkait

- [[05-Templates/README|Documentation Templates]] — katalog 29 master template
- [[05-Templates/Template-Registry|Template Registry]] — SSOT namespace `TPL` saja
