---
title: Approval Policy
document_id: GOV-005
category: governance
version: 0.1.0
status: draft
owner: owner
author: hermes-default
reviewer: null
approved_by: null
approved_at: null
created_at: 2025-11-24
updated_at: 2025-11-24
tags: ['ai-office', 'governance', 'draft', 'approval']
---

# Approval Policy

## Ringkasan

Menetapkan siapa dapat menyetujui apa, dengan Owner sebagai otoritas akhir untuk keputusan berdampak besar.

## Otoritas Owner (wajib persetujuan eksplisit)

- Kebijakan strategis AI Office (governance documents).
- Perubahan material agent (peran, akses, instruksi strategis).
- Project charter dan perubahan scope proyek signifikan.
- Keputusan dengan dampak luas pada knowledge base, keamanan, atau operasi.

## Alur persetujuan kebijakan

1. Author menyiapkan dokumen (status **Draft**).
2. Review internal → **In Review** (`reviewer` diisi pada metadata).
3. Owner evaluation → **Pending Approval** → **Approved** (`approved_by`, `approved_at` diisi).

Delegasi review ke role lain — **proposed/TBD** kecuali Owner menetapkan secara eksplisit.

## Draft di Git

Publish untuk review diperbolehkan tanpa status Approved ([[Document-Lifecycle]]).

## Dokumen proyek dan teknis

- Ringkasan keputusan di vault: ikuti lifecycle yang sama jika bersifat kebijakan organisasi.
- ADR teknis detail: SSOT di repository GitHub; approval tim teknis proyek — skema formal **TBD** di tingkat AI Office.

## Dokumen terkait

- [[AI-Office-Charter]]
- [[Document-Lifecycle]]
- [[Agent-Access-Policy]]
