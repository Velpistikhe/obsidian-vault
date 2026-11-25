---
title: Agent Access Policy
document_id: GOV-006
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
tags: ['ai-office', 'governance', 'draft', 'agents', 'access']
---

# Agent Access Policy

## Ringkasan

Kebijakan akses resource, command execution, credential handling, dan kontrol lapisan untuk agent AI Office. Dokumen ini adalah sumber utama **resource access policy**; approval dan delegation authority mengikuti [[Approval-Policy]].

Pertahankan **centralized knowledge management** dan **single server-side vault writer** (Hermes default) sampai keputusan Owner lebih lanjut.

**Target operasional** dan **technical enforcement** dibedakan; instruksi governance, SOUL.md, skills, atau dokumen draft bukan bukti isolasi akses teknis.

## Existing versus target access

| Status | Aktor | Ringkasan |
|---|---|---|
| Existing | Owner | Full organizational authority; dapat mengelola vault via Obsidian Desktop yang dikonfigurasi. |
| Existing | Hermes default profile | Server-side vault read/write terotorisasi; satu-satunya vault writer saat ini. |
| Target | Admin Agent | Manage shared KB setelah aktivasi resmi — **Planned**. |
| Target | Project Manager | Scoped project coordination — **Planned**. |
| Target | Specialist Agents | Read shared knowledge; proposal via workspace — **Planned**. |

## Access Control Principles

- **Least privilege** — Akses minimum yang diperlukan untuk tugas.
- **Deny by default** — Tidak ada akses implisit dari role target.
- **Role-based authorization** — Selaras dengan [[Approval-Policy]] dan assignment aktif.
- **Project and resource scope** — Batasi path, branch, dan project.
- **Separation of duties** — Bedakan review, approval, execution, publication.
- **Access revocation** — Dapat dicabut saat assignment/delegasi berakhir atau insiden.
- **No unauthorized privilege escalation** — Agent tidak memperluas permission sendiri.

Bedakan **organizational authority** (kebijakan) dari **technical access** (runtime/tooling).

## Four Control Layers

Seluruh lapisan yang relevan harus terpenuhi sebelum tindakan berisiko:

1. **Governance authorization** — GOV-005/006 dan dokumen approved terkait.
2. **Agent operational instructions** — Skills, workflow (mis. knowledge-sync), task scope.
3. **Tool and command permissions** — Konfigurasi Hermes, profile, command approval — **Pending Verification**.
4. **Technical runtime enforcement** — Filesystem ACL, multi-agent coordination — **Planned** / belum lengkap.

Instruksi governance atau skills **bukan** bukti layer 3–4 aktif.

## Role-Based Resource Access (target matrix)

Legenda: **R** read, **W** write, **X** execute, **M** manage, **S** scoped, **P** proposal only, **—** restricted / not authorized.

| Resource | Owner | Admin Agent (target) | Project Manager (target) | Specialist Agents (target) |
|---|---|---|---|---|
| Shared Obsidian Vault | M | S-W* | R / P publish | R |
| Governance documents | M | S-R / P edit | R | R |
| Agent Registry | M | S-W | R | R |
| Shared Workspace | M | S-W | S-W | S-W |
| GitHub Project Repository | M | S-W | S-W | S-X scoped |
| Git branches (non-protected) | M | S-W | S-W | S-W |
| Git protected/production branches | M | P | P | — |
| Hermes Kanban | M | S-M* | S-W | S-W |
| Own Agent Memory | M | S-W | S-W | S-W |
| Other Agent Memory | M | — | — | — |
| Skills (use) | M | S-X | S-X | S-X assigned |
| Skills (modify) | M | P | — | — |
| Profiles / runtime config | M | P | — | — |
| External tools | M | S-X scoped | S-X scoped | S-X scoped |
| Credentials | M | — | — | — |

\*Setelah aktivasi resmi dan otorisasi vault writer; saat ini publish vault: Hermes default saja.

## Shared Knowledge Access

- Hermes default tetap **satu-satunya authorized server-side vault writer** sampai keputusan Owner lebih lanjut ([[Knowledge-Management-Policy]]).
- Future Admin Agent mengambil tanggung jawab publish/manage hanya setelah aktivasi resmi.
- Future Project Manager dan Specialist Agents: **read** shared knowledge sesuai otorisasi; perubahan melalui **workspace proposal**; **tanpa** direct publish ke vault.
- Owner dapat mengelola vault melalui Obsidian Desktop; bukan bukti runtime enforcement untuk agent lain.

## Workspace and Project Repository

Akses dibatasi oleh project, role, assignment, directory, dan branch.

Target branch strategy (contoh; aktual per proyek):

- `main`, `develop`, feature branches, fix branches.

Protected branches dan merge restrictions harus diimplementasikan dan **diverifikasi terpisah** di masing-masing repository. Tugas ini **tidak** mengubah project Akura atau repository settings.

## Kanban Access

- Future Admin Agent: koordinasi Kanban berdasarkan delegasi (target).
- Project Manager: mengelola task dalam project scope terotorisasi (target).
- Specialist Agents: update task sesuai assignment (target).

Native role permissions dan integrasi Kanban — **Pending Verification** (GOV-002). Jangan anggap telah diverifikasi.

## Agent Memory Isolation

- **Shared Knowledge** (vault) ≠ **Individual Agent Memory** ([[Information-Architecture]]).
- Agent mengakses memory individualnya sendiri sesuai kemampuan/runtime.
- Akses memory agent lain **restricted**; memerlukan kebutuhan dan otorisasi jelas.
- Koordinasi normal melalui task updates, laporan, dan shared knowledge — bukan unrestricted memory access.

Isolasi memory — **Pending Verification**.

## Skills, Profiles, and External Tools

- Agent hanya menggunakan skills/tools **relevan** dengan role dan assignment.
- Perubahan skill, profile, strategic instructions, runtime configuration → [[Approval-Policy]] (Owner / governance path).
- Ketersediaan tool/skill **bukan** otorisasi penggunaan.
- External tools dan transfer data harus sesuai scope dan ketentuan sensitivitas ([[Knowledge-Management-Policy]]).

## Command Execution

Target kebijakan (bukan blanket Always Allow):

| Jenis | Panduan |
|---|---|
| Authorized read-only commands | Diagnosis, listing, read file dalam scope. |
| Scoped file retrieval | Path dalam assignment/project. |
| System date retrieval | Untuk metadata/timestamp aktual. |
| Authorized knowledge synchronization | `vault-sync.sh` pull/publish terotorisasi. |
| Development and test commands | Sesuai assignment; bukan production. |
| Scoped Git modification | Branch non-protected sesuai proyek. |
| Restricted configuration/permission changes | Owner approval; tidak self-service agent. |
| Restricted privileged execution | Explicit approval. |
| Destructive / high-impact operations | Owner approval; assessment risiko. |

Penilaian command mempertimbangkan **arguments, target path, scripts, environment, resource, side effects**. Command tidak aman hanya berdasarkan nama.

Hermes Command Approval dan permission per profile — **Pending Verification**; tidak diubah dalam tugas ini.

## Credential and Secret Handling

- Least-privilege credential access; use hanya untuk pekerjaan terotorisasi.
- Jangan menampilkan raw secret pada response atau execution report.
- Jangan menyalin credential ke vault, workspace draft, agent memory, atau task descriptions.
- Jangan membagikan credential antar-agent tanpa otorisasi dan mekanisme aman.
- Creation, rotation, revocation, permission changes credential → **Owner authorization** ([[Approval-Policy]]).

## Agent-to-Agent Communication

Komunikasi dibatasi oleh role, scope, assignment, dan kebutuhan pekerjaan. Pesan agent lain **bukan** authorization baru tanpa delegasi sah.

## Access Revocation

Penghentian atau pembatasan akses apabila:

- Assignment selesai, delegasi berakhir/dicabut, agent dinonaktifkan.
- Project scope berubah material.
- Insiden keamanan memerlukan pembatasan.

Bedakan **revocation kebijakan** (Owner/delegator) dari **technical revocation** (config/runtime) — yang terakhir Pending Verification/Planned.

## Audit and Execution Logging

Catat secara aman (sanitized):

- Agent identity, task reference, action, resource, authorization reference, timestamp, result, error/blocker.

Jangan menyimpan raw credentials atau raw runtime logs ke shared vault; gunakan ringkasan aman ([[Knowledge-Management-Policy]], [[03-Hermes/Execution-Logs]]).

Retensi log terpusat dan audit implementation — **TBD** / **Planned**.

## Larangan

- Specialist agents (present dan future) **tidak** direct publish ke shared vault.
- Tidak ada agent yang mengubah governance tanpa otorisasi [[Approval-Policy]].
- Tidak ada self-grant permission, blanket terminal Always Allow, atau penyimpanan secret di vault.

## Implementation Status

Selaras baseline [[Information-Architecture]] (GOV-002):

| Komponen | Status | Catatan |
|---|---|---|
| Shared Obsidian vault + GitHub Knowledge Repository | Operational | `vault-sync.sh`, pull/publish terotorisasi. |
| Knowledge Sync Skill | Operational | Pre-task pull; publish eksplisit. |
| Native Obsidian Skill | Operational | Operasi baca/tulis note. |
| Hermes Default Profile | Operational | Setup writer aktif. |
| Hermes Workspace | Available | Scoped kerja; tanpa klaim enforcement otomatis. |
| GitHub Project Repository | Available | SSOT kode; branch policy per repo. |
| Command Approval / profile permissions | Pending Verification | Tidak diuji/diubah dalam tugas ini. |
| Kanban integration | Pending Verification | GOV-002. |
| Individual agent memory isolation | Pending Verification | |
| Runtime/filesystem access enforcement | Planned | Tidak dianggap aktif. |
| Admin Agent activation | Planned | |
| Specialist Agent Profiles | Planned | |
| Multi-agent write coordination | Planned | |
| Automatic secret scanning | Planned | |
| Metadata schema validation | Planned | |

Role-based filesystem enforcement **belum** aktif.

## Future improvements

- Secret scanning pada konten vault.
- Concurrency control multi-writer.
- Enforcement role-based write dan audit trail terpusat.
- Verified Command Approval integration dengan governance matrix.

## Dokumen terkait

- [[Approval-Policy]]
- [[Knowledge-Management-Policy]]
- [[Document-Lifecycle]]
- [[Information-Architecture]]
- [[03-Hermes/Agent-Registry]]
