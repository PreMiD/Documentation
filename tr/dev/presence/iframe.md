---
title: iFrame Sınıfı
description:
published: true
date: 2021-07-01T14:03:55.793Z
tags:
---

# iFrame Sınıfı

## Tanıtım

Bazı durumlarda, servisiniz `iframelerin` içerisindeki bilgilere erişme ihtiyacında bulunabilir.

`iframe.ts` dosyasına yazdığınız kod, sayfada bulunan tüm iframe elementlerinin içine yazılır ve işlemeye başlar.

Servisler gibi, `iframe`'lerin de kendilerine ait bir sınıfı vardır ve verileri otomatik olarak güncellenir.

```typescript
let iframe = new iFrame();

iframe.on("UpdateData", async () => {
    // Kod buraya geliyor...
});
```

## Metodlar

### `send(Object)`
Veriyi servis koduna gönderir. Bu metodu kullanmak servis kodunda bir `iFrameData` eventi çalıştıracaktır.

### `getUrl()`
`iframe`'in bağlantısını gösterir.

## Eventler/Eylemler
`iframe` elementlerinde, eventler aynı `presence` sınıfında olduğu gibi çalışır.

```typescript
iframe.on("UpdateData", async () => {
    // Kod buraya geliyor...
});
```

Kullanabileceğiniz eventlerin listesi:

#### `UpdateData`

Bu event, iframeden her bilgi geldiğinde çalışacaktır.
