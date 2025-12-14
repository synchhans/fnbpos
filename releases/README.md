# Releases (Manifest)

Folder ini berisi **manifest kompatibilitas** antar komponen.
Gunanya: web/desktop/mobile selalu tahu API versi berapa yang kompatibel.

## Aturan
- Setiap ada perubahan yang mempengaruhi client (response/field/perilaku), buat file release baru.
- Breaking change = wajib release note di sini.

## Format
Gunakan `release-template.md` sebagai dasar:
- nama file: `release-YYYYMMDD.md`
- isi: versi tiap repo + catatan perubahan + kompatibilitas minimum
