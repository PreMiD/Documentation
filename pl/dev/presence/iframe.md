---
title: Klasa iFrame
description:
published: true
date: 2021-12-20T14:27:18.034Z
tags:
editor: markdown
dateCreated: 2021-09-07T01:44:57.665Z
---

# Klasa iFrame

## Wprowadzenie

W niektórych scenariuszach Twój presence może wymagać dostępu do elementów wewnątrz `iframes`.

Kod, który zapisujesz wewnątrz pliku `iframe.ts` jest wybierany do każdego iframe na stronie.

Podobnie jak presence, `iframes` mają własne klasy zaprojektowane do automatycznej aktualizacji danych.

```ts
let iframe = new iFrame();

iframe.on("UpdateData", async () => {
    // Kod idzie tutaj...
});
```

## Metody

### `send(Object)`
Wysyła dane do presence. Użycie tej metody sprawi, że presence będzie wydarzeniem `iFrameData`.

### `getUrl()`
Zwraca adres URL `iframe`.

## Wydarzenia
W `iframe` zdarzenia działają podobnie jak w klasie `presence`.

```ts
iframe.on("UpdateData", async () => {
    // Kod idzie tutaj...
});
```

Oto lista wszystkich wydarzeń:

#### `UpdateData`

To zdarzenie jest uruchamiane za każdym razem, gdy element iframe jest aktualizowany.
