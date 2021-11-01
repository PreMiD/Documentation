---
title: Clase de iFrame
description:
published: true
date: 2021-09-18T14:31:12.831Z
tags:
editor: markdown
dateCreated: 2021-09-07T01:44:57.665Z
---

# Clase de iFrame

## Introducción

En algunos argumentos, tu presence puede necesitar acceder a elementos dentro de `iframes`.

El código que escribes dentro de tu archivo `iframe.ts` se inyecta en cada iframe de la página.

Al igual que las presences, `iframes` tienen sus propias clases diseñadas para actualizar automáticamente los datos.

```typescript
iframe.on("UpdateData", async () => {
    //El código va aquí...
});
```

## Métodos

### `send(Object)`
Envía datos a la presence. Usar este método hará que la presence arroje un evento de `iFrameData`.

### `getUrl()`
Devuelve la URL del `iframe`.

## Eventos
En `iframes`, los eventos funcionan de forma similar a como funcionan en la clase `presence`.

```typescript
iframe.on("UpdateData", async () => {
    //El código va aquí...
});
```

Aquí hay una lista de todos los eventos:

#### `UpdateData`

Este evento se activa cada vez que se actualiza el iframe.
