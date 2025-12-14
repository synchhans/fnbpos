# fnbpos Project Hub

Repo induk untuk dokumentasi, aturan main, dan release manifest sistem **fnbpos** (POS F&B) yang terdiri dari:
- **fnbpos-api** (NestJS backend)
- **fnbpos-backoffice-web** (Web admin/backoffice)
- **fnbpos-pos-desktop** (Windows POS/desktop)
- **fnbpos-mobile** (Kitchen/Owner mobile)

> Repo ini **tidak menyimpan source code aplikasi**. Repo ini adalah pusat standar & dokumentasi lintas sistem.

## Quick Links
- Flow utama: `docs/flows.md`
- Roles & permissions: `docs/roles-permissions.md`
- API guidelines: `docs/api-guidelines.md`
- Env guidelines: `docs/env-guidelines.md`
- Architecture overview: `docs/architecture.md`
- Release manifest: `releases/`

## Prinsip (ringkas)
- Semua perubahan masuk via PR (tidak push langsung ke `main`)
- Breaking change API wajib dicatat di `releases/`
- Simpan uang sebagai **integer Rupiah**
- Waktu di DB **UTC**, tampilan **Asia/Jakarta**
- Semua repo aplikasi wajib punya `.env.example` (tanpa secrets)

## Repository Map
- API: https://github.com/synchhans/fnbpos-api
- Backoffice Web: https://github.com/synchhans/fnbpos-backoffice-web
- POS Desktop: https://github.com/synchhans/fnbpos-pos-desktop
- Mobile: https://github.com/synchhans/fnbpos-mobile
