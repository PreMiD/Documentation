---
title: Kelas iFrame
description:
published: true
date: 2021-07-01T14:03:55.793Z
tags:
---

# Kelas iFrame

## Perkenalan

Dalam beberapa skenario, presence kamu mungkin perlu mengakses elemen di dalam `iframes`.

Kode yang kamu tulis di dalam file `iframe.ts` kamu, akan disuntikkan ke setiap iframe pada halaman.

Seperti presence, `iframes` memiliki kelasnya tersendiri yang dirancang untuk memperbarui data secara otomatis.

```typescript
let iframe = new iFrame();

iframe.on("UpdateData", async () => {
    // Kode di sini...
});
```

## Metode

### `send(Object)`
Mengirim data ke presence. Menggunakan metode ini akan membuat presence melemparkan acara `iFrameData`.

### `getUrl()`
Mengembalikan URL `iframe`.

## Acara
Pada bagian `iframes`, events bekerja sama dengan cara kerjanya di kelas `presence`.

```typescript
iframe.on("UpdateData", async () => {
    // Kode di sini...
});
```

Berikut adalah daftar semua events:

#### `UpdateData`

Event ini akan diluncurkan setiap kali iframe diperbarui.
