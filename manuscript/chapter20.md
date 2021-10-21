# Pengembangan web 

Memahami dasar atau fundamental pengembangan web merupakan hal krusial bagi setiap developer JavaScript developer. Mari kita bahas topik ini.

> Beberapa bab ini terinspirasi dari [Dokumentasi Symfony PHP framework](http://symfony.com/doc/current/introduction/http_fundamentals.html).

## TL;DR

* Data bertukaran di web mengikuti paradigma **permintaan/respons**. Satu **client** melakukan permintaan ke **server**, yang memproses permintaan tersebut dan mengirimkan kembali hasilnya ke client.

* **HTTP** (HyperText Transfer Protocol), adalah protokol yang memungkinkan dua mesin untuk berkomunikasi dengan lainnya di web. Versi amannya adalah **HTTPS**.

* HTTP didasari oleh perintah tekstual. **Method** HTTP mendefinisikan tipe dari permintaan. Method utama HTTP adalah `GET` untuk mengakses satu resource dan `POST` untuk mendorong beberapa informasi ke server.

* Respons HTTP mengandung **kode status** yang mengindikasikan hasil dari permintaan: 200 untuk sukses, 404 untuk resource yang tidak ditemukan, dan lainnya.

* Resources web beralamat unik diambil dari **URL** (Uniform resource locator). URL adalah teks dari bentuk `http://www.mywebsite.com/myresourcepath/myresource`.

* Pada skenario pengembangan web tradisional, aksi pengguna di halaman web memicu pembukaan kembali halaman secara penuh setelah permintaan sinkron ke server. Pengembangan web lainnya, disebut **AJAX** (Asynchronous JavaScript and XML), menggunakan JavaScript dan permintaan HTTP secara **asynchronous** untuk mengambil data ketika dibutuhkan dan meng-update hanya bagian yang diinginkan dari halaman. Hal ini memungkinkan pembuatan **aplikasi web**, yang bertujuan untuk menawarkan *user experience* dari aplikasi *native*.

* Permintaan cross-domain AJAX dimungkinkan jika server telah dikonfigurasi untuk menerima permintaan tersebut dengan mengatur **cross-origin resource sharing** (CORS).

* **JSON** (JavaScript Object Notation), sintaks tekstual untuk mendeskripsikan informasi yang terstruktur, telah menggantikan XML sebagai format data di web. Dokumen JSON terdiri dari satu set pasangan nama/nilai.

## Bagaimana web bekerja

Menjelajahi web sangatlah mudah. Katakanlah Kamu ingin baca komik hari ini dari situs web populer [xkcd](https://xkcd.com). Kamu ketik teks `"xkcd.com"` di kotak alamat browser Kamu dan tadaa, komik muncul (asumsi tidak ada permasalahan jaringan).

Mari kita coba memahami apa yang terjadi dibalik layar.

### Server web 

Untuk bisa online, sebuah situs web harus dipublikasikan di **server**. Ini adalah mesin jenis spesial yang tugasnya adalah untuk menunggu dan menjawab permintaan dari klien. Server yang mempublikasikan resource di web secara logika dinamakan **server web**.

Lebih tepatnya, mesin server web menjalankan program perangkat lunak tertentu (juga dinamakan server web) dapat mempublikasikan situs web. Yang paling populer adalah [Apache](http://httpd.apache.org/), [Microsoft IIS](http://www.iis.net/) dan [nginx](http://nginx.org).

### Web client

Mesin yang meminta server untuk resource dinamakan **web client**. Sebenarnya, client sebenarnya adalah program perangkat lunak berjalan di mesin. Web client yang cukup dikenal adalah **browser**, satu program yang memiliki spesialisasi dalam menampilkan halaman web. Web browser terkenal diantaranya [Mozilla Firefox](https://www.mozilla.org/firefox), [Chrome](https://www.google.com/chrome/browser/), [Safari](https://www.apple.com/safari/) dan [Opera](http://www.opera.com/fr).

Tidak semua web client adalah browser. Contohnya, robot mesin pencari dan aplikasi mobile juga mengkontak server dan memintanya untuk konten.

### Komunikasi antara client dan server

Pertukaran data di Web mengikuti paradigma **permintaan/respons**.

![A web exchange example](images/chapter20-01.png)

1. Pertukaran dimulai oleh client, yang mengirimkan satu **permintaan** ke server untuk mengakses resource web tertentu.
1. Server mempersiapkan hasil dari permintaan.
1. Server mengirim balik hasil ini ke client.

Untuk memahami satu dengan yang lainnya, client dan server web menggunakan protokol umum: HTTP.

## HTTP, protokol web 

HTTP, singkatan dari **HyperText Transfer Protocol**, adalah fondasi teknikal dari World Wide Web. Ini adalah **protokol**, bahasa yang memungkinkan dua mesin untuk berkomunikasi satu dengan lainnya.

> HTTPS adalah versi aman dari HTTP.

Dari sisi teknis, HTTP cukup sederhana didasari oleh **perintah tekstual**.

### Anatomi permintaan HTTP 

Mari kita pelajari bagian pertama pertukaran web yang sebelumnya dijelaskan: permintaan.

![A web request example](images/chapter20-02.png)

Permintaan HTTP ini datang dari bentuk teks yang mirip dengan berikut.

```http
GET / HTTP/1.1
Host: xkcd.com
Accept: text/html
User-Agent: Mozilla/5.0 (Macintosh)
...
```

Yang paling penting adalah baris pertama. Baris tersebut mengandung:

* HTTP **method** (tipe permintaan, juga dinamakan **perintah**). Di sini, method `GET` mengindikasikan satu permintaan akses resource.
* **Resource** yang diminta. Di sini, `/` (simbol root) mengindikasikan satu permintaan untuk dokumen biasa.
* **Versi** protokol HTTP, di sini 1.1.

Baris lain dari teks dinamakan **header fields**. Baris ini memberikan tambaha informasi tentang permintaan client: nama server (`Host`), menerima tipe konten (`Accept`), detail perangkat lunak client (`User-Agent`). Ada banyak kemungkinan header fields lainnya.

Method utama HTTP adalah `GET` untuk mengakses satu resource dan `POST` untuk mendorong informasi ke server. Ada juga lainnya seperti `HEAD`, `PUT` atau `DELETE`.

### Anatomi respons HTTP 

Saat menerima permintaan HTTP, server mencari informasi ke dalam. Lalu membuat jawaban yang tepat dan mengembalikannya.

![A web response example](images/chapter20-01.png)

Respons HTTP dikirim oleh server seperti ini.

```http
HTTP/1.1 200 OK
Date: Fri, 22 Apr 2017 18:05:05 GMT
Server: Apache/2.2
Content-Type: text/html

<html>
<!-- HTML code of the page -->
<!-- ... -->
</html>
```

Baris pertama mengandung **status** respons: tiga digit angka mengindikasikan hasil dari permintaan. Baris lainnya adalah **header fields** (`Date`, `Content-Type`, dan lainnya) memberikan tambahan informasi tentang respons.

Respons HTTP kemungkinan juga termasuk data. Di contoh ini, respons mengandung kode HTML dari halaman web yang berkaitan dengan resource yang diminta.

### Kode status HTTP 

Kode status HTTP ada beberapa keluarga, tergantung dari digit pertamanya.

Keluarga | Arti | Contoh 
--------|---------------|---------
**1xx** | Informasi |
**2xx** | SUkses | 200: permintaan ditangani dengan sukses 
**3xx** | Redirection |
**4xx** | Eror client | 404: resource tidak ditemukan 
**5xx** | Eror server | 500: eror internal server 

> Untuk detail lebih dalam tentang protokol HTTP protocol, bisa kunjungi [Mozilla Developer Network](https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview).

### Menangani resource dengan URL

Situs web biasanya diakses melalui alamatnya, sepotong teks dalam bentuk:

<http://www.sitename.com/path/to/resource>

Alamat ini bisa dibagi menjadi beberapa bagian kecil

* `http://` artinya satu akses melalui protokol HTTP.
* `www.sitename.com` adalah the **nama domain** dari situs web.
* `/path/to/resource` adalah **jalur** dari resource yang diminta.

Satu alamat seperti ini dinamakan URL, atau **Uniform Resource Locator**. URL secara unik mendeskripsikan resource web dan cara memintanya.

## Dari situs web ke aplikasi web 

### Model pengembangan web 

Pada skenario pengembangan web tradisional, ketika Kamu meng-klik satu link atau mengirim formulir, browser Kamu mengirim ke server satu permintaan yang mengembalikan halaman penuh web sesuai permintaan Kamu. MOdel ini biasanya membutuhkan waktu membuka halaman lebih lama dan interaksi yang terbatas. 

Model pengembangan lainnya bertujuan mencegah pengiriman halaman penuh web untuk setiap aksi pengguna. Begini yang terjadi:

* Aksi pengguna pada halaman dicegat melalui event handler JavaScript.
* Permintan HTTP dikirim ke server tanpa mengganggu navigasi pada halaman.
* Hanya porsi yang dibutuhkan dari halaman yang di update dengan hasil yang diminta.

Walaupun lebih menantang, model pengembangan web ini bisa berujung pada pembatasan pembukaan resource, meningkatkan interaksi dan experience pengguna yang hampir setara dengan aplikasi native.

Sekumpulan teknologi yang dapat memicu pembuatan aplikasi web di kode namakan **AJAX** (*Asynchronous JavaScript and XML*). Panggilan AJAX adalah permintaan HTTP asinkron untuk menerima atau mengirimkan data dari/ke server.

### Permintaan sinkron vs asinkron

Pada pertukaran **sinkron**, peminta menunggu sampai dia mendapat info yang diinginkan. Panggilan telepon merupakan satu contoh pertukaran sinkron.

Sebaliknya, peminta di pertukaran **asinkron** bisa melakukan hal lainnya sambil menunggu penyelesaian permintaannya. Email adalah satu contoh pertukaran asinkron.

Model pengembangan web tradisional menggunakan permintaan sinkron: web client diblok ketika menunggu server untuk menyelesaikan permintaannya. Model AJAX menggunakan permintaan asinkron: data diambil sesuai kebutuhan dibalik layar.

### Permintaan cross-domain 

Untuk alasan keamanan, banyak situs web memiliki kebijakan konservatif terkait permintaan AJAX. *Same origin policy* ini menyatakan bahwa permintaan dibatasi pada domain asal: `"http://mysite"` tidak boleh mengirim permintaan ke `"http://anothersite"`. Hal ini mencegah beberapa server bisa diakses melalui panggilan AJAX.

Mengaktifkan permintaan cross-domain bisa dilakukan dengan mengeset konfigurasi **cross-origin resource sharing** (CORS) pada server.

> Untuk informasi lebih lanjut tentang topik ini, lihat [artikel MDN ini](https://developer.mozilla.org/en-US/docs/Web/HTTP/Access_control_CORS).

## JSON, data format untuk web

Huruf `"X"` AJAX merupakan singkatan dari XML, bahasa markup umum yang digunakan untuk pertukaran data cross-platform. Karena masih digunakan, XML cukup kompleks dan kemungkinan akan digantikan oleh JSON sebagai standar data format di web.

JSON, atau **JavaScript Object Notation**, adalah sintaks tekstual untuk mendeskripsikan informasi terstruktur. Seperti yang akan Kamu lihat di contoh berikut, JSON mengambil inspirasi dari sintaks objek JavaScript.

```json
{
  "cars": [
    {
      "model": "Peugeot",
      "color": "blue",
      "registration": 2012,
      "checkups": [2015, 2017]
    },
    {
      "model": "Citroën",
      "color": "white",
      "registration": 1999,
      "checkups": [2003, 2005, 2007, 2009, 2011, 2013]
    }
  ]
}
```

Dokumen JSON adalah satu set pasangan nama/nilai. Nama selalu diapit oleh tanda petik ganda `""`. Nilai bisa angka, string, boolean, array, ataupun objek.

Banyak bahasa pemrograman memiliki dukungan native untuk format JSON format... termasuk JavaScript, tentunya!
