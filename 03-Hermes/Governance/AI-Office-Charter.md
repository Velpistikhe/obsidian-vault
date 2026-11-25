---
title: AI Office Charter
document_id: GOV-001
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
tags: ['ai-office', 'governance', 'draft']
---

# AI Office Charter

## Ringkasan

Dokumen ini mendefinisikan tujuan, ruang lingkup, dan prinsip AI Office sebagai lingkungan kolaborasi manusia–agent dengan knowledge base terpusat.

## Vision

Membangun lingkungan kerja berbasis AI Agent yang terorganisasi, kolaboratif, terukur, dan berkelanjutan untuk mendukung pengelolaan proyek, pengembangan perangkat lunak, penelitian, dokumentasi, serta otomasi pekerjaan di bawah pengawasan Owner.

## Tujuan

- Menyelaraskan pekerjaan teknis, dokumentasi, dan operasi agent.
- Menetapkan Owner sebagai otoritas akhir untuk keputusan strategis dan scope proyek.
- Mencegah duplikasi pengetahuan melalui arsitektur informasi yang jelas ([[Information-Architecture]]).

## Ruang lingkup

AI Office meliputi:

- Shared Obsidian vault (organizational knowledge dan governance).
- Hermes Agent (eksekusi tugas, skills, profiles, memory per agent).
- Repository proyek per aplikasi (kode dan dokumentasi teknis detail).
- Hermes Kanban dan workspace untuk draft serta artefak kerja.

Di luar ruang lingkup charter ini: kebijakan hukum perusahaan, klasifikasi data enterprise, dan enforcement akses filesystem — ditandai **TBD/proposed** hingga disetujui Owner. Struktur dan peran agent di bawah ini menjelaskan target organisasi; tidak menyatakan bahwa Admin Agent, Project Manager, atau Specialist Agents telah dibentuk.

## Prinsip

1. **Single source of truth** — Setiap jenis informasi punya lokasi otoritatif (lihat [[Information-Architecture]]).
2. **Referensi, bukan salinan** — Dokumen saling menaut (wikilink), tidak mengulang kebijakan penuh.
3. **Draft dapat direview** — Publish Git untuk review tidak sama dengan persetujuan kebijakan ([[Document-Lifecycle]]).
4. **Keamanan pengetahuan** — Tidak ada secret di vault ([[Knowledge-Management-Policy]]).
5. **Otoritas jelas** — Owner menyetujui kebijakan strategis, perubahan agent material, project charter, dan keputusan berdampak besar ([[Approval-Policy]]).

## Organizational Structure

Target hierarchy AI Office:

```text
Owner → Admin Agent → Project Manager dan Specialist Agents
```

Struktur organisasi bersifat extensible sesuai kebutuhan. Hierarchy ini adalah target architecture dan tidak menyatakan bahwa peran agent selain Hermes default telah diaktifkan.

## Roles and Responsibilities

| Peran | Tanggung jawab |
|-------|----------------|
| Owner | Strategic direction, final authority, policy approval, dan project scope approval. |
| Admin Agent | Central orchestrator: delegation, coordination, governance, knowledge management, monitoring, dan reporting. Peran ini belum aktif sampai disetujui Owner. |
| Project Manager | Project planning, scope, milestones, dependencies, dan progress management sesuai assignment. |
| Specialist Agents | Eksekusi berdasarkan role, kompetensi, dan authorized assignment. Tidak dianggap sudah dibentuk. |
| Hermes Default | Menjalankan fungsi setup hingga secara resmi ditetapkan sebagai Admin Agent; tetap satu-satunya authorized server-side vault writer sampai ada keputusan lebih lanjut. |

## Agent Autonomy Principles

Tingkatan berikut bersifat konseptual; rincian authorization matrix mengikuti [[Approval-Policy]] dan [[Agent-Access-Policy]].

1. **Autonomous** — Membaca, menganalisis, melakukan riset, dan membuat draft yang diizinkan.
2. **Delegated** — Menjalankan pekerjaan berdasarkan kewenangan dan assignment yang diberikan.
3. **Owner Approval** — Memerlukan persetujuan Owner untuk perubahan strategis, scope, kebijakan, permission, destructive operations, dan komitmen biaya baru.

## Office Development Phases

1. **Setup & Foundation** — Menyiapkan fondasi, governance draft, knowledge base, dan proses kerja. Hermes default menjalankan fungsi setup.
2. **Admin Agent Activation** — Aktivasi Admin Agent hanya setelah Owner secara eksplisit menyetujui aktivasi, tanggung jawab, dan batas kewenangannya. Setup phase berakhir pada persetujuan eksplisit tersebut.
3. **Multi-Agent Operations** — Operasi Project Manager dan Specialist Agents sesuai kebutuhan, role, assignment, dan otorisasi yang ditentukan.

Fase 2 dan 3 adalah target, bukan klaim bahwa agent telah dibentuk atau diaktifkan. Hermes default tetap satu-satunya authorized server-side vault writer sampai terdapat keputusan lebih lanjut.

## Agent Contributors

Kontributor manusia dan agent lain dapat menyiapkan draft, proposal, atau implementasi sesuai kebijakan akses ([[Agent-Access-Policy]]); keberadaan peran target tidak dengan sendirinya memberikan akses atau kewenangan.

## Dokumen terkait

- [[Information-Architecture]]
- [[Knowledge-Management-Policy]]
- [[Approval-Policy]]
