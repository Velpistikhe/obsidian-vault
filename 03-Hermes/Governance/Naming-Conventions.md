---
title: Naming Conventions
document_id: GOV-008
category: governance
version: 1.0.0
status: approved
owner: owner
author: hermes-default
reviewer: owner
approved_by: owner
approved_at: 2026-11-25T08:58:26+07:00
created_at: 2026-11-24
updated_at: 2026-11-25
tags: ['ai-office', 'governance', 'naming']
---

# Naming Conventions

## Ringkasan

Konvensi penamaan file, folder, identifier organisasi, metadata, dan tag untuk konsistensi vault AI Office. Organizational ID melengkapi — **tidak menggantikan** — native ID sistem (Kanban, GitHub Issues/PR, Git commits, technical ADR di repo).

Contoh ID dalam dokumen ini bersifat ilustratif; bukan alokasi aktual. Automatic allocation dan concurrency enforcement tetap **Planned** atau belum terverifikasi ([[Information-Architecture]]).

## Organizational Identifiers

| Pola | Penggunaan | Contoh ilustratif |
|------|------------|-------------------|
| `GOV-NNN` | Governance policy | `GOV-007` |
| `PRJ-NNN` | Project identity | `PRJ-001` |
| `AGT-NNN` | Agent registry entry | `AGT-001` |
| `KNW-NNNNNN` | Knowledge artifact (cross-cutting) | `KNW-000042` |
| `SOP-NNN` | Standard operating procedure | `SOP-003` |
| `WF-NNN` | Workflow definition | `WF-002` |
| `TPL-NNN` | Template | `TPL-001` |
| `PRJ-NNN-DOC-NNN` | Project document instance | `PRJ-001-DOC-002` |
| `DEL-NNNNNN` | Delegation record | `DEL-000015` |
| `APR-NNNNNN` | Approval record | `APR-000088` |
| `REV-NNNNNN` | Revision proposal | `REV-000001` |

Aturan umum ID organisasi:

- **Unik** dalam namespace yang berlaku.
- **Immutable** setelah dialokasikan; tidak didaur ulang.
- **Non-reusable** — ID yang pernah dipakai tidak dipakai ulang untuk entitas lain.
- **Traceable** — dapat dihubungkan ke registry atau catatan otoritatif.
- Dialokasikan melalui **mekanisme terpusat** oleh pihak berwenang (Owner atau delegate yang ditetapkan).

Sebelum alokasi: **periksa namespace dan registry** yang berlaku. Jangan mengklaim **collision prevention otomatis** telah tersedia — validasi metadata dan registry terpusat masih **Planned** ([[Agent-Access-Policy]], [[Information-Architecture]]).

### Centralized ID allocation (manual workflow)

Alokasi ID organisasi dilakukan secara **manual** oleh pihak berwenang melalui alur berikut:

```text
Request → Authorization → Synchronize → Namespace Check → Allocate → Register → Publish → Verify
```

| Tahap | Kegiatan |
|-------|----------|
| Request | Permintaan alokasi ID dengan jenis entitas dan konteks. |
| Authorization | Persetujuan pihak berwenang sebelum alokasi. |
| Synchronize | Sinkronisasi knowledge base ([[Knowledge-Management-Policy]]) sebelum membaca/menulis registry. |
| Namespace Check | Periksa ID **reserved**, **allocated**, dan **retired** dalam namespace yang berlaku. |
| Allocate | Berikan nomor berikutnya secara **serial**; jangan gunakan ID yang pernah dialokasikan untuk entitas berbeda. |
| Register | Catat entri di registry otoritatif setelah alokasi. |
| Publish | Publikasi terotorisasi ke knowledge base bila diperlukan. |
| Verify | Verifikasi konsistensi registry dan tidak adanya duplikasi. |

Aturan:

- Alokasi dilakukan **serial** oleh pihak berwenang; tidak ada automatic allocation yang dianggap operasional.
- Periksa ID reserved, allocated, dan retired **sebelum** mengalokasikan nomor berikutnya.
- **Jangan** menggunakan ID yang pernah dialokasikan untuk entitas berbeda (non-reusable).
- Jika terjadi duplicate ID, konflik Git, atau ketidakpastian registry, **hentikan** registrasi sampai diselesaikan.
- Standar ini **tidak** membuat registry atau mengalokasikan ID aktual.

### Identifier lifecycle

Status **identifier** terpisah dari project lifecycle, document lifecycle, dan agent lifecycle:

| Status | Makna |
|--------|--------|
| `reserved` | ID dicadangkan; registrasi entitas belum selesai. |
| `allocated` | ID diberikan kepada entitas sah dan tercatat di registry. |
| `retired` | ID tidak aktif; **tidak boleh** digunakan kembali untuk entitas lain. |

- Pertahankan riwayat ID, termasuk reservation yang dibatalkan.
- Pencabutan reservation tidak menghapus jejak historis dari registry.

### Native identifiers (dipertahankan)

Tetap gunakan ID asli sistem untuk:

- Hermes Kanban (native board/task IDs).
- GitHub Issues dan Pull Requests.
- Git commit hashes dan refs.
- Technical ADR numbering/format di GitHub Project Repository sesuai standar proyek.

Hindari organizational ID tambahan jika native ID sudah memadai untuk traceability. Organizational ID dipakai untuk artefak vault, registry, dan catatan governance yang tidak memiliki native ID tunggal.

## Resource Naming

| Jenis resource | Konvensi | Contoh |
|----------------|----------|--------|
| Markdown files (governance/strategis) | Pascal-Case with hyphens | `Project-Registration-Standard.md` |
| Project folders | Pascal-Case | `02-Projects/AI-Office/` |
| Agent profiles | kebab-case | `hermes-default` |
| Skills | kebab-case | `knowledge-sync` |
| Scripts (agent-operational) | kebab-case | `vault-sync.sh` |
| Agent display names | Title Case | `Hermes Default` |
| YAML fields dan nilai status enum | snake_case | `project_status`, `pending_approval` |
| Tags | lowercase-hyphenated | `ai-office`, `governance` |
| Git branches | project-specific | Mengikuti konvensi repo proyek (`main`, `develop`, `feature/...`) |
| Commit messages | Conventional Commits | `docs(governance): ...`, `feat(api): ...` |
| Document versions | `MAJOR.MINOR.PATCH` | Mengikuti [[Document-Lifecycle]] |

Umum:

- **Bahasa**: Deskriptif; istilah teknis Inggris diperbolehkan.
- **Hindari**: spasi pada nama file, tanggal di nama file kecuali artefak sekali pakai di workspace.

**Jangan** melakukan mass rename terhadap resource existing tanpa otorisasi dan rencana migrasi terpisah.

### Naming exceptions

Konvensi penamaan organisasi **tidak** dipaksakan pada kategori berikut:

| Kategori | Contoh / catatan |
|----------|------------------|
| File sistem dan kebijakan inti | `README.md`, `SOUL.md`, `HERMES.md`, `SKILL.md`, dan nama khusus sistem yang telah ditetapkan. |
| Hermes profile (native) | Profile existing termasuk `default` — nama native profil tetap `default`. |
| Identitas author organisasi | `hermes-default` dapat menjadi organizational author identity pada metadata governance; berbeda dari nama profile native. |
| File konfigurasi | Mengikuti konvensi aplikasi atau tool yang bersangkutan. |
| Source code | Mengikuti standar bahasa dan konvensi proyek di GitHub Project Repository. |
| Laporan/snapshot bertanggal | Nama file boleh menyertakan tanggal bila tanggal merupakan bagian identitas artefak. |
| Revision proposal | Menggunakan prefix `proposal_id` pada metadata; lihat bagian Revision Proposal. |

Standar ini **tidak** mengotorisasi rename aktual terhadap resource existing.

## Metadata Standard

### Core document metadata (governance dan shared knowledge)

Selaras [[Document-Lifecycle]] (GOV-004):

| Field | Wajib | Null | Format / makna |
|-------|-------|------|----------------|
| `title` | Ya | — | Judul manusia. |
| `document_id` | Ya (dokumen governance) | — | ID stabil (`GOV-NNN`, dll.). |
| `category` | Ya | — | Mis. `governance`, `project`. |
| `version` | Ya | — | Semver dokumentasi. |
| `status` | Ya | — | Document lifecycle status. |
| `owner` | Ya | — | Document owner; default `owner` untuk fondasi AI Office. |
| `author` | Ya | — | Mis. `hermes-default` jika dibuat agent default. |
| `reviewer` | Tidak | `null` | Reviewer ditugaskan. |
| `approved_by` | Tidak | `null` | Hanya setelah approval sah. |
| `approved_at` | Tidak | `null` | ISO 8601 + timezone setelah approval sah. |
| `created_at` | Ya | — | `YYYY-MM-DD`; tanggal pembuatan awal. |
| `updated_at` | Ya | — | `YYYY-MM-DD`; pembaruan terakhir dokumen. |
| `tags` | Disarankan | — | Array lowercase-hyphenated. |

**Core metadata requirements:**

- Dokumen terkelola yang menggunakan organizational identifier **wajib** memiliki `document_id` di YAML frontmatter.
- Core metadata mengikuti [[Document-Lifecycle]] (GOV-004).
- Untuk dokumen **draft**: `approved_by` dan `approved_at` harus **`null`**.
- Untuk dokumen **approved**: `approved_by` dan `approved_at` **wajib** terisi berdasarkan approval sah.
- `reviewer` mengikuti lifecycle dan otorisasi yang berlaku; reviewer bukan otomatis approver.
- Native resources (issue GitHub, task Kanban, commit) dan temporary working drafts **tidak** dipaksa menggunakan seluruh core metadata.
- Pertahankan context-specific metadata sesuai jenis entitas (lihat tabel di bawah).

### Context-specific metadata

Entity records dapat memiliki field tambahan sesuai jenis; jangan memaksakan seluruh core metadata pada native system resources (issue GitHub, task Kanban, commit):

| Konteks | Field tambahan (contoh) |
|---------|-------------------------|
| Project (`Project-Profile`) | `project_id`, `project_status`, `repository`, `kanban_reference`, `delegation_references` — lihat [[Project-Registration-Standard]]. |
| Agent registry | `agent_id`, `profile_name`, `activation_status`. |
| Delegation | `delegation_id`, `granted_by`, `granted_to`, `valid_from`, `valid_until` (ISO 8601 + timezone untuk validity). |
| Approval | `approval_id`, `decision`, `requested_by`. |
| Research note | `source`, `verification_status`. |
| Workflow / SOP | `workflow_id` / `sop_id`, `version`, `supersedes`. |
| Revision proposal | Lihat bagian Revision Proposal. |

Schema validation otomatis — **Planned**; metadata mengikuti konvensi ini secara manual sampai validasi otomatis terverifikasi.

## Revision Proposal

Usulan revisi dokumen **approved** bukan kebijakan otoritatif. Versi approved sebelumnya tetap berlaku sampai pengganti disetujui ([[Document-Lifecycle]]).

### Metadata proposal

| Field | Wajib | Makna |
|-------|-------|--------|
| `proposal_id` | Ya | Identitas unik proposal (`REV-NNNNNN`); **wajib** dan dicatat pada metadata — nama file bukan pengganti `proposal_id`. |
| `document_type` | Ya | `revision_proposal` |
| `document_id` | Ya | Referensi ke dokumen resmi yang diusulkan direvisi. |
| `base_version` | Ya | Versi approved yang menjadi dasar. |
| `target_version` | Ya | Versi yang dituju setelah approval. |
| `status` | Ya | Mengikuti document lifecycle proposal. |
| `approved_by` / `approved_at` | — | `null` sampai proposal disetujui; setelah approval, terisi sesuai keputusan sah. |

### Penerapan proposal approved

Sebelum menerapkan proposal yang disetujui ke file resmi:

1. Verifikasi `base_version` terhadap versi resmi terakhir dokumen target.
2. Jika baseline berubah sejak proposal disusun, **hentikan** penerapan.
3. Lakukan evaluasi ulang dan approval baru apabila diperlukan.

### Penamaan file proposal

Contoh ilustratif:

```text
REV-000001-AI-Office-Charter.md
```

Lokasi target proposal governance (belum dibuat kecuali diotorisasi):

```text
03-Hermes/Governance/Proposals/
```

Standar ini **tidak** membuat folder `Proposals/` atau file proposal aktual.

## Date & Time Conventions

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

**Delegation records:** field validity (`valid_from`, `valid_until`) menggunakan **ISO 8601 dengan timezone**, selaras timestamp approval.

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

- Lowercase, hyphenated: `ai-office`, `governance`.
- Tambah tag domain: `architecture`, `agents`, `projects`, `naming`, dll.

## Dokumen terkait

- [[Document-Lifecycle]]
- [[Knowledge-Management-Policy]]
- [[Project-Registration-Standard]]
- [[Approval-Policy]]
