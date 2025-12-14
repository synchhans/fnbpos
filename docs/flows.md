# Flows (POS F&B)

Dokumen ini mendeskripsikan flow utama MVP.

## A. Open/Close Shift (Kasir)
### Open Shift
1. Kasir login
2. Pilih outlet
3. Open shift dengan `opening_cash` (opsional tapi disarankan)
4. Sistem membuat `shift` status OPEN

### Cash In / Cash Out (opsional)
- Cash in/out dicatat sebagai `cash_movement` (reason wajib)

### Close Shift
1. Kasir input `closing_cash_counted`
2. Sistem hitung expected cash = opening + cash_sales + cash_in - cash_out - refunds
3. Simpan selisih (over/short) + catatan
4. Shift status CLOSED (readonly)

## B. Order (Counter / Quick Service) - MVP utama
1. Kasir buat order (type: TAKEAWAY/DELIVERY/DINE_IN)
2. Tambah items + modifiers + notes
3. Submit order -> status `NEW`
4. Kasir klik "Send to Kitchen" -> status `SENT_TO_KITCHEN`
5. Kitchen melihat order realtime (KDS)
6. Kitchen update status: `COOKING` -> `READY`
7. Kasir menerima pembayaran (cash/transfer/qris)
8. Setelah payment sukses -> order `COMPLETED` + cetak struk

## C. Void / Cancel Order
- Hanya role tertentu yang boleh void
- Void wajib alasan
- Void mengunci order agar tidak bisa dibayar lagi
- Event log harus menyimpan siapa, kapan, alasan

## D. Reprint Receipt
- Kasir bisa reprint untuk order COMPLETED
- Semua reprint dicatat di audit log (opsional di MVP)

## E. Minimal status yang dipakai
- NEW
- SENT_TO_KITCHEN
- COOKING
- READY
- COMPLETED
- VOIDED
