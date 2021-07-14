# Apa itu halaman web?

Di bab singkat ini meringkas apa yang perlu Kamu ketahui tentang web dan halaman web.

## TL;DR

* [World Wide Web](https://en.wikipedia.org/wiki/World_Wide_Web) (atau **Web**) adalah sebuah ruang informasi yang dibuat di atas [Internet](https://en.wikipedia.org/wiki/Internet). Sumber daya Web bisa diakses melalui [URL](https://en.wikipedia.org/wiki/Uniform_Resource_Locator), dan bisa mengandung [hyperlinks](https://en.wikipedia.org/wiki/Hyperlink) ke sumber lainnya.

* Halaman web adalah dokumen yang cocok dengan Web. Membuat halaman web biasanya melibatkan tiga teknologi: [HTML](https://en.wikipedia.org/wiki/HTML) untuk strukturisasi konten, [CSS](https://en.wikipedia.org/wiki/Cascading_Style_Sheets) untuk mendefinisikan presentasi halaman web dan JavaScript untuk menambah interaktivitas. 

* Dokumen HTML terbuat dari teks dan struktural elemen dinamakan **tag** yang mendeskripsikan konten halaman, seperti: paragraf, heading, hyperlink, gambar, dan lainnya.

* CSS menggunakan **selector** untuk mendeklarasikan elemen HTML yang akan diterapkan. Elemen bisa dipilih dengan nama tag (`h1`), dengan class (`.done`) atau dengan identifier (`#rude`).

* Dokumen HTML di dalamnya termasuk CSS stylesheet dengan sebuah tag `<link>` tag dan JavaScript file dengan tag `<script>`.

```html
<!doctype html>
<html>

<head>
    <!-- Informasi halaman: judul, karakter, dan lainnya -->

    <!-- Link ke CSS stylesheet -->
    <link href="path/to/file.css" rel="stylesheet" type="text/css">
</head>

<body>
    <!-- Konten halaman -->

    <!-- Link ke file JavaScript -->
    <script src="path/to/file.js"></script>
</body>

</html>
```

* **Browser** adalah perangkat lunak yang Kamu gunakan untuk mengunjungi halan web dan menggunakan aplikasi web. Pada browser modern juga terdapat seperangkat **developer tool** untuk memudahkan dalam pengembangan web.

## Internet dan Web

Seperi yang Kamu ketahui, [World Wide Web](https://en.wikipedia.org/wiki/World_Wide_Web) (atau disingkat **Web**) adalah ruang informasi luas yang dibangun di atas [Internet](https://en.wikipedia.org/wiki/Internet). Sumber daya Web bisa diakses melalu alamatnya, dinamakan [URL](https://en.wikipedia.org/wiki/Uniform_Resource_Locator), dan bisa mengandung [hyperlink](https://en.wikipedia.org/wiki/Hyperlink) ke sumber lainnya. Bersamaan, semua sumber daya ini tersambung  membentuk jaringan besar yang mirip dengan jala laba-laba.

Dokumen yang cocok untuk web dinamakan halaman web. Dokumen ini dikelompokkan dalam **website** dan dapat dikunjungi melalui perangkat lunak khusus dinamakan [browser](https://en.wikipedia.org/wiki/Web_browser).

## Bahasa Web

Ada tiga teknologi utama dalam membuat halaman web: HTML, CSS dan JavaScript.

### HTML

HTML, singkatan dari [HyperText Markup Language](https://en.wikipedia.org/wiki/HTML), adalah format dokumen dari halaman web. Sebuah dokumen HTML dibuat dari teks dan elemen struktural dinamakan **tag**. Tag digunakan untuk mendeskripsikan konten halaman: paragrag, heading, hyperlinks, gambar, dan lainnya.

Berikut contoh dari halaman web sederhana, biasanya disimpan dalam file `.html`.

```html
<!doctype html>
<html>

<head>
    <meta charset="utf-8">
    <title>My web page</title>
</head>

<body>
    <h1>My web page</h1>
    <p>Hello! My name's Baptiste.</p>
    <p>I live in the great city of <a href="https://en.wikipedia.org/wiki/Bordeaux">Bordeaux</a>.</p>
</body>

</html>
```

![Display result](images/chapter13-01.png)

Berikut beberapa referensi untuk pembelajaran lebih lanjut tentang HTML:

* [Interneting is Hard - A friendly web development tutorial for complete beginners](https://internetingishard.com/html-and-css/)
* [Khan Academy - Intro to HTML](https://www.khanacademy.org/computing/computer-programming/html-css#intro-to-html)
* [Mozilla Developer Network - HTML reference](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference)

### CSS

CSS, atau [Cascading Style Sheets](https://en.wikipedia.org/wiki/Cascading_Style_Sheets), adalah bahasa yang digunakan untuk mengubah tampilan dari halaman web.

CSS menggunakan **selector** untuk mendeklarasikan elemen HTML mana yang akan diterapkan. Banyak strategi pemilihan yang memungkinkan, beberapa diantaranya: 

* Semua elemen yang ada nama tag-nya.
* Elemen yang ada  **class**-nya (sintaks selector: `.myClass`).
* Elemen yang ada **identifier** unik (sintaks selector: `#MyId`).

Berikut contoh penulisan CSS, biasanya disimpan dalam file `.css`.

```css
/* Semua halaman elemen h1 elements berwarna merah muda */
h1 {
   color: pink;
}

/* Semua elemen dengan "done" dicoret */
.done {
  text-decoration: line-through;
}

/* Semua elemen yang memiliki id "rude" ditampilkan dengan huruf kapital dengan font tertentu */
#rude {
  font-family: monospace;
  text-transform: uppercase;
}
```

Style sheet diasosiasikan dengan dokumen HTML menggunakan tag `link` di bagian halaman `head`.

```html
<!-- Link ke stylesheet -->
<link href="path/to/file.css" rel="stylesheet" type="text/css">
```

Untuk pembelajaran lebih lanjut, kunjungi link berikut:

* [Khan Academy - Intro to CSS](https://www.khanacademy.org/computing/computer-programming/html-css#intro-to-css)
* [Mozilla Developer Network - CSS reference](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference)

### JavaScript

JavaScript bisa berinteraksi dengan dokumen HTML supaya lebih interaktif dan dinamis: response terhadap aksi dari pengguna pada halaman, tampilan dinamis, animasi, dan lainnya. Hanya bahasa ini yang dipahami oleh semua browser web.

File JavaScript, biasanya disimpan dalam file `.js`, dibuka oleh halaman web dengan tag `<script>`.

```html
<!-- Membuka file JavaScript -->
<script src="path/to/file.js"></script>
```

## Mengembangkan halaman web 

Untuk membuat halaman web interaktif, Kamu perlu menulis kode HTML, CSS dan JavaScript. Jika Kamu baru saja mulai, cara termudahnya adalah dengan menggunakan playround JavaScript. Tetapi, Kamu mungkin juga ingin mengembangkan web secara lebih profesional nantinya, atau Kamu perlu bekerja secara offline.

Lihat lampiran untuk detail cara menge-set environment Kamu.

## Waktu koding!

Kamu bisa lewatkan latihan ini jika Kamu sudah berpengalaman dengan HTML dan CSS.

### Halamn web pertama Kamu 

Ikuti tutorial [Getting started with the Web](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web) dari Mozilla Developer Network untuk membuat halaman web sederhana menggunakan HTML dan CSS. Langkah yang diperlukan adalah:

1. [What will your website look like?](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/What_will_your_website_look_like)
1. [Dealing with files](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/Dealing_with_files)
1. [HTML basics](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/HTML_basics)
1. [CSS basics](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/CSS_basics)

![Expected result](images/chapter12-02.png)
