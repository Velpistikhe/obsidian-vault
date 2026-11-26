---
title: Agent Change Request
document_id: TPL-016
template_id: TPL-016
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
tags: ['ai-office', 'templates', 'agents', 'change-request']
---
# Agent Change Request

## 1. Purpose

Agent Change Request mendokumentasikan **usulan perubahan** terhadap agent tanpa melakukan perubahan runtime secara otomatis.

- Perubahan dapat mencakup role, profile configuration, skills, tool access, resource boundaries, atau operational instructions.
- **Tidak** memberikan permission untuk menerapkan perubahan.
- Perubahan governance, approved agent documents, atau authority mengikuti **Revision Proposal** ([[05-Templates/Knowledge-Management/Revision-Proposal|Revision Proposal]] — TPL-010) bila berlaku.
- **TPL-010 restriction:** official revision proposal hanya untuk target dengan organizational ID; GOV-008 path-based revision improvement masih pending — **jangan** menghindari governance revision requirements melalui change request.
- `change_status` **berbeda** dari `status` dokumen dan dari `implementation_status` pelaksanaan.



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

Simpan instance pada lokasi agent atau governance yang diotorisasi, misalnya di bawah `03-Hermes/Agent-Registry/{Agent-Name}/` — **pending** keputusan SSOT. Jangan menerapkan perubahan runtime dari vault.

## 4. Generated Metadata

Blueprint — **bukan** metadata dokumen siap publikasi. `document_id` instance mengikuti GOV-008, bukan namespace `TPL`. **Jangan** memasukkan identitas, approval, author, atau timestamp master sebagai nilai aktual instance.

```yaml
title: null
document_id: null
document_type: agent_change_request
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
# --- konteks change ---
agent_id: null
requested_by: null
change_status: null
target_resource_reference: null
baseline_reference: null
approval_references: []
implementation_references: []
implementation_status: null
```

## 5. Required Sections

1. **Change Summary**
2. **Target Agent and Baseline**
3. **Background and Justification**
4. **Proposed Changes**
5. **Authority and Access Impact**
6. **Runtime Configuration Impact**
7. **Memory and Knowledge Impact**
8. **Risks and Mitigation**
9. **Implementation Plan**
10. **Validation and Rollback Plan**
11. **Review Findings (kondisional)**
12. **Approval Decision (kondisional)**
13. **Linked Execution Evidence (kondisional)**

## 6. Optional Sections

- **Alternative Options**
- **Related Revision Proposals**

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


### Change request checks

- [ ] Perubahan pada approved governance tidak dilakukan melalui change request saja — gunakan TPL-010 bila berlaku.
- [ ] `implementation_status` tidak disimpulkan dari approval dokumen.
- [ ] Linked Execution Evidence hanya bila pelaksanaan benar-benar terjadi.

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
