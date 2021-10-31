---
title: Kelas Presence
description: Kelas utama untuk setiap presence PreMiD
published: true
date: 2021-05-23T09:14:06.963Z
tags:
editor: markdown
dateCreated: 2021-02-21T21:13:14.449Z
---

# Kelas Presence

## Pendahuluan

Kelas `Presence` sangat berguna karena memiliki metode dasar yang diperlukan untuk membuat presence.

Saat Anda membuat kelas, Anda harus menentukan properti `clientId`.

```typescript
const presence = new Presence({
  clientId: "514271496134389561" // Contoh clientId
});
```

### Properti

Terdapat tiga properti yang tersedia untuk kelas `Presence`.

#### `clientId`

Properti ini diperlukan agar presencemu bekerja, karena properti ini menggunakan id aplikasimu untuk menampilkan logo dan asetnya. Kamu bisa mendapatkannya di [halaman aplikasi kamu](https://discordapp.com/developers/applications).

#### `injectOnComplete` - *Sudah tidak digunakan kembali sejak 2.2.4*

Ketika pengaturan `injectOnComplete` adalah `true` maka event `UpdateData` pertama untuk file `presence.ts` dan `iframe.ts` hanya akan dinyalakan ketika halaman sudah sepenuhnya termuat.

#### `appMode` - *Sudah tidak digunakan kembali sejak 2.2.4*

Ketika mengatur `appMode` menjadi `true` dan jika presence mengirim `PresenceData` kosong, maka app akan memunculkan aplikasi (gambar dan nama) pada profil pengguna dari pada tampil kosong.

## Metode

### `getActivity()`

Mengembalikan objek `PresenceData` dari apa yang sedang ditampilkan presence.

### `setActivity(PresenceData | Slideshow, Boolean)`

Tetapkan aktivitas profil Anda sesuai dengan data yang disediakan.

Parameter pertama membutuhkan interface [`PresenceData`](#presencedata-interface) atau kelas [`Slideshow`](/dev/presence/slideshow) untuk mendapatkan semua informasi yang ingin kamu tampilkan di profilmu.

Parameter kedua menentukan apakah presence memainkan sesuatu atau tidak. Selalu gunakan `true` jika kamu memberikan timestamp di `PresenceData`.

### `clearActivity()`

Menghapus aktivitasmu saat ini dan judul tray.

### `setTrayTitle(String)` - *Deprecated since 2.2.3*

> Metode ini hanya bekerja di Mac OS. 
> 
> {.is-warning}

Setel judul baki pada bilah Menu.

### `createSlideshow()`

Membuat kelas `Slideshow` baru.

```typescript
const slideshow = presence.createSlideshow();
```

Disarankan untuk melakukan ini setelah membuat Kelas `Presence`:

```typescript
const presence = new Presence({
    clientId: "514271496134389561" // Contoh clientId
  }),
  slideshow = presence.createSlideshow();
```

Kamu bisa menemukan dokumentasi untuk kelas `Slideshow` [disini](/dev/presence/slideshow).

### `getStrings(Object)`

Metode asinkron yang memungkinkan kamu untuk mendapatkan string terjemahan dari extension.

Kamu harus memberikan `Object` dengan kunci sebagai kunci untuk string, `keyValue` adalah nilai string. Daftar string terjemahan bisa ditemukan di titik akhir ini: `https://api.premid.app/v2/langFile/presence/id/`

```typescript
// Mengembalikan string `Playing` dan` Paused`
// dari ekstensi.
const strings = await presence.getStrings({
  play: "general.playing",
  pause: "general.paused"
});

const playString = strings.play; // hasil: Playing
const pauseString = strings.pause; // hasil: Paused
```

Sejak ekstensi v2.2.0 kamu sekarang bisa mendapatkan string dari bahasa tertentu. Ini sudah bekerja baik dengan opsi pengaturan `multiLanguage` yang baru ditambahkan.

Kami menyarankan kamu untuk menggunakan kode berikut agar PresenceData secara otomatis diperbarui jika pengguna merubah bahasa yang dipilih;

```typescript
async function getStrings() {
  return presence.getStrings(
    {
      play: "general.playing",
      pause: "general.paused"
    },
    // ID adalah ID dari pengaturan multiLanguage.
    await presence.getSetting("ID").catch(() => "en");
  );
}

let strings = getStrings(),
  // ID adalah ID dari pengaturan multiLanguage.
  oldLang: string = await presence.getSetting("ID").catch(() => "en");

//! Kode berikut harus berada didalam event updateData!
// The ID is the ID of the multiLanguage setting.
const newLang = await presence.getSetting("ID").catch(() => "en");
if (oldLang !== newLang) {
  oldLang = newLang;
  strings = getStrings();
}

const playString = (await strings).play, // hasil: Playing
  pauseString = (await strings).pause; // hasil: Paused
```

### `getPageletiable(String)`

Mengembalikan variabel dari situs web jika ada.

**Peringatan: Fungsi ini dapat menyebabkan penggunaan CPU yang tinggi & melambatkan situs jika terlalu sering dijalankan.**

```typescript
const pageVar = getPageletiable(".pageVar");
console.log(pageVar); // Ini akan mencatat "Variable content"
```

### `getExtensionVersion(Boolean)`

Mengembalikan versi dari ekstensi yang digunakan oleh pengguna.

```typescript
getExtensionVersion(onlyNumeric?: boolean): string | number;

const numeric = presence.getExtensionVersion();
console.log(numeric); // Akan mencatat 210
const version = presence.getExtensionVersion(false);
console.log(version); // Akan mencatat 2.1.0
```

### `getSetting(String)`

Mengembalikan value dari pengaturan.

```typescript
const setting = await presence.getSetting("pdexID"); //Ubah pdexID dengan id dari setting
console.log(setting); // Ini akan mencatat isi dari setting
```

### `hideSetting(String)`

Sembunyikan pengaturan yang telah diberikan.

```typescript
presence.hideSetting("pdexID"); // Ubah pdexID dengan id dari pengaturan
```

### `showSetting(String)`

Menampilkan pengaturan yang diberikan (Hanya bekerja jika pengaturan telah disembunyikan).

```typescript
presence.showSetting("pdexID"); // Ubah pdexID dengan id dari pengaturan
```

### `getLogs()`

Mengembalikan catatan dari konsol situs web.

```typescript
const logs = await presence.getLogs();
console.log(logs); // Ini akan mencatat 100 catatan terbaru (dalam array).
```

**Catatan:** Membutuhkan `readLogs` menjadi `true` di file `metadata.json`.

### `info(String)`

Cetak pesan yang diberikan di konsol dengan format berdasarkan presence pada style `success`.

```typescript
presence.info("Test") // Ini akan mencatat "test" dengan styling yang benar.
```

### `success(String)`

Cetak pesan yang diberikan oleh konsol dengan format berdasarkan presence dengan style `success`.

```typescript
presence.success("Test") // Ini akan mencatat "test" dengan styling yang benar.
```

### `error(String)`

Mencetak pesan yang diberikan di konsol dengan format berdasarkan presence pada style`error`.

```typescript
presence.error("Test") // Ini akan mencatat "test" dengan styling yang benar.
```

### `getTimestampsfromMedia(HTMLMediaElement)`

Mengembalikan 2 timestamp `snowflake` pada sebuah `Array` yang dapat digunakan untuk `startTimestamp` dan `endTimestamp`.

```typescript
const timestamps = presence.getTimestampsfromMedia(document.querySelector(".video"));
presenceData.startTimestamp = timestamps[0];
presenceData.endTimestamp = timestamps[1];
```

** Catatan: ** ` String ` yang diberikan di querySelector merupakan sebuah contoh.

### `getTimestamps(Number, Number)`

Mengembalikan 2 timestamp `snowflake` pada sebuah `Array` yang dapat digunakan untuk `startTimestamp` dan `endTimestamp`.

```typescript
const video = document.querySelector(".video"),
  timestamps = presence.getTimestamps(video.currentTime, video.duration);
presenceData.startTimestamp = timestamps[0];
presenceData.endTimestamp = timestamps[1];
```

**Catatan:** `String` yang diberikan pada querySelector merupakan sebuah contoh.

### `timestampFromFormat(String)`

Mengonversi sebuah string dengan format `JJ:MM:DD` atau `MM:DD` atau `DD` menjadi sebuah integer (Tidak mengembalikan timestamp snowflake).

```typescript
const currentTime = presence.timestampFromFormat(document.querySelector(".video-now").textContent),
  duration = presence.timestampFromFormat(document.querySelector(".video-end").textContent),
  timestamps = presence.getTimestamps(currentTime, duration);
presenceData.startTimestamp = timestamps[0];
presenceData.endTimestamp = timestamps[1];
```

**Catatan:** `String` yang diberikan di querySelector merupakan sebuah contoh.

## `PresenceData` Interface

Interface `presenceData` disarankan untuk digunakan saat kamu menggunakan metode `setActivity()`.

Interface ini memiliki variabel berikut, semuanya merupakan opsional.

<table>
  <thead>
    <tr>
      <th style="text-align:left">Variabel</th>
      <th style="text-align:left">Deskripsi</th>
      <th style="text-align:left">Tipe</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">details</td>
      <td style="text-align:left">Baris pertama di presencemu, biasanya digunakan sebagai header.</td>
      <td style="text-align:left"><code>String</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">state</td>
      <td style="text-align:left">Baris kedua di presencemu.</td>
      <td style="text-align:left"><code>String</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">startTimestamp</td>
      <td style="text-align:left">Menentukan waktu saat ini.<br>
        Digunakan jika kamu ingin menampilkan berapa banyak <code>jam:menit:detik</code> tersisa.
          <br>Kamu harus mengonversi waktumu menjadi <code>timestamp</code> atau kamu akan mendapatkan hitungan mundur
          yang salah.
      </td>
      <td style="text-align:left"><code>Number</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">endTimestamp</td>
      <td style="text-align:left">Menentukan durasi penuh.
        <br>Digunakan jika kamu ingin menampilkan berapa <code>jam:menit:detik</code> tersisa.
          <br>Kamu harus mengonversi waktumu ke <code>timestamp</code> atau kamu akan mendapatkan hitungan mundur yang salah.
      </td>
      <td style="text-align:left"><code>Number</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">largeImageKey</td>
      <td style="text-align:left">Menentukan logo untuk presence.</td>
      <td style="text-align:left"><code>String</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">smallImageKey</td>
      <td style="text-align:left">Menentukan ikon kecil di sebelah logo presence.</td>
      <td style="text-align:left"><code>String</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">smallImageText</td>
      <td style="text-align:left">Menentukan teks yang akan ditampilkan ketika pengguna mengarahkan kursor ke ikon
        kecil.</td>
      <td style="text-align:left"><code>String</code>
      </td>
    </tr>
        <tr>
      <td style="text-align:left">buttons</td>
      <td style="text-align:left">Susunan tombol, maksimal 2, label merupakan teks tombol, dan url merupakan tautan.</td>
      <td style="text-align:left"><code>Array&lt;Object&gt;</code>
      </td>
    </tr>
  </tbody>
</table>

```typescript
const presenceData: PresenceData = {
  details: "Judul saya",
  state: "Deskripsi saya",
  largeImageKey: "service_logo",
  smallImageKey: "small_service_icon",
  smallImageText: "You hovered me, and what now?",
  startTimestamp: 1564444631188,
  endTimestamp: 1564444634734
};
```

## Events

Events memungkinkan kamu untuk mendeteksi dan menangani beberapa perubahan atau panggilan yang telah dilakukan. Kamu dapat berlangganan pada event dengan menggunakan metode `on`.

```typescript
presence.on("UpdateData", async () => {
  // Melakukan sesuatu ketika data diperbarui.
});
```

Ada beberapa event yang tersedia:

#### `UpdateData`

Event ini akan diluncurkan setiap kali presence diperbarui.

#### `iFrameData`

Diluncurkan saat berhasil menerima data dari iFrame script.
