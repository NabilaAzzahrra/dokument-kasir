# APPLIKASI KASIR BERBASIS WEB

## Deskripsi

> Aplikasi Kasir ini ditujukan untuk memenuhi kebutuhan pada Rumah Enterpreneur di Politeknik LP3I Kampus Tasikmalaya. Dibuat dengan menggunakan Laravel 11, Tailwindcss, Breeze, PHP, serta JavaScript.

## Penunjang

1. PHP versi V 8.2,
2. Composer,
3. NodeJs versi minimal v.18.13.0-x64.msi keatas atau [Klik disini](https://nodejs.org/en ':target=_blank')

<!-- ## Manajemen Fitur -->

## Rancangan Database

Rancangan database aplikasi kasir ini dapat di lihat [disini](https://dbdiagram.io/d/kasir-re-66a324b78b4bb5230e66612e ':target=_blank')

## Tahap Develop

### Installasi Laravel Breeze

> Laravel Breeze merupakan template dari laravel yang sudah menggunakan tailwindcss.

- Install Laravel dengan ketik kode ini pada terminal ``composer create-project laravel/laravel kasir``
- Masuk ke dalam folder laravel yang sudah di install atau ketikan kode berikut pada terminal ``cd kasir``
- Ketik kode berikut pada terminal ``composer require laravel/breeze --dev``, kode tersebut digunakan untuk install template breeze pada laravel
- Masih di dalam terminal, ketik kode berikut ``php artisan breeze:install`` jika terdapat pilihan maka pilih blade, kemudian pilih PHPUnit atau ketik 1
- Kemudian ketikkan kode berikut pada terminal``npm install`` dan setelah itu run tailwindcss dengan kode berikut ``npm run dev``
- Kemudian ketikka kode berikut pada terminal yang berbeda ``php artisan serve`` dan klik pada port ``http://127.0.0.1:8000``

### Penambahan Routing untuk API

> Ketikkan kode berikut pada terminal untuk penambahan routing api.php ``php artisan install:api``

### Melakukan Connecting dengan Database

> Untuk melakukan connecting database maka bisa di setting pada file ``.env`` kemudian cari kode seperti gambar di bawah

![](/img/env.png ':size=300')

**Ubah kode di atas menjadi seperti gambar di bawah**

![](/img/env_edit.png ':size=300')

> Note : Nama Database yang digunakan adalah *kasir_re* untuk database menggunakan *MySQL* dan setelah di ubah maka ketikkan kode berikut di terminal ``php artisan migrate``