---
title: Kelas Presence
description: Kelas utama untuk setiap Presence di PreMiD
published: true
date: 2021-05-23T09:14:06.963Z
tags:
editor: markdown
dateCreated: 2021-02-21T21:13:14.449Z
---

# Kelas Presence

## Pengenalan

Kelas `Presence` sangat berguna kerana ia mempunyai kaedah asas yang diperlukan untuk mencipta Presence.

Apabila anda mencipta kelas, anda mesti nyatakan sifat `clientId`.

```typescript
const presence = new Presence({
  clientId: "514271496134389561" // Contoh clientId
});
```

### Sifat-sifat

Terdapat tiga sifat yang wujud untuk kelas `Presence`.

#### `clientId`

Sifat ini diperlukan untuk membolehkan Presence anda berfungsi, kerana ia menggunakan id aplikasi anda untuk memaparkan logo dan asetnya. Anda boleh dapatkannya di [halaman aplikasi](https://discordapp.com/developers/applications) anda.

#### `injectOnComplete` - *Deprecated since 2.2.4*

Apabila menetapkan nilai `injectOnComplete` ke `true`, peristiwa `UpdateData` yang pertama untuk kedua-dua fail `presence.ts` dan `iframe.ts` hanya akan dijalankan apabila halaman telah dimuatkan sepenuhnya.

#### `appMode` - *Deprecated since 2.2.4*

Apabila menetapkan nilai `appMode` ke `true` dan Presence menghantar `PresenceData` yang kosong, aplikasi akan hantarkan (imej dan nama) aplikasi di profil pengguna menggantikan kekosongan.

## Kaedah

### `getActivity()`

Mengembalikan objek `PresenceData` berkaitan apa yang Presence paparkan.

### `setActivity(PresenceData | Slideshow, Boolean)`

Tetapkan aktiviti profil anda mengikut data yang diberikan.

Parameter pertama memerlukan antara muka [`PresenceData`](#presencedata-interface) atau kelas [`Slideshow`](/dev/presence/slideshow) untuk mendapatkan segala maklumat yang anda ingin paparkan di profil anda.

Parameter kedua menentukan sama ada Presence sedang memainkan sesuatu atau tidak. Sentiasa gunakan nilai `true` sekiranya anda sediakan cap masa dalam `PresenceData`.

### `clearActivity()`

Mengosongkan aktiviti semasa dan tajuk talam.

### `setTrayTitle(String)`

> Kaedah ini hanya berfungsi di Mac OS. 
> 
> {.is-warning}

Menetapkan tajuk talam di bar menu.

### `createSlideshow()`

Mencipta kelas `Slideshow` yang baharu.

```typescript
const slideshow = presence.createSlideshow();
```

Ia digalakkan untuk melakukan perkara ini sebaik mencipta kelas `Presence`:

```typescript
const presence = new Presence({
    clientId: "514271496134389561" // Contoh clientId
  }),
  slideshow = presence.createSlideshow();
```

Anda boleh cari pendokumenan untuk kelas `Slideshow` di [sini](/dev/presence/slideshow).

### `getStrings(Object)`

Kaedah tak segerak yang membolehkan anda dapatkan rentetan terjemahan dari sambungan.

Amda mesti sediakan objek `Object` dengan kekuncinya sebagai kekunci untuk rentetan, `keyValue` ialah nilai rentetan. Senarai rentetan yang diterjemah boleh dijumpai di titik akhir ini: `https://api.premid.app/v2/langFile/presence/en/`

```typescript
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

```typescript
// Sebuah antara muka bagi rentetan yang anda akan terima (contoh bagus untuk kualiti kod dan autolengkap).
interface LangStrings {
  play: string;
  pause: string;
}

async function getStrings(): Promise<LangStrings> {
  return presence.getStrings(
    {
      // Rentetan yang anda dapatkan, pastikan ia sesuai dengan antara muka LangStrings anda.
      play: "general.playing",
      pause: "general.paused"
    },
    // ID ini ialah ID bagi tetapan multiLanguage.
    await presence.getSetting("ID").catch(() => "en");
  );
}

let strings: Promise<LangStrings> = getStrings(),
  // ID ini ialah ID bagi tetapan multiLanguage.
  oldLang: string = await presence.getSetting("ID").catch(() => "en");

//! Kod di bawah mestilah berada dalam peristiwa updateData!
// ID ini ialah ID bagi tetapan multiLanguage.
const newLang = await presence.getSetting("ID").catch(() => "en");
if (oldLang !== newLang) {
  oldLang = newLang;
  strings = getStrings();
}

const playString = (await strings).play, // hasilnya: Bermain
  pauseString = (await strings).pause; // hasilnya: Dijedakan
```

### `getPageletiable(String)`

Mengembalikan pemboleh ubah dari laman sesawang jika ia wujud.

**Warning: This function can cause high CPU usage & site lagging when it has been executed too many times.**

```typescript
const pageVar = presence.getPageletiable("pageVar");
console.log(pageVar); // This will log the "Variable content"
```

### `getExtensionVersion(Boolean)`

Returns version of the extension the user is using.

```typescript
getExtensionVersion(onlyNumeric?: boolean): string | number;

const numeric = presence.getExtensionVersion();
console.log(numeric); // Akan mengelog 210
const version = presence.getExtensionVersion(false);
console.log(version); // Akan mengelog 2.1.0
```

### `getSetting(String)`

Mengembalikan nilai tetapan.

```typescript
const setting = await presence.getSetting("pdexID"); //Gantikan pdexID dengan ID tetapan
console.log(setting); // Ini akan log nilai tetapan
```

### `hideSetting(String)`

Sembunyikan tetapan yang diberi.

```typescript
presence.hideSetting("pdexID"); // Gantikan pdexID dengan ID tetapan
```

### `showSetting(String)`

Shows given setting (Only works if the setting was already hidden).

```typescript
presence.showSetting("pdexID"); // Gantikan pdexID dengan ID tetapan
```

### `getLogs()`

Returns the logs of the websites console.

```typescript
const logs = await presence.getLogs();
console.log(logs); // Ini akan mengelog 100 log terbaru (dalam tatasusunan).
```

**Note:** Requires `readLogs` to be `true` in the `metadata.json` file.

### `info(String)`

Prints the given message in the console in a format based of the presence in the `info` style.

```typescript
presence.info("Test") // Ini akan mengelog "test" dalam penggayaan yang betul.
```

### `success(String)`

Prints the given message in the console in a format based of the presence in the `success` style.

```typescript
presence.success("Test") // Ini akan mengelog "test" dalam penggayaan yang betul.
```

### `error(String)`

Prints the given message in the console in a format based of the presence in the `error` style.

```typescript
presence.error("Test") // Ini akan mengelog "test" dalam penggayaan yang betul.
```

### `getTimestampsfromMedia(HTMLMediaElement)`

Returns 2 `snowflake` timestamps in an `Array` that can be used for `startTimestamp` and `endTimestamp`.

```typescript
const timestamps = presence.getTimestampsfromMedia(document.querySelector(".video"));
presenceData.startTimestamp = timestamps[0];
presenceData.endTimestamp = timestamps[1];
```

**Note:** The given `String` in querySelector is an example.

### `getTimestamps(Number, Number)`

Returns 2 `snowflake` timestamps in an `Array` that can be used for `startTimestamp` and `endTimestamp`.

```typescript
const video = document.querySelector(".video"),
  timestamps = presence.getTimestamps(video.currentTime, video.duration);
presenceData.startTimestamp = timestamps[0];
presenceData.endTimestamp = timestamps[1];
```

**Note:** The given `String` in querySelector is an example.

### `timestampFromFormat(String)`

Converts a string with format `HH:MM:SS` or `MM:SS` or `SS` into an integer (Does not return snowflake timestamp).

```typescript
const currentTime = presence.timestampFromFormat(document.querySelector(".video-now").textContent),
  duration = presence.timestampFromFormat(document.querySelector(".video-end").textContent),
  timestamps = presence.getTimestamps(currentTime, duration);
presenceData.startTimestamp = timestamps[0];
presenceData.endTimestamp = timestamps[1];
```

**Note:** The given `String` in querySelector is an example.

## Antara Muka `presenceData`

The `PresenceData` interface is recommended to use when you are using the `setActivity()` method.

This interface has following variables, all of them are optional.

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

```typescript
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

Events allow you to detect and handle some changes or calls that were made. You can subscribe to events using the `on` method.

```typescript
presence.on("UpdateData", async () => {
  // Buat sesuatu apabila data dikemas kini.
});
```

There are few events available:

#### `UpdateData`

This event is fired every time the presence is being updated.

#### `iFrameData`

Fired when data is received from iFrame script.
