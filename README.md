# UTS PWEB — CIGARRAY (Laravel + Blade, MVC)

**NIM:** 252410102106

Aplikasi web **CIGARRAY**: sistem pengelolaan toko rokok sederhana (tampilan hitam putih) yang dibuat dengan Laravel murni (tanpa template UI siap pakai) untuk mempelajari alur **request → route → controller → view → response**.

## Fitur

- **Login (simulasi)** — form username & password, divalidasi di controller, lalu `redirect` ke dashboard membawa `?username=...`.
- **Dashboard** — menyapa pengguna, menampilkan kartu statistik dan aktivitas hari ini (data array dari controller, di-loop dengan `@foreach`).
- **Pengelolaan (CRUD)** — admin dapat menambah, mengubah, dan menghapus produk rokok (kode, nama, kategori, harga, stok, status). Data berupa array di controller yang disimpan di session, dirender dengan `@forelse`, lengkap dengan pencarian dan validasi.
- **Profile** — detail akun; username diteruskan lewat request parameter.
- **Tata letak eksklusif** — sidebar hitam (navbar) di kiri, login layar terbelah, panel form di samping tabel. Di layar kecil sidebar menjadi bar atas dengan menu buka-tutup dan tabel berubah menjadi kartu.

## Struktur File

```
routes/web.php
app/Http/Controllers/PageController.php
resources/views/
├── layouts/app.blade.php
├── login.blade.php
├── dashboard.blade.php
├── pengelolaan.blade.php
├── profile.blade.php
├── components/
│   ├── navbar.blade.php
│   ├── footer.blade.php
│   └── page-header.blade.php
└── partials/
    ├── head.blade.php
    └── stat-card.blade.php
public/css/style.css
```

## Penerapan Konsep

| Konsep | Lokasi |
| --- | --- |
| MVC (view dipanggil dari controller) | `PageController` memanggil `view(...)` |
| `@extends` | semua view halaman |
| `@section` / `@endsection` | semua view halaman |
| `@yield` | `layouts/app.blade.php` |
| `@include` | `layouts/app` → `partials.head`, `dashboard` → `partials.stat-card` |
| `x-component` | `<x-navbar>`, `<x-footer>` di layout; `<x-page-header>` di tiap halaman |
| Request parameter | `?username=` dibaca lewat `$request->query('username')` |
| Array rendering | `@foreach` / `@forelse` pada dashboard, pengelolaan, profile |


## Screenshot

<img width="1600" height="900" alt="Image" src="https://github.com/user-attachments/assets/31f52c27-1f2c-4200-9a6d-e46024c9f0ec" />
<img width="1600" height="900" alt="Image" src="https://github.com/user-attachments/assets/a4e554c8-4225-495b-aeb4-a4e151212961" />
<img width="1600" height="900" alt="Image" src="https://github.com/user-attachments/assets/f0b2d245-5073-4d3b-a065-f20e86970c1b" />
<img width="1600" height="900" alt="Image" src="https://github.com/user-attachments/assets/d50c6866-e08a-4cf1-8bb6-4b58b0b25b71" />
