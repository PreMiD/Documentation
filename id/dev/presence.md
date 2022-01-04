---
title: Pengembangan Presence
description:
published: true
date: 2021-12-20T14:27:18.034Z
tags:
editor: markdown
dateCreated: 2020-06-11T18:04:02.843Z
---

> Semua presence disimpan disini: https://github.com/PreMiD/Presences 
> 
> {.is-info}

Versi `2.x` memperkenalkan [toko presence](https://premid.app/store). Pengguna sekarang bisa menambah dan menghapus presence favorit lewat tampilan pengguna [website](https://premid.app/).

> Sebelum memulai, sangat dianjurkan untuk melihat aturan presence kami. 
> 
> {.is-warning}

- [Aturan](https://docs.premid.app/dev/presence/guidelines)
{.links-list}

# Struktur

Semua presence ditulis dalam [TypeScript](https://www.typescriptlang.org/). [TypeScript](https://www.typescriptlang.org/) memiliki tipe definisi tambahan dari JavaScript, jadi identifikasi dan perbaikan bug menjadi lebih mudah.

## Pemasangan

1. Pasang [Git](https://git-scm.com/).
2. Pasang [Node](https://nodejs.org/en/) (sudah disertai [npm](https://www.npmjs.com/)).
3. Pasang [TypeScript](https://www.typescriptlang.org/index.html#download-links) (buka terminal dan `npm install -g typescript`).

## Mengkloning project

1. Buka terminal dan ketik `git clone https://github.com/PreMiD/Presences`.
2. Pilih folder pilihanmu.
3. Buka di editor kodemu.

## Membuat folder dan file

1. Pergi ke folder `website` kemudian pergi ke folder dengan huruf pertama dari **nama** (bukan URL) dari layanan yang ingin didukung.
2. Buat folder dengan **nama** (bukan URL) dari layanan yang diinginkan.
3. Buatlah file `presence.ts` dan `tsconfig.json`.
4. Buatlah folder dinamakan `dist` didalamnya.
5. Buatlah file `metadata.json` didalam folder `dist`.

## Mengisi file tsconfig.json

Isi kode berikut kedalam file `tsconfig.json`.

```json
{
  "extends": "../../../tsconfig.json",
  "compilerOptions": {
    "outDir": "./dist/"
  }
}
```

Untuk mempelajari lebih lanjut tentang konfgurasi TypeScript klik [disini](/dev/presence/tsconfig).

## Mengisi file metadata.json

Kami telah membuat pembuat file `metadata.json` untuk para pemalas [disini](https://eggsy.xyz/projects/premid/mdcreator). Dianjurkan untuk membaca secara seksama agar anda mengerti bagaimana caranya.

```json
{
  "$schema": "https://schemas.premid.app/metadata/1.6",
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
      "id": "ID",
      "multiLanguage": true
    },
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
      "value": "\"%song%\" by %artist%",
      "placeholder": "use %song% or %artist%"
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

Salin kode diatas dan tempel pada file `metadata.json`. Sekarang kamu harus mengubah value dari properti tersebut. Harap diingat bahwa properti berikut adalah opsional dalam file `metadata.json` anda, jika anda tidak berniat menggunakannya anda harus menghapusnya.

- `contributors`
- `altnames`
- `regExp`
- `iframe`
- `iFrameRegExp`
- `readLogs`
- `settings`

**Memperjelas beberapa preset value:**

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
      <td style="text-align:left">Harus berisi sebuah Object dengan <code>name</code> dan <code>id</code> dari pengembang presence. <code>name</code> adalah username Discordmu tanpa identifier(#0000). <code>id</code> pengguna dapat disalin dari Discord dengan mengaktifkan mode
        developer dan klik kanan pada profil anda.</td>
      <td style="text-align:left"><code>Object</code></td>
      <td style="text-align:left"><code>Tidak</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>contributors</b></td>
      <td style="text-align:left">Harus berisi sebuah Object dengan <code>name</code> dan <code>id</code> dari pengembang presence. <code>name</code> adalah username Discordmu tanpa identifier(#0000). <code>id</code> pengguna dapat disalin dari Discord dengan mengaktifkan mode
        developer dan mengeklik kanan pada profilmu.</td>
      <td style="text-align:left"><code>Array&lt;Object&gt;</code></td>
      <td style="text-align:left"><code>Ya</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>service</b></td>
      <td style="text-align:left">Judul dari layanan harus didukung oleh presence ini.<br>
      (Harus bernama sama dengan folder dimana semua file berada)</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Tidak</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>altnames</b></td>
      <td style="text-align:left">Dapat mencari presence menggunakan nama alternatif.<br>
      Dimaksudkan untuk presence yang memiliki nama yang berbeda di bahasa lain (misal Pokémon dan 포켓몬스터).<br>
      Kamu juga dapat menggunakannya untuk presence yang memiliki karakter spesial jadi kamu tidak harus mengetik simbol tersebut (misal Pokémon dan Pokemon).</td>
      <td style="text-align:left"><code>Array&lt;String&gt;</code></td>
      <td style="text-align:left"><code>Ya</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>description</b></td>
      <td style="text-align:left">Sedikit deskripsi dari presence, kamu dapat menggunakan deskripsi dari layanan tersebut jika kehabisan ide. Deskripsi harus memiliki key pair values yang menandakan bahasa, dan deskripsi dengan bahasa tersebut. Buat deskripsi dengan bahasa yang <i>kamu pahami</i>, translator kami yang akan mengubah file metadatamu.</td>
      <td style="text-align:left"><code>Object</code></td>
      <td style="text-align:left"><code>No</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>url</b></td>
      <td style="text-align:left">URL dari layanan.<br><b>Contoh:</b><code>vk.com</code><br>
      <b>URL ini harus sama dengan URL pada website karena akan mendeteksi apakah ini adalah website yang akan di injeksikan skrip atau tidak. </b><br> <b>JANGAN</b> menambahkan <code>https://</code> atau <code>http://</code> didalam URL atau garis miring diakhir:      <code>https://premid.app/</code>-> <code>premid.app</code><br>
      <b>Catatan</b>:Beberapa URL mungkin memiliki <code>www.</code> atau lainnya didepan domainnya. <b>JANGAN</b> lupa menambahkannya!<br>
      Kamu dapat menambahkan beberapa URL dengan melakukan hal berikut:<br>
      <code>["URL1", "URL2", "ETC."]</code><br>
      Kamu juga dapat menggunakan regExp juga dikenal sebagai Regex untuk hal ini, dijelaskan dibawah ini.</td>
      <td style="text-align:left"><code>String, Array&lt;String&gt;</code></td>
      <td style="text-align:left"><code>No</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>regExp</b></td>
      <td style="text-align:left">Sebuah string regular expression yang digunakan untuk mencocokkan url.<br>
      regExp atau yang dikenal sebagai Regex, dapat digunakan jika sebuah website memiliki beberapa subdomain.<br>
      Kamu dapat menggunakan regExp berikut ini untuk itu:<br>
      <code>([a-z0-9]+)[.]domain[.]TLD"</code><br>
      TLD adalah singkatan dari Top Level Domain contohnya: .com .net ( jangan masukkan titik).<br>
      <code>([a-z0-9]+)</code> berarti apapun dari a sampai z dan dari 0 sampai 9.<br>
      Kamu dapat mendapatkan permulaan singkat dengan menonton <a href="https://youtu.be/sXQxhojSdZM">video</a> ini.<br>
      Kamu dapat menguji regExpmu pada <a href="https://regex101.com/">Regex101</a>.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Yes</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>version</b></td>
      <td style="text-align:left">Versi dari presencemu.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>No</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>logo</b></td>
      <td style="text-align:left">Link ke logotype dari layanan.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Tidak</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>thumbnail</b></td>
      <td style="text-align:left">Link ke thumbnail presence.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Tidak</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>color</b></td>
      <td style="text-align:left"><code>#HEX</code> value. Kami sarankan untuk menggunakan warna utama dari layanan        yang didukung oleh presence anda.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Tidak</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>tags</b></td>
      <td style="text-align:left">Array dengan tag, ini akan membantu pengguna untuk mencari presencemu pada website.</td>
      <td style="text-align:left"><code>String, Array&lt;String&gt;</code></td>
      <td style="text-align:left"><code>No</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>category</b></td>
      <td style="text-align:left">String yang digunakan untuk mewakili kategori yang dimilki presence. Lihat semua kategori valid <a href="https://docs.premid.app/dev/presence/metadata#presence-categories">disini</a>.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>No</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>iframe</b></td>
      <td style="text-align:left">Menentukan apakah <code>iFrames</code> digunakan.</td>
      <td style="text-align:left"><code>Boolean</code></td>
      <td style="text-align:left"><code>Yes</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>iFrameRegExp</b></td>
      <td style="text-align:left">Penentu regular expression yang memilih iframe yang di inject. Lihat regExp untuk informasi lebih lanjut.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Yes</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>readLogs</b></td>
      <td style="text-align:left">Menentukan apakah ekstensi harus membaca log.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Yes</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>settings</b></td>
      <td style="text-align:left">Sebuah susunan pengaturan yang dapat dirubah oleh pengguna.<br>
      Baca lebih lanjut tentang pengaturan presence <a href="https://docs.premid.app/dev/presence/metadata#presence-settings">disini</a>.</td>
      <td style="text-align:left"><code>Array&lt;Object&gt;</code></td>
      <td style="text-align:left"><code>Yes</code></td>
    </tr>
  </tbody>
</table>

## Memulai

```ts
const presence = new Presence({
    clientId: "000000000000000000" //Client ID dari aplikasi yang dibuat di https://discordapp.com/developers/applications
  }),
  strings = presence.getStrings({
    play: "presence.playback.playing",
    pause: "presence.playback.paused"
    //Kamu dapat menggunakan ini untuk mendapatkan string yang sudah diterjemahkan pada bahasa browser mereka
  });

/*

function myOutsideHeavyLiftingFunction(){
    //Ambil dan proses semua datamu disini

    // element grabs //
    // api calls //
    // variable sets //
}

setInterval(myOutsideHeavyLiftingFunction, 10000);
//Jalankan fungsi terpisah dari event UpdateData setiap 10 detik untuk mendapatkan dan menyiapkan variabel yang diambil oleh UpdateData

*/

presence.on("UpdateData", async () => {
  /*UpdateData selalu dijalankan, oleh karena itu lebih baik digunakan sebagai refresh cycle , atau 'tick`. Ini dipanggil beberapa kali dalam sedetik jika memungkinkan.

    Disarankan untuk mengatur fungsi lain diluar fungsi event ini yang akan mengubah value variabel dan mengurus proses berat jika kamu memanggil data dari sebuah API.*/

  const presenceData: PresenceData = {
      //Large Image pada presence. Ini dapat berupa key dari sebuah gambar yang telah di upload pada Discord Developer Portal - Rich Presence - Art Assets, atau URL ke sebuah gambar
    largeImageKey: "key",
    //Gambar kecil pada presence. This can be a key of an image uploaded on the Discord Developer Portal - Rich Presence - Art Assets, or a URL to an image
    smallImageKey: "https://mycrazywebsite.com/coolImage.png",
    //The text which is displayed when hovering over the small image
    smallImageText: "Some hover text",
     //The upper section of the presence text
    details: "Browsing Page Name",
    //The lower section of the presence text
    state: "Reading section A",
    //The unix epoch timestamp for when to start counting from
    startTimestamp: 3133657200000,
    //If you want to show Time Left instead of Elapsed, this is the unix epoch timestamp at which the timer ends
    endTimestamp: 3133700400000
    //Optionally you can set a largeImageKey here and change the rest as variable subproperties, for example presenceData.type = "blahblah"; type examples: details, state, etc.
  };
  //Perbarui presence dengan semua value dari objek presenceData
  if (presenceData.details) presence.setActivity(presenceData);
  //Perbarui presence tanpa data, oleh karena itu bersihkan dan jadikan gambar besar sebagai ikon Application Discord, dan teks nama Application Discord
  else presence.setActivity(); 
});
```

Kamu bisa menyalinnya ke file `presence.ts` dan mengubah valuenya. Pengaturan semua value dilakukan pada event updateData.

Untuk contoh kami sarankan untuk melihat kode dari presence seperti: 1337x atau 9GAG. Untuk informasi tentang kelas `Presence` klik [disini](/dev/presence/class).

Sejak v2.2.0 sekarang ada Slideshow, ini memungkinkan kamu untuk menampilkan beberapa antarmuka `PresenceData` pada suatu interval, untuk info lebih lanjut klik tentang kelas `Slideshow` [di sini](/dev/presence/slideshow).

## Tidak bisa mendapat data tertentu?!

Banyak situs web yang menggunakan ([Inlineframe](https://en.wikipedia.org/wiki/HTML_element#Frames)) [iframe](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe). Tag html tersebut bisa berisi beberapa sumber seperti video. Tapi mereka kadang tidak relevan. Beberapa tersembunyi atau tidak sering dipakai. Periksa jika kamu bisa ekstrak informasi yang dibutuhkan tanpa informasi tersebut sebelum melakukan pekerjaan sia-sia.

1. Periksa didalam konsol browser (pastikan anda berada pada tab **Elements**).
2. Cari (<kbd>CTRL</kbd>+<kbd>F</kbd> (Windows) atau <kbd>CMD</kbd>+<kbd>F</kbd> (MacOS)).
3. Jalankan `document.querySelectorAll("iframe")`.

Jika datamu ditemukan pada iFrame, kamu harus melakukan hal berikut:

1. Buatlah file `iframe.ts`.
2. Atur iFrame menjadi `true` pada file metadata.
3. Mengisi file iFramemu.

```ts
const iframe = new iFrame();
iframe.on("UpdateData", async () => {
  /*
  Dapatkan semua data yang kamu butuhkan dari iFrame, simpan mereka dalam variable
  dan kirim mereka menggunakan iframe.send 
  */
  iframe.send({
    //mengirim data
    video: video,
    time: video.duration
  });
});
```

4. Membuat file presencemu menerima data dari file iFrame.

```ts
presence.on("iFrameData", (data) => {
  iFrameVideo = data.video;
  currentTime = data.time;
});
```

**Catatan:** ini harus diletakkan diluar dari event updateData.

## Penyusunan

Buka konsol pada foldermu dan ketik `tsc -w` untuk menyusun `presence.ts` ke folder `/dist`.

# Memuat presence

1. Buka popup ekstensi di browser dan tahan tombol <kbd>Shift</kbd> pada keyboardmu.
2. **Muat Presence** akan muncul pada bagian Presences.
3. Klik sambil menahan tombol <kbd>Shift</kbd>.
4. Pilih folder /dist dari presence anda.

# Beberapa hal berguna

## Hot-reloading

Situs web yang sedang kamu kembangkan akan memuat ulang otomatis setiap kali kamu menyimpan file di folder.

## Debugging

- Anda dapat memberi `console.log("Test");` diantara kode dan melihat apakah konsol browser memberi output tersebut. Jika iya lanjutkan dan ulangi pada function selanjutnya. Jika tidak berarti terdapat eror diatas.
- Jika itu tidak membantumu, tanyakan pada pengembang presence di [server Discord](https://discord.premid.app/) kami untuk bantuan.

# File dijelaskan

- [Kelas Presence](/dev/presence/class)
- [Kelas Slideshow](/dev/presence/slideshow)
- [Kelas iFrame](/dev/presence/iframe)
- [File Metadata](/dev/presence/metadata)
- [Konfigurasi TypeScript](/dev/presence/tsconfig ""){.links-list}
