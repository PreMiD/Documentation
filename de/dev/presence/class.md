---
title: Presence-Klasse
description: Die Hauptklasse für jede PreMiD-Presence
published: true
date: 2021-05-23T09:14:06.963Z
tags:
editor: markdown
dateCreated: 2021-02-21T21:13:14.449Z
---

# Presence-Klasse

## Introduction

Die Klasse `Presence` ist sehr nützlich, da sie grundlegende Methoden zum Erstellen einer Presence enthält.

Wenn du eine Klasse erstellst, musst du die Eigenschaft `clientId` angeben.

```typescript
const presence = new Presence({
  clientId: "514271496134389561" // Beispiel clientid
});
```

### Eigenschaften

Für die `Presence`-Klasse, gibt es drei verfügbare Eigenschaften.

#### `clientId`

Diese Eigenschaft wird benötigt, damit deine Presence funktioniert, weil es die Anwendungs-Id benutzt, um Logo und Elemente anzuzeigen. Du bekommst dies auf deiner[Anwendungsseite](https://discordapp.com/developers/applications).

#### `injectOnComplete` - *Deprecated since 2.2.4*

Beim setzen von `InjectOnComplete` zu `true`, wird das erste `UpdateData` Event für beide, die `presence.ts` und `iframe.js` Dateien erst gestartet, wenn die Seite fertig geladen ist.

#### `appMode` - *Deprecated since 2.2.4*

Beim setzen von `appMode` zu `true` und die Presence sollte leere `PresenceData` senden, zeigt die App die Anwendung (Bild und Name) auf dem Benutzerprofil, anstatt nichts.

## Methoden

### `getActivity()`

Wirft ein `PresendeData` Objekt zurück, was die Presence anzeigt.

### `setActivity(PresenceData | Slideshow, Boolean)`

Legt Ihre Profilaktivität gemäß den bereitgestellten Daten fest.

Der erste Parameter benötig eine [`PresenceData`](#presencedata-interface) Schnittstelle oder eine [`Slideshow`](/dev/presence/slideshow) Klasse um alle Informationen zu erhalten, die Sie in Ihrem Profil anzeigen möchten.

Der zweite Parameter definiert, wann Presence etwas spielt oder nicht. Verwende immer `true`, wenn Sie einen Zeitstempel in `PresenceData` verwenden.

### `clearActivity()`

Löscht deine akutelle Aktivität und den Tray-Titel.

### `setTrayTitle(String)`

> Diese Methode funktioniert nur unter Mac OS. 
> 
> {.is-warning}

Legt den Tray-Titel in der Menüleiste fest.

### `createSlideshow()`

Erstellt eine neue `Slideshow` Klasse.

```typescript
const slideshow = presence.createSlideshow();
```

Es wird empfohlen, dies direkt nach dem erstellen der `Presence` Klasse zu tun:

```typescript
const presence = new Presence({
    clientId: "514271496134389561" // Beispiel clientId
  }),
  slideshow = presence.createSlideshow();
```

Die Dokumentation für die `Slideshow` Klasse kannst du [hier](/dev/presence/slideshow) finden.

### `getStrings(Object)`

Eine asynchrone Methode, mit der du übersetzte Zeichenketten von der Erweiterung erhalten kannst.

Sie müssen ` Object ` mit Schlüsseln versehen, die der Schlüssel für die Zeichenfolge sind. ` keyValue ` ist der Zeichenfolgenwert. Eine Zusammenstellung der übersetzten Zeichenketten kann mit diesem Endpunkt gefunden werden: `https://api.premid.app/v2/langFile/presence/en/`

```typescript
// Gibt `Playing` und `Paused` Strings
// der Erweiterung wieder.
const strings = await presence.getStrings({
  play: "general.playing",
  pause: "general.paused"
});

const playString = strings.play; // Ergebnis:  Playing
const pauseString = strings.pause; // Ergebnis: Paused
```

Seit v2.2.0 der Erweiterung können Sie nun die Zeichenketten einer bestimmten Sprache erhalten. Dies funktioniert gut mit der neu hinzugefügten `multiLanguage` Einstellung.

Wir empfehlen Ihnen, den folgenden Code zu verwenden, damit die PresenceData automatisch aktualisiert, wenn der Benutzer die ausgewählte Sprache ändert;

```typescript
// Eine Schnittstelle der Zeichenketten, die Sie erhalten (gut für Code-Qualität und Autovervollständigung).
interface LangStrings {
  play: string;
  pause: string;
}

async function getStrings(): Promise<LangStrings> {
  return presence.getStrings(
    {
      // Die Zeichenketten, die du erhältst, stellen sicher, dass diese zu Ihrer LangStrings Schnittstelle passen.
      play: "general.playing",
      pause: "general.paused"
    },
    // Die ID ist die ID der multiLanguage Einstellung.
    await presence.getSetting("ID")
  );
}

let strings: Promise<LangStrings> = getStrings(),
  // Die ID ist die ID der multiLanguage Einstellung.
  oldLang: string = await presence.getSetting("ID").catch(() => "en");

//! Der folgende Code muss innerhalb des updateData Events sein!
// Die ID ist die ID von der multiLanguage Einstellung.
const newLang = await presence.getSetting("ID").catch(() => "en");
if (oldLang !== newLang) {
  oldLang = newLang;
  strings = getStrings();
}

const playString = (await strings).play, // result: Playing
  pauseString = (await strings).pause; // result: Paused
```

### `getPageletiable(String)`

Gibt eine Variable von der Webseite zurück, falls sie vorhanden ist.

**Warning: This function can cause high CPU usage & site lagging when it has been executed too many times.**

```typescript
const pageVar = presence.getPageletiable("pageVar");
console.log(pageVar); // This will log the "Variable content"
```

### `getExtensionVersion(Boolean)`

Returns version of the extension the user is using.

```typescript
getExtensionVersion(onlyNumeric?: boolean): string | number;

const numeric = presence.getExtensionVersion();
console.log(numeric); // Wird 210 loggen
const version = presence.getExtensionVersion(false);
console.log(version); // Wird 2.1.0 loggen
```

### `getSetting(String)`

Returns value of setting.

```typescript
var setting = await presence.getSetting("pdexID"); // pdexID mit der Id von der Einstellung ersetzen
console.log(setting); // Dies loggt den Wert der Einstellung
```

### `hideSetting(String)`

Hides given setting.

```typescript
presence.hideSetting("pdexID"); // Ersetze pdexID mit der ID der Einstellung
```

### `showSetting(String)`

Shows given setting (Only works if the setting was already hidden).

```typescript
presence.showSetting("pdexID"); // Ersetze pdexID mit der id der Einstellung
```

### `getLogs()`

Returns the logs of the websites console.

```typescript
const logs = await presence.getLogs();
console.log(logs); // Dies logt die neusten 100 Logs (in einem Array).
```

**Note:** Requires `readLogs` to be `true` in the `metadata.json` file.

### `info(String)`

Prints the given message in the console in a format based of the presence in the `info` style.

```typescript
presence.info("Test") // Dies loggt "test" im korrekten Stil.
```

### `success(String)`

Prints the given message in the console in a format based of the presence in the `success` style.

```typescript
presence.success("Test") // Dies loggt "test" im korrekten Stil.
```

### `error(String)`

Prints the given message in the console in a format based of the presence in the `error` style.

```typescript
presence.error("Test") // Dies loggt "test" im korrekten Stil.
```

### `getTimestampsfromMedia(HTMLMediaElement)`

Returns 2 `snowflake` timestamps in an `Array` that can be used for `startTimestamp` and `endTimestamp`.

```typescript
const timestamps = presence.getTimestampsfromMedia(document.querySelector(".video"));
presenceData.startTimestamp = timestamps[0];
presenceData.endTimestamp = timestamps[1];
```

**Note:** The given `String` in querySelector is an example.

### `getTimestamps(Number, Number)`

Returns 2 `snowflake` timestamps in an `Array` that can be used for `startTimestamp` and `endTimestamp`.

```typescript
const video = document.querySelector(".video"),
  timestamps = presence.getTimestamps(video.currentTime, video.duration);
presenceData.startTimestamp = timestamps[0];
presenceData.endTimestamp = timestamps[1];
```

**Note:** The given `String` in querySelector is an example.

### `timestampFromFormat(String)`

Converts a string with format `HH:MM:SS` or `MM:SS` or `SS` into an integer (Does not return snowflake timestamp).

```typescript
const currentTime = presence.timestampFromFormat(document.querySelector(".video-now").textContent),
  duration = presence.timestampFromFormat(document.querySelector(".video-end").textContent),
  timestamps = presence.getTimestamps(currentTime, duration);
presenceData.startTimestamp = timestamps[0];
presenceData.endTimestamp = timestamps[1];
```

**Note:** The given `String` in querySelector is an example.

## `PresenceData`-Schnittstelle

The `PresenceData` interface is recommended to use when you are using the `setActivity()` method.

This interface has following variables, all of them are optional.

<table>
  <thead>
    <tr>
      <th style="text-align:left">Variable</th>
      <th style="text-align:left">Beschreibung</th>
      <th style="text-align:left">Type</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">details</td>
      <td style="text-align:left">Die erste Zeile in deiner Presence, die normalerweise als Überschrift verwendet wird.</td>
      <td style="text-align:left"><code>String</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">state</td>
      <td style="text-align:left">Zweite Zeile in deiner Presence.</td>
      <td style="text-align:left"><code>String</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">startTimestamp</td>
      <td style="text-align:left">Legt die aktuelle Uhrzeit fest.<br>
        Wird verwendet, wenn du anzeigen möchtest, wie viel <code>Stunden: Minuten: Sekunden</code> übrig sind.
          <br>Du musst deine Zeit in <code>Zeitstempel</code> umwandeln, sonst erhälst du einen falschen Countdown.
      </td>
      <td style="text-align:left"><code>Number</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">endTimestamp</td>
      <td style="text-align:left">Definiert die volle Dauer.
        <br>Wird verwendet, wenn du anzeigen möchtest, wie viel <code>Stunden: Minuten: Sekunden</code> übrig sind.
          <br>Du musst deine Zeit in einen <code>Zeitstempel</code> konvertieren, sonst erhältst du einen falschen Countdown.
      </td>
      <td style="text-align:left"><code>Number</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">largeImageKey</td>
      <td style="text-align:left">Definiert das Logo für die Presence.</td>
      <td style="text-align:left"><code>String</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">smallImageKey</td>
      <td style="text-align:left">Definiert das kleine Symbol neben dem Logo der Anwesenheit&apos;.</td>
      <td style="text-align:left"><code>String</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">smallImageText</td>
      <td style="text-align:left">Definiert den Text, der dem Benutzer angezeigt wird, wenn er mit der Maus über das kleine
        Symbol fährt.</td>
      <td style="text-align:left"><code>String</code>
      </td>
    </tr>
        <tr>
      <td style="text-align:left">buttons</td>
      <td style="text-align:left">Array von Schaltflächen, max. 2, label ist der Schaltflächentext, und url ist der Link.</td>
      <td style="text-align:left"><code>Array&lt;Object&gt;</code>
      </td>
    </tr>
  </tbody>
</table>

```typescript
const presenceData: PresenceData = {
  Details: "Mein Titel",
  state: "Meine Beschreibung",
  largeImageKey: "service_logo",
  smallImageKey: "small_service_icon",
  smallImageText: "Du schwebst über mir und was jetzt?" ,
  StartTimestamp: 1564444631188,
  endTimestamp: 1564444634734
};
```

## Events

Events allow you to detect and handle some changes or calls that were made. You can subscribe to events using the `on` method.

```typescript
presence.on("UpdateData", async () => {
  // Tut etwas, wenn Daten aktualisiert werden.
});
```

There are few events available:

#### `UpdateData`

This event is fired every time the presence is being updated.

#### `iFrameData`

Fired when data is received from iFrame script.
