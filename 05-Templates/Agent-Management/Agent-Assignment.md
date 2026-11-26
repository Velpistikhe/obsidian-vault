---
title: Agent Assignment
document_id: TPL-012
template_id: TPL-012
document_type: template
category: agent-management
version: "0.1.0"
status: draft
owner: owner
author: hermes-default
reviewer: null
approved_by: null
approved_at: null
created_at: 2026-11-26
updated_at: 2026-11-26
tags: ['ai-office', 'templates', 'agents', 'assignment']
---
# Agent Assignment

## 1. Purpose

Agent Assignment mendokumentasikan **penugasan pekerjaan** kepada agent tanpa memberikan kewenangan tambahan secara otomatis.

Mengikuti GOV-005 dan GOV-006.

- **Task assignment ≠ delegation.** Assignment mencatat penugasan; delegasi memerlukan Delegation Record terpisah bila authority diperlukan.
- **Proposed assignment ≠ authorized assignment ≠ actual completion.**
- Penugasan hanya dapat dijalankan dalam batas authority dan runtime permission yang **benar-benar berlaku**.
- Operational task SSOT adalah **Hermes Kanban** setelah integrasi diverifikasi (GOV-002 — **Pending Verification**). Jangan mengklaim Kanban sudah operational.
- GOV-008 **belum** menetapkan namespace ID khusus assignment; **jangan** mengalokasikan identifier baru untuk instance assignment.



### Batasan governance (berlaku untuk master dan instance)

- Organizational Owner tetap strategic authority.
- **Admin Agent belum diaktifkan** (GOV-002 — Planned).
- Default Hermes saat ini adalah setup actor yang terotorisasi.
- Target role matrix di policy **bukan** active delegation.
- Assignment **tidak** otomatis memberikan delegasi.
- Delegasi **tidak** otomatis memberikan technical permission runtime.
- Approval **tidak** otomatis memberikan execution authority.
- Dokumentasi **tidak** otomatis mengubah runtime.
- Entri registry **tidak** otomatis berarti aktivasi agent.
- Supporting evidence **tidak** membuktikan autentikasi identitas independen.


## 2. Usage Instructions

1. Baca master sesuai **Gate 1 — Master Template** pada bagian 7.
2. Ekstrak **Generated Metadata blueprint** (bagian 4), **Required Sections** (bagian 5), dan **applicable optional sections** (bagian 6) yang memang relevan. **Jangan** menyalin seluruh isi master ke instance.
3. Isi metadata dan konten instance dari **fakta aktual** — jangan membawa frontmatter master, approval master, Usage Instructions, atau Validation Checklist internal.
4. Isi `author` dengan **pembuat aktual instance**, `source_template_id` dengan **ID master yang benar-benar digunakan**, `source_template_version` dengan **versi master yang benar-benar digunakan**, serta `created_at` dan `updated_at` dengan **tanggal aktual** (GOV-008).
5. Isi approval metadata (`reviewer`, `approved_by`, `approved_at`) **hanya** bila terdapat keputusan sah sesuai kewenangan; biarkan `null` bila belum ada (GOV-004, GOV-005).
6. Validasi instance terhadap **Gate 2 — Generated Document** pada bagian 7, lalu simpan pada Target SSOT.

**Jangan** mengubah master ini saat menghasilkan instance. **Jangan** mewariskan approval, author, identifier, atau timestamp master ke instance.


## 3. Target SSOT

Lokasi vault untuk assignment record **belum ditetapkan** secara eksplisit. Simpan instance pada path yang diotorisasi per proyek atau agent, misalnya di bawah `02-Projects/{Project-Name}/` atau `03-Hermes/Agent-Registry/{Agent-Name}/`, setelah Owner menetapkan SSOT.

**Operational task SSOT (target):** Hermes Kanban — integrasi berstatus Pending Verification (GOV-002). Assignment vault adalah dokumentasi organisasional, bukan live task board.

## 4. Generated Metadata

Blueprint — **bukan** metadata dokumen siap publikasi. `document_id` instance mengikuti GOV-008, bukan namespace `TPL`. **Jangan** memasukkan identitas, approval, author, atau timestamp master sebagai nilai aktual instance.

```yaml
title: null
document_id: null
document_type: agent_assignment
category: agent-management
version: "0.1.0"
status: draft
owner: null
author: null
reviewer: null
approved_by: null
approved_at: null
created_at: null
updated_at: null
tags: []
source_template_id: null
source_template_version: null
# --- konteks assignment ---
agent_id: null
project_id: null
task_reference: null
assigned_by: null
assignment_status: null
delegation_references: []
approval_references: []
assigned_at: null
due_at: null
```

## 5. Required Sections

1. **Assignment Summary**
2. **Assigned Agent and Assigning Authority**
3. **Objective**
4. **Task Scope**
5. **Out of Scope**
6. **Input References**
7. **Deliverables**
8. **Acceptance Criteria**
9. **Dependencies and Constraints**
10. **Required Authority and Delegation**
11. **Reporting and Escalation**
12. **Completion Evidence (kondisional sesuai tahap)**

## 6. Optional Sections

- **Related Assignments**
- **Follow-up Actions**

## 7. Validation Checklist

Manual sebelum publikasi instance. Pemeriksaan ad-hoc — **bukan** automated governance validation.

### Gate 1 — Master Template

- [ ] Master `approved` → penggunaan resmi.
- [ ] Master `draft` → hanya untuk review atau simulasi terotorisasi.
- [ ] Master `archived` → hanya referensi historis, bukan penggunaan resmi baru.

### Gate 2 — Generated Document

- [ ] `draft` — boleh belum lengkap, dengan penjelasan pada bagian yang belum terisi.
- [ ] `in_review` — memenuhi persyaratan review.
- [ ] `pending_approval` — memenuhi persyaratan pengajuan keputusan.
- [ ] `approved` — metadata lengkap dan approval sah sesuai kewenangan.
- [ ] `archived` — pengarsipan terotorisasi.

### Provenance dan metadata

- [ ] `author` = pembuat aktual instance.
- [ ] `created_at` dan `updated_at` = tanggal aktual (Asia/Jakarta; GOV-008).
- [ ] `source_template_id` = ID master yang benar-benar digunakan.
- [ ] `source_template_version` = versi master yang benar-benar digunakan.
- [ ] Approval metadata hanya terisi atas keputusan sah.
- [ ] Field entity/operational tidak tertukar dengan `status` dokumen (GOV-004).
- [ ] Tidak ada kredensial atau raw secret.


### Assignment checks

- [ ] `assignment_status` tidak tertukar dengan `status` dokumen.
- [ ] Completion Evidence diisi hanya bila completion benar-benar terjadi atau tahap relevan dicapai.
- [ ] Tidak ada klaim delegasi hanya dari assignment.

## 8. Governance References

- [[03-Hermes/Governance/Agent-Access-Policy|Agent Access Policy]] (GOV-006)
- [[03-Hermes/Governance/Approval-Policy|Approval Policy]] (GOV-005)
- [[03-Hermes/Governance/Document-Lifecycle|Document Lifecycle]] (GOV-004)
- [[03-Hermes/Governance/Information-Architecture|Information Architecture]] (GOV-002)
- [[03-Hermes/Governance/Naming-Conventions|Naming Conventions]] (GOV-008)
- [[03-Hermes/Governance/Knowledge-Management-Policy|Knowledge Management Policy]] (GOV-003)
- [[03-Hermes/Governance/Authorization-Evidence/README|Authorization Evidence]]
- [[05-Templates/Template-Standard|Template Standard]]

## Dokumen terkait

- [[05-Templates/Template-Registry|Template Registry]] — alokasi identifier master
- [[03-Hermes/Governance/Authorization-Evidence/Template-Phase-3-Authorization|Template Phase 3 Authorization]] — bukti otorisasi pembuatan draft master; path eksplisit: `03-Hermes/Governance/Authorization-Evidence/Template-Phase-3-Authorization.md`
