---
title: Agent Access Policy
document_id: GOV-006
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
tags: ['ai-office', 'governance', 'draft', 'agents', 'access']
---

# Agent Access Policy

## Ringkasan

Model akses terhadap shared knowledge dan kemampuan publish untuk agent di AI Office. **Kebijakan ini mendeskripsikan target operasional; enforcement teknis belum lengkap.**

## Model: centralized knowledge management

| Aktor | Shared vault | Publish ke vault | Catatan |
|-------|--------------|------------------|---------|
| **Owner** | Full authority | Keputusan dan approval | Otoritas akhir |
| **Hermes (default profile)** | Read/write (server-side) | Authorized writer selama fase setup | Satu-satunya writer terotorisasi saat ini |
| **Future Admin Agent** | Manage shared KB | Direncanakan setelah ditetapkan resmi | Belum ada agent ini |
| **Future Specialist Agents** | Read-only shared | Tidak; draft proposal via workspace sahaja | Tidak direct publish ke vault |

## Larangan

- Specialist agents (present dan future) **tidak** melakukan direct publish ke shared vault.
- Tidak ada agent yang mengeksekusi perubahan governance tanpa otorisasi sesuai [[Approval-Policy]].

## Klaim implementasi

Pembatasan di atas **belum** dianggap sepenuhnya diterapkan pada runtime, filesystem ACL, atau multi-agent coordination. Perilaku aktual bergantung konfigurasi Hermes dan disiplin proses.

## Future improvements

- Secret scanning pada konten vault.
- Concurrency control untuk multi-writer.
- Enforcement role-based write dan audit trail terpusat.

## Dokumen terkait

- [[Knowledge-Management-Policy]]
- [[03-Hermes/Agent-Registry]]
- [[Approval-Policy]]
