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
            'konsumen' => $request->input('konsumen'),
            'status' => $request->input('status'),
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

11.  tambahkan link berikut pada file ``app.blade.php`` (di dalam tag head) ``<link href="https://cdn.jsdelivr.net/npm/select2@4.1.0-rc.0/dist/css/select2.min.css" rel="stylesheet" />`` 

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.7.1/jquery.min.js" integrity="sha512-v2CJ7UaYy4JwqLDIrZUI/4hqeoQieOmAZNXBeQyjo21dadnwR+8ZaIJVT8EE2iyI61OV8e6M8PP2/4hpQINQ/g==" crossorigin="anonymous" referrerpolicy="no-referrer"></script>
<style>
        .select2-container .select2-selection--single {
            width: 100% !important;
            background-color: #f9fafb;
            border: 1px solid #d1d5db !important;
            padding: 0.5rem 0.75rem;
            font-size: 0.875rem;
            height: 43px;
            border-radius: 0.4rem;
            color: #1f2937;
        }

        .select2-container .select2-selection--single .select2-selection__arrow {
            top: 20% !important;
            right: 8px;
        }

        .select2-container .select2-selection--single .select2-selection__rendered {
            font-size: 14px !important;
            top: -2px;
            left: -6px;
            position: relative;
            color: #1f2937;
        }

        .select2-search__field {
            font-size: 14px !important;
            border-radius: 0.5rem;
        }

        .select2-results {
            font-size: 14px !important;
            border-radius: 0px 10px 0px 10px;
        }
    </style>
```
12. ketik kode berikut dibawah tutup tag body ``</body>`` pada file ``app.blade.php``
    
    ```html
        <script src="https://cdn.jsdelivr.net/npm/select2@4.1.0-rc.0/dist/js/select2.min.js"></script>
        <script>
            // In your Javascript (external .js resource or <script> tag)
            $(".js-example-placeholder-single").select2({
                placeholder: "Pilih...",
                allowClear: true,
                width:'100%'
            });
        </script>
        @stack('scripts')
    ```
13.  Buatlah kode di dalamnya seperti kode di bawah ini

```html
<x-app-layout>
    <x-slot name="header">
        <h2 class="font-semibold text-xl text-gray-800 dark:text-gray-200 leading-tight">
            {{ __('KONSUMEN') }}
        </h2>
    </x-slot>

    <div class="py-12">
        <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
            <div class="bg-white dark:bg-gray-800 overflow-hidden shadow-sm sm:rounded-lg">
                <div class="p-4 flex items-center justify-between">
                    <div>DATA KONSUMEN</div>
                    <div>
                        <a href="#" onclick="return functionAdd()"
                            class="bg-sky-600 p-2 hover:bg-sky-400 text-white rounded-xl">Add</a>
                    </div>
                </div>
                <div class="p-6 text-gray-900 dark:text-gray-100">
                    <div class="relative overflow-x-auto shadow-md sm:rounded-lg">
                        <table class="w-full text-sm text-left rtl:text-right text-gray-500 dark:text-gray-400">
                            <thead
                                class="text-xs text-gray-700 uppercase bg-gray-50 dark:bg-gray-700 dark:text-gray-400">
                                <tr>
                                    <th scope="col" class="px-6 py-3">
                                        NO
                                    </th>
                                    <th scope="col" class="px-6 py-3">
                                        KONSUMEN
                                    </th>
                                    <th scope="col" class="px-6 py-3">
                                        STATUS
                                    </th>
                                    <th scope="col" class="px-6 py-3">

                                    </th>
                                </tr>
                            </thead>
                            <tbody>
                                @php
                                    $no = 1;
                                @endphp
                                @foreach ($konsumen as $k)
                                    <tr
                                        class="bg-white border-b dark:bg-gray-800 dark:border-gray-700 hover:bg-gray-50 dark:hover:bg-gray-600">
                                        <th scope="row"
                                            class="px-6 py-4 font-medium text-gray-900 whitespace-nowrap dark:text-white">
                                            {{ $no++ }}
                                        </th>
                                        <td class="px-6 py-4">
                                            {{ $k->konsumen }}
                                        </td>
                                        <td class="px-6 py-4">
                                            {{ $k->status }}
                                        </td>
                                        <td class="px-6 py-4">
                                            <button type="button" data-id="{{ $k->id }}"
                                                data-modal-target="sourceModalEdit" data-konsumen="{{ $k->konsumen }}"
                                                data-status="{{ $k->status }}" onclick="editSourceModal(this)"
                                                class="bg-amber-500 hover:bg-amber-600 px-3 py-1 rounded-md text-xs text-white">
                                                Edit
                                            </button>
                                            <button onclick="return konsumenDelete('{{$k->id}}','{{$k->konsumen}}')" class="bg-red-500 hover:bg-bg-red-300 px-3 py-1 rounded-md text-xs text-white">Delete</button>
                                        </td>
                                    </tr>
                                @endforeach
                            </tbody>
                        </table>
                    </div>
                </div>
            </div>
        </div>
    </div>
    <div class="fixed inset-0 flex items-center justify-center z-50 hidden" id="sourceModal">
        <div class="fixed inset-0 bg-black opacity-50" onclick="sourceModalClose()"></div>
        <div class="fixed inset-0 flex items-center justify-center">
            <div class="w-full md:w-1/2 relative bg-white rounded-lg shadow mx-5">
                <div class="flex items-start justify-between p-4 border-b rounded-t">
                    <h3 class="text-xl font-semibold text-gray-900" id="title_source">
                        Tambah Sumber Database
                    </h3>
                    <button type="button" onclick="sourceModalClose()"
                        class="text-gray-400 bg-transparent hover:bg-gray-200 hover:text-gray-900 rounded-lg text-sm w-8 h-8 ml-auto inline-flex justify-center items-center">
                        <i class="fa-solid fa-xmark"></i>
                    </button>
                </div>
                <form method="POST" id="formSourceModal">
                    @csrf
                    <div class="flex flex-col p-4 space-y-6">
                        <div class="mb-5">
                            <label for="konsumen"
                                class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Konsumen</label>
                            <input type="text" id="konsumen" name="konsumen"
                                class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
                                required />
                        </div>
                        <div class="mb-5">
                            <label for="status"
                                class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Status</label>
                            <select class="js-example-placeholder-single js-states form-control w-full m-6"
                                name="status" data-placeholder="Pilih Status">
                                <option value="">Pilih...</option>
                                <option value="MAHASISWA">MAHASISWA</option>
                                <option value="KARYAWAN">KARYAWAN</option>
                            </select>
                        </div>
                    </div>
                    <div class="flex items-center p-4 space-x-2 border-t border-gray-200 rounded-b">
                        <button type="submit" id="formSourceButton"
                            class="bg-green-400 m-2 w-40 h-10 rounded-xl hover:bg-green-500">Simpan</button>
                        <button type="button" onclick="sourceModalClose()"
                            class="bg-red-500 m-2 w-40 h-10 rounded-xl text-white hover:shadow-lg hover:bg-red-600">Batal</button>
                    </div>
                </form>
            </div>
        </div>
    </div>
    <div class="fixed inset-0 flex items-center justify-center z-50 hidden" id="sourceModalEdit">
        <div class="fixed inset-0 bg-black opacity-50" onclick="sourceModalClose()"></div>
        <div class="fixed inset-0 flex items-center justify-center">
            <div class="w-full md:w-1/2 relative bg-white rounded-lg shadow mx-5">
                <div class="flex items-start justify-between p-4 border-b rounded-t">
                    <h3 class="text-xl font-semibold text-gray-900" id="title_source">
                        Update Konsumen
                    </h3>
                    <button type="button" onclick="sourceModalClose()"
                        class="text-black bg-transparent hover:bg-gray-200 hover:text-gray-900 rounded-lg text-sm w-8 h-8 ml-auto inline-flex justify-center items-center">
                        <i class="fa-solid fa-xmark"></i>
                    </button>
                </div>
                <form method="POST" id="formSourceModalEdit">
                    @csrf
                    <div class="flex flex-col p-4 space-y-6">
                        <div class="mb-5">
                            <label for="konsumen"
                                class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Konsumen</label>
                            <input type="text" id="konsumen_edit" name="konsumen"
                                class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
                                required />
                        </div>
                        <div class="mb-5">
                            <label for="status"
                                class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Status</label>
                            <select id="status_edit"
                                class="js-example-placeholder-single js-states form-control w-full" name="status"
                                data-placeholder="Pilih Status">
                                <option value="">Pilih...</option>
                                <option value="MAHASISWA">MAHASISWA</option>
                                <option value="KARYAWAN">KARYAWAN</option>
                            </select>
                        </div>
                    </div>
                    <div class="flex items-center p-4 space-x-2 border-t border-gray-200 rounded-b">
                        <button type="submit" id="formSourceButtonEdit"
                            class="bg-green-400 m-2 w-40 h-10 rounded-xl hover:bg-green-500">Simpan</button>
                        <button type="button" onclick="sourceModalClose()"
                            class="bg-red-500 m-2 w-40 h-10 rounded-xl text-white hover:shadow-lg hover:bg-red-600">Batal</button>
                    </div>
                </form>
            </div>
        </div>
    </div>
    <script>
        const functionAdd = () => {
            const formModal = document.getElementById('formSourceModal');
            const modal = document.getElementById('sourceModal');

            // Set form action URL
            let url = "{{ route('konsumen.store') }}";
            document.getElementById('title_source').innerText = "Add Jurusan";
            formModal.setAttribute('action', url);

            // Display the modal
            modal.classList.remove('hidden');
            modal.classList.add('flex');

            // Ensure CSRF token is added once
            if (!formModal.querySelector('input[name="_token"]')) {
                let csrfToken = document.createElement('input');
                csrfToken.setAttribute('type', 'hidden');
                csrfToken.setAttribute('name', '_token');
                csrfToken.setAttribute('value', '{{ csrf_token() }}');
                formModal.appendChild(csrfToken);
            }
        }

        const editSourceModal = (button) => {
            const formModal = document.getElementById('formSourceModalEdit');
            const modalTarget = button.dataset.modalTarget;
            const id = button.dataset.id;
            const konsumen = button.dataset.konsumen;
            const statusValue = button.dataset.status;

            let url = "{{ route('konsumen.update', ':id') }}".replace(':id', id);

            console.log(url);
            document.getElementById('title_source').innerText = `Update Konsumen ${konsumen}`;

            document.getElementById('konsumen_edit').value = konsumen;
            document.getElementById('status_edit').value = statusValue;

            let event = new Event('change');
            document.getElementById('status_edit').dispatchEvent(event);

            formModal.setAttribute('action', url);

            if (!formModal.querySelector('input[name="_token"]')) {
                let csrfToken = document.createElement('input');
                csrfToken.setAttribute('type', 'hidden');
                csrfToken.setAttribute('name', '_token');
                csrfToken.setAttribute('value', '{{ csrf_token() }}');
                formModal.appendChild(csrfToken);
            }

            if (!formModal.querySelector('input[name="_method"]')) {
                let methodInput = document.createElement('input');
                methodInput.setAttribute('type', 'hidden');
                methodInput.setAttribute('name', '_method');
                methodInput.setAttribute('value', 'PATCH');
                formModal.appendChild(methodInput);
            }

            document.getElementById(modalTarget).classList.remove('hidden');
        }

        const sourceModalClose = () => {
            document.getElementById('sourceModalEdit').classList.add('hidden');
            document.getElementById('sourceModal').classList.add('hidden');
        }

        const konsumenDelete = async (id, konsumen) => {
            let tanya = confirm(`Apakah anda yakin untuk menghapus Konsumen ${konsumen} ?`);
            if (tanya) {
                await axios.post(`/konsumen/${id}`, {
                        '_method': 'DELETE',
                        '_token': $('meta[name="csrf-token"]').attr('content')
                    })
                    .then(function(response) {
                        // Handle success
                        location.reload();
                    })
                    .catch(function(error) {
                        // Handle error
                        alert('Error deleting record');
                        console.log(error);
                    });
            }
        }
    </script>
</x-app-layout>
```

> TUGAS
>
> Membuat halaman untuk Create, Update, Delete data PRODUK, untuk rancangan table dapat dilihat di rancangan database yang sudah di cantumkan.

### Membuat Halaman Supplier

1. Membuat Table Supplier
   ```php artisam make:migration create_supplier```
2. Buka migration file yang sudah dibuat, lalu samakan dengan gambar di bawah, kemudian migrate atau ketik kode berikut pada terminal ```php artisan migrate```

![](/img/edit_migration_supplier.png ':size=400')

3. Membuat model supplier ```php artisan make:model Supplier```
4. Buka file Model Supplier yang sudah dibuat tadi, lalu samakan dengan gambar di bawah

![](/img/model_supplier.png ':size=400')

5. Membuat Controller Supplier
   ```php artisan make:controller SupplierController --resource```

6. membuat routing pada ```web.php```, simpan routingnya di bawah routing konsumen agar rapi.
   ```Route::resource('supplier', SupplierController::class)->middleware('auth');```

7. Ubah route supplier menjadi redirect ke routing supplier ```bukan dashboard```
   
```html
<x-dropdown-link :href="route('supplier.index')">
    {{ __('Supplier') }}
</x-dropdown-link>
```

8. Isi function function pada controller supplier
   
   function index

```html
   $supplier = Supplier::paginate(5);
        return view('page.supplier.index')->with([
            'supplier' => $supplier,
    );
```

function store

```html
        $data = [
            'supplier' => $request->input('supplier'),
            'no_hp' => $request->input('no_hp'),
            'alamat' => $request->input('alamat')
        ];

        Supplier::create($data);

        return back()->with('message_delete', 'Data Supplier Sudah dihapus');
```

function update

```html
        $data = [
            'supplier' => $request->input('supplier'),
            'no_hp' => $request->input('no_hp'),
            'alamat' => $request->input('alamat')
        ];

        $datas = Supplier::findOrFail($id);
        $datas->update($data);
        return back()->with('message_delete', 'Data Supplier Sudah dihapus');
```

function destroy

```html
        $data = Supplier::findOrFail($id);
        $data->delete();
        return back()->with('message_delete','Data Suppier Sudah dihapus');
```

9. buat folder ```supplier``` di dalam folder page kemudian buat file ```index.blade.php``` di dalamnya, lebih jelasnya seperti pada gambar di bawah

![](/img/view_supplier.png ':size=400')

10. Membuat tampilan supplier, coppy terlebih dahulu kode pada file dashboard.blade.php kemudian salin pada file index.blade.php yang ada pada folder supplier
     
     #### Membuat table data supplier

    hapus baris yang di blok pada gambar di bawah

     ![](/img/hapush_dashboard_supplier.png ':size=400') 

    ganti dengan kode table di bawah

    ```html
{{-- TABLE SUPPLIER --}}
                    <div class="w-full">
                        <div class="relative overflow-x-auto shadow-md sm:rounded-lg">
                            <table class="w-full text-sm text-left rtl:text-right text-gray-500 dark:text-gray-400">
                                <thead
                                    class="text-xs text-gray-700 uppercase bg-gray-50 dark:bg-gray-700 dark:text-gray-400">
                                    <tr>
                                        <th scope="col" class="px-6 py-3">
                                            NO
                                        </th>
                                        <th scope="col" class="px-6 py-3">
                                            SUPPLIER
                                        </th>
                                        <th scope="col" class="px-6 py-3">
                                            NO HP
                                        </th>
                                        <th scope="col" class="px-6 py-3">
                                            ALAMAT
                                        </th>
                                        <th scope="col" class="px-6 py-3">
                                        </th>
                                    </tr>
                                </thead>
                                <tbody>
                                    @php
                                        $no = 1;
                                    @endphp
                                    @foreach ($supplier as $key => $k)
                                        <tr
                                            class="bg-white border-b dark:bg-gray-800 dark:border-gray-700 hover:bg-gray-50 dark:hover:bg-gray-600">
                                            <th scope="row"
                                                class="px-6 py-4 font-medium text-gray-900 whitespace-nowrap dark:text-white">
                                                {{ $supplier->perPage() * ($supplier->currentPage() - 1) + $key + 1 }}
                                            </th>
                                            <td class="px-6 py-4">
                                                {{ $k->supplier }}
                                            </td>
                                            <td class="px-6 py-4">
                                                {{ $k->no_hp }}
                                            </td>
                                            <td class="px-6 py-4">
                                                {{ $k->alamat }}
                                            </td>
                                            <td class="px-6 py-4">
                                                <button type="button" data-id="{{ $k->id }}"
                                                    data-modal-target="sourceModal"
                                                    data-supplier="{{ $k->supplier }}" data-no_hp="{{ $k->no_hp }}"
                                                    data-alamat="{{ $k->alamat }}" onclick="editSourceModal(this)"
                                                    class="bg-amber-500 hover:bg-amber-600 px-3 py-1 rounded-md text-xs text-white">
                                                    Edit
                                                </button>
                                                <button
                                                    onclick="return supplierDelete('{{ $k->id }}','{{ $k->supplier }}')"
                                                    class="bg-red-500 hover:bg-bg-red-300 px-3 py-1 rounded-md text-xs text-white">Delete</button>
                                            </td>
                                        </tr>
                                    @endforeach
                                </tbody>
                            </table>
                        </div>
                        <div class="mt-4">
                            {{ $supplier->links() }}
                        </div>
                    </div>
```

    #### Membuat Title data supplier

    Pada baris ke 10 di enter untuk mendapatkan baris kosong di baris ke 11, kemudian ketik kode berikut di baris ke 11
    ```html
                {{-- TITLE --}}
                <div class="p-4">
                    <div>DATA SUPPLIER</div>
                </div>
    ```

    #### Membuat Form Tambah Data Supplier

    Pada baris ke 14 tambahkan ```flex gap-5``` pada ```class```, kemudian enter pada baris ke 14 sehingga menghasilkan baris kosong di baris ke 15
    kemudian ketik kode berikut di baris ke 15
    ```html
{{-- FORM ADD SUPPLIER --}}
                    <div class="w-full bg-gray-100 p-4 rounded-xl" >
                        <div class="mb-5">
                            INPUT DATA SUPPLIER
                        </div>
                        <form action="{{route('supplier.store')}}" method="post">
                            @csrf
                            <div class="mb-5">
                                <label for="base-input" class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Supplier</label>
                                <input name="supplier" type="text" id="base-input" class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500">
                            </div>
                            <div class="mb-5">
                                <label for="base-input" class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">No HP</label>
                                <input name="no_hp" type="text" id="base-input" class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500">
                            </div>
                            <div class="mb-5">
                                <label for="base-input" class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Alamat</label>
                                <textarea name="alamat" type="text" id="base-input" class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"></textarea>
                            </div>
                            <button type="submit"
                            class="text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm w-full sm:w-auto px-5 py-2.5 text-center dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800">SIMPAN</button>
                        </form>
                    </div>
```
 #### Membuat form modal update data supplier

 Simpan kode ini di atas tutup tag ```</x-app-layout>```

 ```html
 <div class="fixed inset-0 flex items-center justify-center z-50 hidden" id="sourceModal">
        <div class="fixed inset-0 bg-black opacity-50"></div>
        <div class="fixed inset-0 flex items-center justify-center">
            <div class="w-full md:w-1/2 relative bg-white rounded-lg shadow mx-5">
                <div class="flex items-start justify-between p-4 border-b rounded-t">
                    <h3 class="text-xl font-semibold text-gray-900" id="title_source">
                        Update Sumber Database
                    </h3>
                    <button type="button" onclick="sourceModalClose(this)" data-modal-target="sourceModal"
                        class="text-gray-400 bg-transparent hover:bg-gray-200 hover:text-gray-900 rounded-lg text-sm w-8 h-8 ml-auto inline-flex justify-center items-center"
                        data-modal-hide="defaultModal">
                        <i class="fa-solid fa-xmark"></i>
                    </button>
                </div>
                <form method="POST" id="formSourceModal">
                    @csrf
                    <div class="flex flex-col  p-4 space-y-6">
                        <div class="">
                            <label for="text" class="block mb-2 text-sm font-medium text-gray-900">Supplier</label>
                            <input type="text" id="supplier" name="supplier"
                                class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
                                placeholder="Masukan kelas disini...">
                        </div>
                        <div class="">
                            <label for="text" class="block mb-2 text-sm font-medium text-gray-900">No HP</label>
                            <input type="text" id="no_hp" name="no_hp"
                                class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
                                placeholder="Masukan kelas disini...">
                        </div>
                        <div class="">
                            <label for="text" class="block mb-2 text-sm font-medium text-gray-900">Alamat</label>
                            <textarea type="text" id="alamat" name="alamat"
                                class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
                                placeholder="Masukan kelas disini..."></textarea>
                        </div>
                    </div>
                    <div class="flex items-center p-4 space-x-2 border-t border-gray-200 rounded-b">
                        <button type="submit" id="formSourceButton"
                            class="bg-green-400 m-2 w-40 h-10 rounded-xl hover:bg-green-500">Simpan</button>
                        <button type="button" data-modal-target="sourceModal" onclick="sourceModalClose(this)"
                            class="bg-red-500 m-2 w-40 h-10 rounded-xl text-white hover:shadow-lg hover:bg-red-600">Batal</button>
                    </div>
                </form>
            </div>
        </div>
    </div>
 ```

 #### Membuat script function update modal
 buat tag script di paling bawah setelah tutp tag ```</x-app-layout>```
 buat function update berikut di dalam tag script
 ```html
 const editSourceModal = (button) => {
            const formModal = document.getElementById('formSourceModal');
            const modalTarget = button.dataset.modalTarget;
            const id = button.dataset.id;
            const supplier = button.dataset.supplier;
            const no_hp = button.dataset.no_hp;
            const alamat = button.dataset.alamat;
            let url = "{{ route('supplier.update', ':id') }}".replace(':id', id);

            let status = document.getElementById(modalTarget);
            document.getElementById('title_source').innerText = `UPDATE SUPPLIER ${supplier}`;

            document.getElementById('supplier').value = supplier;
            document.getElementById('no_hp').value = no_hp;
            document.getElementById('alamat').value = alamat;

            document.getElementById('formSourceButton').innerText = 'Simpan';
            document.getElementById('formSourceModal').setAttribute('action', url);
            let csrfToken = document.createElement('input');
            csrfToken.setAttribute('type', 'hidden');
            csrfToken.setAttribute('value', '{{ csrf_token() }}');
            formModal.appendChild(csrfToken);

            let methodInput = document.createElement('input');
            methodInput.setAttribute('type', 'hidden');
            methodInput.setAttribute('name', '_method');
            methodInput.setAttribute('value', 'PATCH');
            formModal.appendChild(methodInput);

            status.classList.toggle('hidden');
        }

        const sourceModalClose = (button) => {
            const modalTarget = button.dataset.modalTarget;
            let status = document.getElementById(modalTarget);
            status.classList.toggle('hidden');
        }
 ```

 #### Membuat Script function delete

buat function berikut di dalam tag script, boleh di atas function edit atau di bawah 

```html
        const kelasDelete = async (id, kelas) => {
            let tanya = confirm(`Apakah anda yakin untuk menghapus kelas ${kelas} ?`);
            if (tanya) {
                await axios.post(`/kelas/${id}`, {
                        '_method': 'DELETE',
                        '_token': $('meta[name="csrf-token"]').attr('content')
                    })
                    .then(function(response) {
                        // Handle success
                        location.reload();
                    })
                    .catch(function(error) {
                        // Handle error
                        alert('Error deleting record');
                        console.log(error);
                    });
            }
        }

```






