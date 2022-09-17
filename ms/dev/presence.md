---
title: Pembangunan Presence
description:
published: true
date: 2021-12-20T14:27:18.034Z
tags:
editor: markdown
dateCreated: 2020-06-11T18:04:02.843Z
---

> Kesemua Presence kini disimpan di sini: https://github.com/PreMiD/Presences 
> 
> {.is-info}

Versi `2.x` memperkenalkan [Kedai Presence](https://premid.app/store). Pengguna kini boleh menambah dan membuang Presence kegemaran mereka secara manual menerusi antara muka pengguna di [laman sesawang](https://premid.app/).

> Sebelum anda mula, anda amat digalakkan untuk melihat garis panduan Presence kami. 
> 
> {.is-warning}

- [Garis Panduan](https://docs.premid.app/dev/presence/guidelines)
{.links-list}

# Struktur

Kesemua Presence dicipta menggunakan [TypeScript](https://www.typescriptlang.org/). [TypeScript](https://www.typescriptlang.org/) mempunyai pentakrifan jenis yang lebih pedas berbanding JavaScript, jadi pembaikian dan pengenalpastian pepijat adalah lebih mudah.

## Keperluan

1. [Git](https://git-scm.com/)
2. [Node](https://nodejs.org/en/) (didatangkan dengan [npm](https://www.npmjs.com/))

## Klon projek

1. Buka terminal dan taip `git clone https://github.com/PreMiD/Presences`.
2. Pilih folder yang anda suka.
3. Buka ia dalam penyunting kod anda.

## Mulakan

1. Buka terminal baharu dalam folder `Presences`
2. Pasang kebergantungan repositori menggunakan `npm i` (Atau pengurus pakej pilihan anda)

### Mencipta Presence
1. Jalankan `npx pmd` (atau jalankan `pmd` menggunakan pengurus pakej pilihan anda)
2. Pilih pilihan yang pertama
3. Isikan kesemua soalan yang dipaparkan

### Mengkompil / Mengubah Suai Presence
1. Jalankan `npx pmd`
2. Pilih pilihan yang kedua
3. Masukkan nama Presence yang anda ingin sunting > Ini akan mulakan pengkompil TypeScript dalam folder Presence tersebut, apabila anda menyunting fail `presence.ts` sekarang ia akan kompil presence tersebut untuk anda secara automatik.
{.is-info}

Untuk inspirasi atau contoh cara untuk menstrukturkan kod Presence anda, sila lihat pada Presence sedia ada seperti 1337x atau 9GAG

Untuk maklumat lanjut mengenai kelas `Presence` sila klik [sini](/dev/presence/class).

Kelas Slideshow wujud sejak v2.2.0, ini membolehkan anda menunjukkan beberapa antara muka `PresenceData` pada selang masa tertentu, untuk maklumat lanjut mengenai kelas `Slideshow` sila klik [sini](/dev/presence/slideshow).

## Tidak mampu dapatkan sesetengah data?!

Banyak laman sesawang menggunakan [iframe](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe) ([Inlineframes](https://en.wikipedia.org/wiki/HTML_element#Frames)). Tag HTML ini boleh mengandungi beberapa sumber seperti video. Tetapi bukan semuanya mempunyai kaitan pada setiap masa. Sesetengahnya disembunyikan atau cuma tidak digunakan secara aktif. Periksa jika anda boleh sarikan maklumat yang anda perlukan tanpanya sebelum anda membuat apa-apa kerja yang tidak diperlukan.

1. Periksanya di konsol pelayar anda (pastikan anda berada di tab **Elements** atau Unsur).
2. Cari (<kbd>CTRL</kbd>+<kbd>F</kbd> (Windows) atau <kbd>CMD</kbd>+<kbd>F</kbd> (MacOS)).
3. Lakukan `document.querySelectorAll("iframe")`.

Jika anda nampak yang data anda berada dalam iFrame anda perlu lakukan berikut:

1. Cipta fail `iframe.ts`.
2. Tetapkan iFrame menjadi `true` dalam fail metadata anda.
3. Isikan fail iFrame anda.

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

4. Buatkan fail Presence anda terima data dari fail iFrame.

```ts
presence.on("iFrameData", (data) => {
  iFrameVideo = data.video;
  currentTime = data.time;
});
```

**Nota:** Ini perlu diletakkan di luar peristiwa updateData.

# Memuatkan Presence anda

1. Buka tetingkap sambungan dalam pelayar dan terus memegang butang <kbd>Shift</kbd> di papan kekunci anda.
2. **Muatkan Presence** akan muncul di bahagian Presence.
3. Click on it while you are still holding the <kbd>Shift</kbd> button.
4. Select the /dist folder of your presence.

# Beberapa perkara yang berguna

## Muat semula panas

The website you are developing on is automatically reloading every time you save a file in your folder.

## Nyahpepijat

- You can put `console.log("Test");` between your code and see if your browser console gives you that output. If yes then go on and try again after the next function. If not then there is an error above.
- If that doesn't help you either then ask a presence developer on our [Discord server](https://discord.premid.app/) for help.

# Fail dijelaskan

- [Kelas Presence](/dev/presence/class)
- [Kelas Slideshow](/dev/presence/slideshow)
- [Kelas iFrame](/dev/presence/iframe)
- [Metadata File](/dev/presence/metadata)
- [Tatarajah TypeScript](/dev/presence/tsconfig ""){.links-list}
