# Environment Guidelines

Tujuan: semua repo konsisten untuk local/staging/production.

## Standard env vars (common)
- FNBPOS_ENV=local|staging|production
- FNBPOS_LOG_LEVEL=debug|info|warn|error

## API (fnbpos-api)
- PORT=3000
- DATABASE_URL=postgresql://...
- JWT_SECRET=...
- CORS_ORIGIN=...
- WS_ENABLED=true|false (opsional)

## Web/Desktop/Mobile
- FNBPOS_API_BASE_URL=https://...
- FNBPOS_WS_URL=wss://... (jika realtime)
- APP_ENV=local|staging|production

## Rules
- Setiap repo wajib punya `.env.example` (tanpa secrets).
- Secrets hanya lewat CI/CD secrets atau server env.
- Jangan commit `.env`, credential, atau token.
