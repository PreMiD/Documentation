---
title: iFrame клас
description: 
published: true
date: 2021-09-18T14:44:52.424Z
tags: 
editor: markdown
dateCreated: 2021-09-07T02:00:46.278Z
---

# iFrame клас

## Вступ

В деяких сценаріях ваша присутність може мати доступ до елементів всередині `iframes`.

Код, який ви пишете всередині вашого `iframe.ts` файлу вставляється в кожен iframe на сторінці.

Як такі, `iframes` мають свої власні класи, розроблені для автоматичного оновлення даних.

```typescript
let iframe = new iFrame();

iframe.on("UpdateData", async () => {
    // Code goes here...
});
```

## Методи

### `send(Object)`
Надсилає дані присутності. Використання цього методу призведе до події `iFrameData`.

### `getUrl()`
Повертає URL для `iframe`.

## Події
В `iframes`події працюють аналогічно до плану `присутності`.

```typescript
iframe.on("UpdateData", async () => {
    // Code goes here...
});
```

Тут наведено список всіх подій:

#### `UpdateData`

Ця подія запускається щоразу, коли iframe оновлюється.
