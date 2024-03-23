---
title: Класс iFrame
description:
published: true
date: 2021-12-20T14:27:18.034Z
tags:
editor: markdown
dateCreated: 2021-09-07T01:44:57.665Z
---

# Класс iFrame

## Введение

В некоторых сценариях вашему Presence может потребоваться доступ к элементам внутри `iframes`.

Код, который вы пишете внутри файла `iframe.ts` , вводится в каждый iframe на странице.

Как и Presence, `iframes` имеют свои собственные классы, предназначенные для автоматического обновления данных.

```ts
let iframe = new iFrame();

iframe.on("UpdateData", async () => {
    // Здесь начинается код...
});
```

## Методы

### `send(Object)`
Отправляет данные в Presence. Использование этого метода позволит Presence пробросить события `iFrameData`.

### `getUrl()`
Возвращает URL `iframe`.

## События
События в `iframes` работают аналогично тому, как они работают в классе `Presence`.

```ts
iframe.on("UpdateData", async () => {
    // Здесь начинается код...
});
```

Список всех событий:

#### `UpdateData`

Это событие запускается каждый раз, когда iframe обновляется.
