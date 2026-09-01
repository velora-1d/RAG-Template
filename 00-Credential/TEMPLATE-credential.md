# Credential: [Nama Layanan]

> PERINGATAN: Jangan simpan password plaintext di sini.
> Gunakan referensi ke password manager atau environment variable.

## [Nama Layanan / API]

- **URL / Endpoint:** [URL]
- **Username / Email:** [username]
- **API Key / Token:** `[gunakan env variable: APP_API_KEY]`
- **Catatan:** [info tambahan]

---

## Template Referensi .env

```env
APP_NAME=[NamaAplikasi]
APP_URL=https://[domain].com

DB_CONNECTION=pgsql
DB_HOST=[host]
DB_PORT=5432
DB_DATABASE=[nama_database]
DB_USERNAME=[username]
DB_PASSWORD=[password — simpan di password manager]

REDIS_HOST=127.0.0.1
REDIS_PORT=6379

QUEUE_CONNECTION=redis
CACHE_DRIVER=redis
SESSION_DRIVER=redis
```
