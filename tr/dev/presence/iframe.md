---
title: iFrame Sınıfı
description:
published: true
date: 2021-09-18T14:31:12.831Z
tags:
editor: markdown
dateCreated: 2021-09-07T01:44:57.665Z
---

# iFrame Sınıfı

## Tanıtım

Bazı durumlarda, servisiniz `iframelerin` içerisindeki bilgilere erişme ihtiyacında bulunabilir.

`iframe.ts` dosyasına yazdığınız kod, sayfada bulunan tüm iframe elementlerinin içine yazılır ve işlemeye başlar.

Servisler gibi, `iframe`'lerin de kendilerine ait bir sınıfı vardır ve verileri otomatik olarak güncellenir.

```ts
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

```ts
iframe.on("UpdateData", async () => {
    // Kod buraya geliyor...
});
```

Kullanabileceğiniz eventlerin listesi:

#### `UpdateData`

Bu event, iframeden her bilgi geldiğinde çalışacaktır.
