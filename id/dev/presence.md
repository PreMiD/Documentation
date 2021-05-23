---
title: Pengembangan Presence
description:
published: true
date: 2021-02-07T17:11:34.449Z
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

## Instalasi

1. Install [Git](https://git-scm.com/).
2. Install [Node](https://nodejs.org/en/) (comes with [npm](https://www.npmjs.com/)).
3. Install [TypeScript](https://www.typescriptlang.org/index.html#download-links) (open a terminal and `npm install -g typescript`).

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

```typescript
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
      "id": "ID",
      "multiLanguage": true
    },
    {
      "id": "ID",
      "title": "TAMPILKAN JUDUL",
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
      "values": ["1", "2", "etc."]
    }
  ]
}
```

Salin kode diatas dan tempel pada file `metadata.json`. Sekarang anda harus mengubah value dari properti tersebut. Harap diingat bahwa properti berikut adalah opsional dalam file `metadata.json` anda, jika anda tidak berniat menggunakannya anda harus menghapusnya.

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
      <td style="text-align:left">Harus berisi sebuah Object dengan <code>name</code> dan <code>id</code> dari pengembang presence. <code>name</code> adalah username Discordmu tanpa identifier(#0000). User <code>id</code> can be copied from Discord by enabling developer
        mode and right-clicking on your profile.</td>
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
      <td style="text-align:left">URL of the service.<br><b>Example:</b><code>vk.com</code><br>
      <b>This URL must match the URL of the website as it will detect whether or not this is the website to inject the script to.</b><br> Do <b>NOT</b> add <code>https://</code> or <code>http://</code> inside of the URL nor a slash at the end:
      <code>https://premid.app/</code> -> <code>premid.app</code><br>
      <b>Note</b>: Some URLs may have <code>www.</code> or something else in front of their domain. Do <b>NOT</b> forget to add it!<br>
      You can add multiple URLs by doing the following:<br>
      <code>["URL1", "URL2", "ETC."]</code><br>
      You could also use regExp also known as Regex for this task, explained further below.</td>
      <td style="text-align:left"><code>String, Array&lt;String&gt;</code></td>
      <td style="text-align:left"><code>No</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>regExp</b></td>
      <td style="text-align:left">Sebuah string regular expression yang digunakan untuk mencocokkan url.<br>
      regExp atau Regex, dapat digunakan jika sebuah website memiliki beberapa subdomain.<br>
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
      <td style="text-align:left"><code>No</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>thumbnail</b></td>
      <td style="text-align:left">Link ke thumbnail presence.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>No</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>color</b></td>
      <td style="text-align:left"><code>#HEX</code> value. Kami sarankan untuk menggunakan warna utama dari layanan        yang didukung oleh presence anda.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>No</code></td>
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
      <td style="text-align:left">A regular expression selector that selects iframes to inject into. Lihat regExp untuk informasi lebih lanjut.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Yes</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>readLogs</b></td>
      <td style="text-align:left">Defines whether the extension should be reading logs.</td>
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

```typescript
const presence = new Presence({
    clientId: "000000000000000000" //The client ID of the Application created at https://discordapp.com/developers/applications
  }),
  strings = presence.getStrings({
    play: "presence.playback.playing",
    pause: "presence.playback.paused"
    //You can use this to get translated strings in their browser language
  });

/*

function myOutsideHeavyLiftingFunction(){
    //Grab and process all your data here

    // element grabs //
    // api calls //
    // variable sets //
}

setInterval(myOutsideHeavyLiftingFunction, 10000);
//Run the function separate from the UpdateData event every 10 seconds to get and set the variables which UpdateData picks up

*/

presence.on("UpdateData", async () => {
  /*UpdateData is always firing, and therefore should be used as your refresh cycle, or `tick`. This is called several times a second where possible.

    It is recommended to set up another function outside of this event function which will change variable values and do the heavy lifting if you call data from an API.*/

  const presenceData: PresenceData = {
    largeImageKey:
      "key" /*The key (file name) of the Large Image on the presence. Ini di upload dan diberi nama di Rich Presence dari aplikasi anda, yang disebut Art Assets*/,
    smallImageKey:
      "key" /*Key (nama file) dari Small Image di presence. These are uploaded and named in the Rich Presence section of your application, called Art Assets*/,
    smallImageText: "Some hover text", //The text which is displayed when hovering over the small image
    details: "Browsing Page Name", //The upper section of the presence text
    state: "Reading section A", //The lower section of the presence text
    startTimestamp: 1577232000, //The unix epoch timestamp for when to start counting from
    endTimestamp: 1577151472000 //If you want to show Time Left instead of Elapsed, this is the unix epoch timestamp at which the timer ends
  }; /*Optionally you can set a largeImageKey here and change the rest as variable subproperties, for example presenceSata.type = "blahblah"; type examples: details, state, etc.*/

  if (presenceData.details == null) {
    //This will fire if you do not set presence details
    presence.setTrayTitle(); //Clears the tray title for mac users
    presence.setActivity(); /*Update the presence with no data, therefore clearing it and making the large image the Discord Application icon, and the text the Discord Application name*/
  } else {
    //This will fire if you set presence details
    presence.setActivity(presenceData); //Update the presence with all the values from the presenceData object
  }
});
```

You can copy this into your `presence.ts` file and edit the values. Setting all the values is done inside of the updataData event.

For examples we suggest to look at the code of presences like: 1337x or 9GAG. For more information about the `Presence` class click [here](/dev/presence/class).

Sejak v2.2.0 sekarang ada Slideshow, ini memungkinkan kamu untuk menampilkan beberapa antarmuka `PresenceData` pada suatu interval, untuk info lebih lanjut klik tentang kelas `Slideshow` [di sini](/dev/presence/slideshow).

## Tidak bisa mendapat data tertentu?!

Banyak situs web yang menggunakan ([Inlineframe](https://en.wikipedia.org/wiki/HTML_element#Frames)) [iframe](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe). Tag html tersebut bisa berisi beberapa sumber seperti video. But they're not relevant every time. Some are hidden or just not actively used. Check if you can extract the information you need without them before you do unnecessary work.

1. Periksa didalam konsol browser (pastikan anda berada pada tab **Elements**).
2. Cari (<kbd>CTRL</kbd>+<kbd>F</kbd> (Windows) atau <kbd>CMD</kbd>+<kbd>F</kbd> (MacOS)).
3. Jalankan `document.querySelectorAll("iframe")`.

Jika datamu ditemukan pada iFrame, kamu harus melakukan hal berikut:

1. Buatlah file `iframe.ts`.
2. Atur iFrame menjadi `true` pada file metadata.
3. Mengisi file iFramemu.

```typescript
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

```typescript
presence.on("iFrameData", (data) => {
  iFrameVideo = data.video;
  currentTime = data.time;
});
```

**Catatan:** ini harus diletakkan diluar dari event updateData.

## Penyusunan

Open a console in your folder and type `tsc -w` to compile the `presence.ts` into the `/dist` folder.

# Memuat presence

1. Open the extension popup in the browser and hold the <kbd>Shift</kbd> button on your keyboard.
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
