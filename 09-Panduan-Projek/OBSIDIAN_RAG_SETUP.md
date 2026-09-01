# OBSIDIAN RAG SETUP â€” PANDUAN LENGKAP AI AGENT MEMORY SYSTEM
> Versi: 1.0 | Terakhir diperbarui: [TANGGAL]
> Vault: `C:\Users\p\Documents\Obsidian Vault`
> AGY Memory Root: `C:\Users\p\Documents\Obsidian Vault\00-AGY-Memory`

---

## FILOSOFI SISTEM INI

Obsidian Vault berfungsi sebagai **long-term memory + knowledge base** untuk semua AI agent (Antigravity, Claude, OpenCode, Codex).
Setiap sesi kerja, agent **wajib baca dulu** konteks proyek dari vault sebelum menyentuh kode.
Vault adalah **single source of truth** â€” lebih dipercaya dari ingatan agent atau asumsi.

---

## BAGIAN 1: STRUKTUR FOLDER IDEAL

```
C:\Users\p\Documents\Obsidian Vault\
â”‚
â”œâ”€â”€ 00-AGY-Memory/                    â† MEMORI AI AGENT (UTAMA)
â”‚   â”œâ”€â”€ INDEX.md                      â† Pintu masuk utama â€” daftar semua proyek & path
â”‚   â”œâ”€â”€ GLOBAL_SYSTEM_RULES.md        â† Rules global lintas semua proyek (single source of truth)
â”‚   â”œâ”€â”€ MASTER-PROMPT-LARAVEL-PERFORMANCE.md
â”‚   â”‚
â”‚   â”œâ”€â”€ General-AGY-Sessions/         â† Log sesi umum (tidak terkait 1 proyek)
â”‚   â”‚   â”œâ”€â”€ CONTEXT.md
â”‚   â”‚   â””â”€â”€ Sessions/
â”‚   â”‚
â”‚   â””â”€â”€ <NamaProyek>/                 â† 1 folder per proyek
â”‚       â”œâ”€â”€ CONTEXT.md                â† Konteks proyek (wajib ada)
â”‚       â”œâ”€â”€ DESIGN.md                 â† Desain sistem / arsitektur (opsional)
â”‚       â”œâ”€â”€ SCHEMA.md                 â† Skema database (opsional, jika kompleks)
â”‚       â””â”€â”€ Sessions/                 â† Log per sesi kerja
â”‚           â”œâ”€â”€ Sesi-01_YYYY-MM-DD_<hash>.md
â”‚           â””â”€â”€ Sesi-02_YYYY-MM-DD_<hash>.md
â”‚
â”œâ”€â”€ 00-Credential/                    â† Credential & secrets (JANGAN simpan plaintext password)
â”‚   â””â”€â”€ <NamaLayanan>.md
â”‚
â”œâ”€â”€ 01-Dokumen/                       â† Dokumen proyek (PRD, spesifikasi, notulen)
â”œâ”€â”€ 09-Panduan-Projek/                â† SOP & panduan teknis
â”‚   â”œâ”€â”€ ATURAN_DATABASE_SAFETY_GLOBAL.md
â”‚   â”œâ”€â”€ MASTER-PROMPT-LARAVEL-PERFORMANCE.md
â”‚   â”œâ”€â”€ MASTER_SETUP.md
â”‚   â””â”€â”€ PRD-MASTER-TEMPLATE.md
â”‚
â”œâ”€â”€ 10-Modul-Ajar/                    â† Modul pendidikan / materi ajar
â”œâ”€â”€ Assets/                           â† Gambar, logo, aset visual
â”œâ”€â”€ Excalidraw/                       â† Diagram & wireframe
â”‚
â”œâ”€â”€ GEMINI.md                         â† Rules khusus Gemini/Antigravity (dibaca otomatis)
â””â”€â”€ HOME.md                           â† Halaman utama vault (navigasi manual)
```

### Naming Convention Folder Proyek

| Kondisi | Format | Contoh |
|---|---|---|
| Nama pendek, satu kata | PascalCase | `POS`, `UNBL`, `Inventory` |
| Nama multi-kata | PascalCase atau kebab-case | `JBR-Minpo`, `SkillVillage` |
| Nama dengan versi | Nama + suffix | `POS-2`, `undangan-digital` |
| **Hindari** | Spasi di nama folder | ~~`Undangan Digital`~~ â†’ `undangan-digital` |

> **Aturan:** Jangan buat 2 folder untuk proyek yang sama. Merge jika ada duplikat.

---

## BAGIAN 2: FILE INDEX.md (SOLUSI MCP SEARCH TERBATAS)

> **Masalah:** MCP Obsidian `search_notes` tidak bisa full-text search isi file.
> **Solusi:** Buat `INDEX.md` sebagai direktori manual â€” AI agent baca ini dulu di awal sesi.

**Path:** `00-AGY-Memory/INDEX.md`

```markdown
# INDEX â€” AGY Memory Projects

> AI Agent: Baca file ini di AWAL SETIAP SESI untuk menemukan proyek yang sedang dikerjakan.

## Cara Pakai
1. Temukan proyek di tabel bawah
2. Baca CONTEXT.md-nya via path yang tersedia
3. Baca Sessions terbaru untuk sambung konteks

## Daftar Proyek Aktif

| Proyek | Domain | Stack | Path CONTEXT | Status |
|---|---|---|---|---|
| JBR-Minpo | Marketplace | Laravel + React | `00-AGY-Memory/JBR-Minpo/CONTEXT.md` | Aktif |
| POS | Retail | Laravel + Vue | `00-AGY-Memory/POS/CONTEXT.md` | Aktif |
| SkillVillage | EdTech | Laravel + Inertia | `00-AGY-Memory/SkillVillage/CONTEXT.md` | Aktif |
| Velora_id-P | Fashion | Laravel + Next.js | `00-AGY-Memory/Velora_id-P/CONTEXT.md` | Aktif |
| ... | ... | ... | ... | ... |

## Proyek Non-Aktif / Arsip
| Proyek | Keterangan |
|---|---|
| santrix-archive | Diarsipkan 2026-07 |
```

---

## BAGIAN 3: FORMAT CONTEXT.md STANDAR

**Path:** `00-AGY-Memory/<NamaProyek>/CONTEXT.md`

```markdown
---
project: <NamaProyek>
domain: <Domain bisnis>
status: aktif | staging | arsip
last_updated: YYYY-MM-DD
agent_rules: GLOBAL_SYSTEM_RULES.md
---

# CONTEXT: <NamaProyek>

## Deskripsi Singkat
<!-- 2-3 kalimat tentang apa proyek ini dan tujuannya -->

## Tech Stack
- **Backend:** Laravel 11 / Go / dst
- **Frontend:** React + Inertia / Next.js / Vue / dst
- **Database:** PostgreSQL 16 / MySQL 8
- **Package Manager:** pnpm (WAJIB)
- **Cache/Queue:** Redis
- **Deployment:** VPS / Vercel / dst

## Struktur Direktori Proyek
```
/
â”œâ”€â”€ app/
â”œâ”€â”€ resources/
â”œâ”€â”€ database/
â””â”€â”€ ...
```

## Database â€” Tabel Utama
| Tabel | Keterangan |
|---|---|
| `users` | Data pengguna |
| `products` | Data produk |
| ... | ... |

## Aturan Khusus Proyek Ini
<!-- Rules tambahan di luar GLOBAL_SYSTEM_RULES.md -->
- ...

## Environment
- **Repo:** https://github.com/...
- **Staging URL:** https://staging.xxx.com
- **Production URL:** https://xxx.com
- **Database Host:** localhost / IP VPS

## Tim
| Nama | Role |
|---|---|
| [Nama Kamu] | Project Owner / Developer |

## Status Proyek Saat Ini
<!-- Update ini setiap sesi selesai -->
- **Fase:** Development / Testing / Production
- **Sprint/Milestone aktif:** ...
- **Blocker:** ...

## Sesi Terbaru
<!-- AI Agent: update link ini setiap akhir sesi -->
- [[00-AGY-Memory/<NamaProyek>/Sessions/Sesi-XX_YYYY-MM-DD_<hash>]]
```

---

## BAGIAN 4: FORMAT SESSIONS LOG STANDAR

**Nama file:** `Sesi-<nomor>_<YYYY-MM-DD>_<6char-hash>.md`

Contoh: `Sesi-03_[TANGGAL]_a3f91c.md`

```markdown
---
sesi: 03
tanggal: [TANGGAL]
proyek: <NamaProyek>
agent: Antigravity IDE (Claude Sonnet)
durasi_estimasi: ~2 jam
---

# Sesi-03 â€” <Judul Singkat Pekerjaan>

## Konteks Awal
<!-- Apa kondisi proyek saat sesi dimulai? Sambung dari mana? -->

## Yang Dikerjakan
- [ ] Task 1
- [x] Task 2 â€” selesai
- [x] Task 3 â€” selesai

## File yang Diubah
| File | Perubahan |
|---|---|
| `app/Models/User.php` | Tambah relasi hasMany orders |
| `database/migrations/xxx.php` | Migrasi kolom baru |

## Keputusan Teknis
<!-- Catat keputusan penting yang diambil di sesi ini dan alasannya -->
- Pilih Redis over Memcached karena: ...

## Masalah & Solusi
<!-- Bug/error yang ditemukan dan cara fix-nya -->

## Next Step (Sesi Berikutnya)
- [ ] ...
- [ ] ...

## Catatan Penting untuk Agent Selanjutnya
<!-- Hal yang WAJIB diketahui agent di sesi berikutnya -->
```

---

## BAGIAN 5: GLOBAL_SYSTEM_RULES.md â€” SINGLE SOURCE OF TRUTH

**Path:** `00-AGY-Memory/GLOBAL_SYSTEM_RULES.md`

> Ini adalah file rules utama. Semua AI agent **wajib baca** file ini.
> File `C:\Users\p\.gemini\config\rules\GEMINI.md` harus **sinkron** dengan file ini.

### Aturan yang WAJIB ada di file ini:

1. **Database Safety** â€” Larangan `migrate:fresh`, `db:seed`, `db:wipe`
2. **Package Manager** â€” Wajib `pnpm`, larang `npm`/`yarn`
3. **Laravel Performance** â€” 10 aturan wajib
4. **Git Push Control** â€” Commit boleh, push hanya jika user perintah eksplisit
5. **UI Rules** â€” No emoji, wajib Lucide SVG icons
6. **Obsidian RAG Protocol** â€” Cara baca vault tiap sesi
7. **Mandatory Components** â€” 11 komponen wajib aktif
8. **Response Rules** â€” Bahasa Indonesia, singkat (caveman mode)
9. **User Preferences** â€” Biru (no purple), pnpm, auto-approve permission

---

## BAGIAN 6: WORKFLOW AI AGENT TIAP SESI

```
START SESI
    â”‚
    â–¼
1. Baca INDEX.md
   â†’ 00-AGY-Memory/INDEX.md
   â†’ Temukan proyek yang dikerjakan
    â”‚
    â–¼
2. Baca GLOBAL_SYSTEM_RULES.md
   â†’ 00-AGY-Memory/GLOBAL_SYSTEM_RULES.md
   â†’ Aktivkan semua 11 mandatory components
    â”‚
    â–¼
3. Baca CONTEXT.md Proyek
   â†’ 00-AGY-Memory/<NamaProyek>/CONTEXT.md
   â†’ Pahami stack, database, aturan khusus
    â”‚
    â–¼
4. Baca Sessions Terbaru (1-2 sesi terakhir)
   â†’ 00-AGY-Memory/<NamaProyek>/Sessions/Sesi-XX_*.md
   â†’ Sambung dari mana sesi sebelumnya berhenti
    â”‚
    â–¼
5. Kerjakan Task
   â†’ Terapkan semua rules
   â†’ Catat keputusan penting
    â”‚
    â–¼
6. AKHIR SESI: Tulis Log
   â†’ Buat file Sessions/Sesi-<N+1>_<tanggal>_<hash>.md
   â†’ Update CONTEXT.md bagian "Sesi Terbaru"
   â†’ Update INDEX.md jika ada proyek baru
    â”‚
    â–¼
END SESI
```

---

## BAGIAN 7: INTEGRASI MCP OBSIDIAN

### Tools yang Tersedia

| Tool | Fungsi | Cara Pakai |
|---|---|---|
| `search_notes` | Cari berdasarkan keyword di nama file | Gunakan nama proyek / nama file |
| `read_notes` | Baca isi file by path | Gunakan path langsung dari INDEX.md |

### Keterbatasan MCP Obsidian
- `search_notes` **tidak bisa** full-text search isi konten
- Hanya mencari berdasarkan nama/path file
- **Solusi:** Selalu gunakan path langsung (`read_notes` by path) via INDEX.md

### Contoh Penggunaan

```
# Baca CONTEXT.md proyek JBR-Minpo
read_notes(paths: ["00-AGY-Memory/JBR-Minpo/CONTEXT.md"])

# Cari semua file yang mengandung "POS" di namanya
search_notes(query: "POS")

# Baca rules global
read_notes(paths: ["00-AGY-Memory/GLOBAL_SYSTEM_RULES.md"])
```

---

## BAGIAN 8: CARA BUAT PROYEK BARU

Setiap kali mulai proyek baru, AI agent **wajib otomatis** membuat:

```powershell
# 1. Buat folder proyek
New-Item -ItemType Directory "C:\Users\p\Documents\Obsidian Vault\00-AGY-Memory\<NamaProyek>\Sessions"

# 2. Buat CONTEXT.md dari template
# Copy template dari Bagian 3 di atas

# 3. Buat Sesi-00_Init.md
# Isi dengan kondisi awal proyek

# 4. Update INDEX.md â€” tambah entry proyek baru
```

**Checklist Proyek Baru:**
- [ ] Folder `00-AGY-Memory/<NamaProyek>/` dibuat
- [ ] `CONTEXT.md` dibuat dari template standar (Bagian 3)
- [ ] `Sessions/Sesi-00_<tanggal>_Init.md` dibuat
- [ ] `INDEX.md` diupdate dengan entry proyek baru
- [ ] Rules khusus proyek dicatat di `CONTEXT.md`

---

## BAGIAN 9: ATURAN SINKRONISASI RULES

> **Single Source of Truth:** `00-AGY-Memory/GLOBAL_SYSTEM_RULES.md`

```
GLOBAL_SYSTEM_RULES.md (Obsidian)
        â”‚
        â”œâ”€â”€â†’ C:\Users\p\.gemini\config\rules\GEMINI.md  [harus sinkron]
        â”œâ”€â”€â†’ C:\Users\p\.gemini\config\rules\global-agents-rules.md  [extend]
        â””â”€â”€â†’ C:\Users\p\Documents\Obsidian Vault\GEMINI.md  [harus sinkron]
```

**Rules yang wajib ada di semua lokasi (konsisten):**
- Database safety (migrate:fresh dilarang)
- Git push restriction
- Mandatory 11 components

**Rules yang cukup di GLOBAL_SYSTEM_RULES.md saja:**
- Laravel performance (10 rules) â€” spesifik stack
- No emoji / Lucide icons â€” UI specific
- Bahasa Indonesia caveman mode â€” response style

---

## BAGIAN 10: CHECKLIST AUDIT BERKALA

Lakukan cek ini setiap 1 bulan atau saat vault terasa berantakan:

- [ ] Semua folder proyek di `00-AGY-Memory` punya `CONTEXT.md` dan `Sessions/`
- [ ] Tidak ada folder duplikat (nama sama, penulisan beda)
- [ ] `INDEX.md` sudah update dengan semua proyek
- [ ] `GLOBAL_SYSTEM_RULES.md` sinkron dengan `C:\Users\p\.gemini\config\rules\GEMINI.md`
- [ ] Proyek yang sudah selesai/non-aktif dipindah ke status "arsip" di INDEX.md
- [ ] Sessions log tidak ada yang kosong (setiap sesi kerja harus ada log-nya)

---

## REFERENSI CEPAT

| Butuh | Baca File Ini |
|---|---|
| Daftar proyek | `00-AGY-Memory/INDEX.md` |
| Rules global | `00-AGY-Memory/GLOBAL_SYSTEM_RULES.md` |
| Konteks proyek X | `00-AGY-Memory/X/CONTEXT.md` |
| Lanjut dari sesi kemarin | `00-AGY-Memory/X/Sessions/Sesi-<terakhir>.md` |
| Panduan Laravel performance | `09-Panduan-Projek/MASTER-PROMPT-LARAVEL-PERFORMANCE.md` |
| Database safety rules | `09-Panduan-Projek/ATURAN_DATABASE_SAFETY_GLOBAL.md` |
| Setup baru proyek | `09-Panduan-Projek/MASTER_SETUP.md` |

