# README — Obsidian RAG Template untuk AI Agent

Template ini adalah setup sistem memori persistent untuk AI agent menggunakan Obsidian.
Cocok untuk developer yang bekerja dengan AI tools seperti **Antigravity IDE, Claude Code, OpenCode, atau Codex**.

---

## Apa itu RAG Obsidian ini?

AI agent tidak punya memori antar sesi. Dengan sistem ini, **Obsidian jadi "otak" permanen** agent kamu.
Setiap sesi, agent baca dulu konteks proyek dari vault → kerja → tulis log → sesi berikutnya sambung dari sana.

---

## Cara Pakai

### 1. Salin folder ini ke Obsidian Vault kamu
```
Salin seluruh isi folder Obsidian-RAG-Template/ ke:
C:\Users\<nama_kamu>\Documents\Obsidian Vault\
```

### 2. Sesuaikan path di GEMINI.md
Buka `GEMINI.md` di root vault, ganti:
```
[SESUAIKAN: path vault Obsidian kamu]
```
Dengan path vault kamu yang sebenarnya.

### 3. Setup MCP Obsidian di AGY / Claude Code
Tambahkan MCP Obsidian server ke config tool AI kamu.
Pastikan vault path sudah benar.

### 4. Buat proyek pertamamu
```
Duplikat folder: 00-AGY-Memory/NamaProyek-Contoh/
Ganti nama folder sesuai proyek
Isi CONTEXT.md dengan info proyekmu
Update 00-AGY-Memory/INDEX.md
```

### 5. Mulai sesi pertama
Di chat AI agent, cukup bilang:
> "Baca INDEX.md dan CONTEXT.md proyek [NamaProyek], lalu kita mulai kerja."

---

## Struktur Folder

```
Obsidian-RAG-Template/
├── GEMINI.md                          ← Rules AI agent (dibaca otomatis)
├── HOME.md                            ← Navigasi vault
│
├── 00-AGY-Memory/                     ← MEMORI AI AGENT (UTAMA)
│   ├── INDEX.md                       ← Pintu masuk — daftar semua proyek
│   ├── GLOBAL_SYSTEM_RULES.md         ← Rules global lintas semua proyek
│   ├── General-AGY-Sessions/          ← Sesi umum
│   │   ├── CONTEXT.md
│   │   └── Sessions/
│   └── NamaProyek-Contoh/             ← Template 1 proyek
│       ├── CONTEXT.md                 ← Konteks proyek (wajib ada)
│       └── Sessions/
│           ├── Sesi-00_Init.md        ← Template sesi pertama
│           └── Sesi-01_YYYY-MM-DD_TEMPLATE.md  ← Template sesi reguler
│
├── 00-Credential/                     ← Credential & API keys
│   └── TEMPLATE-credential.md
│
├── 01-Dokumen/                        ← PRD, spesifikasi, notulen
├── 09-Panduan-Projek/                 ← SOP & panduan teknis
│   └── OBSIDIAN_RAG_SETUP.md          ← Panduan lengkap sistem ini
├── 10-Modul-Ajar/
├── Assets/
└── Excalidraw/
```

---

## File-file Penting

| File | Fungsi | Wajib Edit? |
|---|---|---|
| `GEMINI.md` | Rules AI agent | Ya — sesuaikan path vault |
| `00-AGY-Memory/INDEX.md` | Daftar semua proyek | Ya — tambah proyekmu |
| `00-AGY-Memory/GLOBAL_SYSTEM_RULES.md` | Rules global agent | Opsional — bisa kustomisasi |
| `00-AGY-Memory/NamaProyek-Contoh/CONTEXT.md` | Template konteks proyek | Ya — duplikat & isi |
| `09-Panduan-Projek/OBSIDIAN_RAG_SETUP.md` | Panduan lengkap | Baca dulu |

---

## Kompatibel dengan

- Antigravity IDE (AGY)
- Claude Code
- OpenCode
- Codex (GitHub Copilot)
- Cursor AI

---

> Dibuat dengan sistem AGY Memory Protocol. Sesuaikan isi sesuai kebutuhan proyekmu.
