---
title: iFrame Klasse
description:
published: true
date: 2021-12-20T14:27:18.034Z
tags:
editor: markdown
dateCreated: 2021-09-07T01:44:57.665Z
---

# iFrame Klasse

## Introductie

In sommige scenario's heeft jouw presence mogelijk toegang nodig tot elementen in `iframes`.

De code die je in je `iframe.ts` bestand schrijft, wordt in elk iframe op de pagina geïnjecteerd.

Zoals presences hebben `iframes` hun eigen klasse ontworpen om de gegevens automatisch bij te werken.

```ts
let iframe = new iFrame();

iframe.on("UpdateData", async () => {
    // Code gaat hier...
});
```

## Methodes

### `send(Object)`
Verzendt gegevens naar de presence. Met behulp van deze methode gooit u een `iFrameData` event.

### `getUrl()`
Geeft als resultaat de URL van de `iframe`.

## Events
In `iframes`werkt events net zoals de manier waarop ze werken in de `presence` klas.

```ts
iframe.on("UpdateData", async () => {
    // Code gaat hier...
});
```

Hier is een lijst van alle events:

#### `UpdateData`

Dit evenement wordt afgevuurd elke keer dat de iframe wordt bijgewerkt.
