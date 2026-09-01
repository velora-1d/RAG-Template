# GLOBAL SYSTEM RULES & COMPONENT REGISTRY (ALL WORKSPACES & ALL PROJECTS)
# Binding for: Antigravity IDE, Claude Code, OpenCode, Codex, Gemini

## 1. STRICT DATABASE SAFETY (WAJIB — HARAM SEED & RESET)
1. **DILARANG KERAS**: `db:seed`, `migrate:fresh`, `db:wipe`, `migrate:reset`, `drop database`, `prisma db seed`
   - Perintah ini HANYA BOLEH dieksekusi jika USER secara eksplisit mengetiknya di chat
2. **OPERASI DATABASE HANYA INCREMENTAL**:
   - Perubahan skema baru: jalankan migrasi standar (incremental) saja
   - Seeding: wajib `firstOrCreate` / `insertOrIgnore`
3. **TESTING**:
   - Wajib mock atau `DatabaseTransactions`
   - DILARANG `RefreshDatabase` pada database utama

## 2. PACKAGE MANAGER: WAJIB `pnpm`
- `pnpm install`, `pnpm build`, `pnpm run dev`, `pnpm add`, `pnpm dlx`
- DILARANG `npm` atau `yarn` kecuali user minta secara eksplisit

## 3. LARAVEL PERFORMANCE (10 ATURAN WAJIB)
1. Cache Route: `php artisan route:cache` (no Closure di route definitions)
2. Cache Config: `php artisan config:cache` (`env()` hanya di `config/*.php`)
3. Autoloader: `composer install --optimize-autoloader --no-dev`
4. Eager Loading: Wajib `with()`, `load()`, `withCount()` — DILARANG query relasi di dalam loop/view
5. Queue: Logic berat (email, PDF, export, resize) wajib di Job/Queue
6. Cache Query: `Cache::remember()` untuk data yang jarang berubah
7. Database Indexing: Kolom WHERE/JOIN/ORDER BY wajib berindeks
8. Asset: `pnpm build` untuk production (minified)
9. OPcache: `opcache.enable=1` di PHP server production
10. Driver Cache/Session: Redis/Memcached untuk cache & session di production

## 4. STRICT GIT PUSH CONTROL
- **Git Commit**: Boleh — untuk checkpoint lokal
- **Git Push**: DILARANG otomatis tanpa perintah eksplisit user ("push", "push ke main")

## 5. UI/UX RULES — STRICT NO EMOJIS
- DILARANG KERAS emoji di seluruh frontend, backend messages, dan dokumentasi
- WAJIB gunakan SVG / Lucide Icons (`CheckCircle2`, `AlertCircle`, `ShieldCheck`, dll.)
- Prefer warna biru — hindari ungu

## 6. OBSIDIAN AGY-MEMORY PROTOCOL
- **Vault Location**: `[SESUAIKAN dengan path vault Obsidian kamu]`
- **AGY Memory Root**: `[VAULT]/00-AGY-Memory`
- Setiap sesi WAJIB:
  1. Baca `00-AGY-Memory/INDEX.md`
  2. Baca `00-AGY-Memory/<NamaProyek>/CONTEXT.md`
  3. Baca 1-2 Sessions terbaru
  4. Tulis log sesi baru di akhir sesi

## 7. MANDATORY ACTIVE COMPONENTS
1. **ponytail** — Database change detection & auto-migration
2. **codegraph** — Code dependency & database schema mapping
3. **serena** — LSP compiler & data type validator (Go, TS, Dart, Python)
4. **caveman** — Database backup & instant recovery
5. **contextmode** — Multi-agent real-time context synchronization
6. **headroom** — Dynamic response token allocation
7. **rtk** — Redux Toolkit integration & state sync
8. **Graphify** — Dependency graph analysis & codebase mapping
9. **delphitools** — Offline developer toolkit (`dt` CLI)
10. **skills** — System-wide skill registry & loader
11. **mcp** — Model Context Protocol client

## ATURAN RESPONS
- Bahasa Indonesia (kecuali user minta bahasa lain)
- Singkat & padat — hindari basa-basi dan recap panjang
- Auto-approve permission jika didukung tool
