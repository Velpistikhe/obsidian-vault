---
title: Knowledge Management Policy
document_id: GOV-003
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
tags: ['ai-office', 'governance', 'draft', 'knowledge']
---

# Knowledge Management Policy

## Ringkasan

Kebijakan pengelolaan pengetahuan bersama AI Office dengan model **centralized knowledge management**. GOV-002 menetapkan sumber otoritatif per jenis informasi; dokumen ini mengatur bagaimana pengetahuan diperoleh, divalidasi, dipublikasikan, dan dipelihara.

## Model terpusat dan otoritas

- Shared Obsidian Vault adalah knowledge base organisasi untuk konten non-kode yang disetujui atau sedang direview; GitHub Knowledge Repository menjadi version control dan sarana sinkronisasinya (lihat [[Information-Architecture]]).
- Hermes default tetap satu-satunya **authorized server-side vault writer** sampai ada keputusan Owner lebih lanjut (lihat [[Agent-Access-Policy]]).
- Future Admin Agent hanya mengambil tanggung jawab tersebut setelah aktivasi resmi oleh Owner. Aktivasi belum diberikan oleh dokumen ini.
- Future Specialist Agents dapat mengakses shared knowledge sesuai otorisasi dan mengajukan draft/proposal melalui workspace, tanpa direct publish ke vault.
- Owner dapat mengelola vault melalui mekanisme Obsidian Desktop yang telah dikonfigurasi. Aturan otorisasi ini tidak dengan sendirinya membuktikan adanya runtime access enforcement.

## Knowledge Classification dan SSOT

Klasifikasi berikut mengelompokkan informasi berdasarkan fungsi, bukan tingkat kerahasiaan. Lokasi otoritatif mengikuti [[Information-Architecture]]:

| Kategori | Cakupan | Lokasi SSOT |
|---|---|---|
| Organizational Knowledge | Governance, keputusan organisasi, workflows dan registry bersama | Obsidian Vault; version control di GitHub Knowledge Repository |
| Project Knowledge | Project charter, project scope, business requirements, business decisions, project status reports, dan historical milestone reports | Obsidian Vault: project charter, project scope, business requirements, business decisions, project status reports, dan historical milestone reports. GitHub Project Repository tetap SSOT untuk dokumentasi engineering dan source code sesuai GOV-002. Obsidian dapat menyimpan laporan perkembangan sebagai snapshot bertanggal dengan sumber yang jelas; bukan sumber otoritatif live task status. |
| Reusable Technical Knowledge | Solusi teknis terverifikasi yang berguna lintas tugas/proyek | Obsidian Vault, termasuk `01-Knowledge-Base`; kode tetap di repositori proyek yang relevan |
| Research Knowledge | Temuan, sintesis, dan referensi riset | Obsidian Vault, termasuk `04-Research`, dengan sumber/provenance |
| Individual Knowledge | Konteks dan pengalaman milik satu agent | Agent Memory individual; bukan shared knowledge atau audit resmi |
| Temporary Working Information | Draft sementara, working files, generated artifacts | Hermes Workspace; bukan SSOT jangka panjang tanpa publish |
| Operational Task Information | Task assignment, current task status, task progress, priority, dependencies, blockers | Target SSOT: Hermes Kanban. Integrasi Kanban tetap Pending Verification menurut GOV-002; jangan anggap integrasi telah diverifikasi. |

Klasifikasi ini tidak menetapkan klasifikasi kerahasiaan enterprise atau masa retensi. Keduanya **TBD** dan memerlukan keputusan Owner.

## Knowledge Acquisition

Simpan pengetahuan bila memenuhi satu atau lebih kebutuhan berikut: verified technical knowledge, reusable solutions, approved decisions, relevant research, useful project documentation, atau operational procedures. Jangan menyimpan setiap percakapan atau hasil pekerjaan secara otomatis.

Jika relevan, catat sumber/provenance, referensi, tanggal pemeriksaan, dan tingkat verifikasi. Bedakan secara eksplisit fakta terverifikasi, asumsi, dan hipotesis; jangan menyajikan asumsi atau hipotesis sebagai fakta.

## Knowledge Retrieval

Untuk pekerjaan substantif AI Office:

1. Jalankan pre-task synchronization melalui workflow knowledge-sync.
2. Baca `HERMES.md` dan instruksi operasional yang relevan.
3. Cari knowledge yang relevan sebelum membuat catatan baru.
4. Periksa sumber otoritatif sesuai GOV-002, termasuk versi dan statusnya.
5. Hindari duplikasi serta penggunaan dokumentasi yang diketahui usang atau telah digantikan.
6. Gunakan knowledge-sync dan native Obsidian skill sesuai instruksi operasional.

Apabila pre-task synchronization gagal, hentikan pekerjaan yang bergantung pada Shared Knowledge Base dan laporkan kendalanya. Pekerjaan yang tidak bergantung pada vault hanya dapat dilanjutkan apabila aman, tidak melanggar instruksi operasional, dan tetap berada dalam scope yang diotorisasi. Jangan menggunakan knowledge yang mungkin sudah usang sebagai dasar keputusan tanpa menjelaskan keterbatasannya.

Sinkronisasi dan retrieval ini tidak diwajibkan untuk percakapan umum yang tidak terkait pekerjaan AI Office.

## Knowledge Validation

Sebelum publikasi, validasi:

- Accuracy dan relevance.
- Source/provenance dan verification status.
- Potensi duplikasi serta kesesuaian dengan SSOT.
- Informasi sensitif.
- Status dokumen dan metadata yang relevan.
- Otorisasi perubahan dan publikasi.

Knowledge yang belum diverifikasi tidak boleh disajikan sebagai fakta pasti; nyatakan ketidakpastian dan batas bukti.

## Knowledge Publication

Workflow umum:

```text
Synchronize → Retrieve → Execute → Extract → Classify → Draft → Validate → Review → Publish → Maintain
```

- Pertahankan centralized knowledge management dan satu sumber otoritatif untuk tiap jenis informasi.
- Publikasi draft ke GitHub Knowledge Repository dapat dilakukan untuk review yang diotorisasi; publikasi bukan approval kebijakan.
- Publikasi oleh agent dilakukan melalui `vault-sync.sh` dengan daftar file eksplisit, sesuai workflow knowledge-sync.
- Owner dapat mengelola vault melalui mekanisme Obsidian Desktop yang telah dikonfigurasi.
- Hermes default tetap satu-satunya authorized server-side vault writer sampai keputusan Owner lebih lanjut. Future Admin Agent mengambil tanggung jawab itu hanya setelah aktivasi resmi.
- Future Specialist Agents menggunakan workspace untuk draft/proposal dan tidak melakukan direct publish ke shared vault.

## Knowledge Approval

- Strategic knowledge dan governance yang menetapkan kebijakan organisasi memerlukan Owner approval.
- Project charter dan perubahan scope proyek memerlukan Owner approval sesuai [[Approval-Policy]].
- Operational dan technical knowledge dapat diproses berdasarkan delegasi yang secara eksplisit disetujui; tidak ada delegasi yang diasumsikan aktif tanpa persetujuan Owner.
- Temporary drafts untuk kerja internal tidak memerlukan formal policy approval, tetapi tidak boleh ditampilkan sebagai kebijakan yang disetujui.
- Detail otoritas mengikuti [[Approval-Policy]] dan [[Agent-Access-Policy]]. Dokumen ini tidak menduplikasi authorization matrix.

## Knowledge Maintenance

Pihak yang berwenang memelihara knowledge bertanggung jawab mengenali informasi yang usang, memperbaiki informasi yang terbukti salah, dan mengusulkan arsip sesuai kewenangan serta lifecycle dokumen. Pertahankan sumber/jejak perubahan yang relevan dan jangan menghapus atau menimpa informasi tanpa otorisasi.

Jadwal review dan masa retensi belum ditetapkan (**TBD**, memerlukan persetujuan Owner). Pengarsipan mengikuti [[Document-Lifecycle]]; penghapusan memerlukan otorisasi.

## Conflict Resolution

Untuk konflik antar informasi:

1. Periksa SSOT yang ditetapkan GOV-002.
2. Periksa versi/status, sumber, tanggal, dan bukti pendukung.
3. Jangan sajikan klaim yang belum terselesaikan sebagai fakta.
4. Eskalasi konflik yang membutuhkan keputusan kepada Owner atau pihak berwenang; catat ketidakpastian sampai terselesaikan.

Untuk konflik Git/sinkronisasi: hentikan operasi sinkronisasi yang gagal; jangan force push, membuang perubahan yang belum disimpan, atau menimpa conflicting edits. Laporkan konflik kepada pihak berwenang dan lanjutkan hanya setelah resolusi aman.

## Security and Implementation Limitations

Jangan menyimpan password, API key, token, private key, kredensial lain, atau raw execution logs di vault. Otorisasi atas informasi yang sensitivitasnya belum jelas tidak menghapus larangan penyimpanan kredensial. Jika agent tidak dapat memastikan suatu informasi aman untuk Shared Knowledge Base, jangan publikasikan sampai memperoleh klarifikasi atau otorisasi dari pihak berwenang. Klasifikasi kerahasiaan enterprise dan kebijakan retensi tetap **TBD**. Gunakan ringkasan yang aman sesuai kebutuhan dan [[03-Hermes/Execution-Logs]].

Bedakan:

- **Governance policy:** aturan dan kewenangan yang ditetapkan dokumen berstatus sesuai lifecycle.
- **Operational instructions:** langkah workflow, termasuk knowledge-sync dan `vault-sync.sh`.
- **Technical enforcement:** kontrol runtime/filesystem yang secara terpisah harus diimplementasikan dan diverifikasi.

Instruksi agent atau authorized-writer policy tidak membuktikan enforcement teknis. Automatic secret scanning, metadata validation, full-cycle write coordination, dan runtime access enforcement belum diimplementasikan. Status operasional sinkronisasi vault mengikuti GOV-002.

## Dokumen terkait

- [[Information-Architecture]]
- [[Agent-Access-Policy]]
- [[Document-Lifecycle]]
- [[Approval-Policy]]
- [[Naming-Conventions]]
