---
title: Naming Conventions
document_id: GOV-008
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
tags: ['ai-office', 'governance', 'draft', 'naming']
---

# Naming Conventions

## Ringkasan

Konvensi penamaan file, folder, identifier organisasi, metadata, dan tag untuk konsistensi vault AI Office. Organizational ID melengkapi — **tidak menggantikan** — native ID sistem (Kanban, GitHub Issues/PR, Git commits, technical ADR di repo).

Dokumen ini **draft**. Contoh ID ilustratif; bukan alokasi aktual. Mekanisme alokasi terpusat dan pencegahan collision otomatis **belum** dianggap operasional kecuali diverifikasi terpisah.

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

Schema validation otomatis — **Planned**; metadata tetap mengikuti konvensi ini secara manual saat draft/review.

Setiap dokumen governance memuat `document_id` di YAML frontmatter.

## Revision Proposal

Usulan revisi dokumen **approved** bukan kebijakan otoritatif. Versi approved sebelumnya tetap berlaku sampai pengganti disetujui ([[Document-Lifecycle]]).

### Metadata proposal (konseptual)

| Field | Makna |
|-------|--------|
| `proposal_id` | Identitas unik proposal (`REV-NNNNNN` atau setara dalam nama file). |
| `document_type` | `revision_proposal` |
| `document_id` | Referensi ke dokumen resmi yang diusulkan direvisi. |
| `base_version` | Versi approved yang menjadi dasar. |
| `target_version` | Versi yang dituju setelah approval. |
| `status` | Mengikuti document lifecycle proposal (biasanya `draft`). |
| `approved_by` / `approved_at` | `null` sampai proposal disetujui; publikasi final menggantikan file resmi hanya setelah otorisasi. |

### Penamaan file proposal

Contoh ilustratif:

```text
REV-000001-AI-Office-Charter.md
```

Lokasi proposal governance yang diusulkan (belum dibuat dalam revisi ini):

```text
03-Hermes/Governance/Proposals/
```

Tugas revisi GOV-008 **tidak** membuat folder `Proposals/` atau file proposal aktual.

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

- Lowercase, hyphenated: `ai-office`, `governance`, `draft`.
- Tambah tag domain: `architecture`, `agents`, `projects`, dll.

## Dokumen terkait

- [[Document-Lifecycle]]
- [[Knowledge-Management-Policy]]
- [[Project-Registration-Standard]]
- [[Approval-Policy]]
