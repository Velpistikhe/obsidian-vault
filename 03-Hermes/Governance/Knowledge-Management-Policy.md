---
title: Knowledge Management Policy
document_id: GOV-003
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
tags: ['ai-office', 'governance', 'draft', 'knowledge']
---

# Knowledge Management Policy

## Ringkasan

Kebijakan pengelolaan pengetahuan bersama AI Office dengan model **centralized knowledge management**.

## Model terpusat

- Vault Obsidian adalah basis pengetahuan organisasi untuk konten non-kode yang disetujui atau sedang direview.
- Hermes default adalah satu-satunya **authorized server-side vault writer** selama tahap setup (lihat [[Agent-Access-Policy]]).
- Agent specialist di masa depan: akses baca shared knowledge; proposal draft melalui workspace — **tanpa** direct publish ke vault.

## Apa yang disimpan di vault

- Governance dan SOP yang disetujui atau dalam review.
- Dokumentasi proyek tingkat organisasi (charter, status, keputusan bisnis).
- Pengetahuan teknis terverifikasi yang reusable (folder `01-Knowledge-Base`).
- Registry agent dan workflows (lihat [[Information-Architecture]]).

## Apa yang tidak disimpan di vault

- Password, API key, token, private key, atau kredensial apa pun.
- Log mentah runtime (gunakan ringkasan di [[03-Hermes/Execution-Logs]]).
- Salinan penuh spesifikasi teknis yang SSOT-nya di GitHub.

## Praktik wajib

1. Baca nota existing sebelum membuat nota baru (`HERMES.md`).
2. Gunakan wikilink; hindari duplikasi ([[Naming-Conventions]]).
3. Publish vault hanya melalui `vault-sync.sh` dengan daftar file eksplisit.
4. Status **draft** boleh di Git untuk review — bukan persetujuan ([[Document-Lifecycle]]).

## Future improvements (belum tersedia)

- Secret scanning otomatis pada commit vault.
- Concurrency control multi-writer.
- Enforcement teknis role-based write pada filesystem.

Catatan: kebijakan **retensi** dan **klasifikasi data** organisasi — **TBD**; memerlukan persetujuan Owner sebelum ditetapkan.

## Dokumen terkait

- [[Agent-Access-Policy]]
- [[Document-Lifecycle]]
- [[Approval-Policy]]
