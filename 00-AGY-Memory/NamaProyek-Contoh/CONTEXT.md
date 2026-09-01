---
project: NamaProyek-Contoh
domain: [Domain bisnis, contoh: E-commerce / EdTech / CRM]
status: aktif
last_updated: YYYY-MM-DD
agent_rules: 00-AGY-Memory/GLOBAL_SYSTEM_RULES.md
---

# CONTEXT: NamaProyek-Contoh

## Deskripsi Singkat
<!-- 2-3 kalimat tentang apa proyek ini dan tujuannya -->
Contoh: Aplikasi POS untuk toko retail yang mengelola transaksi, stok, dan laporan penjualan harian.

## Tech Stack
- **Backend:** Laravel 11
- **Frontend:** React + Inertia.js
- **Database:** PostgreSQL 16
- **Package Manager:** pnpm (WAJIB)
- **Cache/Queue:** Redis
- **Deployment:** VPS / Vercel / dst

## Struktur Direktori Proyek
```
/
├── app/
│   ├── Http/Controllers/
│   ├── Models/
│   └── Services/
├── resources/
│   ├── js/
│   └── views/
├── database/
│   ├── migrations/
│   └── seeders/
└── ...
```

## Database — Tabel Utama
| Tabel | Keterangan |
|---|---|
| `users` | Data pengguna & autentikasi |
| `[nama_tabel]` | [Keterangan] |
| `[nama_tabel]` | [Keterangan] |

## Aturan Khusus Proyek Ini
<!-- Rules tambahan di luar GLOBAL_SYSTEM_RULES.md -->
- [Aturan spesifik 1]
- [Aturan spesifik 2]

## Environment
- **Repo:** https://github.com/[username]/[repo]
- **Staging URL:** https://staging.[domain].com
- **Production URL:** https://[domain].com
- **Database Host:** localhost / [IP VPS]

## Tim
| Nama | Role |
|---|---|
| [Nama] | Project Owner / Developer |
| [Nama] | Frontend Developer |

## Status Proyek Saat Ini
<!-- Update setiap sesi selesai -->
- **Fase:** Development / Testing / Production
- **Sprint/Milestone aktif:** [Sprint X — fitur Y]
- **Blocker:** [Ada atau tidak ada]

## Sesi Terbaru
<!-- AI Agent: update link ini setiap akhir sesi -->
- [[00-AGY-Memory/NamaProyek-Contoh/Sessions/Sesi-00_Init]]
