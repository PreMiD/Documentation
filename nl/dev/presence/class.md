---
title: Presence Klasse
description: De belangrijkste klasse voor elke PreMiD presence
published: true
date: 2021-05-23T09:14:06.963Z
tags:
editor: markdown
dateCreated: 2021-02-21T21:13:14.449Z
---

# Presence Klasse

## Introductie

De `Presence` klasse is erg handig omdat deze over basismethoden beschikt die we nodig hebben om presence te creëren.

Wanneer u een klasse aanmaakt, dient u de eigenschap `clientId` te specificeren.

```typescript
const presence = new presence({
  clientId: "514271496134389561" // Voorbeeld clientId
});
```

### Eigenschappen

Er zijn drie eigenschappen beschikbaar voor de `Presence` klasse.

#### `clientId`

Deze eigenschap is vereist om je presence te laten werken, omdat je client-id gebruikt word om het logo en de assets te weergeven. Je kunt het op je [applicatiepagina](https://discordapp.com/developers/applications) krijgen.

#### `injectOnComplete` - *verouderd sinds 2.2.4*

Wanneer je `injectOnComplete` op `true` zet dan wordt de eerste `UpdateData` evenement voor de `presence.ts` en `iframe.ts` bestanden pas afgevuurd als de pagina volledig geladen is.

#### `appMode` - *verouderd sinds 2.2.4*

Wanneer je `appMode` op `true` zet en de presence zou een lege `PresenceData` versturen, dan toont de app de applicatie (afbeelding en naam) op het profiel van de gebruiker in plaats van niets.

## Methodes

### `getActivity()`

Geeft als resultaat een `PresenceData` object van wat de presence die wordt weergegeven.

### `setActivity(PresenceData | Slideshow, Boolean)`

Stelt je profielactiviteit in volgens de verstrekte gegevens.

De eerste parameter vereist een [`PresenceData`](#presencedata-interface) interface of een [`Slideshow`](/dev/presence/slideshow) klasse om alle informatie te krijgen die je wilt weergeven in je profiel.

Tweede parameter definieert wanneer presence iets afspeelt of niet. Gebruik altijd `true` als u timestamps verstrekt in `PresenceData`.

### `clearActivity()`

Wist je huidige activiteit en de tray titel.

### `setTrayTitle(String)`

> Deze methode werkt alleen op Mac OS. 
> 
> {.is-warning}

Stelt de systeemtitel in op de menubalk.

### `createSlideshow()`

Maakt een nieuwe `Slideshow` klasse aan.

```typescript
const slideshow = presence.createSlideshow();
```

Dit wordt aanbevolen om gelijk te doen wanneer je de `Presence` klasse maakt:

```typescript
const presence = new presence({
    clientId: "514271496134389561" // Voorbeeld clientId
  }),
  slideshow = presence.createSlideshow();
```

Je kunt de documentatie voor de `Slideshow` klasse [hier](/dev/presence/slideshow) vinden.

### `getStrings(Object)`

Een asynrone methode waarmee u vertaalde strings uit de extensie kunt krijgen.

Je moet `Object` opgeven met sleutels die de sleutel voor teksten zijn, `keyValue` is de waarde van de tekst. Op dit eindpunt kan een lijst van vertaalde tekenreeksen worden gevonden: `https://api.premid.app/v2/langFile/presence/nl/`

```typescript
// Retourneert `Playing` en `Paused` strings
// uit extensie.
const strings = await presence.getStrings({
  play: "general.playing",
  pause: "general.paused"
});

const playString = strings.play; // Geeft: Playing
const pauseString = strings.pause; // Geeft: Paused
```

Sinds v2.2.0 van de extensie kunt u nu de strings van een bepaalde taal krijgen. Dit werkt goed met de nieuw toegevoegde `multiLanguage` instelling optie.

We raden je aan om de volgende code te gebruiken, zodat de presenceData automatisch wordt bijgewerkt als als de gebruiker de geselecteerde taal verandert;

```typescript
// Een interface van de strings die u krijgt (goed voor code kwaliteit en autocomplete).
interface LangStrings {
  play: string;
  pause: string;
}

async function getStrings(): Promise<LangStrings> {
  return presence.getStrings(
    {
      // De strings die je krijgt, zorg ervoor dat dit past bij je LangStrings interface.
      play: "general.playing",
      pause: "general.paused"
    },
    // De ID is de ID van de multiLanguage instelling.
    await presence.getSetting("ID").catch(() => "en");
  );
}

let strings: Promise<LangStrings> = getStrings(),
  // De ID is de ID van de multiLanguage instelling.
  oldLang: string = await presence.getSetting("ID").catch(() => "en");

//! De volgende code moet binnen het updateData evenement!
// De ID is de ID van de multiLanguage instelling.
const newLang = await presence.getSetting("ID").catch(() => "en");
if (oldLang !== newLang) {
  oldLang = newLang;
  strings = getStrings();
}

const playString = (await strings).play, // Geeft: Playing
  pauseString = (await strings).pause; // Geeft: Paused
```

### `getPageletiable(String)`

Retourneert een variabele van de website als deze bestaat.

**Waarschuwing: Deze functie kan hoog CPU-verbruik & website-haperingen veroorzaken wanneer deze te vaak is uitgevoerd.**

```typescript
const pageVar = presence.getPageletiable("pageVar");
console.log(pageVar); // This will log the "Variable content"
```

### `getExtensionVersion(Boolean)`

Returns version of the extension the user is using.

```typescript
getExtensionVersion(onlyNumeric?: boolean): string | number;

const numeric = presence.getExtensionVersion();
console.log(numeric); // Geeft terug: 210
const version = presence.getExtensionVersion(false);
console.log(version); // Geeft terug: 2.1.0
```

### `getSetting(String)`

Retourneert de waarde van de instelling.

```typescript
const setting = await presence.getSetting("pdexID"); // Vervang pdexID met de id van de instelling
console.log(setting); // Dit zal de waarde van de instelling loggen
```

### `hideSetting(String)`

Verbergt de gegeven instelling.

```typescript
presence.hideSetting("pdexID"); // vervang pdexID met het id van de instelling
```

### `showSetting(String)`

Shows given setting (Only works if the setting was already hidden).

```typescript
presence.showSetting("pdexID"); // vervang pdexID met het id van de instelling
```

### `getLogs()`

Returns the logs of the websites console.

```typescript
const logs = await presence.getLogs();
console.log(logs); // Dit zal de laatste 100 logs loggen (in een array).
```

**Note:** Requires `readLogs` to be `true` in the `metadata.json` file.

### `info(String)`

Prints the given message in the console in a format based of the presence in the `info` style.

```typescript
presence.info("Test") // Dit zal "test" in de juiste stijl loggen.
```

### `success(String)`

Prints the given message in the console in a format based of the presence in the `success` style.

```typescript
presence.success("Test") // Dit zal "test" in de juiste styling loggen.
```

### `error(String)`

Prints the given message in the console in a format based of the presence in the `error` style.

```typescript
presence.error("Test") // Dit zal "test" in de juiste stijl loggen.
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

## `PresenceData` Interface

The `PresenceData` interface is recommended to use when you are using the `setActivity()` method.

This interface has following variables, all of them are optional.

<table>
  <thead>
    <tr>
      <th style="text-align:left">Variabele</th>
      <th style="text-align:left">Beschrijving</th>
      <th style="text-align:left">Type</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">details</td>
      <td style="text-align:left">De eerste regel in je presence, meestal gebruikt als header.</td>
      <td style="text-align:left"><code>String</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">state</td>
      <td style="text-align:left">Tweede regel in je presence.</td>
      <td style="text-align:left"><code>String</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">startTimestamp</td>
      <td style="text-align:left">Definieert de huidige tijd.<br>
        Wordt gebruikt als je wilt weergeven hoeveel <code>uur:minuten:seconden</code> er over is.
          <br>Je moet je tijd omzetten in <code>timestamp</code> anders krijg je een verkeerde
          aftelling.
      </td>
      <td style="text-align:left"><code>Number</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">endTimestamp</td>
      <td style="text-align:left">Definieert de volledige duur.
        <br>Gebruikt als je wilt laten zien hoeveel <code>uren:minuten:seconden</code> er over is.
          <br>Je moet je tijd omzetten in <code>timestamp</code> anders krijg je een verkeerde
          aftelling.
      </td>
      <td style="text-align:left"><code>Number</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">largeImageKey</td>
      <td style="text-align:left">Definieert het logo voor de presence.</td>
      <td style="text-align:left"><code>String</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">smallImageKey</td>
      <td style="text-align:left">Definieert het kleine pictogram naast presence&apos;s logo.</td>
      <td style="text-align:left"><code>String</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">smallImageText</td>
      <td style="text-align:left">Definieert de tekst die wordt getoond aan de gebruiker wanneer hij over de kleine
        pictogram beweegt.</td>
      <td style="text-align:left"><code>String</code>
      </td>
    </tr>
        <tr>
      <td style="text-align:left">buttons</td>
      <td style="text-align:left">Array van buttons, max. 2, label is de knoptekst, en url is de link.</td>
      <td style="text-align:left"><code>Array&lt;Object&gt;</code>
      </td>
    </tr>
  </tbody>
</table>

```typescript
const presenceData: presenceData = {
  details: "Mijn titel",
  state: "Mijn beschrijving",
  largeImageKey: "service_logo",
  smallImageKey: "small_service_icon",
  smallImageText: "Je hebt me bekeken, en wat nu?" ,
  startTimestamp: 1564444631188,
  endTimestamp: 1564444634734,
  buttons: [
    {
            label: "Testknop 1",
            url: "https://premid.app/"
        },
        {
            label: "Testknop 2",
            url: "https://premid.app/contributors"
        }
    ]
};
```

## Evenementen

Events allow you to detect and handle some changes or calls that were made. You can subscribe to events using the `on` method.

```typescript
presence.on("UpdateData", async () => {
  // Doe iets wanneer data wordt bijgewerkt.
});
```

There are few events available:

#### `UpdateData`

This event is fired every time the presence is being updated.

#### `iFrameData`

Fired when data is received from iFrame script.
