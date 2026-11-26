---
title: Agent Onboarding Checklist
document_id: TPL-017
template_id: TPL-017
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
tags: ['ai-office', 'templates', 'agents', 'onboarding']
---
# Agent Onboarding Checklist

## 1. Purpose

Agent Onboarding Checklist memverifikasi **kesiapan sebelum aktivasi** — bukan bukti aktivasi agent.

- **Checklist lengkap ≠ agent aktif.** Activation membutuhkan keputusan Owner dan runtime readiness yang diverifikasi.
- Outcome checklist (`Planned`, `Pending verification`, `Verified`, `Failed`, `Not applicable`) adalah **label hasil**, bukan governance lifecycle baru.
- Jangan mengklaim memory isolation, runtime enforcement, multi-agent coordination, atau Kanban integration **operational** (GOV-002 — Pending Verification / Planned).


### Reusable checklist matrix

Gunakan matriks berikut pada instance (local `Check reference` — bukan organizational ID baru):

| Check reference | Requirement | Result | Evidence | Blocker | Responsible party |
|-----------------|-------------|--------|----------|---------|-------------------|
| (contoh ilustratif) | (contoh ilustratif) | Planned | null | null | null |

**Result** yang didukung sebagai label outcome: `Planned`, `Pending verification`, `Verified`, `Failed`, `Not applicable` (dengan alasan pada kolom Blocker atau catatan).

Contoh di atas **hanya ilustrasi** — jangan terbawa sebagai hasil aktual.


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

Simpan instance pada lokasi agent yang diotorisasi, misalnya `03-Hermes/Agent-Registry/{Agent-Name}/Agent-Onboarding-Checklist.md` — **pending** keputusan SSOT final.

## 4. Generated Metadata

Blueprint — **bukan** metadata dokumen siap publikasi. `document_id` instance mengikuti GOV-008, bukan namespace `TPL`. **Jangan** memasukkan identitas, approval, author, atau timestamp master sebagai nilai aktual instance.

```yaml
title: null
document_id: null
document_type: agent_onboarding_checklist
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
# --- konteks onboarding ---
agent_id: null
runtime_profile_reference: null
onboarding_status: null
readiness_status: null
checked_at: null
approval_references: []
evidence_references: []
```

## 5. Required Sections

1. **Agent Identity Verification**
2. **Approved Role and Responsibility**
3. **Runtime Profile Readiness**
4. **Model and Provider Readiness**
5. **Knowledge Base Access**
6. **Workspace Access**
7. **Memory Isolation**
8. **Skills Readiness**
9. **Tool and Resource Boundaries**
10. **Delegation and Approval Readiness**
11. **Security and Secret Handling**
12. **Operational Testing**
13. **Readiness Findings and Blockers**
14. **Activation Decision Reference**

## 6. Optional Sections

- **Remediation Plan**
- **Post-activation Follow-up**

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


### Onboarding checks

- [ ] Checklist tidak disamakan dengan aktivasi agent.
- [ ] Activation Decision Reference hanya merujuk keputusan yang benar-benar ada.
- [ ] Tidak mengklaim integrasi atau enforcement operational tanpa bukti.

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
