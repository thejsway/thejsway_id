# Bekerja dengan string

Banyak kode yang Kamu tulis akan melibatkan modifikasi berantai untuk karakter teks - atau [string]( https://en.wikipedia.org/wiki/String_(computer_science) ). Mari lihat caranya!

## TL;DR

* Walaupun nilai string adalah tipe JavaScript yang primitif, beberapa **property** dan **method** bisa diterapkan pada string seperti halnya objek.

* Properti `length` mengembalikan jumlah karakter pada string.

* String JavaScript **[immutable]( https://en.wikipedia.org/wiki/Immutable_object )**: ketika dibuat, nilai string tidak akan pernah berubah. Method string tidak pernah mempengaruhi nilai inisial dan selalu mengembalikan nilai string yang baru.

* Method `toLowerCase()` and `toUpperCase()` mengembalikan perubahan string ke huruf kapital dan huruf kecil.

* Nilai string bisa dibandingkan dengan menggunakan operator `===`, yang case sensitive.

* A string may be seen as an **array of characters** identified by their **index**. The index of the first character is 0 (not 1).

* Kamu bisa meng-iterasi string dengan menggunakan loop `for` atau `for-of` yang lebih baru.

* Method `Array.from()` bisa digunakan untuk mengubah string ke array yang bisa dijelajahi huruf demi huruf dengan method `forEach()`.

* Mencari nilai di dalam string memungkinkan dengan method `indexOf()`, `startsWith()` dan `endsWith()`.

* Method `split()` memecah string ke beberapa bagian yang dibatasi oleh sebuah pemisah.

## Ringkasan string 

Mari kita rekapitulasi apa yang sudah kita tahu tentang string:

* Nilai string merepresentasikan teks.

* Di JavaScript,  string didefinisikan dengan menempatkan teks di dalam tanda petik tunggal (`'I am a string'`) atau tanda petik ganda (`"I am a string"`).

* Kamu bisa menggunakan karakter spesial di dalam string dengan menempatka tanda `\` ("backslash") diikuti oleh karakter lain. Contohnya, gunakan `\n` untuk menambah baris baru.

* Operator `+` menggabungkan dua atau lebih string.

Selain fungsi dasar ini, string bahkan memiliki kemampuan lain yang serba guna.

## Mendapatkan panjang string 

Untuk mendapatkan **panjang** string (jumlah karakternya), tambahkan `.length`. Panjang string ini bernilai integer.

```js
console.log("ABC".length); // 3
const str = "I am a string";
const len = str.length;
console.log(len); // 13
```

Walaupun nilai string adalah tipe primitif JavaScript, beberapa properti dan methods bisa diaplikasikan seperti halnya objek menggunakan **notasi dot**. Properti `length` adalah salah satunya.

## Mengubah bentuk string 

Kamu bisa mengubah teks string ke bentuk **huruf kecil** dengan menggunakan method `toLowerCase()`. Alternatif lain, Kamu juga bisa mengubah ke huruf kapital dengan menggunakan `toUpperCase()`.

```js
const originalWord = "Bora-Bora";

const lowercaseWord = originalWord.toLowerCase();
console.log(lowercaseWord); // "bora-bora"

const uppercaseWord = originalWord.toUpperCase();
console.log(uppercaseWord); // "BORA-BORA"
```

`toLowerCase()` dan `toUpperCase()` adalah dua method string. Seperti setiap method string, keduanya tidak mempengaruhi nilai awal dan mengembalikan string baru.

> Penting untuk memahami bahwa ketika dibuat, nilai string tidak akan pernah berubah: string adalah **immutable** di JavaScript.

## Membandingkan dua string

Kamu bisa membandingkan dua string dengan menggunakan operator `===`. Operasi ini mengembalikan nilai boolean: `true` jika string sama, `false` jika tidak.

```js
const word = "koala";
console.log(word === "koala");    // true
console.log(word === "kangaroo"); // false
```

> Perbandingan string comparison adalah case sensitive. Perhatikan huruf kecil dan besarnya!

```js
console.log("Qwerty" === "qwerty");               // false
console.log("Qwerty".toLowerCase() === "qwerty"); // true
```

## String sebagai kumpulan dari huruf 

### Identifikasi huruf tertentu

Kamu bisa berpikir bahwa string adalah array dari beberapa huruf. Setiap huruf diidentifikasi dengan nomor yang dinamakan index, seperti halnya pada array. Peraturannya juga sama:

* Index huruf pertama pada string adalah 0, bukan 1.
* Nomor index tertinggi adalah panjang string dikurangi 1.

### Akses huruf tertentu

Kamu tahu cara mengidentifikasi huruf berdasarkan index-nya. Untuk mengaksesnya, Kamu bisa gunakan **notasi tanda kurung siku** `[]` dengan nomor index ditempatkan di dalam tanda tersebut.

> Mencoba mengakses huruf dari string melebihi panjang string akan menghasilkan `undefined`.

```js
const sport = "basketball";
console.log(sport[0]);  // first "b"
console.log(sport[6]);  // second "b"
console.log(sport[10]); // undefined: huruf terakhir berada di index ke 9
```

### Iterasi string

Sekarang bagaimanak kalau Kamu ingin mengakses semua huruf pada string satu per satu? Kamu bisa mengaksesnya, seperti contoh berikut:

```js
const name = "Sarah"; // 5 huruf
console.log(name[0]); // "S"
console.log(name[1]); // "a"
console.log(name[2]); // "r"
console.log(name[3]); // "a"
console.log(name[4]); // "h"
```

Hal ini tidaklah praktis kalau string Kamu mengandung huruf yang tidak sedikit. Kamu perlu solusi lebih baik untuk *mengulang* akses ke huruf tersebut. Apakah kata "mengulang" terbesit di benak Kamu, mengingat konsep sebelumnya yang sudah kita bahas? Loop, *dong*!

Kamu bisa menulis **loop** untuk mengakses setiap huruf dari string. Biasanya, loop `for` adalah pilihan yang lebih baik daripada loop `while`, karena kita tahu bahwa loop perlu berjalan sekali untuk setiap huruf di dalam string. 

```js
for (let i = 0; i < myString.length; i++) {
    // Menggunakan myString[i] untuk mengakses setiap huruf satu per satu
}
```

Penghitung loop `i` terbentang mulai 0 (index huruf pertama dari string) sampai dengan panjang string - 1 (index dari huruf terakhir). Ketika nilai penghitung sama dengan panjang string, ekspresinya menjadi false dan loop berakhir.

Jadi, contoh sebelumnya bisa juga ditulis dengan loop `for` untuk hasil yang identik. 

```js
const name = "Sarah";
for (let i = 0; i < name.length; i++) {
  console.log(name[i]);
}
```

Untuk array yang sudah dibahas sebelumnya, evolusi JavaScript terbaru telah mengenalkan opsi lain untuk meng-iterasi string: loop `for-of`. Contoh sebelumnya juga bisa ditulis:

```js
const name = "Sarah";
for (const letter of name) {
  console.log(letter);
}
```

Jika index tidak diperlukan di dalam loop, sintaks ini lebih sederhana dibandingkan loop standar `for`.

## Mengubah string menjadi array 

Method JavaScript `Array.from()` bisa digunakan untuk mengubah string menjadi array. Array ini bisa dijelajahi lebih lanjut dengan method `forEach()`. Seperti sebelumnya, contoh ini menampilkan huruf string satu per satu. 

```js
const name = "Sarah";
const nameArray = Array.from(name);
nameArray.forEach(letter => {
  console.log(letter);
});
```

## Mencari di dalam string

Mencari nilai tertentu di dalam string adalah satu aktivitas yang sering dilakukan.

Method `indexOf()` mengambil parameter nilai yang akan dicari. Jika nilai ini ditemukan di dalam string, method ini mengembalikan index yang pertama kali ditemukan. Jika tidak, akan mengembalikan nilai -1.

```js
const song = "Honky Tonk Women";
console.log(song.indexOf("onk")); // 1
console.log(song.indexOf("Onk")); // -1 karena perbedaan huruf besar/kecil
```

Kalau ingin mencari nilai di awal atau di akhir string, Kamu bisa gunakan method `startsWith()` dan `endsWith()`. Keduanya mengembalikan nilai antara `true` atau `false`, tergantung apakah nilainya ditemukan atau tidak. Hati-hati: method ini case-sensitive.

```js
const song = "Honky Tonk Women";

console.log(song.startsWith("Honk")); // true
console.log(song.startsWith("honk")); // false
console.log(song.startsWith("Tonk")); // false

console.log(song.endsWith("men")); // true
console.log(song.endsWith("Men")); // false
console.log(song.endsWith("Tonk")); // false
```

## Memecah string menjadi beberapa bagian

Terkadang string dibuat dari beberapa bagian nilai tertentu. Pada kasus ini, untuk mendapatkan bagian masing-masing ini bisa menggunakan method `split()`. Method ini mengambil parameter pemisah dan mengembalikan array yang mengadung bagian dari string.

```js
const monthList = "Jan,Feb,Mar,Apr,May,Jun,Jul,Aug,Sep,Oct,Nov,Dec";
const months = monthList.split(",");
console.log(months[0]);  // "Jan"
console.log(months[11]); // "Dec"
```

## Waktu koding!

### Informasi kata

Tulis program yang meminta pengguna untuk menulis kata lalu menampilkan jumlah total hurufnya, jumlah huruf kecil, dan huruf besarnya.

### Menghitung huruf vokal

Perbarui program sebelumnya sehingga dapat juga menampilkan jumlah vokal di dalam kata.

### Kata terbalik 

Perbarui program sebelumnya sehingga bisa menampilkan kata yang ditulis secara terbalik.

### Palindrome

Perbarui program sebelumnya untuk mengecek apakah kata tersebut palindrome. Palindrome adalah kata yang tetap sama walaupun ditulis secara terbalik.

> `"radar"` termasuk palindrome, `"Radar"` juga.
