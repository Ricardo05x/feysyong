# Fey-Syong

Fey-Syong adalah aplikasi penilaian kesehatan untuk UMKM fashion di Indonesia. Aplikasi menggunakan enam faktor penilaian:
Sumber Daya Fashion, Operasional & Inovasi, Pasar & Keuangan, Budaya Tim, Kepemimpinan Fashion, dan Lingkungan Kerja.

Aplikasi dibuat sebagai situs statis dengan JavaScript dan Supabase untuk autentikasi serta penyimpanan data.

## Struktur

- `index.html` - halaman utama dan metadata Fey-Syong
- `css/style.css` - tampilan situs
- `js/app.js` - konten, navigasi, pertanyaan, dan alur penilaian
- `js/config.js` - URL serta publishable key Supabase
- `supabase/01_schema.sql` - tabel, keamanan, fungsi, dan view
- `supabase/02_seed_survei.sql` - data pembanding historis
- `supabase/03_admin_role.sql` - penambahan peran administrator pada proyek lama

## Jalankan Supabase

1. Jalankan `supabase/01_schema.sql` sekali pada SQL Editor Supabase.
2. Jalankan `supabase/02_seed_survei.sql` untuk mengisi data pembanding fashion.
3. Untuk proyek lama, jalankan `supabase/03_admin_role.sql` bila diperlukan.
4. Isi URL dan publishable key pada `js/config.js`.
5. Aktifkan Email authentication dan konfirmasi email sesuai kebutuhan.

## Jalankan situs

```bash
python -m http.server 8000
```

Buka `http://localhost:8000`.

## Alur penggunaan

1. Pemilik mendaftarkan usaha fashion dan mengisi 16 pertanyaan pemilik.
2. Karyawan mendaftarkan diri dengan nama usaha yang sama persis dan mengisi 19 pertanyaan karyawan.
3. Ringkasan menampilkan skor gabungan.
4. Halaman Data Fashion membandingkan usaha terdaftar dengan data pembanding fashion.

## Keamanan

Kunci yang disimpan pada `js/config.js` harus berupa publishable/anon key, bukan service_role key. Semua penulisan kuesioner dilakukan melalui fungsi database dengan Row Level Security.
