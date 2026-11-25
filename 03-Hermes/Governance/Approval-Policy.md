---
title: Approval Policy
document_id: GOV-005
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
tags: ['ai-office', 'governance', 'draft', 'approval']
---

# Approval Policy

## Ringkasan

Menetapkan organizational authority, tingkat agent autonomy, klasifikasi risiko, approval matrix, delegation, bukti persetujuan, dan emergency escalation untuk AI Office. Owner tetap otoritas akhir untuk keputusan strategis dan berdampak besar.

Dokumen ini adalah sumber utama **approval dan delegation authority**. Detail akses resource mengikuti [[Agent-Access-Policy]]. Lifecycle dan pemisahan publikasi/approval mengikuti [[Document-Lifecycle]].

Tidak ada future role, delegasi, atau kewenangan yang dianggap **aktif** hanya karena disebutkan di dokumen ini.

## Existing authority versus target authority

| Status | Peran / kondisi | Keterangan |
|---|---|---|
| **Existing (aktif)** | Owner | Strategic authority dan final approval; berlaku operasional. |
| **Existing (aktif)** | Hermes default | Menjalankan tugas setup terotorisasi; satu-satunya authorized server-side vault writer saat ini (lihat [[Agent-Access-Policy]], GOV-003). |
| **Target (belum aktif)** | Admin Agent | Central orchestrator dan delegated operational authority setelah aktivasi resmi Owner. |
| **Target (belum aktif)** | Project Manager | Project-level planning, scheduling, task coordination berdasarkan assignment. |
| **Target (belum aktif)** | Specialist Agents | Execution authority berdasarkan role, kompetensi, dan authorized assignment. |

## Organizational Authority

- **Owner** — Strategic direction, final approval, persetujuan governance, perubahan scope material, aktivasi agent, permission, credential management, komitmen biaya baru, production deployment, dan destructive operations.
- **Admin Agent (target)** — Central orchestrator: delegation, coordination, governance operations, knowledge management oversight, monitoring, reporting. **Belum aktif** tanpa aktivasi eksplisit Owner.
- **Project Manager (target)** — Project planning, milestones, dependencies, progress, dan koordinasi task dalam project scope yang di-assign. **Belum dibentuk**.
- **Specialist Agents (target)** — Eksekusi pekerjaan sesuai role dan assignment; tidak memperluas kewenangan sendiri. **Belum dibentuk**.
- **Hermes default (existing)** — Fungsi setup, draft governance terotorisasi, dan publish vault melalui workflow yang berlaku selama tidak ada keputusan Owner lebih lanjut.

## Agent Autonomy Levels

Tingkat berikut bersifat konseptual dan harus selaras dengan approval matrix serta delegasi aktif (jika ada).

### 1. Autonomous

Membaca informasi terotorisasi, riset, analisis, membuat draft yang diizinkan, read-only diagnostics, dan rekomendasi — **tanpa** mengubah kebijakan, permission, credential, atau environment produksi.

### 2. Delegated

Task management, agent coordination (setelah multi-agent aktif), code changes, testing, scoped commit/push branch non-protected, dan routine knowledge management — **hanya** jika delegasi atau assignment aktif dan dalam batasannya.

Agent tidak membutuhkan approval berulang untuk tindakan yang sudah tercakup dalam delegasi aktif yang masih berlaku.

### 3. Owner Approval Required

Governance changes, project charter dan perubahan scope material, perubahan material agent, permission, credential management, komitmen biaya baru, production deployment, destructive operations, dan aktivasi Admin Agent / Specialist Agents.

Agent **tidak boleh** memperluas kewenangannya sendiri atau menganggap draft/target policy sebagai otorisasi aktif.

## Risk Classification

Klasifikasi risiko membantu assessment; **tidak** otomatis memberikan authorization. Tindakan **prohibited** tetap terlarang meskipun diklasifikasikan atau diajukan untuk approval.

| Level | Panduan | Contoh indikator |
|---|---|---|
| **Low risk** | Dampak terbatas, reversible, tidak menyentuh production/credential/governance. | Retrieval, draft internal, diagnostics read-only. |
| **Medium risk** | Dampak pada project atau shared knowledge; masih dalam scope assignment/delegasi. | Scoped code/test, draft vault untuk review, branch feature. |
| **High risk** | Dampak luas pada security, biaya, scope strategis, atau data sensitif. | Governance, permission, credential, production deploy, destructive ops. |
| **Prohibited actions** | Selalu terlarang tanpa otorisasi eksplisit yang sah dan mekanisme aman. | Menyimpan secret di vault, force push, bypass approval, self-grant permission, unrestricted credential sharing. |

Pertimbangkan: scope, impact, reversibility, data sensitivity, resource consumption, dan target environment.

## Approval Matrix

Legenda: **A** = Autonomous (dalam batas role/delegasi); **D** = Delegated (memerlukan delegasi/assignment aktif); **P** = Proposal Only; **N** = Not Authorized.

| Kategori tindakan | Owner | Admin Agent (target) | Project Manager (target) | Specialist Agents (target) | Catatan |
|---|---|---|---|---|---|
| Knowledge retrieval | A | D | D | A | Substantif mengikuti [[Knowledge-Management-Policy]]. |
| Research and analysis | A | D | D | A | Bukan fakta pasti tanpa verifikasi. |
| Draft creation | A | D | D | A | Termasuk draft workspace; bukan approval. |
| Diagnostics (read-only) | A | D | D | A | Tanpa perubahan sistem. |
| Kanban task creation | A | D | D | D | Integrasi Kanban Pending Verification (GOV-002). |
| Task assignment | A | D | D | N | Specialist hanya task yang di-assign. |
| Agent coordination | A | D | P | N | Multi-agent Planned. |
| Project planning | A | D | D | P | Scope material → Owner. |
| Source code modification | A | D | D | D | Dalam project assignment. |
| Testing | A | D | D | D | Scoped environment. |
| Commit/push development branches | A | D | D | D | Bukan protected/production tanpa aturan proyek + otorisasi. |
| Vault knowledge publication | A / langsung | D* | N | N | *Setelah aktivasi resmi; saat ini hanya Hermes default server-side writer. |
| Routine knowledge approval | A | D | D† | D† | †Hanya dengan delegasi eksplisit. |
| Technical ADR approval (rutin) | A | D | D† | D† | ADR SSOT di GitHub; delegasi proyek belum aktif. |
| Governance approval | A | P | N | N | Hanya Owner sebagai final approver kebijakan organisasi. |
| Project scope changes | A | P | P | N | Material → Owner. |
| Persistent agent creation/activation | A | P | N | N | Termasuk Admin Agent activation. |
| Permission changes | A | P | N | N | Runtime/config terpisah; Owner approval. |
| Credential management | A | N | N | N | Owner only. |
| Production deployment | A | P | P | N | Owner approval untuk deploy produksi. |
| Cost commitments | A | P | N | N | Biaya baru memerlukan Owner. |
| Destructive operations | A | P | P | N | Explicit Owner approval. |

Hak **review**, **approval**, **execution**, dan **publication** harus dibedakan. Publisher tidak memperoleh approval authority hanya karena akses tulis ([[Document-Lifecycle]]).

## Otoritas Owner (wajib persetujuan eksplisit)

- Kebijakan strategis AI Office (governance documents).
- Perubahan material agent (peran, akses, instruksi strategis).
- Project charter dan perubahan scope proyek signifikan.
- Keputusan dengan dampak luas pada knowledge base, keamanan, atau operasi.
- Aktivasi Admin Agent, Specialist Agents, delegasi baru, permission, credential, production deployment, dan destructive operations.

## Alur persetujuan kebijakan

Mengikuti [[Document-Lifecycle]]: `draft` → `in_review` → `pending_approval` → `approved`. Pending tetap pending sampai keputusan; rejection/revisi kembali ke `draft` dengan alasan tercatat.

1. Author menyiapkan dokumen.
2. Reviewer mengevaluasi (`reviewer` pada metadata) — bukan approver otomatis.
3. Owner atau authorized approver memberi persetujuan sah (`approved_by`, `approved_at`).

Delegasi review atau approval ke role lain — **proposed/TBD** kecuali Owner menetapkan secara eksplisit dan mencatat delegasi.

## Draft di Git

Publish untuk review diperbolehkan tanpa status approved ([[Document-Lifecycle]]). Publikasi bukan approval.

## Technical ADR Approval

Technical ADR detail berada pada **GitHub Project Repository** sebagai SSOT ([[Information-Architecture]]).

- ADR rutin proyek dapat disetujui oleh **authorized technical reviewer** berdasarkan delegasi proyek — **delegasi belum aktif** kecuali ditetapkan Owner.
- Perubahan arsitektur yang berdampak material terhadap scope, biaya, keamanan, infrastruktur, atau strategic direction memerlukan **Owner approval**.
- Ringkasan keputusan organisasi di vault mengikuti lifecycle governance jika bersifat kebijakan organisasi.

## Delegation Management

Delegasi harus diberikan oleh pihak berwenang, dapat ditelusuri, memiliki batas, dan dapat dicabut. Perubahan assignment **tidak** memperluas permission secara otomatis.

Jenis delegasi:

- Task-based, project-based, role-based, time-based.
- Mencakup: scope, allowed actions, resource boundaries, constraints, validity, revocation, sub-delegation.

**Sub-delegation** hanya jika secara eksplisit diizinkan dan tidak melebihi delegasi asal.

Tugas ini **tidak** memberikan delegasi aktif. Contoh record konseptual (proposed):

```yaml
delegation_id: TBD
delegation_status: proposed
granted_by: owner
granted_to: TBD-role-or-agent
delegation_type: project-based
scope: TBD-project
allowed_actions:
  - draft-creation
  - scoped-testing
constraints:
  - no-vault-publish
  - no-production
valid_from: null
valid_until: null
revocable: true
sub_delegation_allowed: false
approval_reference: null
```

Standar ID final delegasi mengikuti review [[Naming-Conventions]] (GOV-008).

## Approval Evidence and Traceability

Setiap approval material harus dapat ditelusuri dan terikat pada tindakan, resource, dan versi dokumen yang relevan. Gunakan **system clock** aktual (Asia/Jakarta untuk tanggal dokumen; ISO 8601 untuk timestamp).

Catatan minimum:

- Approval reference / request ID.
- Requested by, approved by, decision (approved/rejected/revise).
- Approved scope, target resource, constraints.
- Timestamp, evidence (metadata, catatan persetujuan, referensi Git jika relevan).
- Validity period jika berlaku.

Jika terjadi perubahan material setelah approval, lakukan assessment ulang sebelum eksekusi lanjutan.

Agent tidak boleh memberikan approval atas perluasan kewenangan sendiri.

## Emergency Escalation dan stop conditions

Hentikan tindakan terdampak secara aman dan laporkan status, dampak, blocker, serta rekomendasi apabila:

- Scope atau authority tidak jelas.
- Delegasi habis masa berlaku atau dicabut.
- Tindakan melampaui authorization.
- Risiko kehilangan data.
- Unexpected production access.
- Konflik atau indikasi kebocoran kredensial.
- Owner memerintahkan penghentian.

Emergency stop terpusat pada runtime **belum diimplementasikan**; prosedur ini adalah kebijakan organisasi yang mengandalkan eskalasi manual dan penghentian aman oleh pelaksana.

## Dokumen terkait

- [[AI-Office-Charter]]
- [[Document-Lifecycle]]
- [[Agent-Access-Policy]]
- [[Knowledge-Management-Policy]]
- [[Information-Architecture]]
