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

Versi `2.x` memperkenalkan [Toko Presence](https://premid.app/store). Pengguna sekarang bisa menambah dan menghapus presence favorit lewat tampilan pengguna [website](https://premid.app/).

> Sebelum memulai, sangat dianjurkan untuk melihat aturan presence kami. 
> 
> {.is-warning}

- [Aturan](https://docs.premid.app/dev/presence/guidelines)
{.links-list}

# Struktur

Semua presence ditulis menggunakan [TypeScript](https://www.typescriptlang.org/). [TypeScript](https://www.typescriptlang.org/) memiliki tipe definisi tambahan dari JavaScript, jadi identifikasi dan perbaikan bug menjadi lebih mudah.

## Persyaratan

1. [Git](https://git-scm.com/)
2. Pasang [Node](https://nodejs.org/en/) (sudah disertai [npm](https://www.npmjs.com/)).

## Mengkloning project

1. Buka terminal dan ketik `git clone https://github.com/PreMiD/Presences`.
2. Pilih folder pilihanmu.
3. Buka di editor kodemu.

## Memulai

1. Buka terminal pada folder `Presence`
2. Pasang dependensi repositori menggunakan `npm i` (Atau menggunakan package manager pilihanmu)

### Membuat sebuah Presence
1. Jalankan `npx pmd` (atau jalankan `pmd` pada package manager pilihanmu)
2. Pilih opsi pertama
3. Isi semua pertanyaan yang ditampilkan

### Compile / Merubah Presence
1. Jalankan `npx pmd`
2. Pilih opsi kedua
3. Masukkan nama Presence yang ingin kamu edit > Ini akan memulai compiler TypeScript pada folder Presence tersebut, sekarang jika kamu mengedit `presence.ts` TypeScript akan otomatis compile presencemu.
{.is-info}

Untuk inspirasi atau contoh bagaimana untuk menstruktur kode presencemu, lihat presence yang sudah ada seperti 1337x atau 9GAG

Untuk informasi lebih lanjut terkait class `Presence` klik [disini](/dev/presence/class).

Slideshow tersedia sejak v2.2.0, ini memungkinkan kamu manampilkan beberapa interface`PresenceData` pada suatu interval, untuk informasi lebih lanjut terkait class `Slideshow`klik [disini](/dev/presence/slideshow).

## Tidak bisa mendapatkan data tertentu?!

Banyak situs web menggunakan [iframes](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe) ([Inlineframes](https://en.wikipedia.org/wiki/HTML_element#Frames)). Tag html tersebut dapat berisi beberapa sumber seperti video. Tapi mereka kadang tidak relevan. Beberapa tersembunyi atau jarang dipakai. Periksa jika kamu dapat mengambil informasi yang dibutuhkan tanpa tag tersebut sebelum melakukan pekerjaan sia-sia.

1. Periksa pada konsol browser (pastikan kamu berada pada tab **Elements**).
2. Cari (<kbd>CTRL</kbd>+<kbd>F</kbd> (Windows) atau <kbd>CMD</kbd>+<kbd>F</kbd> (MacOS)).
3. Jalankan `document.querySelectorAll("iframe")`.

Jika data yang diinginkan ditemukan pada iFrame, kamu harus melakukan hal berikut:

1. Buatlah file `iframe.ts`.
2. Set iFrame menjadi `true` pada file metadata.
3. Mengisi file iFramemu.

```ts
const iframe = new iFrame();
iframe.on("UpdateData", async () => {
  //Get all the data you need out of the iFrame save them in variables and then send them using iframe.send
  iframe.send({
    //sending data
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

**Catatan:** Ini harus diletakkan diluar dari event updateData.

# Memuat presencemu

1. Buka popup ekstensi di browser dan tahan tombol <kbd>Shift</kbd> pada keyboardmu.
2. **Muat Presence** akan muncul pada bagian Presence.
3. Klik sambil menahan tombol <kbd>Shift</kbd>.
4. Pilih folder /dist presencemu.

# Beberapa hal berguna

## Hot-reloading

Situs web yang sedang kamu kembangkan akan memuat ulang otomatis setiap kali kamu menyimpan file di folder.

## Debugging

- Kamu dapat memberi `console.log("Test");` diantara kode dan melihat apakah konsol browser memberi output tersebut. Jika iya lanjutkan dan ulangi pada fungsi selanjutnya. Jika tidak berarti terdapat eror.
- Jika itu tidak membantumu, tanyakan pada pengembang presence di [server Discord](https://discord.premid.app/) kami untuk bantuan.

# File dijelaskan

- [Kelas Presence](/dev/presence/class)
- [Kelas Slideshow](/dev/presence/slideshow)
- [Kelas iFrame](/dev/presence/iframe)
- [File Metadata](/dev/presence/metadata)
- [Konfigurasi TypeScript](/dev/presence/tsconfig ""){.links-list}
