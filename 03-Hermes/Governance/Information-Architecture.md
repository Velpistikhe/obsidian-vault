---
title: Information Architecture
document_id: GOV-002
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
tags: ['ai-office', 'governance', 'draft', 'architecture']
---

# Information Architecture

## Ringkasan

Pemetaan **single source of truth (SSOT)** untuk AI Office. Setiap sistem punya tanggung jawab eksklusif; lintas sistem menggunakan tautan, bukan duplikasi.

## SSOT per sistem

| Sistem | Konten otoritatif | Tidak untuk |
|--------|-------------------|-------------|
| **Obsidian Vault** | Governance, business requirements, project management docs, shared knowledge, agent registry, workflows organisasi | Source code, migration SQL, secret |
| **GitHub Project Repository** | Source code, technical architecture detail, technical ADR, API specification, database migrations, build/deployment | Kebijakan organisasi draft tanpa review |
| **Hermes Workspace** | Draft dokumen, project checkout, working files, generated artifacts sementara | SSOT jangka panjang tanpa publish |
| **Hermes Kanban** | Task assignment, status, priority, dependency, blockers | Dokumen kebijakan |
| **Agent Memory** | Konteks dan pengalaman individual agent | Kebijakan shared atau audit resmi |
| **Hermes Skills** | Prosedur operasional terautomasi yang dapat dieksekusi ulang | Narrative governance panjang |
| **Hermes Profiles** | Identity aktif, instruksi runtime, konfigurasi sesi | Registry organisasi resmi (lihat [[03-Hermes/Agent-Registry]]) |

## Aliran informasi (konseptual)

```
Draft (Workspace) → Review (Vault, status draft/in review) → Approved (Vault)
Kode/Tech detail (GitHub) ← referensi ← Ringkasan (Vault/Projects)
```

## Aturan integrasi

- Proyek baru didaftarkan di vault sesuai [[Project-Registration-Standard]] sebelum dokumentasi substantif menyebar.
- Knowledge publish ke vault mengikuti skill knowledge-sync dan [[Knowledge-Management-Policy]].
- Penamaan file dan ID mengikuti [[Naming-Conventions]].

## Batasan yang belum diimplementasikan

Sinkronisasi otomatis GitHub ↔ Vault, validasi schema metadata, dan enforcement path — **future improvement**; tidak diasumsikan aktif di runtime saat ini.

## Dokumen terkait

- [[AI-Office-Charter]]
- [[Knowledge-Management-Policy]]
- [[Project-Registration-Standard]]
