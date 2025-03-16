---

# **Lab7Web - Praktikum CodeIgniter 4**  

## **Deskripsi**  
Repositori ini berisi hasil praktikum Pemrograman Web 2 dengan menggunakan PHP Framework **CodeIgniter 4**.  

## **Persiapan**  
1. **Instalasi XAMPP**  
   - Pastikan Apache dan MySQL aktif.  
   - Aktifkan ekstensi PHP berikut di `php.ini`:  
     - `json`, `mysqlnd`, `xml`, `intl`, `libcurl` (opsional).  

2. **Instalasi CodeIgniter 4**  
   - Unduh CodeIgniter 4 dari [https://codeigniter.com/download](https://codeigniter.com/download).  
   - Ekstrak ke folder `htdocs/lab11_php_ci/`, lalu **ubah nama folder** menjadi `ci4`.  
   - Buka browser dan akses:  
     ```
     http://localhost/lab11_php_ci/ci4/public/
     ```  

## **Struktur Direktori**  
```bash
lab11_php_ci/
├── app/ (Kode aplikasi utama)
├── public/ (File yang dapat diakses publik, CSS, JS)
├── writable/ (File yang di-generate aplikasi)
├── .env (Konfigurasi environment)
├── README.md (Dokumentasi proyek)
└── composer.json (Dependensi proyek)
```

## **Konfigurasi Debugging**  
- Ubah nama file `env` menjadi `.env`.  
- Edit isi file `.env`:  
  ```ini
  CI_ENVIRONMENT = development
  ```

## **Routing dan Controller**  
1. **Tambahkan route di `app/Config/Routes.php`**  
   ```php
   <?php

   use CodeIgniter\Router\RouteCollection;

   /**
    * @var RouteCollection $routes
    */

   // Mengaktifkan Auto Routing
   $routes->setAutoRoute(true);

   // Routing untuk halaman utama
   $routes->get('/', 'Home::index');

   // Routing untuk halaman Page
   $routes->get('/about', 'Page::about');
   $routes->get('/contact', 'Page::contact');
   $routes->get('/faqs', 'Page::faqs');
   $routes->get('/page/tos', 'Page::tos'); 
   ```
   
2. **Buat Controller di `app/Controllers/Page.php`**  
   ```php
   <?php

   namespace App\Controllers;

   class Page extends BaseController
   {
       public function about()
       {
           return view('about', [
               'title'   => 'Halaman About',
               'content' => 'Ini adalah halaman about yang menjelaskan tentang isi halaman ini.'
           ]);
       }

       public function contact()
       {
           echo "Ini halaman Contact";
       }

       public function faqs()
       {
           echo "Ini halaman FAQ";
       }

       public function tos()
       {
           echo "Ini halaman Term of Services";
       }
   }
   ?>
   ```

## **Membuat Tampilan (View)**  
1. **Buat file `app/Views/about.php`**  
   ```php
   <?= $this->include('template/header'); ?>

   <h1><?= $title; ?></h1>
   <hr>
   <p><?= $content; ?></p>

   <?= $this->include('template/footer'); ?>
   ```
   
2. **Buat template header dan footer** di `app/Views/template/`.  
   - **`header.php`**  
     ```php
     <!DOCTYPE html>
     <html lang="en">
     <head>
         <meta charset="UTF-8">
         <meta name="viewport" content="width=device-width, initial-scale=1.0">
         <title><?= $title; ?></title>
         <link rel="stylesheet" href="<?= base_url('/style.css'); ?>">
     </head>
     <body>
         <div id="container">
             <header>
                 <h1>Layout Sederhana</h1>
             </header>

             <nav>
                 <a href="<?= base_url('/'); ?>" class="active">Home</a>
                 <a href="<?= base_url('/artikel'); ?>">Artikel</a>
                 <a href="<?= base_url('/about'); ?>">About</a>
                 <a href="<?= base_url('/contact'); ?>">Kontak</a>
             </nav>

             <section id="wrapper">
                 <section id="main">
     ```

   - **`footer.php`**  
     ```php
                 </section>

                 <aside id="sidebar">
                     <div class="widget-box">
                         <h3 class="title">Widget Header</h3>
                         <ul>
                             <li><a href="#">Widget Link</a></li>
                             <li><a href="#">Widget Link</a></li>
                         </ul>
                     </div>

                     <div class="widget-box">
                         <h3 class="title">Widget Text</h3>
                         <p>
                             Vestibulum lorem elit, iaculis in nisl volutpat, malesuada tincidunt arcu. 
                             Proin in leo fringilla, vestibulum mi porta, faucibus felis. 
                             Integer pharetra est nunc, nec pretium nunc pretium ac.
                         </p>
                     </div>
                 </aside>

             </section>

             <footer>
                 <p>&copy; 2025 - Universitas Pelita Bangsa</p>
             </footer>

         </div>
     </body>
     </html>
     ```

## **Menjalankan Aplikasi**  
Gunakan perintah berikut untuk menjalankan aplikasi:  
```bash
php spark serve
```
Kemudian akses di browser:  
```
http://localhost:8080/about
```

## **Menggunakan GitHub**  
1. **Inisialisasi Git di dalam folder proyek:**  
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin https://github.com/username/Lab7Web.git
   git push -u origin main
   ```
2. **Tambahkan file `.gitignore`** untuk menghindari upload file yang tidak perlu:  
   ```
   writable/*
   vendor/*
   .env
   ```
