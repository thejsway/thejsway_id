# Style guide {#style-guide}

Berikut aturan dan prinsip koding yang digunakan di seluruh buku ini.

> Bab ini sebenarnya subjektif dan mengandung opini. Silakan putuskan berdasarkan pilihan Kamu sendiri.

## Penamaan

Penamaan diatur agar kode lebih bershi dan mudah dipahami. Beberapa aturan penamaan dipresentasikan di bawah ini.

### Pilih nama yang bermakna

Aturan paling penting adalah memberikan setiap elemen (variabel, fungsi, class, dan lainnya) satu nama yang spesifik yang mencerminkan perannya. Variabel yang mengandung nilai jari-jari (radius) lingkaran harus dinamakan `radius` rather dibandingkan `num` or `myVal`.

Keringkasan harus dibatasi pada elemen yang pendek penggunaannya, seperti perhitungan loop.

### Jangan gunakan kata yang sudah direservasi

Setiap kata kunci JavaScript adalah nama yang telah direservasi. Kata ini tidak boleh digunakan untuk penamaan variabel. Berikut adalah [daftar kata direvervasi di JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Lexical_grammar#Keywords).

### Ikuti aturan penamaan

Dibutuhkan beberapa kata untuk mendeskripsikan peran elemen tertentu dengan tepat. Buku ini mengadopsi aturan penamaan [camelCase](https://en.wikipedia.org/wiki/Camel_case) yang populer, berdasarkan dua prinsip utama:

* Semua nama dimulai dengan huruf **kecil**.
* Jika nama terdiri dari beberapa kata, huruf pertama dari setiap kata (kecuali kata pertama) adalah **kapital**.

Selain itu, buku ini menggunakan aturan penamaan berikut ini:

* Nama fungsi dan method adalah **kata kerja aktif**: `computeTotal()`, `findFirstParent()`, `attackTarget()`, dan lainnya.
* Agar tetap konsisten dengan bahasa pemrograman lainnya, nama class dimulai dengan huruf **kapital** letter: `User` dibandingkan `user`.
* Karena kemungkinan terdiri dari banyak element, array dimakan **secara jamak** atau diakhiri dengan `List`: `movies` atau `movieList`, bukan `movie`.
* Untuk membedakannya dengan variabel lainnya, elemen DOM diakhiri dengan `Element` (or `Elements` untuk variabel mirip dengan array): `divElement` dibandingkan hanya `div`.

> Seperti banyak bahasa lainnya, JavaScript **sensitif terhadap huruf besar/kecil**. Sebagai contoh, `myVariable` dan `myvariable` adalah dua nama variabel yang berbeda. Hati-hati!

## Memformat kode

Hal ini merupakan subjek yang banyak diperdebatkan di komunitas JavaScript: penggunaan spasi atau tabulasi untuk indentasi, penambahan tanda titik koma, tanda kutip satu atau tanda kutip dua untuk string, dan lainnya.

Solusi termudah dan sederhana adalah dengan mengandalkan tool untuk mengotomasi pekerjaan tingkat rendah dalam memformat kode, sehingga Kamu bisa fokus pada pekerjaan tingkat tinggi. Buku ini menggunakan [Prettier](https://github.com/prettier/prettier) dengan konfigurasi bawaan (penggunaan kutip dua dan tidik koma).

## Kualitas kode

Karena JavaScript adalah bahasa yang ditulis secara dinamis, beberapa kesalahan tidak muncul sampai ketika dieksekusi: kesalahan pemberian nama fungsi, memuat module yang tidak ada, dan lainnya. Selain itu, banyak kesalahan lainnya seperti mendeklarasikan satu variabel tanpa pernah menggunakannya tidak akan berpengaruh pada hasil eksekusi, tetapi akan membuat kode Kamu lebih sulit dibaca dan menurunkan kualitas secara keseluruhan.

Untungnya, tool spesial dinamakan **linters** bisa mengecek kode Kamu terhadap aturannya ketika penulisan dan memperingatkan tentang potensi kerusakan/kesalahan. Dengan memungkinkannya perbaikan banyak bug sebelum terjadi, linters dapat meningkatkan produktivitas developer dengan sangat luar biasa.

Buku ini menggunakan [ESLint](http://eslint.org) untuk kode linters. ESLint adalah tool yang sangat fleksibel dan Kamu bisa menyesuaikannya sesuai kebutuhan. Beberapa aturan ESLint telah muncul, di mana yang sangat populer adalah [AirBnb Style Guide](https://github.com/airbnb/javascript).

> Opini style guide ini sangat pantas untuk dibaca.

Konfigurasi ESLint buku ini memperluas aturan AirBnb dan Prettier (Prettier lebih diutamakan), dengan sedikit deviasi minor.

Berikut ini file `.eslintrc` dari konfigurasi buku ini.

```json
{
  "extends": ["airbnb", "prettier"],
  "env": {
    "browser": true
  },
  "plugins": ["prettier"],
  "rules": {
    "no-console": "off",
    "no-alert": "off",
    "no-plusplus": "off",
    "default-case": "off",
    "no-param-reassign": [
      "error",
      {
        "props": false
      }
    ],
    "arrow-body-style": [
      "error",
      "as-needed",
      { "requireReturnForObjectLiteral": true }
    ]
  }
}
```

Deviasi dari aturan bawaannya dijelaskan sebagai berikut.

* `"no-console"` dan `"no-alert"`: untuk mengaktifkan panggilan `console.XXX()` dan `alert()`.
* `"no-plusplus"`: untuk mengaktifkan operator unary seperti `++`, umumnya digunakan dan biasanya tidak merusak.
* `"default-case"`: untuk mengaktifkan pernyataan `switch` tanpa case `default` case, yang merupakan hal umum.
* `"no-param-reassign"`: untuk mengaktifkan update properti dari objek yang ditempatkan sebagai parameter.
* `"arrow-body-style"`: untuk menggunakan sintaks `return` yang lebih eksplisit untuk fungsi panah yang mengembalikan objek literal.
