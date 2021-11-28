---
title: Kelas iFrame
description:
published: true
date: 2021-09-18T14:31:12.831Z
tags:
editor: markdown
dateCreated: 2021-09-07T01:44:57.665Z
---

# Kelas iFrame

## Pengenalan

Dalam sesetengah senario, Presence anda mungkin perlu capai unsur di dalam `iframes`.

Kod yang anda tulis di dalam fail `iframe.ts` anda disuntik masuk ke setiap iFrame di halaman tersebut.

Seperti Presence, `iframes` mempunyai kelas mereka sendiri yang direka untuk mengemas kini data secara automatik.

```typescript
let iframe = new iFrame();

iframe.on("UpdateData", async () => {
    // Kod ditulis di sini...
});
```

## Kaedah

### `send(Object)`
Hantar data ke Presence. Penggunaan kaedah ini akan buatkan Presence mengembalikan peristiwa `iFrameData`.

### `getUrl()`
Mengembalikan URL untuk `iframe`.

## Peristiwa
Dalam `iFrame`, peristiwa dijalankan dengan cara yang serupa dengan cara peristiwa dijalankan dalam kelas `presence`.

```typescript
iframe.on("UpdateData", async () => {
    // Kod ditulis di sini...
});
```

Ini senarai kesemua peristiwa:

#### `UpdateData`

Peristiwa ini dijalankan setiap kali iFrame dikemas kini.
