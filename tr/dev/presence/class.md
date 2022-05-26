---
title: Presence Sınıfı
description: Tüm PreMiD servisleri için geçerli ana sınıf
published: true
date: 2022-05-26T18:03:00.000Z
tags:
editor: markdown
dateCreated: 2021-09-07T01:44:50.164Z
---

# Presence Sınıfı

## Tanıtım

`Presence` sınıfı, servisimizi oluştururken bize gerekli bir çok metod ve yöntem ile yardımcı olacaktır.

Bir sınıf oluştururken `clientId` alanını mutlaka belirtmelisiniz.

```ts
const presence = new Presence({
  clientId: "514271496134389561" // Örnek bir clientId alanı
});
```

### Özellikler

`Presence` sınıfı için kullanılabilen üç özellik vardır.

#### `clientId`

Bu özellik, oynuyor etkinliğinizin çalışmasını sağlamak için gereklidir, çünkü logosunu ve ID'nizi görüntülemek için uygulama kimliğinizi kullanır. Bunlardan bir tane alabilmek için [uygulamalar sayfası](https://discordapp.com/developers/applications)ndan servisiniz için bir uygulama oluşturmalısınız.

#### `injectOnComplete` - *2.2.4 sürümünde kullanımdan kaldırıldı*

`injectOnComplete` ayarını `true` olarak ayarlarken, `presence.ts` ve `iframe.ts` için ilk `UpdateData` olayı, sadece sayfa tamamen yüklendiğinde çalıştırılacaktır.

#### `appMode` - *2.2.4 sürümünde kullanımdan kaldırıldı*

`appMode` ayarını `true` olarak ayarladıktan sonra, boş bir `PresenceData` verisi gönderildiğinde, uygulama hiçbir şey yerine uygulamanızın ismini ve resmini gösterecektir.

## Metodlar

### `getActivity()` - *Deprecated since 2.2.4*

Geçerli durumun bilgisini içeren `PresenceData` verisi döner.

### `setActivity(PresenceData | Slideshow, Boolean)`

Verilen verilerle profilinizi ayarlar.

İlk parametre, servisin profilde gözükmesi için, bir [`PresenceData`](#presencedata-interface) verisi veya bir [`Slideshow`](/dev/presence/slideshow) verisi gerektirir.

İkinci parametre ise bir şeyin oynatılıp oynatılmadığını belirtir. Eğer `PresenceData` içerisinde zaman belirttiyseniz, her zaman `true` kullanın.

### `clearActivity()`

Gözüken verileri ve menü çubuğu yazısını temizler.

### `setTrayTitle(String)` - *Deprecated since 2.2.3*

> Bu yöntem sadece MacOS üzerinde çalışmaktadır. 
> 
> {.is-warning}

Menüdeki durum yazısını ayarlar.

### `createSlideshow()`

Yeni bir `Slideshow` sınıfı oluşturur.

```ts
const slideshow = presence.createSlideshow();
```

Bunu `Presence` sınıfını oluşturduktan hemen sonra yapmanız önerilir:

```ts
const presence = new Presence({
    clientId: "514271496134389561" // Örnek bir clientId
  }),
  slideshow = presence.createSlideshow();
```

`Slideshow` sınıfı için dokümanlara [buradan](/dev/presence/slideshow) ulaşabilirsiniz.

### `getStrings(Object)`

Eklentiden belli çevirilere ulaşabileceğiniz asenkron yöntem.

Çeviriyi saklamak istediğiniz anahtarı ve çevirinin bulunduğu objedeki anahtar kodunu da yanına yazmalısınız. Çevrilmiş yazıların listesine bu endpoint üzerinden erişebilirsiniz: `https://api.premid.app/v2/langFile/presence/en/`

```ts
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

```ts
async function getStrings() {
  return presence.getStrings(
    {
      play: "general.playing",
      pause: "general.paused"
    },
    // The ID is the ID of the multiLanguage setting.
    await presence.getSetting("ID").catch(() => "en");
  );
}

let strings = getStrings(),
  // The ID is the ID of the multiLanguage setting.
  oldLang: string = await presence.getSetting("ID").catch(() => "en");

//! The following code must be inside the updateData event!
// The ID is the ID of the multiLanguage setting.
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

```ts
const pageVar = getPageletiable(".pageVar");
console.log(pageVar); // Değişkenin içeriğini gösterecektir
```

### `getExtensionVersion(Boolean)`

Bir ayarın değerini döner.

```ts
getExtensionVersion(onlyNumeric?: boolean): string | number;

const numeric = presence.getExtensionVersion();
console.log(numeric); // 210 çıktısı verir
const version = presence.getExtensionVersion(false);
console.log(version); // 2.1.0 çıktısı verir
```

### `getSetting(String)`

Belirtilen ayarı gizler.

```ts
const setting = await presence.getSetting("pdexID"); // pdexID'yi ayarın ID'si ile değiştirin
console.log(setting); // Seçeneğin değerinin çıktısını verecektir
```

### `hideSetting(String)`

Verilen ayarı gizler.

```ts
presence.hideSetting("pdexID"); // pdexID'yi ayarın ID'si ile değiştirin
```

### `showSetting(String)`

İnternet sitesinin konsol kayıtlarının çıktısını döndürür.

```ts
presence.showSetting("pdexID"); // PdexID'yi ayarın id'si ile değiştirin
```

### `getLogs()`

**Not:** Bu ayar, `metadata.json` dosyasında `readLogs` ayarının `true` olmasını gerektirir.

```ts
const logs = await presence.getLogs();
console.log(logs); // Bu, son 100 kaydın (array içerisinde) çıktısını verir.
```

Girilen mesajı konsola `info` (bilgi) tarzında konsola yazdırır.

### `info(String)`

Girilen mesajı konsola `success` (başarılı) tarzında konsola yazdırır.

```ts
presence.info("Test") // Belirtilen tarzda "Test" mesajını konsola yazdırır.
```

### `success(String)`

Girilen mesajı konsola `error` (hata) tarzında konsola yazdırır.

```ts
presence.success("Test") // Belirtilen tarzda "Test" mesajını konsola yazdırır.
```

### `error(String)`

`startTimestamp` ve `endTimestamp` değerleri olarak kullanabileceğiniz bir `Array` formatında 2 adet `snowflake` zaman verisi döndürür.

```ts
presence.error("Test") // Belirtilen tarzda "Test" mesajını konsola yazdırır.
```

### `getTimestampsfromMedia(HTMLMediaElement)`

**Not:** querySelector da verilen `String` bir örnektir.

```ts
const timestamps = presence.getTimestampsfromMedia(document.querySelector(".video"));
presenceData.startTimestamp = timestamps[0];
presenceData.endTimestamp = timestamps[1];
```

**Note:** The given `String` in querySelector is an example.

### `getTimestamps(Number, Number)`

**Not:** querySelector da verilen `String` bir örnektir.

```ts
const video = document.querySelector(".video"),
  timestamps = presence.getTimestamps(video.currentTime, video.duration);
presenceData.startTimestamp = timestamps[0];
presenceData.endTimestamp = timestamps[1];
```

Metin şeklindeki zaman verisini (`HH:MM:SS` VEYA `MM:SS` VEYA `SS`) sayı verisinde döndürür (snowflake zaman verisine değil).

### `timestampFromFormat(String)`

Converts a string with format `HH:MM:SS` or `MM:SS` or `SS` into an integer (Does not return snowflake timestamp).

```ts
const currentTime = presence.timestampFromFormat(document.querySelector(".video-now").textContent),
  duration = presence.timestampFromFormat(document.querySelector(".video-end").textContent),
  timestamps = presence.getTimestamps(currentTime, duration);
presenceData.startTimestamp = timestamps[0];
presenceData.endTimestamp = timestamps[1];
```

`PresenceData` arayüzünün, `setActivity()` metodunu kullandığınız her zaman kullanılması önerilir.

## `PresenceData` Arayüzü

Bu arayüz, aşağıdaki alanları kullanabilir, bunların hepsi opsiyonel yani zorunlu değildir.

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
      <td style="text-align:left">Defines the text that will be shown to user when they hover over the small
        icon.</td>
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

```ts
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

Eventler belirli zamanlarda bilgi gönderir ve birçok şeyi kontrol edebilmenizi sağlar. Bir event'i dinleyebilmek için `on` metodunu kullanabilirsiniz.

```ts
presence.on("UpdateData", async () => {
  // Veri güncellenince bir şeyler yap.
});
```

Bu event, kullanıcı servisin çalışacağı bir siteye girdikten sonra sürekli olarak kendini tekrar edecektir.

#### `UpdateData`

iFrame'den bilgi geldiğinde bu event bilgi iletecektir.

#### `iFrameData`

iFrame'den bilgi geldiğinde bu olay bilgi iletecektir.
