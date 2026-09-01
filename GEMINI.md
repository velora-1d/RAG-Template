# GLOBAL SYSTEM RULES & COMPONENT REGISTRY
# Binding for: Antigravity IDE, Claude Code, OpenCode, Codex, Gemini

## STRICT DATABASE SAFETY (WAJIB)
1. **DILARANG KERAS**: `migrate:fresh`, `db:seed`, `db:wipe`, `migrate:reset`, `drop database`
   - Hanya boleh dijalankan jika USER mengetik perintah tersebut secara eksplisit di chat
2. **OPERASI DATABASE HANYA INCREMENTAL**: Gunakan migrasi standar, seeding pakai `firstOrCreate` / `insertOrIgnore`
3. **TESTING**: Wajib pakai mock atau `DatabaseTransactions` — dilarang `RefreshDatabase` di database utama

## MANDATORY PACKAGE MANAGER: WAJIB `pnpm`
- Seluruh perintah Node.js wajib pakai `pnpm` (`pnpm install`, `pnpm build`, `pnpm dev`, `pnpm add`)
- DILARANG `npm` atau `yarn`

## LARAVEL PERFORMANCE (10 ATURAN WAJIB)
1. Cache Route: `php artisan route:cache` (no Closure di route)
2. Cache Config: `php artisan config:cache` (`env()` hanya di `config/*.php`)
3. Autoloader: `composer install --optimize-autoloader --no-dev`
4. Eager Loading: Wajib `with()`, `load()`, `withCount()` — dilarang N+1
5. Queue: Proses berat (email, PDF, export) wajib pakai Job/Queue
6. Cache Query: `Cache::remember()` untuk data jarang berubah
7. Indexing: Kolom WHERE/JOIN/ORDER BY wajib berindeks
8. Asset: `pnpm build` untuk production
9. OPcache: `opcache.enable=1` di PHP production
10. Driver Cache: Gunakan Redis/Memcached untuk cache & session

## STRICT GIT PUSH CONTROL
- **Git Commit**: Boleh (untuk checkpoint lokal)
- **Git Push**: DILARANG otomatis — hanya jika USER eksplisit perintahkan "push"

## UI/UX RULES
- DILARANG KERAS menggunakan emoji di seluruh UI/UX frontend & backend
- WAJIB gunakan SVG / Lucide Icons

## MANDATORY ACTIVE COMPONENTS (Aktifkan di semua tool)
1. **ponytail** — Database change detection & auto-migration
2. **codegraph** — Code dependency & database schema mapping
3. **serena** — LSP compiler & data type validator
4. **caveman** — Database backup & recovery
5. **contextmode** — Multi-agent context synchronization
6. **headroom** — Dynamic token allocation
7. **rtk** — Redux Toolkit integration
8. **Graphify** — Dependency graph analysis
9. **delphitools** — Offline developer toolkit (dt CLI)
10. **skills** — Skill registry & capability loader
11. **mcp** — Model Context Protocol client

## OBSIDIAN AGY-MEMORY PROTOCOL
- **Vault Location**: `[SESUAIKAN: path vault Obsidian kamu]`
- **AGY Memory Root**: `[VAULT]/00-AGY-Memory`
- Setiap sesi WAJIB baca `00-AGY-Memory/INDEX.md` terlebih dahulu
- Lalu baca `00-AGY-Memory/<NamaProyek>/CONTEXT.md`
- Lalu baca Sessions terbaru

## USER PREFERENCES
- Prefer warna biru (no purple)
- Package Manager: `pnpm`
- Auto-approve permission: aktif
