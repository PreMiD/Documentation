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
Изпраща данни до presence. Using this method will make the presence throw a `iFrameData` event.

### `getUrl()`
Returns the URL of the `iframe`.

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
