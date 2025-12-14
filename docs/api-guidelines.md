# API Guidelines (NestJS)

Tujuan: konsisten, mudah dipakai 3 client, dan aman untuk evolusi.

## Versioning
- Gunakan SemVer: MAJOR.MINOR.PATCH
- Breaking change (hapus/rename field, ubah tipe, ubah perilaku) => naik MAJOR dan wajib catat di `releases/`.

## Response Shape (recommended)
### Success
{
  "data": ...,
  "meta": {
    "requestId": "uuid",
    "serverTime": "2025-12-14T00:00:00Z"
  }
}

### Error
{
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Invalid payload",
    "details": [{ "field": "itemId", "issue": "required" }]
  },
  "meta": { "requestId": "uuid", "serverTime": "..." }
}

## HTTP Status
- 200 OK (GET)
- 201 Created (POST create)
- 204 No Content (DELETE/void opsional)
- 400 Validation error
- 401 Unauthorized
- 403 Forbidden
- 404 Not found
- 409 Conflict (state conflict, mis. order sudah COMPLETED)
- 422 Unprocessable (opsional untuk aturan bisnis)

## Idempotency (minimal)
- Untuk endpoint payment/complete, pertimbangkan idempotency key:
  - header: `Idempotency-Key`
  - mencegah double charge / double complete saat retry.

## Pagination
Untuk list:
- query: `limit`, `cursor` (recommended) atau `page`
- Response `meta.nextCursor` jika ada data berikutnya.

## Money & Time
- Money: integer Rupiah (contoh 15000)
- Time: simpan UTC ISO string, tampilkan sesuai Asia/Jakarta di client

## Order State Rules
- NEW -> SENT_TO_KITCHEN -> COOKING -> READY -> COMPLETED
- VOIDED terminal state
- Update status wajib append ke `order_events` (audit).

## Security Basics
- JWT auth
- RBAC via role
- Semua endpoint tulis harus validasi payload (DTO/class-validator)
- Jangan pernah expose secrets di response/log
