---
title: Approval Policy
document_id: GOV-005
category: governance
version: 1.0.0
status: approved
owner: owner
author: hermes-default
reviewer: owner
approved_by: owner
approved_at: 2026-11-25T08:35:16+07:00
created_at: 2026-11-24
updated_at: 2026-11-25
tags: ['ai-office', 'governance', 'approval']
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

- **Owner** — Strategic direction, final approval, persetujuan governance, **seluruh perubahan terhadap approved project scope**, aktivasi agent, permission, credential management, komitmen biaya baru, production deployment, dan destructive operations.
- **Admin Agent (target)** — Central orchestrator: delegation, coordination, governance operations, knowledge management oversight, monitoring, reporting. **Belum aktif** tanpa aktivasi eksplisit Owner.
- **Project Manager (target)** — Project planning, milestones, dependencies, progress, dan koordinasi task dalam project scope yang di-assign. **Belum dibentuk**.
- **Specialist Agents (target)** — Eksekusi pekerjaan sesuai role dan assignment; tidak memperluas kewenangan sendiri. **Belum dibentuk**.
- **Hermes default (existing)** — Fungsi setup, draft governance terotorisasi, dan publish vault melalui workflow yang berlaku selama tidak ada keputusan Owner lebih lanjut.

## Agent Autonomy Levels

Tingkat berikut bersifat konseptual dan harus selaras dengan approval matrix serta delegasi aktif (jika ada).

### 1. Autonomous

Membaca informasi terotorisasi, riset, analisis, membuat draft yang diizinkan, read-only diagnostics, dan rekomendasi — **tanpa** mengubah kebijakan, permission, credential, atau environment produksi.

**Autonomous** berarti tidak membutuhkan approval tambahan untuk tindakan yang sudah berada dalam role, assignment, resource access, dan scope yang diizinkan. Autonomous **bukan** unrestricted access. Future roles tetap **belum aktif** sampai ditetapkan Owner.

### 2. Delegated

Task management, agent coordination (setelah multi-agent aktif), code changes, testing, scoped commit/push branch non-protected, dan routine knowledge management — **hanya** jika delegasi atau assignment aktif dan dalam batasannya.

Agent tidak membutuhkan approval berulang untuk tindakan yang sudah tercakup dalam delegasi aktif yang masih berlaku.

### 3. Owner Approval Required

Governance changes, project charter, **seluruh perubahan approved project scope**, perubahan material agent, permission, credential management, komitmen biaya baru, production deployment, destructive operations, dan aktivasi Admin Agent / Specialist Agents.

Agent **tidak boleh** memperluas kewenangannya sendiri atau menganggap draft/target policy sebagai otorisasi aktif.

## Risk Classification

Klasifikasi risiko membantu assessment; **tidak** otomatis memberikan authorization. Perubahan terhadap kebijakan harus mengikuti governance lifecycle dan tidak boleh mengesampingkan pembatasan keamanan yang lebih tinggi.

| Level | Panduan | Contoh indikator |
|---|---|---|
| **Low risk** | Dampak terbatas, reversible, tidak menyentuh production/credential/governance. | Retrieval, draft internal, diagnostics read-only. |
| **Medium risk** | Dampak pada project atau shared knowledge; masih dalam scope assignment/delegasi. | Scoped code/test, draft vault untuk review, branch feature. |
| **High risk** | Tindakan yang **dapat** dilaksanakan setelah persetujuan eksplisit dan memenuhi kontrol keamanan yang berlaku — klasifikasi ini bukan otorisasi. | Production deployment, perubahan permission, rotasi credential, penghapusan data yang secara khusus diotorisasi, perubahan konfigurasi strategis. |
| **Prohibited actions** | Tindakan yang **tidak diperbolehkan** berdasarkan kebijakan dan **tidak dapat dilegalkan** melalui approval task biasa. | Membocorkan credential, menyimpan secret di shared vault, memalsukan approval, self-grant permission, bypass security controls, force push pada GitHub Knowledge Repository. |

Pertimbangkan: scope, impact, reversibility, data sensitivity, resource consumption, dan target environment.

## Approval Matrix

Legenda: **A** = Autonomous (dalam batas role/delegasi); **D** = Delegated (memerlukan delegasi/assignment aktif); **P** = Proposal Only; **N** = Not Authorized.

| Kategori tindakan | Owner | Admin Agent (target) | Project Manager (target) | Specialist Agents (target) | Catatan |
|---|---|---|---|---|---|
| Knowledge retrieval | A | A | A | A | Dalam role, assignment, resource access, dan scope terotorisasi; mengikuti [[Knowledge-Management-Policy]]. |
| Research and analysis | A | A | A | A | Bukan fakta pasti tanpa verifikasi. |
| Draft creation | A | A | A | A | Termasuk draft workspace; bukan approval. |
| Diagnostics (read-only) | A | A | A | A | Tanpa perubahan sistem. |
| Kanban task creation | A | D | D | D | Integrasi Kanban Pending Verification (GOV-002). |
| Task assignment | A | D | D | N | Specialist hanya task yang di-assign. |
| Agent coordination | A | D | P | N | Multi-agent Planned. |
| Project planning | A | D | D | P | Perubahan approved project scope → Owner (lihat bawah). |
| Source code modification | A | D | D | D | Dalam project assignment. |
| Testing | A | D | D | D | Scoped environment. |
| Commit/push development branches | A | D | D | D | Bukan protected/production tanpa aturan proyek + otorisasi. |
| Vault knowledge publication | A / langsung | D* | N | N | *Setelah aktivasi resmi; saat ini hanya Hermes default server-side writer. |
| Routine knowledge approval | A | D | D† | D† | †Hanya dengan delegasi eksplisit. |
| Technical ADR approval (rutin) | A | D | D† | D† | ADR SSOT di GitHub; delegasi proyek belum aktif. |
| Governance approval | A | P | N | N | Hanya Owner sebagai final approver kebijakan organisasi. |
| Project scope changes | A | P | P | N | Seluruh perubahan approved project scope → Owner. |
| Persistent agent creation/activation | A | P | N | N | Termasuk Admin Agent activation. |
| Permission changes | A | P | N | N | Runtime/config terpisah; Owner approval. |
| Credential management | A | N | N | N | Owner only. |
| Production deployment | A | P | P | N | Owner approval untuk deploy produksi. |
| Cost commitments | A | P | N | N | Biaya baru memerlukan Owner. |
| Destructive operations | A | P | P | N | Explicit Owner approval. |

## Approved project scope versus penyesuaian operasional

**Seluruh perubahan terhadap approved project scope** memerlukan Owner approval — bukan hanya perubahan yang dinilai material atau signifikan.

Penyesuaian operasional dalam delegasi/assignment yang masih berlaku (tanpa mengubah scope resmi):

- Menambah task dalam approved scope.
- Mengubah urutan pengerjaan task.
- Memperbaiki detail implementasi.
- Menyesuaikan jadwal internal tanpa mengubah komitmen resmi.

Memerlukan Owner approval:

- Perubahan approved project scope.
- Perubahan project charter.
- Perubahan komitmen biaya.
- Perubahan milestone yang telah menjadi komitmen resmi.

## Pemisahan proposal, review, approval, execution, dan publication

- **Proposal authority** — Mengajukan rencana, draft, atau permintaan keputusan; bukan menyetujui atau mengeksekusi.
- **Review authority** — Mengevaluasi kelengkapan dan kualitas; bukan final approval kecuali secara eksplisit didelegasikan.
- **Approval authority** — Memberikan persetujuan sah yang mengikat scope dan constraints.
- **Execution authority** — Melaksanakan tindakan yang telah disetujui dalam batas approval.
- **Publication authority** — Mempublikasikan artefak sesuai lifecycle; bukan approval authority ([[Document-Lifecycle]]).

Kategori **Proposal Only (P)** berarti agent tidak memiliki kewenangan mandiri untuk menyetujui atau memulai tindakan tersebut.

Setelah Owner memberikan approval eksplisit, **authorized executor** dapat melaksanakan tindakan yang disetujui apabila:

- Tindakan berada dalam scope approval.
- Executor secara eksplisit diotorisasi.
- Resource access tersedia secara sah.
- Seluruh kontrol keamanan terpenuhi.
- Tindakan bukan prohibited action.

Contoh pemisahan approver dan executor (target kebijakan; execution authority tidak aktif dalam environment saat ini):

| Action | Approver | Authorized Executor |
|---|---|---|
| Production deployment | Owner | Authorized DevOps Agent |
| Configuration changes | Owner | Authorized Admin atau DevOps Agent |
| Credential rotation | Owner | Authorized executor melalui mekanisme aman |
| Document archiving | Authorized Approver | Authorized Publisher |
| Persistent agent creation | Owner | Authorized Admin Agent |

Approval terhadap satu tindakan **tidak** memberikan agent kewenangan untuk menyetujui tindakan serupa di masa mendatang.

## Otoritas Owner (wajib persetujuan eksplisit)

- Kebijakan strategis AI Office (governance documents).
- Perubahan material agent (peran, akses, instruksi strategis).
- Project charter dan **seluruh perubahan approved project scope**.
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

Setiap approval material harus dapat ditelusuri dan terikat pada **tindakan, resource, scope, constraints, versi dokumen atau artefak yang relevan**, serta **masa berlaku** jika diperlukan. Gunakan **system clock** aktual (Asia/Jakarta untuk tanggal dokumen; ISO 8601 untuk timestamp).

Catatan minimum:

- Approval reference / request ID (standar ID final mengikuti [[Naming-Conventions]], GOV-008).
- Requested by, approved by, decision (approved/rejected/revise).
- Approved scope, target resource, constraints.
- Timestamp, evidence (metadata, catatan persetujuan, referensi Git jika relevan).
- Validity period jika berlaku.

Apabila tindakan berubah secara material setelah approval:

- Lakukan assessment ulang.
- Jika perubahan melampaui approval awal, **hentikan** tindakan terkait.
- Dapatkan approval baru sebelum melanjutkan.

Riwayat delegasi yang **expired** atau **revoked** harus dipertahankan. Catatan delegasi historis **tidak boleh** dihapus atau ditimpa sehingga riwayat kewenangan hilang. Catat alasan pencabutan, pihak yang mencabut, dan timestamp aktual jika relevan.

Agent tidak boleh memberikan approval atas perluasan kewenangan sendiri. Tugas ini **tidak** mengaktifkan delegasi baru.

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
