---
title: Information Architecture
document_id: GOV-002
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
tags: ['ai-office', 'governance', 'draft', 'architecture']
---

# Information Architecture

## Ringkasan

Pemetaan **single source of truth (SSOT)** untuk AI Office. Setiap sistem memiliki tanggung jawab informasi yang berbeda dan sumber otoritatif yang jelas. Ringkasan, metadata, indeks, tautan, serta referensi lintas sistem diperbolehkan; hindari beberapa versi independen yang sama-sama dianggap otoritatif.

## SSOT per sistem

| Sistem | Konten otoritatif | Tidak untuk |
|--------|-------------------|-------------|
| **Obsidian Vault** | Governance, business requirements, project management docs, shared knowledge, agent registry, workflows organisasi | Source code, migration SQL, secret |
| **GitHub Knowledge Repository** | Version control bagi shared Obsidian vault; governance draft dapat dipublikasikan untuk review | Source code proyek sebagai SSOT |
| **GitHub Project Repository** | Source code, technical architecture detail, technical ADR, API specification, database migrations, build/deployment | Governance draft sebagai SSOT |
| **Hermes Workspace** | Draft dokumen, project checkout, working files, generated artifacts sementara | SSOT jangka panjang tanpa publish |
| **Hermes Kanban** | Task assignment, status, priority, dependency, blockers | Dokumen kebijakan |
| **Agent Memory** | Konteks dan pengalaman individual agent | Kebijakan shared atau audit resmi |
| **Hermes Skills** | Prosedur operasional terautomasi yang dapat dieksekusi ulang | Narrative governance panjang |
| **Hermes Profiles** | Identity aktif, instruksi runtime, konfigurasi sesi | Registry organisasi resmi (lihat [[03-Hermes/Agent-Registry]]) |

## Synchronization Architecture

### Current implementation

| Komponen | Kondisi dan bukti |
|----------|--------------------|
| Obsidian Desktop automatic commit, push, dan pull | Dilaporkan sebagai operational dan diuji pada environment AI Office. |
| Hermes `knowledge-sync` skill | Operational: prosedur mewajibkan pre-task pull dan publish pascatugas yang diotorisasi. |
| Native Obsidian skill | Available untuk operasi baca/tulis note pada vault. |
| `vault-sync.sh` | Operational: pre-task pull telah berhasil; publish pascatugas menggunakan daftar file eksplisit. |
| Obsidian Vault ↔ GitHub Knowledge Repository | Bidirectional synchronization operational; pull terbaru berhasil dan publikasi terdahulu terverifikasi. |

### Future improvements

Hal berikut tidak dianggap sudah diimplementasikan:

- Sinkronisasi lintas sistem antara Project Repository dan Knowledge Base, apabila diperlukan.
- Validasi schema metadata otomatis.
- Secret scanning otomatis.
- Koordinasi write multi-agent.
- Enforcement akses pada runtime.

## Implementation Status

Status menggambarkan bukti yang tersedia, bukan target arsitektur. **Operational** berarti workflow atau fungsi telah digunakan dan diverifikasi; **Available** berarti kemampuan/tooling tersedia tanpa klaim integrasi penuh; **Pending Verification** berarti keadaan aktual belum diuji; **Planned** berarti future improvement.

| Komponen/kemampuan | Status | Catatan |
|--------------------|--------|---------|
| Shared Obsidian vault dan repository knowledge | Operational | Pull/publish melalui `vault-sync.sh` telah digunakan; sinkronisasi GitHub Knowledge Repository aktif. |
| Obsidian Desktop automatic commit, push, dan pull | Operational | Dilaporkan telah diuji pada environment AI Office. |
| Hermes knowledge-sync dan native Obsidian skills | Available | Prosedur dan kemampuan operasi tersedia; sinkronisasi dilakukan sesuai workflow. |
| Hermes Workspace | Available | Lokasi kerja yang ditetapkan; integrasi otomatis lintas sistem tidak diasumsikan. |
| GitHub Project Repository | Available | SSOT yang ditetapkan untuk kode dan dokumentasi engineering proyek. |
| Kanban integration | Pending Verification | Status integrasi aktual belum diverifikasi. |
| Individual agent memory isolation | Pending Verification | Isolasi dan konfigurasi aktual belum diverifikasi. |
| Specialist Agent Profiles | Pending Verification | Tidak diasumsikan tersedia atau telah diuji. |
| Cross-system Project Repository ↔ Knowledge Base sync | Planned | Dapat dipertimbangkan bila dibutuhkan. |
| Automatic schema validation, secret scanning, multi-agent write coordination, runtime access enforcement | Planned | Belum dinyatakan operasional. |

## Information Flow

Sistem-sistem memiliki tanggung jawab informasi berbeda. Alur berikut bersifat konseptual; referensi dan ringkasan lintas sistem diperbolehkan, tetapi satu jenis informasi tetap memiliki satu sumber otoritatif.

```text
Workspace (draft/working files) → Obsidian Vault (shared knowledge dan governance draft)
Obsidian Vault ↔ GitHub Knowledge Repository (version control dan sinkronisasi vault)
GitHub Project Repository (kode dan engineering detail) ↔ referensi/ringkasan di Obsidian
Kanban (task, status, dependency) → koordinasi pekerjaan; bukan SSOT dokumen kebijakan
Agent Memory (konteks individual) → kontribusi kerja; bukan shared knowledge atau audit resmi
Skills (prosedur reusable) → pelaksanaan workflow; Profiles (identitas/instruksi runtime) → konfigurasi agent
```

## Aturan integrasi

- Proyek baru didaftarkan di vault sesuai [[Project-Registration-Standard]] sebelum dokumentasi substantif menyebar.
- Knowledge publish ke vault mengikuti skill knowledge-sync dan [[Knowledge-Management-Policy]].
- Penamaan file dan ID mengikuti [[Naming-Conventions]].

## Dokumen terkait

- [[AI-Office-Charter]]
- [[Knowledge-Management-Policy]]
- [[Project-Registration-Standard]]
