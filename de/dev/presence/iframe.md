---
title: iFrame-Klasse
description:
published: true
date: 2021-09-18T14:31:12.831Z
tags:
editor: markdown
dateCreated: 2021-09-07T01:44:57.665Z
---

# iFrame Class

## Einführung

In einigen Szenarien muss deine Presence möglicherweise auf Elemente innerhalb von `iframes` zugreifen.

Der Code, den du in deine Datei `iframe.ts` schreibst, wird in jeden iframe auf der Seite eingefügt.

Wie bei Presences haben `iframes` ihre eigenen Klassen, um Daten automatisch zu aktualisieren.

```typescript
let iframe = new iFrame();

iframe.on("UpdateData", async () => {
    // Hier gehört der Code rein...
});
```

## Methoden

### `send(Object)`
Sendet Daten an die Presence. Bei Verwendung dieser Methode löst die Presence ein `iFrameData`-Event aus.

### `getUrl()`
Gibt die URL des `iframe` aus.

## Events
In `iframes` funktionieren Events ähnlich wie in der Klasse `Presence`.

```typescript
iframe.on("UpdateData", async () => {
    // Hier gehört der Code rein...
});
```

Hier ist eine Liste aller Events:

#### `UpdateData`

Dieses Event wird jedes Mal ausgelöst, wenn der iframe aktualisiert wird.
