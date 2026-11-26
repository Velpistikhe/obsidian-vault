---
title: Agent Profile
document_id: TPL-011
template_id: TPL-011
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
tags: ['ai-office', 'templates', 'agents', 'profile']
---
# Agent Profile

## 1. Purpose

Agent Profile mendokumentasikan **identitas organisasional dan tanggung jawab** agent yang terdaftar.

Mengikuti [[03-Hermes/Governance/Naming-Conventions|Naming Conventions]] (GOV-008) dan [[03-Hermes/Governance/Agent-Access-Policy|Agent Access Policy]] (GOV-006).

- **Organizational Agent Profile ≠ Hermes runtime profile.** Profile vault adalah dokumentasi registrasi organisasional; konfigurasi runtime berada di Hermes Profiles (GOV-002).
- Pembuatan atau pembaruan profile **tidak** membuat, mengaktifkan, atau mengubah runtime agent.
- `status` (document lifecycle) **berbeda** dari `agent_status` (operational/registration context) dan dari `activation_status` bila digunakan.
- `agent_id` mengikuti pola `AGT-NNN` — **hanya** melalui workflow alokasi terotorisasi; template ini tidak mengalokasikan ID.
- Agent Registry (`03-Hermes/Agent-Registry/`) menyimpan identity index organisasional; registry entry **tidak** otomatis berarti aktivasi.
- **Intended role** (dokumentasi) harus dibedakan dari **actual runtime capabilities** yang diverifikasi terpisah.



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

`03-Hermes/Agent-Registry/{Agent-Name}/Agent-Profile.md`

**Pending location decision:** konvensi nama folder `{Agent-Name}` dan struktur lengkap Agent Registry belum ditetapkan secara eksplisit sebagai SSOT final. Jangan membuat folder registry atau actual profile instance tanpa otorisasi Owner. Simpan instance hanya setelah lokasi ditetapkan atau diotorisasi per registrasi.

## 4. Generated Metadata

Blueprint — **bukan** metadata dokumen siap publikasi. `document_id` instance mengikuti GOV-008, bukan namespace `TPL`. **Jangan** memasukkan identitas, approval, author, atau timestamp master sebagai nilai aktual instance.

```yaml
title: null
document_id: null
document_type: agent_profile
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
# --- konteks agent ---
agent_id: null
agent_name: null
role: null
agent_status: null
runtime_profile_reference: null
supervisor_reference: null
assigned_project_references: []
delegation_references: []
approval_references: []
```

## 5. Required Sections

1. **Agent Identity**
2. **Role and Responsibilities**
3. **Organizational Reporting**
4. **Operating Scope**
5. **Authority and Delegation References**
6. **Resource and Access Boundaries**
7. **Runtime Profile Reference**
8. **Skills and Capability References**
9. **Memory Isolation Requirements**
10. **Activation Readiness**
11. **Approval and Change History**

## 6. Optional Sections

- **Related Documents**
- **Runtime Configuration Change Log**
- **Risk and Compliance Notes**

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


### Agent Profile checks

- [ ] `agent_id` hanya terisi bila benar-benar dialokasikan (`AGT-NNN`).
- [ ] `agent_status` tidak tertukar dengan `status` dokumen.
- [ ] Tidak ada klaim permission, delegasi, atau aktivasi tanpa bukti.
- [ ] `runtime_profile_reference` merujuk konfigurasi runtime yang benar-benar ada — bukan placeholder operasional.

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
