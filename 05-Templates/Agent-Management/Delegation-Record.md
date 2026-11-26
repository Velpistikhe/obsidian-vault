---
title: Delegation Record
document_id: TPL-013
template_id: TPL-013
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
tags: ['ai-office', 'templates', 'agents', 'delegation']
---
# Delegation Record

## 1. Purpose

Delegation Record mendokumentasikan **authority yang benar-benar didelegasikan** sesuai GOV-005 dan GOV-006.

- `delegation_id` mengikuti `DEL-NNNNNN` (GOV-008) — dialokasikan hanya melalui workflow terotorisasi; template **tidak** menciptakan delegasi aktual.
- `delegation_status` **berbeda** dari `status` dokumen.
- Delegasi hanya berlaku dalam authority pihak yang memberikan.
- **Subdelegation tidak default** — hanya jika eksplisit diotorisasi (GOV-005/006).
- Delegasi organisasional **bukan** technical permission runtime.
- Jika delegasi expired atau revoked, dependent actions harus dihentikan secara aman — **tanpa** mengklaim technical revocation terjadi tanpa execution dan verification evidence.



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

Lokasi SSOT untuk Delegation Record instance **belum ditetapkan** secara eksplisit di vault. Simpan pada lokasi governance yang diotorisasi (contoh rencana: `03-Hermes/Governance/Delegations/`) **hanya setelah** Owner menetapkan atau mengotorisasi struktur folder. Jangan membuat folder Delegations tanpa otorisasi.

## 4. Generated Metadata

Blueprint — **bukan** metadata dokumen siap publikasi. `document_id` instance mengikuti GOV-008, bukan namespace `TPL`. **Jangan** memasukkan identitas, approval, author, atau timestamp master sebagai nilai aktual instance.

```yaml
title: null
document_id: null
document_type: delegation_record
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
# --- konteks delegasi ---
delegation_id: null
delegated_by: null
delegated_to: null
delegation_status: null
authorized_actions: []
authorized_resources: []
scope_constraints: null
valid_from: null
valid_until: null
subdelegation_allowed: null
approval_references: []
revocation_references: []
```

## 5. Required Sections

1. **Delegation Summary**
2. **Delegating Authority**
3. **Delegate Identity**
4. **Authorized Actions**
5. **Authorized Resources**
6. **Scope and Constraints**
7. **Validity and Conditions**
8. **Prohibited Actions**
9. **Subdelegation Rules**
10. **Runtime Permission Boundary**
11. **Revocation and Expiry**
12. **Evidence and Traceability**

## 6. Optional Sections

- **Historical Delegation Chain**
- **Related Approval Records**

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


### Delegation checks

- [ ] `delegation_id` terisi hanya bila benar-benar dialokasikan.
- [ ] `subdelegation_allowed` default `null` atau false semantics — bukan true tanpa keputusan eksplisit.
- [ ] Validity memakai ISO 8601 + timezone (GOV-008).

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
