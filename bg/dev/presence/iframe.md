---
title: iFrame клас
description:
published: true
date: 2021-12-20T14:27:18.034Z
tags:
editor: markdown
dateCreated: 2021-09-07T01:44:57.665Z
---

# iFrame клас

## Въведение

В някои случаи може да се наложи вашия presence да получи достъп до елементи в `iframes`.

Кодът, който сте написали във вашия файл `iframe.ts`, се инжектира във всеки iframe на страницата.

Подобно на presence, `iframes` имат свои собствени класове, предназначени за автоматично актуализиране на данните.

```ts
let iframe = new iFrame();

iframe.on("UpdateData", async () => {
    // Кодът идва тук...
});
```

## Методи

### `send(Object)`
Изпраща данни до presence. Използването на този метод ще накара вашия presence да излъчи `iFrameData` event.

### `getUrl()`
Връща URL адреса на `iframe`.

## Евенти
В `iframes`, евентите работят подобно на начина, по който работят в `Presence` класа.

```ts
iframe.on("UpdateData", async () => {
    // Кодът идва тук...
});
```

Ето списък на всички евенти:

#### `UpdateData`

Този евент се задейства всеки път, когато се актуализира iframe.
