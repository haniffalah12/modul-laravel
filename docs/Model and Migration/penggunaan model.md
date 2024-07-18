---
sidebar_position: 4
---

# 8.4 Penggunaan Model

Dengan model Book, kita dapat melakukan operasi CRUD. Berikut adalah beberapa contoh penggunaannya:
**Menambahkan Data**
```
use App\Models\Book;

$book = new Book();
$book->title = 'To Kill a Mockingbird';
$book->author = 'Harper Lee';
$book->published_year = 1960;
$book->save();
```
Atau menggunakan cara mass assignment:
```
Book::create([
    'title' => '1984',
    'author' => 'George Orwell',
    'published_year' => 1949
]);
```

**Mengambil Data**

Mengambil semua data buku:
```
$books = Book::all();
```

Mengambil satu buku berdasarkan ID:
```
$book = Book::find(1);
```

**Mengupdate Data**

Mengupdate data buku:
```
$book = Book::find(1);
$book->title = 'New Title';
$book->save();
```
Atau menggunakan cara mass assignment:
```
Book::where('id', 1)->update(['title' => 'New Title']);
```


**Menghapus Data**

Menghapus satu buku berdasarkan ID:
```
$book = Book::find(1);
$book->delete();
```

Atau menggunakan cara langsung:
```
Book::destroy(1);
```
Dengan Model dan Migration, manajemen dan interaksi dengan database menjadi lebih mudah dan terstruktur dalam aplikasi Laravel.
