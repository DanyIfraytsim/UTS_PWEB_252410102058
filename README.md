# UTS PWEB — CIGARRAY (Laravel + Blade, MVC)

**NIM:** 252410102058

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

<img width="1920" height="1080" alt="Image" src="https://github.com/user-attachments/assets/6b787853-24fb-45ba-bf57-7048dd5bc1bc" />
<img width="1920" height="1080" alt="Image" src="https://github.com/user-attachments/assets/4268b0f4-40b9-4579-9e52-d8e22c17dd99" />
<img width="1920" height="1080" alt="Image" src="https://github.com/user-attachments/assets/30ce3df1-0d72-47bd-8ed1-10ddd899a1f4" />
<img width="1920" height="1080" alt="Image" src="https://github.com/user-attachments/assets/b672cf91-d159-4103-959a-803b57487eca" />

