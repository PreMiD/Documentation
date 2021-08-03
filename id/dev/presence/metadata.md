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

```typescript
{
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
      "value": "\"%song%\" oleh %artist%",
      "placeholder": "pakai %song% atau %artist%"
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
      <td style="text-align:left"><b>tags</b></td>
      <td style="text-align:left">Array with tags, they will help users to search your presence on the website.</td>
      <td style="text-align:left"><code>String, Array&lt;String&gt;</code></td>
      <td style="text-align:left"><code>Tidak</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>category</b></td>
      <td style="text-align:left">String yang digunakan untuk mewakili kategori yang dimilki presence.</td>
      <td style="text-align:left"><code>String</code></td>
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
      <td style="text-align:left"><code>String</code></td>
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

If you want to learn regular expressions, here are a few websites.

#### Learning

• [Quick Starter Video](https://youtu.be/sXQxhojSdZM) • [RegexOne](https://regexone.com/) • [Regular Expressions Info](https://www.regular-expressions.info/tutorial.html)

#### Testing

• [Regexr](https://regexr.com/) • [Regex101](https://regex101.com/)

## Presence languages

PreMiD merupakan layanan poliglot, artinya terdapat banyak bahasa yang terlibat untuk menghubungkan pengguna di seluruh dunia. A full list of languages can be found with this [API endpoint](https://api.premid.app/v2/langFile/list). To customize your presence even more, you can allow users to select their presence display language. See [`multiLanguage`](#multilanguage) for more.

## Presence settings
Setup interactive settings so users can customize the presence!
```typescript
"settings": [
  {
    "id": "ID",
    "multiLanguage": true //See https://docs.premid.app/dev/presence/metadata#multilanguage
  },
  {
    "id": "ID",
    "title": "DISPLAY TITLE",
    "icon": "FONTAWESOME ICON", //Example "fas fa-info"
    "value": true //Boolean value will make it an on/off switch with the value as the default value
  },
  {
    "id": "ID",
    "if": {
      "ID": true //If another setting equals this value (true/false/0/1/etc.) then show this button
    },
    "title": "DISPLAY TITLE",
    "icon": "FONTAWESOME ICON",
    "value": "\"%song%\" by %artist%", //Putting in a string will make the setting an input one, where you can use a custom input.
    "placeholder": "use %song% or %artist%" //When input is empty it will show this grayed out
  },
  {
    "id": "ID",
    "title": "DISPLAY TITLE",
    "icon": "FONTAWESOME ICON",
    "value": 0, //Default value of the selector
    "values": ["1", "2", "etc."] //Will make the setting a selector where you select which one you want
  }
]
```

### `multiLanguage`

#### Introduction

The `multiLanguage` setting is used to allow users to manually select the language they want to presence to be shown in. This requires you to use strings from our [API](https://api.premid.app/v2/langFile/presence/en), for information on how to add strings click [here](https://docs.premid.app/dev/presence/metadata#adding-new-strings).

#### Setup

The `multiLanguage` setting is a special case, it doesn't require a `title` nor `icon` nor `value` or `values` like other settings but it does require you some more things to setup!

The `multiLanguage` key can be set to the following:

`true`: use this if you are only going to use strings of the `general.json` file and the `<service>.json` file of the [Localization Repository](https://github.com/PreMiD/Localization/tree/master/src/Presence). `string`: name of the file excluding the extension (.json) inside the [Localization Repository](https://github.com/PreMiD/Localization/tree/master/src/Presence) (excluding the `general` file, since it's always loaded). Only common languages of both the `general` and inputted file will be listed. `Array<String>`: if you are using more than one file inside the [Localization Repository](https://github.com/PreMiD/Localization/tree/master/src/Presence) you can specify all the values in an array (excluding the `general` file, since it's always loaded). Only common languages of all the files will be listed.

#### Adding new strings

**Note:** Adding custom strings for a presence is only allowed if it has more than 1000 users.

##### Membuat clone project

1. Buka terminal dan ketik `git clone https://github.com/PreMiD/Localization`.
2. Pilih folder pilihanmu.
3. Buka di editor kodemu.

##### Creating the file

1. Go into the `src` folder.
2. Go into the `Presence` folder.
3. Make a file named `<service>.json`. (Service is the **name** (not an URL) in lowercase of the service you want to support.)

##### Adding the strings

Each `string` is an `Object` where from the name starts with the service name and then the so called stringName with a dot in between them.

The stringName is a 1 word identifier of the message.

The `Object` has 2 properties; `message` and `description`. `message` is the text that needs to be translated. `description` is a description of the message to help our translators understand what they are translating.

**Note:** Do not add any duplicate strings. (This includes strings out of the `general.json` file but not the other files.)

Visualization of the file:

```typescript
{
  "<service>.<stringName>": {
    "message": "Text that needs to be translated.",
    "description": "This explains what the message above is."
  },
  "<service>.<stringName>": {
    "message": "Text that needs to be translated.",
    "description": "This explains what the message above is."
  }
}
```

After you have fully made the file with strings you can create a Pull Request on the [Localization Repository](https://github.com/PreMiD/Localization), in the description you **must** include a link to your Pull Request of the presence updated using these new strings from the [Presence Repository](https://github.com/PreMiD/Presences).

#### Default keys
The keys you didn't have to set are automatically set to the following: `title`: "Language" **Note:** This is translated into their default language (browser language). `icon`: "fas fa-language" ([Preview](https://fontawesome.com/icons/language)) `value`: **Set to their browser language if it is available (100% translated), otherwise English.** `values`: **Set to the available languages (languages that have it 100% translated).**

**Note:** These are in no way changeable.

### Metode

Gunakan metode berikut untuk mendapat info pengaturan pada file presence:
#### `getSetting(String)`
Mengembalikan value dari setting.
```typescript
const setting = await presence.getSetting("pdexID"); //Replace pdexID with the id of the setting
console.log(setting); // This will log the value of the setting
```

#### `hideSetting(String)`
Hides given setting.
```typescript
presence.hideSetting("pdexID"); //Replace pdexID with the id of the setting
```

#### `showSetting(String)`
Menampilkan pengaturan yang diberikan (Hanya bekerja jika pengaturan telah disembunyikan).
```typescript
presence.showSetting("pdexID"); //Replace pdexID with the id of the setting
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
      <td style="text-align:left">Any website that has game related content, such as <code>Kahoot</code> or <code>Skribbl.io</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>music</b></td>
      <td style="text-align:left"><b>Musik</b></td>
      <td style="text-align:left">Website ini menawarkan konten yang berhubungan dengan musik, streaming atau download.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>socials</b></td>
        <td style="text-align:left"><b>Sosial</b></td>
      <td style="text-align:left">Website yang dibuat untuk membuat dan membagikan konten atau berpartisipasi dalam social network dalam bentuk apapun.</td>
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

