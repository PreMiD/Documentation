---
title: Clase de iFrame
description:
published: true
date: 2021-12-20T14:27:18.034Z
tags:
editor: markdown
dateCreated: 2021-09-07T01:44:57.665Z
---

# Clase de iFrame

## Introducción

En algunos argumentos, tu presence puede necesitar acceder a elementos dentro de `iframes`.

El código que escribes dentro de tu archivo `iframe.ts` se inyecta en cada iframe de la página.

Al igual que las presences, `iframes` tienen sus propias clases diseñadas para actualizar automáticamente los datos.

```ts
let iframe = new iFrame();

iframe.on("UpdateData", async () => {
    // Inserta aquí el código...
});
```

## Métodos

### `send(Object)`
Envía datos a la presence. Usar este método hará que la presence arroje un evento de `iFrameData`.

### `getUrl()`
Devuelve la URL del `iframe`.

## Eventos
En `iframes`, los eventos funcionan de forma similar a como funcionan en la clase `presence`.

```ts
iframe.on("UpdateData", async () => {
    // Inserta aquí el código...
});
```

Aquí hay una lista de todos los eventos:

#### `UpdateData`

Este evento se activa cada vez que se actualiza el iframe.
