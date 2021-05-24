---
title: Kelas iFrame
description:
published: true
date: 2020-05-03T20:17:51.982Z
tags:
---

# Kelas iFrame
> Sistem iframe pada PreMiD kadang bermasalah dan dapat berperilaku tidak terduga, gunakan dengan hati-hati. 
> 
> {.is-danger}

## Perkenalan

Dalam beberapa skenario, presence kamu mungkin perlu mengakses elemen di dalam `iframes`.

Kode yang kamu tulis di dalam file `iframe.ts` kamu, akan disuntikkan ke setiap iframe pada halaman.

Like presences, `iframes` have their own classes designed to automatically update data.

```typescript
let iframe = new iFrame();

iframe.on("UpdateData", async () => {
    // Kode di sini...
});
```

## Metode

### `send(Object)`
Sends data to the presence. Using this method will make the presence throw a `iFrameData` event.

### `getUrl()`
Returns the URL of the `iframe`.

## Acara
Di `iframes`, acara bekerja sama dengan cara kerjanya di kelas `presence`.

```typescript
iframe.on("UpdateData", async () => {
    // Kode di sini...
});
```

Here is a list of all of the events:

#### `UpdateData`

This event is fired every time the iframe is being updated.