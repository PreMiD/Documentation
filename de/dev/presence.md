---
title: Presence-Entwicklung
description:
published: true
date: 2021-12-20T14:27:18.034Z
tags:
editor: markdown
dateCreated: 2020-06-11T18:04:02.843Z
---

> Alle Presences werden jetzt hier gespeichert: https://github.com/PreMiD/Presences 
> 
> {.is-info}

Version `2.x` führt den [Presence Store](https://premid.app/store) ein. Benutzer haben jetzt die Möglichkeit, ihre Lieblingspräsenzen manuell über die Benutzeroberfläche der [Website](https://premid.app/) hinzuzufügen und zu entfernen.

> Bevor du anfängst, solltest du dir unsere Presencerichtlinien anschauen. 
> 
> {.is-warning}

- [Richtlinien](https://docs.premid.app/dev/presence/guidelines)
{.links-list}

# Struktur

Alle Presences sind in [TypeScript](https://www.typescriptlang.org/) geschrieben. [TypeScript](https://www.typescriptlang.org/) enthält einige besonders strenge Typdefinitionen, sodass das Beheben und Erkennen von Fehlern viel einfacher ist.

## Bedingungen

1. [Git](https://git-scm.com/)
2. Installiere [Node](https://nodejs.org/en/) ([npm](https://www.npmjs.com/) integriert).

## Projekt klonen

1. Öffne ein Terminal und gib `git clone https://github.com/PreMiD/Presences` ein.
2. Wähle einen Ordner Deiner Wahl.
3. Öffne es in Deinem Code-Editor.

## Ordner und Dateien erstellen

1. Gehe in den `Webseiten` Ordner und dann in den Ordner mit dem ersten Buchstaben des **name** (keine URL) des Dienstes, den du unterstützen willst.
2. Erstelle einen Ordner mit dem **Namen** (keine URL) des Dienstes, den Du unterstützen möchtest.

### Eine Presence erstellen
1. Führe `npx pmd` aus (oder führe `pmd` über den Package Manager deiner Wahl aus)
2. Wähle die erste Option
3. Fülle alle Fragen aus

### Kompilieren / Ändern eines Presence
1. Führe `npx pmd` aus
2. Wähle die zweite Option aus
3. Gebe den Presence Namen ein, den du bearbeiten möchtest > Dadurch wird ein TypeScript-Compiler im Ordner dieser Präsenz gestartet, wenn du nun die `presence.ts` datei bearbeitests wird das presence automatisch für dich kompiliert.
{.is-info}

For inspiration or examples on how to structure your Presence's code, take a look at existing Presences like 1337x or 9GAG

For more information about the `Presence` class click [here](/dev/presence/class).

Seit v2.2.0 gibt es Slideshows, die es dir erlauben mehrere `PresenceData`-Schnittstellen in einem Intervall anzuzeigen, für mehr Information über die `Slideshow`-Klasse, klicke [hier](/dev/presence/slideshow).

## Du kannst bestimmte Daten nicht abrufen?!

A lot of websites are using [iframes](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe) ([Inlineframes](https://en.wikipedia.org/wiki/HTML_element#Frames)). These html tags can contain multiple sources such as videos. But they're not relevant every time. Einige sind versteckt oder werden nicht aktiv genutzt. Prüfe, ob du die Informationen die du wirklich brauchst extrahieren kannst, bevor du dir unnötige Arbeit machst.

1. Check for them in your browsers console (be sure that you are on the **Elements** tab).
2. Suche (<kbd>Strg</kbd>+<kbd>F</kbd> (Windows) oder <kbd>CMD</kbd>+<kbd>F</kbd> (MacOS)).
3. Führe `document.querySelectorAll("iframe")` aus.

Wenn du feststellst, dass deine Daten in einem iFrame sind, musst du folgende Schritte ausführen:

1. Erstelle eine `iframe.ts`-Datei.
2. Set iFrame to `true` in your metadata file.
3. Fülle deine iFrame-Datei aus.

```ts
const iframe = new iFrame();
iframe.on("UpdateData", async () => {
  //Get all the data you need out of the iFrame save them in variables and then send them using iframe.send
  iframe.send({
    //sending data
    video: video,
    time: video.duration
  });
});
```

4. Ermögliche deiner Presence-Datei, Daten aus deiner iFrame-Datei zu empfangen.

```ts
presence.on("iFrameData", (data) => {
  iFrameVideo = data.video;
  currentTime = data.time;
});
```

**Hinweis:** Dies muss außerhalb des updateData-Events platziert werden.

# Presence laden

1. Öffne das Erweiterungs-Popup im Browser und halte die <kbd>Umschalt</kbd>-Taste auf deiner Tastatur gedrückt.
2. **Presence laden** wird im Presence Bereich erscheinen.
3. Klicke darauf, während du die Taste <kbd>Shift</kbd> weiterhin gedrückt hälst.
4. Wähle den /dist Ordner deines Presence.

# Einige hilfreiche Dinge

## Neuladen

Die Website, auf der Sie entwickeln, wird jedes Mal automatisch neu geladen, wenn Sie eine Datei in Ihrem Ordner speichern.

## Debugging

- Du kannst `console.log("Test");` zwischen deinen Code setzten und prüfen, ob deine Konsole den Output liefert. Wenn ja, fahre fort und versuche es in der nächsten Funktion erneut. Wenn nicht, liegt oben ein Fehler vor.
- Sollte das nicht helfen, kannst du einen Presence-Entwickler auf unserem [Discord Server](https://discord.premid.app/) um Hilfe fragen.

# Dateien erklärt

- [Presence-Klasse](/dev/presence/class)
- [Slideshow Klasse](/dev/presence/slideshow)
- [iFrame-Klasse](/dev/presence/iframe)
- [Metadatein](/dev/presence/metadata)
- [TypeScript-Konfiguration](/dev/presence/tsconfig ""){.links-list}
