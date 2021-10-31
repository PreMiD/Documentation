---
title: iFrame Trieda
description: 
published: true
date: 2021-09-18T14:42:23.280Z
tags: 
editor: markdown
dateCreated: 2021-09-07T01:57:47.298Z
---

# iFrame Trieda

## Úvod

V niektorých prípadoch, vaša prítomnosť možno bude potrebovať prístup k prvkom vo vnútri `iframu`.

Kód ktorý vpíšete do vnútra vášho `iframe.ts` súboru sa vloží do každého iframe na stránke.

Ako prítomnosti, `iframes` má svoju triedu určenú na automatickú aktualizáciu údajov.

```typescript
let iframe = new iFrame();

iframe.on("UpdateData", async () => {
    // Code goes here...
});
```

## Metódy

### `send(Object)`
Odošle údaje do prítomnosti. Použitím tejto metódy, prítomnosť udeje `iFrameData`.

### `getUrl()`
Vráti URL `iframu`.

## Udalosti
Vo `iframe`, udalostiach pracujú podobným spôsobom ako pracujú v triede `prítomností`.

```typescript
iframe.on("UpdateData", async () => {
    // Code goes here...
});
```

Tu je zoznam všetkých udalostí:

#### `UpdateData`

Táto udalosť sa spustí pri každej aktualizácii prvku iframe.
