# Lab7Web - Praktikum CodeIgniter 4

## Deskripsi
Repositori ini berisi hasil praktikum Pemrograman Web 2 dengan menggunakan PHP Framework CodeIgniter 4.

## Persiapan
1. **Instalasi XAMPP**
   - Pastikan Apache dan MySQL aktif.
   - Aktifkan ekstensi PHP: `json`, `mysqlnd`, `xml`, `intl`, `libcurl`.

2. **Instalasi CodeIgniter 4**
   - Unduh CodeIgniter 4 dari [https://codeigniter.com/download](https://codeigniter.com/download).
   - Ekstrak ke folder `htdocs/lab11_php_ci/` dan ubah nama folder menjadi `ci4`.
   - Buka browser: `http://localhost/lab11_php_ci/ci4/public/` untuk mengecek instalasi.

## Struktur Direktori
```
lab11_php_ci/
├── app/ (Kode aplikasi utama)
├── public/ (File yang dapat diakses publik, CSS, JS)
├── writable/ (File yang di-generate aplikasi)
├── .env (Konfigurasi environment)
├── README.md (Dokumentasi)
└── composer.json (Dependensi proyek)
```

## Konfigurasi Debugging
- Ubah nama file `env` menjadi `.env`.
- Edit `.env`:
  ```
  CI_ENVIRONMENT = development
  ```

## Membuat Routing dan Controller
1. **Tambahkan route di `app/Config/Routes.php`**
   ```php
   $routes->get('/about', 'Page::about');
   ```
2. **Buat Controller di `app/Controllers/Page.php`**
   ```php
   <?php
   namespace App\Controllers;
   class Page extends BaseController {
       public function about() {
           return view('about', [
               'title' => 'Halaman About',
               'content' => 'Ini adalah halaman about.'
           ]);
       }
   }
   ?>
   ```

## Membuat Tampilan (View)
1. **Buat file `app/Views/about.php`**
   ```php
   <?= $this->include('template/header'); ?>
   <h1><?= $title; ?></h1>
   <p><?= $content; ?></p>
   <?= $this->include('template/footer'); ?>
   ```
2. **Buat template header dan footer** di `app/Views/template/`.
   ```php
   <!-- header.php -->
   <header>
       <h1>Website CodeIgniter</h1>
   </header>
   ```

## Menjalankan Aplikasi
```bash
php spark serve
```
Akses di browser: `http://localhost:8080/about`

## GitHub Repository
1. **Inisialisasi Git**
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git remote add origin https://github.com/username/Lab7Web.git
   git push -u origin main
   ```
2. **Tambahkan `.gitignore`**:
   ```
   writable/*
   vendor/*
   .env
   ```
