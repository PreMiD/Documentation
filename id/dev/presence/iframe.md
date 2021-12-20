---
title: Kelas iFrame
description:
published: true
date: 2021-12-20T14:27:18.034Z
tags:
editor: markdown
dateCreated: 2021-09-07T01:44:57.665Z
---

# Kelas iFrame

## Perkenalan

Dalam beberapa skenario, presence kamu mungkin perlu mengakses elemen di dalam `iframes`.

Kode yang kamu tulis di dalam file `iframe.ts` kamu, akan disuntikkan ke setiap iframe pada halaman.

Seperti presence, `iframes` memiliki kelasnya tersendiri yang dirancang untuk memperbarui data secara otomatis.

```ts
let iframe = new iFrame();

iframe.on("UpdateData", async () => {
    // Kode di sini...
});
```

## Metode

### `send(Object)`
Mengirim data ke presence. Menggunakan metode ini akan membuat presence melemparkan event `iFrameData`.

### `getUrl()`
Mengembalikan URL `iframe`.

## Event
Pada bagian `iframes`, events bekerja sama dengan cara kerjanya di kelas `presence`.

```ts
iframe.on("UpdateData", async () => {
    // Kode di sini...
});
```

Berikut adalah daftar semua events:

#### `UpdateData`

Event ini akan diluncurkan setiap kali iframe diperbarui.
