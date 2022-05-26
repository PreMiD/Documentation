---
title: Kelas Presence
description: Kelas utama untuk setiap Presence di PreMiD
published: true
date: 2022-05-26T18:03:00.000Z
tags:
editor: markdown
dateCreated: 2021-09-07T01:44:50.164Z
---

# Kelas Presence

## Pengenalan

Kelas `Presence` sangat berguna kerana ia mempunyai kaedah asas yang diperlukan untuk mencipta Presence.

Apabila anda mencipta kelas, anda mesti nyatakan sifat `clientId`.

```ts
const presence = new Presence({
  clientId: "514271496134389561" // Contoh clientId
});
```

### Sifat-sifat

Terdapat tiga sifat yang wujud untuk kelas `Presence`.

#### `clientId`

Sifat ini diperlukan untuk membolehkan Presence anda berfungsi, kerana ia menggunakan id aplikasi anda untuk memaparkan logo dan asetnya. Anda boleh dapatkannya di [halaman aplikasi](https://discordapp.com/developers/applications) anda.

#### `injectOnComplete` - *Diperkecamkan sejak 2.2.4*

Apabila menetapkan nilai `injectOnComplete` ke `true`, peristiwa `UpdateData` yang pertama untuk kedua-dua fail `presence.ts` dan `iframe.ts` hanya akan dijalankan apabila halaman telah dimuatkan sepenuhnya.

#### `appMode` - *Diperkecamkan sejak 2.2.4*

Apabila menetapkan nilai `appMode` ke `true` dan Presence menghantar `PresenceData` yang kosong, aplikasi akan hantarkan (imej dan nama) aplikasi di profil pengguna menggantikan kekosongan.

## Kaedah

### `getActivity()` - *Diperkecamkan sejak 2.2.4*

Mengembalikan objek `PresenceData` berkaitan apa yang Presence paparkan.

### `setActivity(PresenceData | Slideshow, Boolean)`

Tetapkan aktiviti profil anda mengikut data yang diberikan.

Parameter pertama memerlukan antara muka [`PresenceData`](#presencedata-interface) atau kelas [`Slideshow`](/dev/presence/slideshow) untuk mendapatkan segala maklumat yang anda ingin paparkan di profil anda.

Parameter kedua menentukan sama ada Presence sedang memainkan sesuatu atau tidak. Sentiasa gunakan nilai `true` sekiranya anda sediakan cap masa dalam `PresenceData`.

### `clearActivity()`

Mengosongkan aktiviti semasa dan tajuk talam.

### `setTrayTitle(String)` - *Diperkecamkan sejak 2.2.3*

> Kaedah ini hanya berfungsi di Mac OS. 
> 
> {.is-warning}

Menetapkan tajuk talam di bar menu.

### `createSlideshow()`

Mencipta kelas `Slideshow` yang baharu.

```ts
const slideshow = presence.createSlideshow();
```

Ia digalakkan untuk melakukan perkara ini sebaik mencipta kelas `Presence`:

```ts
const presence = new Presence({
    clientId: "514271496134389561" // Contoh clientId
  }),
  slideshow = presence.createSlideshow();
```

Anda boleh cari pendokumenan untuk kelas `Slideshow` di [sini](/dev/presence/slideshow).

### `getStrings(Object)`

Kaedah tak segerak yang membolehkan anda dapatkan rentetan terjemahan dari sambungan.

Amda mesti sediakan objek `Object` dengan kekuncinya sebagai kekunci untuk rentetan, `keyValue` ialah nilai rentetan. Senarai rentetan yang diterjemah boleh dijumpai di titik akhir ini: `https://api.premid.app/v2/langFile/presence/en/`

```ts
// Mengembalikan rentetan `Bermain` dan `Dijedakan`
// dari sambungan.
const strings = await presence.getStrings({
  play: "general.playing",
  pause: "general.paused"
});

const playString = strings.play; // hasilnya: Bermain
const pauseString = strings.pause; // hasilnya: Dijedakan
```

Sejak v2.2.0 sambungan, anda mampu dapatkan rentetan bagi sesebuah bahasa. Ini berfungsi dengan baik menggunakan pilihan tetapan `multiLanguage` yang baru ditambah.

Kami cadangkan anda gunakan kod di bawah supaya ia mengemas kini PresenceData secara automatik sekiranya pengguna mengubah bahasa yang dipilih;

```ts
async function getStrings() {
  return presence.getStrings(
    {
      play: "general.playing",
      pause: "general.paused"
    },
    // ID di sini ialah ID dalam tetapan multiLanguage.
    await presence.getSetting("ID").catch(() => "en");
  );
}

let strings = getStrings(),
  // ID di sini ialah ID dalam tetapan multiLanguage.
  oldLang: string = await presence.getSetting("ID").catch(() => "en");

//! Kod di bawah ini mestilah berada dalam peristiwa updateData!
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

Mengembalikan pemboleh ubah dari laman sesawang jika ia wujud.

**Amaran: Fungsi ini boleh menyebabkan penggunaan CPU yang tinggi & tapak lembap bertindak balas apabila ia telah dijalankan dengan terlalu banyak kali.**

```ts
const pageVar = presence.getPageletiable("pageVar");
console.log(pageVar); // Ini akan mengelog "Kandungan pemboleh ubah"
```

### `getExtensionVersion(Boolean)`

Mengembalikan versi sambungan yang pengguna guna.

```ts
getExtensionVersion(onlyNumeric?: boolean): string | number;

const numeric = presence.getExtensionVersion();
console.log(numeric); // Akan mengelog 210
const version = presence.getExtensionVersion(false);
console.log(version); // Akan mengelog 2.1.0
```

### `getSetting(String)`

Mengembalikan nilai tetapan.

```ts
const setting = await presence.getSetting("pdexID"); //Gantikan pdexID dengan ID tetapan
console.log(setting); // Ini akan log nilai tetapan
```

### `hideSetting(String)`

Sembunyikan tetapan yang diberi.

```ts
presence.hideSetting("pdexID"); // Gantikan pdexID dengan ID tetapan
```

### `showSetting(String)`

Tunjukkan tetapan yang diberi (Hanya berfungsi jika tetapan telah disembunyikan sebelumnya).

```ts
presence.showSetting("pdexID"); // Gantikan pdexID dengan ID tetapan
```

### `getLogs()`

Mengembalikan log bagi konsol laman sesawang.

```ts
const logs = await presence.getLogs();
console.log(logs); // Ini akan mengelog 100 log terbaru (dalam tatasusunan).
```

**Nota:** Memerlukan nilai `readLogs` ditetapkan ke `true` dalam fail `metadata.json`.

### `info(String)`

Mencetak mesej diberi ke konsol dalam format berasaskan Presence dalam gaya `info`.

```ts
presence.info("Test") // Ini akan mengelog "test" dalam penggayaan yang betul.
```

### `success(String)`

Mencetak mesej diberi ke konsol dalam format berasaskan Presence dalam gaya `success`.

```ts
presence.success("Test") // Ini akan mengelog "test" dalam penggayaan yang betul.
```

### `error(String)`

Mencetak mesej diberi ke konsol dalam format berasaskan Presence dalam gaya `error`.

```ts
presence.error("Test") // Ini akan mengelog "test" dalam penggayaan yang betul.
```

### `getTimestampsfromMedia(HTMLMediaElement)`

Mengembalikan 2 cap masa emping salji `snowflake` di dalam tatasusunan `Array` yang kemudiannya boleh digunakan untuk nilai cap masa mula `startTimestamp` dan cap masa tamat `endTimestamp`.

```ts
const timestamps = presence.getTimestampsfromMedia(document.querySelector(".video"));
presenceData.startTimestamp = timestamps[0];
presenceData.endTimestamp = timestamps[1];
```

**Nota:** Rentetan `String` yang diberi di querySelector ini hanyalah contoh.

### `getTimestamps(Number, Number)`

Mengembalikan 2 cap masa emping salji `snowflake` di dalam tatasusunan `Array` yang kemudiannya boleh digunakan untuk nilai cap masa mula `startTimestamp` dan cap masa tamat `endTimestamp`.

```ts
const video = document.querySelector(".video"),
  timestamps = presence.getTimestamps(video.currentTime, video.duration);
presenceData.startTimestamp = timestamps[0];
presenceData.endTimestamp = timestamps[1];
```

**Nota:** Rentetan `String` yang diberi di querySelector ini hanyalah contoh.

### `timestampFromFormat(String)`

Menukarkan rentetan dengan format JJ:MM:SS `HH:MM:SS` atau MM:SS `MM:SS` atau SS `SS` menjadi nombor bulat (Tidak mengembalikan cap masa emping salji).

```ts
const currentTime = presence.timestampFromFormat(document.querySelector(".video-now").textContent),
  duration = presence.timestampFromFormat(document.querySelector(".video-end").textContent),
  timestamps = presence.getTimestamps(currentTime, duration);
presenceData.startTimestamp = timestamps[0];
presenceData.endTimestamp = timestamps[1];
```

**Nota:** Rentetan `String` yang diberi di querySelector ini hanyalah contoh.

## Antara Muka `presenceData`

Antara muka `PresenceData` digalakkan penggunaannya apabila anda menggunakan kaedah `setActivity()`.

Antara muka ini mempunyai pemboleh ubah berikut, kesemuanya pilihan.

<table>
  <thead>
    <tr>
      <th style="text-align:left">Pemboleh ubah</th>
      <th style="text-align:left">Keterangan</th>
      <th style="text-align:left">Jenis</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">details</td>
      <td style="text-align:left">Baris pertama dalam Presence anda, selalunya digunakan sebagai pengepala.</td>
      <td style="text-align:left"><code>String</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">state</td>
      <td style="text-align:left">Baris kedua dalam Presence anda.</td>
      <td style="text-align:left"><code>String</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">startTimestamp</td>
      <td style="text-align:left">Menentukan waktu semasa.<br>
        Digunakan jika anda ingin paparkan berapa jam:minit:saat <code>hours:minutes:seconds</code> yang tinggal.
          <br>Anda mesti ubah waktu anda ke bentuk cap masa <code>timestamp</code> atau
          anda akan dapat kiraan masa menurun yang salah.
      </td>
      <td style="text-align:left"><code>Number</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">endTimestamp</td>
      <td style="text-align:left">Menentukan jangka masa penuh.
        <br>Digunakan jika anda ingin paparkan berapa jam:minit:saat <code>hours:minutes:seconds</code> yang tinggal.
          <br>Anda mesti ubah waktu anda ke bentuk cap masa <code>timestamp</code> atau anda akan
          dapat kiraan masa menurun yang salah.
      </td>
      <td style="text-align:left"><code>Number</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">largeImageKey</td>
      <td style="text-align:left">Menentukan logo untuk Presence anda.</td>
      <td style="text-align:left"><code>String</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">smallImageKey</td>
      <td style="text-align:left">Menentukan ikon kecil di sebelah logo Presence.</td>
      <td style="text-align:left"><code>String</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">smallImageText</td>
      <td style="text-align:left">Menentukan tulisan yang akan ditunjukkan kepada pengguna apabila
        dia melalukan tetikus di atas ikon kecil.</td>
      <td style="text-align:left"><code>String</code>
      </td>
    </tr>
        <tr>
      <td style="text-align:left">buttons</td>
      <td style="text-align:left">Tatasusunan butang, maksimum 2, label ialah teks di butang, dan url ialah pautan yang berkaitan.</td>
      <td style="text-align:left"><code>Array&lt;Object&gt;</code>
      </td>
    </tr>
  </tbody>
</table>

```ts
const presenceData: PresenceData = {
  details: "Tajuk saya",
  state: "Keterangan saya",
  largeImageKey: "logo_perkhidmatan",
  smallImageKey: "ikon_perkhidmatan_kecil",
  smallImageText: "Anda lalukan tetikus atas saya, jadi nak buat apa sekarang?",
  startTimestamp: 1564444631188,
  endTimestamp: 1564444634734,
  buttons: [
    {
            label: "Butang cubaan 1",
            url: "https://premid.app/"
        },
        {
            label: "Butang cubaan 2",
            url: "https://premid.app/contributors"
        }
    ]
};
```

## Peristiwa

Peristiwa membolehkan anda kesan dan urus beberapa perubahan atau panggilan yang dibuat. Anda boleh melanggan peristiwa menggunakan kaedah `on`.

```ts
presence.on("UpdateData", async () => {
  // Buat sesuatu apabila data dikemas kini.
});
```

Terdapat beberapa peristiwa tersedia:

#### `UpdateData`

Peristiwa ini dijalankan setiap kali Presence dikemas kini.

#### `iFrameData`

Dijalankan apabila data diterima dari skrip iFrame.
