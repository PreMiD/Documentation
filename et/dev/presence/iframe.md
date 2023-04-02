---
title: iFrame'i klass
description:
published: true
date: 2021-12-20T14:27:18.034Z
tags:
editor: markdown
dateCreated: 2021-09-07T01:44:57.665Z
---

# iFrame'i klass

## Sissejuhatus

Mõne stsenaariumi korral võib teie presence-il olla vaja juurdepääsu `iframes`-i elementidele.

Kood, mille kirjutate faili `iframe.ts`, sisestatakse lehe igasse iframe'i.

Sarnaselt presence-itega on `iframe`-il oma klassid, mis on mõeldud andmete automaatseks värskendamiseks.

```ts
let iframe = new iFrame();

iframe.on("UpdateData", async () => {
    //Kood läheb siia...
});
```

## Meetodid

### `send(Object)`
Saadab andmeid presence-ile. Selle meetodi kasutamine paneb presence'i viskama sündmuse `iFrameData`.

### `getUrl()`
Tagastab `iframe` URL-i.

## Sündmused
`iframe`-i sündmused toimivad sarnaselt klassi `presence` toimimisega.

```ts
iframe.on("UpdateData", async () => {
    // Kood läheb siia...
});
```

Siin on kõigi sündmuste loend:

#### `UpdateData`

See sündmus käivitatakse iga kord, kui iframe'i värskendatakse.
