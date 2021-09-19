---
title: Panduan Presence
description: Peraturan yang harus ditaati oleh pengembang presence agar presencenya ditambahkan.
published: true
date: 2021-06-27T16:08:07.318Z
tags:
editor: markdown
dateCreated: 2021-02-26T21:54:41.573Z
---

<div align="center">
    <img src="https://github.com/PreMiD.png?size=2048" width="128px" style="max-width:100%;">
    <h3 style="font-size: 2rem; margin-bottom: 0">Panduan Presence</h3>
    <h4 style="margin-top: 0">Revisi ke-3</h4>
    <br />
</div>

# Panduan

Ketika mempublikasikan Presence ke [Repository Presence](https://github.com/PreMiD/Presences/) kami meminta kamu untuk mengikuti beberapa aturan. Bagi beberapa, peraturan ini mungkin agak kejam. Namun, penerapan aturan ini bertujuan untuk menjaga kami dan user dari masalah.

# Pembuatan

Peraturan umum pembuatan presence adalah sebagai berikut:

- Presence **harus** berhubungan dengan website yang dipilih.
- Presence **harus tidak** dibuat untuk website ilegal. (misal stresor, penjualan obat, pornografi dibawah umur, dll)
- Struktur file harus bersih dan teratur, jangan memasukkan file yang tidak ditentukan. ( misal, vscode dan folder git, file gambar dan teks, dll.)
- Kamu harus memilki struktur file yang baik, draf **tidak** diperbolehkan.
- Presence untuk website dengan (`.onion` TLD) atau website dengan domain/host gratis (misal, `.TK` [semua domain gratis dari Freenom], `.RF`, `GD`, dll.) **tidak** diizinkan, pengecualian dapat dibuat jika bukti pembayaran domain dapat ditunjukkan.
- Domain dari presence harus berumur minimal 2 bulan.
- Presence yang mengarah pada halaman internal browser (seperti Chrome Web Store `chrome://`, `about:` pages, etc) **tidak** diperbolehkan sebab membutuhkan flag experimental diaktifkan oleh pengguna dan bisa menyebabkan kerusakan pada browser.
- Presence dengan dukungan hanya satu halaman **tidak** diperbolehkan, sebab akan terlihat rusak bagi halaman lain ( seperti homepage) pengecualian dapat dibuat untuk halaman kebijakan dan kontak (konten yang jarang digunakan) atau website yang konten lainnya tidak berhubungan. (misal, halaman wikia)
- Presence radio online hanya diperbolehkan jika radio memiliki setidaknya 100 pendengar mingguan dan 15 secara bersamaan dan juga harus memiliki beberapa fitur selain hanya menampilkan album/judul lagu, dll.
- Presence tidak diizinkan menjalankan kode JS dengan fungsinya sendiri untuk mendapatkan variabel. Bila Firefox memiiki masalah dengan fungsi bawaan dalam kelas `Presence`, kamu boleh melakukan fungsimu sendiri dan kamu wajib memberitahu kami di deskripsi Pull Request.
- Presence kualitas rendah (atau yang memiliki sedikit konteks) **tidak** diperbolehkan (contohnya, hanya menampilkan logo dan teks tapi tidak pernah diganti lagi).
- Presences untuk layanan seperti Daftar Server/Bot Discord harus mengikuti persyaratan tambahan berikut ini:
  - Domain harus paling sedikit berusia **6 bulan**.
  - Pengunjung unik per hari:
    - Untuk domain berusia 6 bulan: **20.000 pengunjung unik/hari**.
    - Untuk domain berusia 12+ bulan: **45.000 pengunjung unik/hari**.
  - Situs web tidak boleh menggunakan domain murah seperti `.xyz`, `.club` dan seterusnya.
  - Situs web tersebut harus berkualitas tinggi, desain bagus, dll.
- Presence harus menggunakan [rincian umum](https://api.premid.app/v2/langFile/presence/en) (string yang berawalan "umum."). Kamu dapat mencapai ini menggunakan `multiLanguage` dengan string yang tersedia. Bila presencemu membutuhkan string khusus, maka jangan menggunakan `multiLanguage` sampai presence mendapatkan 1000 pengguna. Kamu bisa mendapatkan contoh [di sini](https://docs.premid.app/dev/presence/class#getstringsobject).
- Wajib mencantumkan folder `dist`, file `presence.ts`, file `iframe.ts`, dan file `metadata.json` agar hasil sesuai dengan skema berikut:

```bash
presence
├── dist
│   └── metadata.json
├── presence.ts
└── tsconfig.json
```

atau jika kamu menggunakan file `iframe.ts`:

```bash
presence
├── dist
│   └── metadata.json
├── presence.ts
├── iframe.ts
└── tsconfig.json
```

## [**metadata.json**](https://docs.premid.app/dev/presence/metadata)

> Untuk kemudahan para pengembang presence, kami telah menyediakan skema yang bisa digunakan untuk memeriksa keutuhan dari file `metadata`. Ini sepenuhnya opsional dan tidak wajib dalam proses review.

> Sangat dianjurkan untuk mengorganisir file `metadata` pada format dibawah ini, dan kamu harus memiliki nama layanan yang benar secara tata bahasa, deskripsi, tag, dan bidang pengaturan. Apapun yang tidak terorganisir menurut spesifikasi **tidak** diperbolehkan.

> Presence untuk situs web yang memiliki konten eksplisit **harus** memiliki tag `nsfw`, dan logo/thumbnail harus **tidak** mengandung hal tersebut.

Setiap presence memiliki file descriptor bernama `metadata.json`, metadata memilki standar yang ketat contoh file bisa dilihat sebagai berikut:

```json
{
  "$schema": "https://schemas.premid.app/metadata/1.3",
  "author": {
    "name": "PENGGUNA",
    "id": "ID"
  },
  "contributors": [
    {
      "name": "PENGGUNA",
      "id": "ID"
    }
  ],
  "service": "LAYANAN",
  "altnames": ["LAYANAN"],
  "description": {
    "en": "DESKRIPSI"
  },
  "url": "URL",
  "version": "VERSI",
  "logo": "URL",
  "thumbnail": "URL",
  "color": "#HEX000",
  "tags": ["TAG1", "TAG2"],
  "category": "KATEGORI",
  "regExp": "REGEXP",
  "iFrameRegExp": "REGEXP",
  "iframe": false,
  "readLogs": false,
  "settings": [
    {
      "id": "multiLanguage",
      "multiLanguage": true
    }
    {
      "id": "ID",
      "title": "TUNJUKKAN JUDUL",
      "icon": "IKON FONTAWESOME",
      "value": true
    },
    {
      "id": "ID",
      "if": {
        "ID": true
      },
      "title": "TUNJUKKAN JUDUL",
      "icon": "IKON FONTAWESOME",
      "value": "\"%song%\" by %artist%",
      "placeholder": "use %song% or %artist%"
    },
    {
      "id": "ID",
      "title": "TUNJUKKAN JUDUL",
      "icon": "IKON FONTAWESOME",
      "value": 0,
      "values": ["1", "2", "dll."]
    }
  ]
}
```

> Jika sebuah kolom terdaftar sebagai opsional pada [dokumentasi](https://docs.premid.app/en/dev/presence/metadata) atau ada `*` disamping key dan presencemu menggunakan value default, jangan mencantumkannya pada file `metadata`. (misal, presence tanpa dukungan iframe tidak memerlukan bidang `iframe`.)

> Semua gambar pada file `metadata` harus dihosting di `i.imgur.com`. Menggunakan konten yang dihost pada website **tidak** diperbolehkan sebab mereka dapat mengubah lokasi dan file tanpa peringatan.

Daftar bidang dan peraturannya tertulis dibawah:

### **`$schema`**

- Skema _key_ **harus** memuat tanda dollar pada awalan, tanda ini akan menandakan editor teksmu untuk memvalidasi file JSON dengan suatu model. _ seperti yang telah disebutkan sebelumnya, kamu tidak perlu mencantumkan sebuah skema, tapi jika kamu mencantumkannya kamu harus memperhitungkan hal tersebut._

### **`author`**

- ID _value_ **harus** ID snowflake Discordmu. Bisa didapatkan dengan mengaktifkan [developer mode](https://support.discord.com/hc/en-us/articles/206346498-Where-can-I-find-my-User-Server-Message-ID-). _harap **tidak** disamakan dengan ID aplikasimu, yang hanya digunakan untuk Presence._

### **`*contributors`**

- **Jangan** menambahkan dirimu sendiri sebagai kontributor dan jangan menambahkan orang lain sebagai kontributor kecuali mereka membantu dengan pembuatan presence.

### **`service`**

- Nama layanan **harus** sesuai dengan nama dari direktori presence. Contohnya, jika presence terletak di `/websites/Y/YouTube/`, nama layanan harus `YouTube`.
- Kamu **tidak boleh** menggunakan url sebagai nama layanan kecuali situs web memakai url sebagai nama resminya. Jika nama tidak deskriptif dan dianggap tidak jelas, **harus** menggunakan url. (untuk contoh, `YouTube` tidak diperbolehkan karena itu nama resmi dan deskriptif, sementara `youtube.com` tidak. `Top` adalah nama non-deskriptif, jadi menggunakan url `top.gg` sangat **dibutuhkan**.)
- Jika sebuah layanan memiliki aturan branding yang eksplisit terhadap nama mereka, kamu harus mengikutinya.

### **`*altnames`**

- **Hanya** gunakan ini jika website menggunakan beberapa nama resmi (misal Pokémon dan 포켓몬스터). _Singkatan_ dari nama layanan berada pada `tags`.

### **`description`**

- **Semua** presence **diharuskan** memilki deskripsi berbahasa inggris terlepas dari bahasa dari website.
- **Jangan** mencoba menerjemahkan deskripsi sendiri kecuali anda mengerti bahasa tersebut, penerjemah akan mengubah `metadata.json` dan mengubah deskripsi jika diperlukan.

### **`url`**

- Url **harus** berupa string jika website hanya menggunakan satu domain. Jika website menggunakan lebih dari satu, jadikan array dan tentukan masing-masing.
- **Jangan** mencantumkan protokol pada url (misal, `http` atau `https`), dan jangan memasukkan query parameter pada url (contoh, `www.google.com/search?gws_rd=ssl` yang seharusnya `www.google.com/`)

### **`version`**

- Selalu pastikan versi mengikuti [semantic versioning standards](https://semver.org), yang diterjemahkan ke skema berikut: `<NEW-FEATURE>.<HUGE-BUGFIX>.<SMALL-BUGFIX-OR-METADATA-CHANGES>`. Hal lain seperti `1.0.0.1`, `1.0`, `1`, `1.0.0-BETA` atau mengubah `1.0.0` to `2.0.0` pada perbaikan bug/perubahan kecil **tidak** diperbolehkan.
- Versi **harus** dimulai dengan `1.0.0` kecuali diberitahu lainnya, versi lain **tidak** diperbolehkan.

### **`logo`**

- Logo **harus** berupa persegi dengan aspect ratio `1:1`.
- Gambar **diharuskan** memiliki resolusi minimal `512x512` pixel. Gambar dapat di upscale menggunakan alat seperti [waifu2x](http://waifu2x.udp.jp/).

### **`thumbnail`**

- Thumbnail **sebaiknya** sebuah [ wide promotional card](https://i.imgur.com/3QfIc5v.jpg) atau sebuah [ screenshot](https://i.imgur.com/OAcBmwW.png) jika opsi pertama **tidak ** tersedia.

### **`color`**

- Warna **harus** menggunakan hexadecimal value antara `#000000` dan `#FFFFFF`.
- String warna **harus** didahulukan dengan hash symbol.

### **`tags`**

- **Semua** presence diharuskan memiliki setidaknya _satu_ tag.
- Tag harus **tidak** memiliki spasi, garis miring, tanda kutip tunggal/ganda, karakter Unicode, dan harus selalu huruf kecil.
- Tag **sebaiknya** mencantumkan nama alternatif untuk memudahkan pencarian ( misal, jika presence Amazon memiliki AWS support, maka akan memiliki tag seperti `amazon-web-services` dan `aws`)
- Anda **diharuskan** menambahkan tag `NSFW` jika presence untuk website NSFW.

### **`category`**

- Kategori **diharuskan** salah satu dari yang tercantum pada [dokumentasi](https://docs.premid.app/dev/presence/metadata#presence-categories).
- Presence harus menggunakan kategori yang sama dengan konten situs web. (untuk contoh, jangan gunakan `anime` ketika situs web tidak terkait dengan anime).

### **`*regExp`** <br /> **`*iFrameRegExp`**

- Regular expressions**harus** valid. Periksa expression menggunakan alat yang dicantumkan pada [dokumentasi](https://docs.premid.app/en/dev/presence/metadata#testing).

### **`readLogs`**

- Harus berupa `boolean` value (e.g. `true` or `false`).
- Mengaktifkan log untuk presencemu.

### **`warning`**

- Mengaktifkan ikon peringatan untuk meminta pengguna jika presence ini membutuhkan lebih banyak langkah daripada hanya menambahkan presence.
- Contoh dari presence yang menggunakan variabel metadata ini adalah `VLC`.

### **`settings`**

- Jika kamu ingin untuk membuat suatu format string (contoh, `%song% oleh %artist%`), kamu harus menaruh variabelnya diantara sebuah tanda persen di kedua sisi. Variabel seperti `%var`, `var%`, atau `%%var%%` dan apa pun lainnya ** tidak** diizinkan demi standarisasi.
- Nama dari setting harus **tidak** berhuruf kapital semua. Misalnya, nama seperti `SHOW BROWSING STATUS` akan **tidak** diizinkan; namun, nama seperti `Show Browsing Status` atau `Show browsing status` diperbolehkan.
- Jika kamu menggunakan opsi `multiLanguage`, ada beberapa hal yang perlu kamu ketahui:
  - Value tipe **Boolean** hanya akan mengaktifkan string [`general.json`](https://github.com/PreMiD/Localization/blob/master/src/Presence/general.json) dari repositori Localization atau dari file Presence (contoh, saat nama presence adalah YouTube, maka ekstensi akan mendapatkan string dari `youtube.json` juga.)
  - Value tipe **String** (contoh, `youtube.json`) akan menentukan nama dari file yang ingin kamu dapatkan string-nya.
  - Value tipe **Array<String>** (contoh, `["youtube", "discord"]`) akan menentukan nama dari file yang ingin kamu dapatkan string-nya.

## [**presence.ts**](https://docs.premid.app/dev/presence/class)

> Kode yang kamu tulis **harus**_ ditulis dengan baik_ dan **harus** _dapat dibaca_ dan semua string harus benar secara tata bahasa ( kesalahan penulisan pada website dapat diabaikan).

> Setiap presence mengikuti aturan ketat yang akan diperiksa saat proses review. Beberapa rekomendasi bisa dilihat dibawah. [Rekomendasi Plugin TypeScript untuk Strict Type Checking](https://github.com/typescript-eslint/typescript-eslint/tree/master/packages/eslint-plugin/docs/rules). [Rekomendasi ESlint](https://eslint.org/docs/rules). [Prettier](https://prettier.io/).

Berikut daftar rules yang harus diikuti saat menulis sebuah file `presence.ts`:

- **Selalu** menyatakan instance baru dari class `Presence` sebelum variabel lainnya untuk menghindari masalah yang mungkin terjadi; hal ini tidak diharuskan pada desain jadi bisa dihapus kedepannya.
- **Jangan pernah** menggunakan custom function jika [ native variant tersedia](https://docs.premid.app/dev/presence#files-explained); hal ini memastikan perbaikan pada tingkat ekstensi dapat berpengaruh pada presence kamu juga. Kamu bebas dalam menggunakan apapun yang dibutuhkan jika tidak menemukannya tercantum di docs.
- It is **forbidden** to code presences for a site without adding support to its primary language (for e.g., a YouTube presence coded with support only for Portueguese and Japanese, but not English itself.)
- Bidang `smallImageKey` dan `smallImageText` dimaksudkan untuk memberi konteks tambahan/konteks kedua (seperti `berputar/dijeda` untuk situs video, `menjelajahi` untuk situs biasa, dan hal lain) bukan untuk mempromosikan profil Discord atau apapun yang tidak berhubungan dengan PreMiD.
- Kamu **tidak** diperbolehkan mengakses `localStorage`.
- Saat mengakses cookie untuk data tersimpan, harap memberi prefix pada key dengan `PMD_`.
- You may only make HTTP/HTTPS requests to `premid.app` or the presence website API. If you are using external domains, you will be required to explain why it is necessary. Only allowed API to make request is [`Fetch API`](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API).
- Do **not** set fields in the presenceData object to undefined after it has been declared, use the `delete` keyword instead. (for e.g., use `delete data.startTimestamp` instead of `data.startTimestamp = undefined`)
- You are **not** allowed to write presences that change the functionality of a given website. This includes the addition, deletion, or modification of DOM elements.
- Presences that use buttons should follow extra requirements:
  - Redirects to main page are prohibited.
  - Promoting websites by them is prohibited.
  - They can't show additional data when you can't show them in other fields.
  - Redirecting directly to audio/video stream is prohibited.


## [**tsconfig.json**](https://docs.premid.app/dev/presence/tsconfig)

> Do **not** write your own `tsconfig.json` file, use what has been provided on [documentation](https://docs.premid.app/dev/presence/tsconfig).

## Modification

> Kamu **harus** mengubah versi di **metadata** menjadi lebih tinggi dari versi sebelumnya ketika membuat perubahan pada **presence.ts**,**iframe** atau **metadata**.

In some situations, presences may behave unexpectedly or could use some minor changes to improve their functionality. Here is a list of rules that you **must** follow while modifiying presences.

- You are **not** allowed to rewrite a presence or change its author. If the presence author was banned from the official server or hasn't made the required changes within a month, you may contact a reviewer to see if you can to rewrite the presence.
- If you make modifications to a presence and change at least a **quarter** of the presence's codebase, you are allowed to add yourself as a contributor. Contact a reviewer for more information about this subject.
- Anyone may provide hotfixes to fix bugs; however, try **not** to make changes that are **not** required. Valid modifications include general fixes (code and typos), additions (descriptions and tags), missing files, etc. Do **not** change images if they are not outdated and are in specifications.

# Verification

> **Semua** kode yang dikontribusi ke toko akan terlisensi dengan `Mozilla Public License 2.0`.

> Jika anda ingin menghubungi seseorang, gunakan server Discord official kami. Semua reviewer akan memilki role `Reviewer` di profilnya.

> Harap diingat bahwa reviewer bekerja secara sukarela dan mengurus repository lainnya selain ini, pull request anda mungkin tidak ditinjau hingga berjam-jam atau bahkan berhari-hari setelah dibuat.

> **Selalu** miliki fork yang up-to-date sebelum membuat pull request. This will help limit false positives from the checks.

The most important process of presence development is getting your presence on the store. This is done by making a [pull request](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/creating-a-pull-request) on GitHub on the `PreMiD/Presences` repository. Our reviewers will confirm that your presence is up to standards and will push it onto the store.

<div>
  <h2 style="font-size: 2rem; margin-bottom: 0;">Peninjau Presence</h2>

  <a href="https://github.com/Bas950"><img src="https://github.com/Bas950.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
  <a href="https://github.com/StrikerFRFX"><img src="https://github.com/StrikerFRFX.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
  <a href="https://github.com/Slowlife01"><img src="https://github.com/Slowlife01.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
  <br />
</div>

## `Larangan`

Pelanggaran berulang seperti melanggar aturan, spam pull request, pengancaman, atau perilaku tidak pantas akan membuatmu dilarang membuat presence.

Pada kejadian seperti ini, perubahan berikut akan terjadi:

- Presences under your management will be transferred to the PreMiD bot or another user (reviewer decision). Id aplikasi untuk setiap presence akan dibuat ulang dengan nama pemilik baru.
- Semua issue dan pull request (pembuatan presence, kontribusi presence, dll) yang dibuat setelah pelanggaran akan segera ditutup.
- Tickets created under your name regarding presence development will be deleted.

## `Peninjauan`

Beberapa hal yang harus anda ketahui setelah membuka pull request:

- Dibutuhkan 2 peninjau untuk merge sebuah pull request.
- Jika pull request tidak aktif selama 7 hari, pull request tersebut akan segera ditutup.
- Semua pemeriksaan **harus** berhasil untuk merge.
- ⚠️ You **must** provide new, unaltered screenshots (taken by you) showing a side-by-side comparison of your profile and the website to prove that your presence works. _You are allowed to stitch screenshots together for viewing pleasure_ This applies for both creation and modification.
- ⚠️ Kamu juga **harus** memasukkan tangkapan layar pengaturan presence di dalam extension jika disediakan. Sebuah contoh dapat dilihat [di sini](https://imgur.com/a/OD3sj5R).

## `Pemeriksaan`

![Example of checks](https://i.imgur.com/T8agbnB.png)

Saat ini, sebuah presence melewati 3 tahapan pemeriksaan. All of these checks help the reviewers determine whether your presence is suitable for deployment.

- `Codacy` adalah bot yang memeriksa kualitas kode. Jika kamu menemui eror pada issue baru, kamu **diharuskan** untuk memperbaikinya. *Warning: Codacy doesn't always give you errors. Please look at CodeFactor warnings instead.*
- `CodeFactor` adalah bot yang memeriksa kualitas kode. Jika kamu menemui eror pada issue baru, kamu **diharuskan** untuk memperbaikinya.
- `Schema Validation` akan mengscan file `metadata.json` mencari eror ( misal, missing fields, invalid value types, dll.). If you ever see any new issues, you are also **required** to fix those. Adding a schema field to your `metadata.json` file will allow your text editor (if supported) to show you these errors during development.

## `Peraturan tambahan`

- **Always** make sure to start your presence in the most appropriate folder, if its name starts with _any_ Latin letter then it must be under its alphabetical match (for e.g., `D/dアニメストア` or `G/Google`). Any other Unicode/non-Latin characters **must** be under the `#` folder (for e.g., `#/巴哈姆特`) and numbers under the `0-9` folder (for e.g., `0-9/4anime`).

Setelah memenuhi semua peraturan dengan review dan pemeriksaan yang sesuai, presence anda akan di merge dengan toko.

# Suggestions

If you have some suggestions about our guidelines, you should contact us @ [PreMiD's discord server](https://discord.premid.app) and we will check them!

# Kontribusi

`Revision 3` of the guidelines was written and was contributed to by the following individuals:

<div>
<a href="https://github.com/ririxidev"><img src="https://github.com/ririxidev.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
</div>

`Revision 2` of the guidelines was written and was contributed to by the following individuals:

<div>
<a href="https://github.com/CobyPowers"><img src="https://github.com/CobyPowers.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
</div>

`Revision 1` was maintained by the following individuals:

<div>
<a href="https://github.com/CobyPowers"><img src="https://github.com/CobyPowers.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
<a href="https://github.com/Bas950"><img src="https://github.com/Bas950.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
<a href="https://github.com/doomlerd"><img src="https://github.com/doomlerd.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
</div>
