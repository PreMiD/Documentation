---
title: Classe iFrame
description:
published: true
date: 2021-07-01T14:03:55.793Z
tags:
---

# Classe iFrame

## Introdução

Em alguns cenários, sua presence pode precisar acessar elementos dentro de `iframes`.

O código que você escreve dentro do seu arquivo `iframe.ts` é injetado em cada iframe na página.

Como as presences, os `iframes` têm suas próprias classes projetadas para atualizar dados automaticamente.

```typescript
let iframe = new iFrame();

iframe.on("UpdateData", async () => {
    // Seu código vai aqui...
});
```

## Métodos

### `send(Object)`
Envia dados para a presence. Usando este método a presence lançará um evento `iFrameData`.

### `getUrl()`
Retorna a URL do `iframe`.

## Eventos
Em `iframes`, os eventos funcionam da mesma forma que na `classe de presence`.

```typescript
iframe.on("UpdateData", async () => {
    // Seu código vai aqui...
});
```

Aqui está uma lista de todos os eventos:

#### `UpdateData`

Este evento é disparado toda vez que o iframe é atualizado.
