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

> Ada beberapa extention pada visual studio code yang dapat di install untuk mempermudah dalam tahap pembuatan aplikasi kasir ini

![](/img/extention1.png ':size=300')

![](/img/extention2.png ':size=300')

![](/img/extention3.png ':size=300')

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

> buat database pada MySQL dengan nama ``kasir_re``

![](/img/database.png ':size=500')

> Note : Nama Database yang digunakan adalah *kasir_re* untuk database menggunakan *MySQL* dan setelah di ubah maka ketikkan kode berikut di terminal ``php artisan migrate``

### Membuat Akun

> Form login dan register sudah dapat digunakan, karena kita menggunakan template dari breeze

![](/img/landing.png ':size=1000')

Pada landing terdapat login dan register yang siap untuk digunakan ``silahkan kalian buat akun terlebih dahulu`` 

### Membuat Menu

Berikut menu yang akan kita buat pada aplikasi kasir ini
- Dashboard
- Master
  - Konsumen
  - Produk
  - Supplier
  - Konsinyasi
  - Konsinyasi Produk
- Transaksi
  - Pembelian
  - Penjualan
- Report
  - Pembelian
  - Penjualan
  - Konsinyasi
  - Piutang

***Membuat Menu***

1. Buka file ``navigation.blade.php`` pada folder resource
   
   ![](/img/navigation.png ':size=200')

2. Lihat kode pada gambar dibawah ini

    ![](/img/menu.png ':size=800')

    Buatlah kode berikut di **bawah** kode yang ada di gambar di atas

```html
                
                <div class="hidden sm:flex sm:items-center sm:ms-6">
                    <li class="relative list-none">
                        <x-dropdown>
                            <x-slot name="trigger">
                                <button
                                    class="inline-flex items-center px-3 py-2 border border-transparent text-sm leading-4 font-medium rounded-md text-gray-500 dark:text-gray-400 bg-white dark:bg-gray-800 hover:text-gray-700 dark:hover:text-gray-300 focus:outline-none transition ease-in-out duration-150">
                                    <div>Master</div>

                                    <div class="ms-1">
                                        <svg class="fill-current h-4 w-4" xmlns="http://www.w3.org/2000/svg"
                                            viewBox="0 0 20 20"> <path fill-rule="evenodd"
                                                d="M5.293 7.293a1 1 0 011.414 0L10 10.586l3.293-3.293a1 1 0 111.414 1.414l-4 4a1 1 0 01-1.414 0l-4-4a1 1 0 010-1.414z"
                                                clip-rule="evenodd" />
                                        </svg>
                                    </div>
                                </button>
                            </x-slot>

                            <x-slot name="content">
                                <x-dropdown-link :href="route('dashboard')">
                                    {{ __('Konsumen') }}
                                </x-dropdown-link>

                                <x-dropdown-link :href="route('dashboard')">
                                    {{ __('Produk') }}
                                </x-dropdown-link>

                                <x-dropdown-link :href="route('dashboard')">
                                    {{ __('Supplier') }}
                                </x-dropdown-link>

                                <x-dropdown-link :href="route('dashboard')">
                                    {{ __('Konsinyasi') }}
                                </x-dropdown-link>

                                <x-dropdown-link :href="route('dashboard')">
                                    {{ __('Konsinyasi Produk') }}
                                </x-dropdown-link>
                            </x-slot>
                        </x-dropdown>
                    </li>
                </div>
```
   
Hasilnya seperti ini:

![](/img/menu_master.png ':size=1000')

3. Buat Menu selanjutnya yaitu menu ``Transaksi`` dan menu ``Report`` yang sub menunya sudah disebutkan di atas sehingga hasilnya seperti ini:

![](/img/menu_navigation.png ':size=1000')

### Membuat Halaman Konsumen


1. Membuat table konsumen
    jalankan kode ini pada terminal ``php artisan make:migration create_konsumen``
2. Buka file migration yang sudah dibuat, lokasinya seperti pada gambar di bawah
   
   ![](/img/create_table_konsumen.png ':size=300')

3. ketik kode berikut dibawah id

```html
$table->string('konsumen');
$table->string('status');
```

sehingga kodenya seperti ini:

![](/img/kolom_konsumen.png ':size=400')

kemudian ketik ``php artisan migrate`` pada terminal untuk membuat table konsumen tersebut di MySQL.

4. Membuat model Konsumen
   Jalankan kode berikut ``php artisan make:model Konsumen`` kemudian buka file model yang sudah dibuat, lokasinya seperti gambar di bawah

![](/img/model_konsumen.png ':size=400')

ketikkan kode berikut dibawah kode HaFactory;

```html
    protected $fillable = [
        'konsumen',
        'status'
    ];

    protected $table = 'konsumen';
```

sehingga kode seperti ini

![](/img/isi_model_konsumen.png ':size=400')

5. Buat controller Konsumen dan controller API Konsumen

ketikkan kode berikut pada terminal ``php artisan make:controller KonsumenController --resource`` dan kode berikut ``php artisan make:controller API/KonsumenAPIController``

6. Buat route untuk memanggil halaman konsumen, buka file web.php kemudian ketik kode berikut ``Route::resource('konsumen', KonsumenController::class)->middleware('auth');``

> Pastikan ketika mengetikkan KonsumenController itu harus ada yang di import yakni file KonsumenController, contohnya ada di bawah

![](/img/route_konsumen.png ':size=800')

hasil importnya ada di bagian atas seperti ini

![](/img/import_konsumen.png ':size=400')

7. Buka kembali ``navigation.blade.php``, kemudian ubah route yang tadinya ``dashboard`` menjadi ``konsumen.index``, sehingga seperti ini

![](/img/navigation_konsumen.png ':size=400')

8. Buka file ``KonsumenController.php`` kemudian pada function ``index`` ketikkan kode berikut ``return view('page.konsumen.index');`` sehingga seperti ini

![](/img/index_konsumen.png ':size=400')

9. Buat folder ``page`` pada folder view lalu buat lagi folder di dalamnya dengan nama ``konsumen`` kemudian buat file ``index.blade.php``

![](/img/page_konsumen.png ':size=300')

10. Buat function ``add``, ``update``, dan ``delete`` pada controller ``KonsumenController.php``

**function index**

```html
    public function index()
    {
        $konsumen = Konsumen::all();
        return view('page.konsumen.index')->with([
            'konsumen' => $konsumen
        ]);
    }
```

**function add**

```html
    public function store(Request $request)
    {
        $data = [
            'konsumen' => $request->input('konsumen'),
            'status' => $request->input('status'),
        ];

        Konsumen::create($data);

        return back()->with('message_delete', 'Data Konsumen Sudah dihapus');
    }
```

**function update**

```html
    public function update(Request $request, string $id)
    {
        $data = [
            'konsumen' => $request->input('konsumen_update'),
            'status' => $request->input('status_update'),
        ];

        $datas = Konsumen::findOrFail($id);
        $datas->update($data);
        return back()->with('message_delete', 'Data Konsumen Sudah dihapus');
    }
```

**function delete**

```html
    public function destroy(string $id)
    {
        $data = Konsumen::findOrFail($id);
        $data->delete();
        return back()->with('message_delete','Data Konsumen Sudah dihapus');
    }
```

11.  Buatlah kode di dalamnya seperti kode di bawah ini

```html
asdf
```