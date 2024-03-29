---
title: Classe iFrame
description:
published: true
date: 2021-12-20T14:27:18.034Z
tags:
editor: markdown
dateCreated: 2021-09-07T01:44:57.665Z
---

# Classe iFrame

## Introduction

Dans certains scénarios, votre présence peut avoir besoin d'accéder à des éléments à l'intérieur des `iframes`.

Le code que tu écris dans ton fichier `iframe.ts` est injecté dans chaque iframe de la page.

Tout comme les présences, `iframes` ont leurs propres classes conçues pour mettre à jour automatiquement les données.

```ts
let iframe = new iFrame();

iframe.on("UpdateData", async () => {
    // Le code va ici...
});
```

## Méthodes

### `send(Object)`
Envoie des données à la présence. L'utilisation de cette méthode fera que la présence lancera un événement `iFrameData`.

### `getUrl()`
Retourne l'URL de l' `iframe`.

## Évènements
En `iframes`, les événements fonctionnent de la même façon que la classe `présence`.

```ts
iframe.on("UpdateData", async () => {
    // Le code va ici...
});
```

Voici une liste de tous les événements :

#### `UpdateData`

Cet événement est déclenché chaque fois que l'iframe est mis à jour.
