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
In `iframes`, events work similarly to the way they work in the `presence` class.

```ts
iframe.on("UpdateData", async () => {
    // Code goes here...
});
```

Here is a list of all of the events:

#### `UpdateData`

This event is fired every time the iframe is being updated.
