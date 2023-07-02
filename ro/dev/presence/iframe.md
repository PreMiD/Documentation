---
title: Clasă iFrame
description:
published: true
date: 2021-12-20T14:27:18.034Z
tags:
editor: markdown
dateCreated: 2021-09-07T01:44:57.665Z
---

# Clasă iFrame

## Introducere

În unele scenarii, prezența ta ar putea avea nevoie să acceseze elemente din `iframes`.

Codul pe care îl scrieți în fișierul `iFrame.ts` este injectat în fiecare iframe de pe pagină.

Ca prezențele, `iframes` au propriile clase proiectate pentru a actualiza automat datele.

```ts
let iframe = new iFrame();

iFrame.on("UpdateData", async () => {
    // Cod merge aici...
});
```

## Metode

### `send(Object)`
Trimite date către prezență. Folosind această metodă va face ca prezența să arunce un eveniment `iFrameData`.

### `getUrl()`
Returnează adresa URL a `iframe`.

## Events
In `iframes`, events work similarly to the way they work in the `presence` class.

```ts
iframe.on("UpdateData", async () => {
    // Code goes here...
});
```

Here is a list of all of the events:

#### `UpdateData`

This event is fired every time the iframe is being updated.
