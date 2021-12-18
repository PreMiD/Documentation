---
title: Metadata.json
description: Berisi data dasar tentang Presence
published: true
date: 2021-02-07T17:12:06.799Z
tags:
editor: markdown
dateCreated: 2020-06-11T18:04:52.965Z
---

# Metadata.json

Jika kamu ingin menerbitkan presence ke toko dan memuatnya lewat ekstensi, kamu harus membuat file `metadata.json` pada folder `dist` milikmu.

Contoh file tersebut dapat ditemukan di bawah.

```ts
{
  "$schema": "https://schemas.premid.app/metadata/1.5",
  "author": {
    "name": "PENGGUNA",
    "id": "ID"
  },
  "contributors": [{
    "name": "PENGGUNA",
    "id": "ID"
  }],
  "service": "LAYANAN",
  "altnames": ["LAYANAN"],
  "description": {
    "en": "DESKRIPSI"
  },
  "url": "URL",
  "regExp": "REGEXP",
  "iFrameRegExp": "REGEXP",
  "version": "VERSI",
  "logo": "URL",
  "thumbnail": "URL",
  "color": "#45A8FC",
  "tags": ["TAG1", "TAG2"],
  "category": "KATEGORI",
  "iframe": false,
  "settings": [
    {
      "id": "ID",
      "title": "JUDUL TAMPILAN",
      "icon": "IKON FONTAWESOME",
      "value": true
    },
    {
      "id": "ID",
      "if": {
        "ID": true
      },
      "title": "JUDUL TAMPILAN",
      "icon": "IKON FONTAWESOME",
      "value": "\"%song%\" oleh %artist%",
      "placeholder": "pakai %song% atau %artist%"
    },
    {
      "id": "ID",
      "title": "JUDUL TAMPILAN",
      "icon": "IKON FONTAWESOME",
      "value": 0,
      "values": ["1", "2", "etc."]
    }
  ]
}
```

## Memahami metadata.json

Contoh itu terlihat sangat aneh, ya? Jangan khawatir, memahami fungsi setiap variable itu tidak terlalu sulit.

<table>
  <thead>
    <tr>
      <th style="text-align:left">Variabel</th>
      <th style="text-align:left">Deskripsi</th>
      <th style="text-align:left">Tipe</th>
      <th style="text-align:left">Opsional</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>author</b></td>
      <td style="text-align:left">Harus berisi sebuah Object dengan <code>name</code> dan <code>id</code> dari pengembang presence. <code>name</code> adalah username Discordmu tanpa identifier(#0000). <code>id</code> pengguna dapat disalin dari Discord dengan mengaktifkan developer
        mode dan klik kanan pada profil kamu.</td>
      <td style="text-align:left"><code>Object</code></td>
      <td style="text-align:left"><code>Tidak</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>contributors</b></td>
      <td style="text-align:left">Harus berisi object dengan <code>nama</code> dan <code>id</code> dari kontributor. <code>name</code> adalah username Discordmu tanpa identifier(#0000). <code>id</code> pengguna dapat disalin dari Discord dengan mengaktifkan developer
        mode dan klik kanan pada profil anda.</td>
      <td style="text-align:left"><code>Array&lt;Object&gt;</code></td>
      <td style="text-align:left"><code>Ya</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>service</b></td>
      <td style="text-align:left">Judul dari layanan yang didukung oleh presence tersebut.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Tidak</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>altnames</b></td>
      <td style="text-align:left">Dapat mencari presence menggunakan nama lain.<br>
      Dimaksudkan untuk presence yang memiliki nama yang berbeda di bahasa yang berbeda (e.g. Pokémon and 포켓몬스터).<br>
      Kamu juga dapat menggunakan ini untuk presence yang memiliki karakter spesial yang kamu tidak bisa ketik (e.g. Pokémon and Pokemon).</td>
      <td style="text-align:left"><code>Array&lt;String&gt;</code></td>
      <td style="text-align:left"><code>Ya</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>description</b></td>
      <td style="text-align:left">Deskripsi dari layanan tersebut <b>BUKAN</b> presencenya. Deskripsi harus memiliki value yang berpasangan yang menandakan bahasa, dan deskripsi dengan bahasa tertentu. Buat deskripsi dengan bahasa yang <i>anda mengerti</i>, translator kami yang akan mengubah file metadata anda. Lihat kategori untuk bahasa presence untuk daftarnya. </td>
      <td style="text-align:left"><code>Object</code></td>
      <td style="text-align:left"><code>Tidak</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>url</b></td>
      <td style="text-align:left">URL layanan.<br>
      <b>Contoh:</b><code>vk.com.com</code><br>
      <b>URL ini harus sama dengan URL dari website karena akan digunakan untuk mendeteksi apakah ini website yang benar untuk inject script. Ini bisa digunakan sebagai kesatuan ketika ada lebih dari satu url.</b></td>
      <td style="text-align:left"><code>String, Array&lt;String&gt;</code></td>
      <td style="text-align:left"><code>Tidak</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>regExp</b></td>
      <td style="text-align:left">Regular expression string yang digunakan untuk mencocokkan url.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Ya</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>version</b></td>
      <td style="text-align:left">Versi dari presencemu.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Tidak</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>logo</b></td>
      <td style="text-align:left">Tautan ke logotype dari layanan.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Tidak</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>thumbnail</b></td>
      <td style="text-align:left">Tautan ke thumbnail presence.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Tidak</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>color</b></td>
      <td style="text-align:left"><code>#HEX</code> value. Kami menganjurkan untuk menggunakan warna utama dari layanan        yang didukung oleh presence kamu.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Tidak</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>category</b></td>
      <td style="text-align:left">String yang digunakan untuk menunujukkan kategori yang dimiliki oleh presence.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Tidak</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>tags</b></td>
      <td style="text-align:left">Array dengan tag, ini akan membantu pengguna mencari presencemu pada website.</td>
      <td style="text-align:left"><code>String, Array&lt;String&gt;</code></td>
      <td style="text-align:left"><code>Tidak</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>iframe</b></td>
      <td style="text-align:left">Menentukan apakah <code>iFrames</code> digunakan</td>
      <td style="text-align:left"><code>Boolean</code></td>
      <td style="text-align:left"><code>Ya</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>iFrameRegExp</b></td>
      <td style="text-align:left">Penentu regular expression yang memilih iframe yang di inject.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Ya</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>readLogs</b></td>
      <td style="text-align:left">Menentukan apakah ekstensi harus membaca catatan.</td>
      <td style="text-align:left"><code>Boolean</code></td>
      <td style="text-align:left"><code>Ya</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>settings</b></td>
      <td style="text-align:left">Kumpulan pengaturan yang bisa dirubah pengguna</td>
      <td style="text-align:left"><code>Array&lt;Object&gt;</code></td>
      <td style="text-align:left"><code>Ya</code></td>
    </tr>
  </tbody>
</table>

## Regular Expressions

Jika kamu ingin mempelajari regular expression, berikut beberapa website.

#### Mempelajari

• [Quick Starter Video](https://youtu.be/sXQxhojSdZM) • [RegexOne](https://regexone.com/) • [Regular Expressions Info](https://www.regular-expressions.info/tutorial.html)

#### Testing

• [Regexr](https://regexr.com/) • [Regex101](https://regex101.com/)

## Bahasa Presence

PreMiD merupakan layanan poliglot, artinya terdapat banyak bahasa yang terlibat untuk menghubungkan pengguna di seluruh dunia. Daftar penuh bahasa dapat dilihat dengan [API endpoint](https://api.premid.app/v2/langFile/list) ini. Untuk lebih menyesuaikan presence kamu, kamu bisa mengizinkan pengguna untuk memilih tampilan bahasa presence mereka. Lihat [`multiLanguage`](#multilanguage) untuk selengkapnya.

## Pengaturan presence
Buat pengaturan interaktif agar pengguna dapat mengatur presencenya!
```ts
"settings": [
  {
    "id": "ID",
    "multiLanguage": true //Lihat https://docs.premid.app/dev/presence/metadata#multilanguage
  },
  {
    "id": "ID",
    "title": "TUNJUKKAN JUDUL",
    "icon": "IKON FONTAWESOME", //Contoh"fas fa-info"
    "value": true //Nilai Boolean akan membuatnya menjadi tombol nyala/mati dengan nilai ini sebagai nilai default
  },
  {
    "id": "ID",
    "if": {
      "ID": true //Jika pengaturan lain sama dengan nilai ini (true/false/0/1/etc.) maka tunjukkan tombol ini
    },
    "title": "TUNJUKKAN JUDUL",
    "icon": "IKON FONTAWESOME",
    "value": "\"%song%\" by %artist%", //Memasukkan string akan membuat pengaturan menjadi pengaturan input, dan memperbolehkan penggunaan input custom.
    "placeholder": "pakai %song% atau %artist%" //Input kosong akan terlihat abu-abu
  },
  {
    "id": "ID",
    "title": "TUNJUKKAN JUDUL",
    "icon": "IKON FONTAWESOME",
    "value": 0, //Nilai default selector
    "values": ["1", "2", "etc."] //Akan membuat pengaturan menjadi selector saat kamu memilih yang mana yang kamu inginkan 
  }
]
```

### `multiLanguage`

#### Pendahuluan

Pengaturan `multiLanguage` dapat digunakan agar pengguna dapat memilih bahasa yang mereka inginkan untuk presence yang ditampilkan. Ini mengharuskan anda untuk menggunakan string dari [API](https://api.premid.app/v2/langFile/presence/en) kami, untuk informasi bagaimana cara menambahkan string klik [disini](https://docs.premid.app/dev/presence/metadata#adding-new-strings).

#### Penyetelan

Pengaturan `multiLanguage` adalah kasus yang spesial, tidak dibutuhkan `title` atau `icon` atau `value` ataupun `values` seperti pengaturan lainnya tapi membutuhkan beberapa konfigurasi!

Key `multiLanguage` bisa di ubah menjadi:

`true`: gunakan ini jika kamu hanya ingin menggunakan string dari file `general.json` dan file `<service>.json` dari [Localization Repository](https://github.com/PreMiD/Localization/tree/master/src/Presence). `string`: nama dari file kecuali ekstensi (.json) di dalam [Localization Repository](https://github.com/PreMiD/Localization/tree/master/src/Presence) (kecuali file `general`, karena selalu dimuat). Hanya bahasa umum dari file `general` dan yang dimasukkan akan dicantumkan. `Array<String>`: jika kamu menggunakan lebih dari satu file di dalam [Localization Repository](https://github.com/PreMiD/Localization/tree/master/src/Presence) kamu bisa menentukan semua value dalam sebuah array (kecuali file `general`, karena selalu dimuat). Hanya bahasa umum dari semua file yang akan dicantumkan.

#### Menambahkan string baru

**Catatan:** Menambahkan string kustom untuk presence hanya diperbolehkan jika presence memiliki lebih dari 1000 pengguna.

##### Mengkloning project

1. Buka terminal dan ketik `git clone https://github.com/PreMiD/Localization`.
2. Pilih folder pilihanmu.
3. Buka di editor kodemu.

##### Membuat file

1. Pergi ke folder `src`.
2. Pergi ke folder `Presence`.
3. Buat file bernama `<service>.json`. (Service adalah **nama** (bukan URL) dalam huruf kecil dari service yang ingin kamu dukung.)

##### Menambahkan string

Setiap `string` adalah `Object` dimana dari namanya dimulai dengan nama service kemudian yang disebut stringName dengan titik diantaranya.

stringName adalah pengidentifikasi 1 kata dari pesan.

`Object` memiliki 2 properti; `message` dan `description`. `message` adalah teks yang harus diterjemahkan. `description` adalah deskripsi pesan untuk membantu penerjemah kami memahami apa yang mereka terjemahkan.

**Catatan:** Jangan menambahkan string ganda. (Hal ini mencakup string di luar file `general.json` tapi tidak file lainnya.)

Visualisasi dari file:

```ts
{
  "<service>.<stringName>": {
    "message": "Teks yang perlu diterjemahkan.",
    "description": "Ini menjelaskan apa teks diatas itu."
  },
  "<service>.<stringName>": {
    "message": "Teks yang perlu diterjemahkan.",
    "description": "Ini menjelaskan apa teks diatas itu."
  }
}
```

Setelah kamu berhasil membuat file dengan string kamu bisa membuat Pull Request ke [Localization Repository](https://github.com/PreMiD/Localization), di deskripsi kamu **harus** mencantumkan tautan ke Pull Request dari presence yang diperbarui menggunakan string baru dari [Presence Repository](https://github.com/PreMiD/Presences).

#### Key default
Key yang tidak perlu kamu atur secara otomatis diatur menjadi: `title`: "Bahasa" **Catatan:** Ini diterjemahkan ke bahasa default mereka (bahasa browser). `icon`: ""fas fa-language" ([Pratinjau](https://fontawesome.com/icons/language)) `value`: **Mengatur ke bahasa browser mereka jika tersedia (100% diterjemahkan), atau bahasa Inggris.** `values`: **Mengatur ke bahasa yang tersedia (bahasa yang sudah 100% diterjemahkan).**

**Catatan:** Ini sama sekali tidak dapat diubah.

### Metode

Gunakan metode berikut untuk mendapat info pengaturan pada file presence:
#### `getSetting(String)`
Mengembalikan value dari setting.
```ts
const setting = await presence.getSetting("pdexID"); //Ubah pdexID dengan id dari setting
console.log(setting); // Ini akan mencatat isi dari setting
```

#### `hideSetting(String)`
Sembunyikan pengaturan yang telah diberikan.
```ts
presence.hideSetting("pdexID"); //Mengganti pdexID dengan id dari pengaturan
```

#### `showSetting(String)`
Menampilkan pengaturan yang diberikan (Hanya bekerja jika pengaturan telah disembunyikan).
```ts
presence.showSetting("pdexID"); //Mengganti pdexID dengan id dari pengaturan
```

## Kategori presence

Saat membuat presence, kamu harus menentukan kategori yang mana presence berada. Berikut adalah daftar kategori yang bisa digunakan.

<table>
  <thead>
    <tr>
      <th style="text-align:left">Kategori</th>
      <th style="text-align:left">Nama</th>
      <th style="text-align:left">Deskripsi</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>anime</b></td>
      <td style="text-align:left"><b>Anime</b></td>
      <td style="text-align:left">Apapun yang berhubungan dengan anime, dari forum hingga platform streaming video.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>games</b></td>
      <td style="text-align:left"><b>Permainan</b></td>
      <td style="text-align:left">Website apapun yang memiliki konten tentang game, seperti <code>Kahoot</code> atau <code>Skribbl.io</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>music</b></td>
      <td style="text-align:left"><b>Musik</b></td>
      <td style="text-align:left">Website ini menawarkan konten yang berhubungan dengan musik, streaming atau download.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>socials</b></td>
        <td style="text-align:left"><b>Sosial</b></td>
      <td style="text-align:left">Websites that are used for the purpose of creating and sharing content or for participating in other forms of social networking.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>videos</b></td>
        <td style="text-align:left"><b>Video dan Stream</b></td>
      <td style="text-align:left">Website yang berguna untuk menyediakan video dan stream.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>other</b></td>
      <td style="text-align:left"><b>Lainnya</b></td>
      <td style="text-align:left">Apapun yang tidak termasuk kategori diatas.</td>
    </tr>
  </tbody>
</table>

