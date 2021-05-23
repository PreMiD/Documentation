---
title: Presence Sınıfı
description: Tüm PreMiD servisleri için geçerli ana sınıf
published: true
date: 2021-05-23T09:14:06.963Z
tags:
editor: markdown
dateCreated: 2021-02-21T21:13:14.449Z
---

# Presence Sınıfı

## Tanıtım

`Presence` sınıfı, servisimizi oluştururken bize gerekli bir çok metod ve yöntem ile yardımcı olacaktır.

Bir sınıf oluştururken `clientId` alanını mutlaka belirtmelisiniz.

```typescript
const presence = new Presence({
  clientId: "514271496134389561" // Örnek bir clientId alanı
});
```

### Özellikler

`Presence` sınıfı için kullanılabilen üç özellik vardır.

#### `clientId`

Bu özellik, oynuyor etkinliğinizin çalışmasını sağlamak için gereklidir, çünkü logosunu ve ID'nizi görüntülemek için uygulama kimliğinizi kullanır. Bunlardan bir tane alabilmek için [uygulamalar sayfası](https://discordapp.com/developers/applications)ndan servisiniz için bir uygulama oluşturmalısınız.

#### `injectOnComplete` - *Deprecated since 2.2.4*

`injectOnComplete` ayarını `true` olarak ayarlarken, `presence.ts` ve `iframe.ts` için ilk `UpdateData` olayı, sadece sayfa tamamen yüklendiğinde çalıştırılacaktır.

#### `appMode` - *Deprecated since 2.2.4*

`appMode` ayarını `true` olarak ayarladıktan sonra, boş bir `PresenceData` verisi gönderildiğinde, uygulama hiçbir şey yerine uygulamanızın ismini ve resmini gösterecektir.

## Metodlar

### `getActivity()`

Geçerli durumun bilgisini içeren `PresenceData` verisi döner.

### `setActivity(PresenceData | Slideshow, Boolean)`

Verilen verilerle profilinizi ayarlar.

İlk parametre, servisin profilde gözükmesi için, bir [`PresenceData`](#presencedata-interface) verisi veya bir [`Slideshow`](/dev/presence/slideshow) verisi gerektirir.

İkinci parametre ise bir şeyin oynatılıp oynatılmadığını belirtir. Eğer `PresenceData` içerisinde zaman belirttiyseniz, her zaman `true` kullanın.

### `clearActivity()`

Gözüken verileri ve menü çubuğu yazısını temizler.

### `setTrayTitle(String)`

> Bu yöntem sadece MacOS üzerinde çalışmaktadır. 
> 
> {.is-warning}

Menüdeki durum yazısını ayarlar.

### `createSlideshow()`

Yeni bir `Slideshow` sınıfı oluşturur.

```typescript
const slideshow = presence.createSlideshow();
```

Bunu `Presence` sınıfını oluşturduktan hemen sonra yapmanız önerilir:

```typescript
const presence = new Presence({
    clientId: "514271496134389561" // Örnek bir clientId
  }),
  slideshow = presence.createSlideshow();
```

`Slideshow` sınıfı için dokümanlara [buradan](/dev/presence/slideshow) ulaşabilirsiniz.

### `getStrings(Object)`

Eklentiden belli çevirilere ulaşabileceğiniz asenkron yöntem.

Çeviriyi saklamak istediğiniz anahtarı ve çevirinin bulunduğu objedeki anahtar kodunu da yanına yazmalısınız. Çevrilmiş yazıların listesine bu endpoint üzerinden erişebilirsiniz: `https://api.premid.app/v2/langFile/presence/en/`

```typescript
// `Oynatılıyor` ve `Durduruldu` çevirilerini
// gösterir.
const strings = await presence.getStrings({
  play: "general.playing",
  pause: "general.paused"
});

const playString = strings.play; // sonuç: Oynuyor
const pauseString = strings.pause; // sonuç: Duraklatıldı
```

Eklentinin v2.2.0 sürümünden bu yana, artık belirli bir dilin çevirilerini alabilirsiniz. Bu, yeni eklenmiş `multiLanguage` ayar seçeneği ile de düzgün çalışıyor.

Kullanıcı dili değiştirdiğinde PresenceData verisini otomatik olarak güncelleyebilmesi için aşağıdaki kodu kullanmanızı öneririz;

```typescript
// Çevirilerde kullanabileceğiniz (kod kalitesi ve otomatik tamamlama için iyi olacak) bir arayüz.
interface LangStrings {
  play: string;
  pause: string;
}

async function getStrings(): Promise<LangStrings> {
  return presence.getStrings(
    {
      // İstediğiniz çevirilerin verisi, dönen verinin LangStrings arayüzünüze uygun olduğundan emin olun.
      play: "general.playing",
      pause: "general.paused"
    },
    // Buradaki ID, multiLanguage ayarındaki ID'dir.
    await presence.getSetting("ID").catch(() => "en");
  );
}

let strings: Promise<LangStrings> = getStrings(),
  // The ID is the ID of the multiLanguage setting.
  oldLang: string = await presence.getSetting("ID").catch(() => "en");

//! Aşağıdaki kod updateData olayının (event) içerisinde olmalıdır!
// Buradaki ID, multiLanguage ayarındaki ID'dir.
const newLang = await presence.getSetting("ID").catch(() => "en");
if (oldLang !== newLang) {
  oldLang = newLang;
  strings = getStrings();
}

const playString = (await strings).play, // result: Playing
  pauseString = (await strings).pause; // result: Paused
```

### `getPageletiable(String)`

Eğer varsa sayfadaki bir değişkenin içeriğini gösterir.

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
console.log(numeric); // 210 çıktısı verir
const version = presence.getExtensionVersion(false);
console.log(version); // 2.1.0 çıktısı verir
```

### `getSetting(String)`

Returns value of setting.

```typescript
const setting = await presence.getSetting("pdexID"); // pdexID'yi ayarın ID'si ile değiştirin
console.log(setting); // Seçeneğin değerinin çıktısını verecektir
```

### `hideSetting(String)`

Hides given setting.

```typescript
presence.hideSetting("pdexID"); // pdexID'yi ayarın ID'si ile değiştirin
```

### `showSetting(String)`

Shows given setting (Only works if the setting was already hidden).

```typescript
presence.showSetting("pdexID"); // PdexID'yi ayarın id'si ile değiştirin
```

### `getLogs()`

Returns the logs of the websites console.

```typescript
const logs = await presence.getLogs();
console.log(logs); // Bu, son 100 kaydın (array içerisinde) çıktısını verir.
```

**Note:** Requires `readLogs` to be `true` in the `metadata.json` file.

### `info(String)`

Prints the given message in the console in a format based of the presence in the `info` style.

```typescript
presence.info("Test") // Belirtilen tarzda "Test" mesajını konsola yazdırır.
```

### `success(String)`

Prints the given message in the console in a format based of the presence in the `success` style.

```typescript
presence.success("Test") // Belirtilen tarzda "Test" mesajını konsola yazdırır.
```

### `error(String)`

Prints the given message in the console in a format based of the presence in the `error` style.

```typescript
presence.error("Test") // Belirtilen tarzda "Test" mesajını konsola yazdırır.
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

## `PresenceData` Arayüzü

The `PresenceData` interface is recommended to use when you are using the `setActivity()` method.

This interface has following variables, all of them are optional.

<table>
  <thead>
    <tr>
      <th style="text-align:left">Değişken</th>
      <th style="text-align:left">Açıklama</th>
      <th style="text-align:left">Tür</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">details</td>
      <td style="text-align:left">Profilinizde gözüken kısımda üst tarafta bulunan yazı.</td>
      <td style="text-align:left"><code>String</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">state</td>
      <td style="text-align:left">Profilinizde gözüken kısımda alt tarafta bulunan yazı.</td>
      <td style="text-align:left"><code>String</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">startTimestamp</td>
      <td style="text-align:left">Geçerli zamanı belirtir.<br>
        Başlangıç zamanını belirterek ondan sonra ne kadar zaman geçtiğini gösterebilirsiniz.
          <br>Zamanınızı <code>timestamp</code> formatına çevirmelisiniz, diğer türlü hesaplamalar yanlış sonuç verecektir.
      </td>
      <td style="text-align:left"><code>Number</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">endTimestamp</td>
      <td style="text-align:left">Uzunluğu belirler.
        <br>Bitiş zamanını belirlerseniz kaç <code>saat:dakika:saniye</code> kaldığını profilde gösterebilirsiniz.
          <br>Zamanınızı <code>timestamp</code> formatına çevirmelisiniz, diğer türlü hesaplamalar yanlış sonuç verecektir.
      </td>
      <td style="text-align:left"><code>Number</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">largeImageKey</td>
      <td style="text-align:left">Servisin büyük resmini belirler.</td>
      <td style="text-align:left"><code>String</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">smallImageKey</td>
      <td style="text-align:left">Büyük resmin yanında bulunacak küçük simgenin ismini belirler.</td>
      <td style="text-align:left"><code>String</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">smallImageText</td>
      <td style="text-align:left">İmleci küçük resmin üzerine tuttuğunuzda gösterilecek yazıyı belirler.</td>
      <td style="text-align:left"><code>String</code>
      </td>
    </tr>
        <tr>
      <td style="text-align:left">buttons</td>
      <td style="text-align:left">Buton array'ı, en fazla 2, label butonun metni, url ise bağlantıdır.</td>
      <td style="text-align:left"><code>Array&lt;Object&gt;</code>
      </td>
    </tr>
  </tbody>
</table>

```typescript
const presenceData: PresenceData = {
  details: "Benim başlığım",
  state: "Benim açıklamam",
  largeImageKey: "servisin_simgesi",
  smallImageKey: "ufak_servis_simgesi",
  smallImageText: "Benim üzerime geldin, ne oldu şimdi?",
  startTimestamp: 1564444631188,
  endTimestamp: 1564444634734,
  buttons: [
    {
            label: "Test tuşu1",
            url: "https://premid.app/"
        },
        {
            label: "Test tuşu2",
            url: "https://premid.app/contributors"
        }
    ]
};
```

## Olaylar

Events allow you to detect and handle some changes or calls that were made. You can subscribe to events using the `on` method.

```typescript
presence.on("UpdateData", async () => {
  // Veri güncellenince bir şeyler yap.
});
```

There are few events available:

#### `UpdateData`

This event is fired every time the presence is being updated.

#### `iFrameData`

Fired when data is received from iFrame script.
