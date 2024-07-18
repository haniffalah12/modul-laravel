---
sidebar_position: 5
---

# 8.5 Contoh kasus

Misalkan kita ingin membuat aplikasi untuk mengelola buku di perpustakaan. Kita akan membuat tabel books dengan kolom id, title, author, dan published_year.

1. Langkah 1: Membuat Migration

Pertama, kita buat migration untuk tabel `books.`
```
php artisan make:migration create_books_table
```

Ini akan membuat file migration di folder `database/migrations.` Buka file tersebut dan edit isinya:
```
<?php
use Illuminate\Database\Migrations\Migration;
use Illuminate\Database\Schema\Blueprint;
use Illuminate\Support\Facades\Schema;

class CreateBooksTable extends Migration
{
    /**
     * Run the migrations.
     *
     * @return void
     */
    public function up()
    {
        Schema::create('books', function (Blueprint $table) {
            $table->id();
            $table->string('title');
            $table->string('author');
            $table->year('published_year');
            $table->timestamps();
        });
    }

    /**
     * Reverse the migrations.
     *
     * @return void
     */
    public function down()
    {
        Schema::dropIfExists('books');
    }
}
```

2. Langkah 2: Menjalankan Migration

Setelah mengedit file migration, jalankan perintah berikut untuk menerapkan perubahan pada database:
```
php artisan migrate
```

3. Langkah 3: Membuat Model

Setelah tabel dibuat, kita buat model Book yang akan berinteraksi dengan tabel books.
```
php artisan make:model Book
```

ini akan membuat file model di `folder app/Models.` Buka file tersebut dan pastikan isinya seperti ini:
```
<?php

namespace App\Models;

use Illuminate\Database\Eloquent\Factories\HasFactory;
use Illuminate\Database\Eloquent\Model;

class Book extends Model
{
    use HasFactory;

    protected $fillable = ['title', 'author', 'published_year'];
}
```