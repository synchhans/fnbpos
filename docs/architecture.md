# Architecture Overview (MVP)

## Components
1) fnbpos-api (NestJS)
- REST API untuk semua client
- WebSocket gateway untuk realtime order ke KDS (kitchen)
- PostgreSQL sebagai sumber data utama

2) fnbpos-pos-desktop (Windows POS)
- UI kasir (cepat)
- Untuk MVP bisa print preview/PDF
- Untuk produksi: modul printing ESC/POS (via desktop app/agent)

3) fnbpos-mobile (Kitchen/Owner)
- Kitchen (KDS): subscribe realtime orders per outlet
- Owner: dashboard ringkas + notifikasi (phase berikutnya)

4) fnbpos-backoffice-web
- Setup menu/modifier/user
- Reports & export

## Data Strategy
- Semua transaksi disimpan di API/DB (single source of truth)
- Order status change dicatat di `order_events` untuk audit

## Realtime Strategy
- WebSocket channel per outlet
- Event minimal:
  - order.created
  - order.sent_to_kitchen
  - order.status_changed
  - order.completed
  - order.voided

## Printing Strategy (later, not MVP)
- Desktop melakukan print ESC/POS (lebih stabil daripada browser print)
- API hanya menyediakan `receipt payload` (items, totals, store info)
