---
title: AI Office Charter
document_id: GOV-001
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
tags: ['ai-office', 'governance', 'draft']
---

# AI Office Charter

## Ringkasan

Dokumen ini mendefinisikan tujuan, ruang lingkup, dan prinsip AI Office sebagai lingkungan kolaborasi manusia–agent dengan knowledge base terpusat.

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

Di luar ruang lingkup charter ini: kebijakan hukum perusahaan, klasifikasi data enterprise, dan enforcement akses filesystem — ditandai **TBD/proposed** hingga disetujui Owner.

## Prinsip

1. **Single source of truth** — Setiap jenis informasi punya lokasi otoritatif (lihat [[Information-Architecture]]).
2. **Referensi, bukan salinan** — Dokumen saling menaut (wikilink), tidak mengulang kebijakan penuh.
3. **Draft dapat direview** — Publish Git untuk review tidak sama dengan persetujuan kebijakan ([[Document-Lifecycle]]).
4. **Keamanan pengetahuan** — Tidak ada secret di vault ([[Knowledge-Management-Policy]]).
5. **Otoritas jelas** — Owner menyetujui kebijakan strategis, perubahan agent material, project charter, dan keputusan berdampak besar ([[Approval-Policy]]).

## Peran (ringkas)

| Peran | Tanggung jawab utama |
|-------|------------------------|
| Owner | Persetujuan kebijakan, scope proyek, agent strategis |
| Hermes (default) | Penulis vault server-side selama fase setup; eksekusi tugas terotorisasi |
| Kontributor (manusia/agent) | Draft, proposal, implementasi sesuai kebijakan akses ([[Agent-Access-Policy]]) |

## Dokumen terkait

- [[Information-Architecture]]
- [[Knowledge-Management-Policy]]
- [[Approval-Policy]]
