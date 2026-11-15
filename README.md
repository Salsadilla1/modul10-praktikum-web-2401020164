# Modul 9 — Pengenalan Laravel dan Pola MVC

Tugas Praktikum Pemrograman Web Pertemuan 9.

- **Nama:** Salsadilla Frisca Anjani
- **NIM:** 2401020164
- **Program studi:** Teknik Informatika, Universitas Maritim Raja Ali Haji

## Tentang aplikasi

Aplikasi daftar buku sederhana yang menerapkan pola Model-View-Controller pada Laravel.
Data buku masih berupa array statis di dalam Model (belum memakai basis data), sesuai
ketentuan Modul 9.

| Kode  | Judul            | Keterangan        |
|-------|------------------|-------------------|
| BK001 | Dasar PHP        | Data bawaan modul |
| BK002 | Belajar Laravel  | Data bawaan modul |
| BK003 | Logika Web       | Data bawaan modul |
| BK004 | Basis Data MySQL | Data tambahan tugas |

## Alur MVC

| Komponen   | Berkas                                        |
|------------|-----------------------------------------------|
| Model      | `app/Models/Buku.php`                         |
| Route      | `routes/web.php`                              |
| Controller | `app/Http/Controllers/BukuController.php`     |
| View       | `resources/views/buku/index.blade.php`        |
| View       | `resources/views/buku/show.blade.php`         |

## Route

| Method | URI            | Aksi                  | Fungsi                        |
|--------|----------------|-----------------------|-------------------------------|
| GET    | `/`            | Closure               | Halaman sambutan Laravel      |
| GET    | `/buku`        | `BukuController@index`| Daftar buku dan pencarian     |
| GET    | `/buku/{kode}` | `BukuController@show` | Detail buku atau 404          |

## Cara menjalankan

```bash
composer install
cp .env.example .env
php artisan key:generate
php artisan serve
```

Buka `http://127.0.0.1:8000/buku`.

## Contoh pengujian

| Skenario             | Alamat                        | Hasil                              |
|----------------------|-------------------------------|------------------------------------|
| Daftar buku          | `/buku`                       | Empat baris BK001–BK004 tampil     |
| Pencarian judul      | `/buku?cari=Laravel`          | Hanya BK002 tampil                 |
| Pencarian data tugas | `/buku?cari=Basis`            | Hanya BK004 tampil                 |
| Detail data tugas    | `/buku/BK004`                 | Kode BK004, judul Basis Data MySQL |
| Pencarian kosong     | `/buku?cari=TidakAda`         | Pesan data tidak ditemukan         |
| Kode tidak terdaftar | `/buku/BK999`                 | HTTP 404 Not Found                 |
