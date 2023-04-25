---
title: Klasa Presence
description: Główna klasa dla każdego PreMiD presence
published: true
date: 2022-05-26T18:03:00.000Z
tags:
editor: markdown
dateCreated: 2021-09-07T01:44:50.164Z
---

# Klasa Presence

## Wprowadzenie

Klasa `Presence` jest bardzo przydatna, ponieważ posiada podstawowe metody, które są nam potrzebne do tworzenia presence.

Podczas tworzenia klasy musisz określić właściwość `ID klienta`.

```ts
const presence = new Presence({
  clientId: "514271496134389561" // Przykładowy id klienta
});
```

### Właściwości

Istnieją trzy właściwości dla klasy `Presence`.

#### `clientId`

Ta właściwość jest wymagana, aby twój status presence zadziałał, ponieważ używa identyfikatora aplikacji do wyświetlania logo i zasobów. Możesz ją zdobyć na [stronie aplikacji](https://discordapp.com/developers/applications).

#### `injectOnComplete` - *Przestarzały od wersji 2.2.4*

Gdy `injectOnComplete` ustawione na `true` pierwsze wydarzenie `UpdateData` dla `presence.ts` i `iframe.ts` obydwa pliki zostaną uruchomione dopiero po pełnym załadowaniu strony.

#### `appMode` - *Przestarzały od wersji 2.2.4*

Gdy `appMode` ustawione na `true` i pustym statusie `PresenceData`, program będzie wyświetlał aplikację (zdjęcie i nazwę) na profilu użytkownika zamiast niczego.

## Metody

### `getActivity()` - *Przestarzały od 2.2.4*

Zwraca obiekt `PresenceData` o tym, co jest wyświetlane.

### `setActivity(PresenceData | Slideshow, Boolean)`

Ustawia aktywność profilu zgodnie z podanymi danymi.

Pierwszy parametr wymaga interfejsu [`PresenceData`](#presencedata-interface) lub klasy [`Slideshow`](/dev/presence/slideshow) w celu uzyskania wszystkich informacji, które chcesz umieścić w twoim profilu.

Drugi parametr określa, kiedy status jest aktywny lub nie. Zawsze używaj `true` jeśli podasz znaczniki czasu w `presenceData`.

### `clearActivity()`

Czyści obecną aktywność i tytuł zasobnika.

### `setTrayTitle(String)` - *Przestarzały od 2.2.3*

> Ta metoda działa tylko na Mac OS. 
> 
> {.is-warning}

Ustawia tytuł zasobnika na pasku menu.

### `createSlideshow()`

Tworzy nową klasę `Slideshow`.

```ts
const slideshow = presence.createSlideshow();
```

Zalecane jest zrobienie tego po utworzeniu klasy `Presence`:

```ts
const presence = new Presence({
    clientId: "514271496134389561" // Przykładowy ID klienta
  }),
  slideshow = presence.createSlideshow();
```

You can find the documentation for the `Slideshow` class [here](/dev/presence/slideshow).

### `getStrings(Object)`

Metoda asynchroniczna, która pozwala na otrzymywanie przetłumaczonych ciągów z rozszerzenia.

Musisz podać `Obiekt` z kluczami dla ciągu znaków, `keyValue` jest wartością ciągu znaków. Kompilację przetłumaczonych ciągów można znaleźć za pomocą tego punktu końcowego: `https://api.premid.app/v2/langFile/presence/pl`

```ts
// Zwraca ciągi znaków `Playing` i `Paused`
// z rozszerzenia.
const strings = await presence.getStrings({
  play: "general.playing",
  pause: "general.paused"
});

const playString = strings.play; // result: Gra
const pauseString = strings.pause; // result: Wstrzymane
```

Od v2.2.0 rozszerzenia możesz teraz pobierać ciągi w określonym języku. Działa to dobrze z nowo dodaną opcją ustawienia `multiLanguage`.

Sugerujemy użycie następującego kodu, aby automatycznie aktualizował PresenceData, jeśli użytkownik zmieni wybrany język;

```ts
async function getStrings() {
  return presence.getStrings(
    {
      play: "general.playing",
      pause: "general.paused"
    },
    // Identyfikator to identyfikator ustawienia wielojęzykowego.
    await presence.getSetting("ID").catch(() => "en");
  );
}

let strings = getStrings(),
  // Identyfikator to identyfikator ustawienia wielojęzykowego.
  oldLang: string = await presence.getSetting("ID").catch(() => "en");

//! Poniższy kod musi znajdować się w wydarzeniu updateData!
// The ID is the ID of the multiLanguage setting.
oldLang: string = await presence.getSetting("ID");

//!
```

### `getPageletiable(String)`

Zwraca zmienną ze strony internetowej, jeśli istnieje.

**Ostrzeżenie: Ta funkcja może spowodować wysokie zużycie procesora & opóźnienie strony, gdy została wykonana zbyt wiele razy.**

```ts
const pageVar = presence.getPageletiable("pageVar");
console.log(pageVar); // To zarejesttuje „Zmienną treść”
```

### `getExtensionVersion(Boolean)`

Zwraca wartość ustawienia.

```ts
getExtensionVersion(onlyNumeric?: boolean): string | number;

const numeric = presence.getExtensionVersion();
console.log(numeric); // Zarejestruje 210
const version = presence.getExtensionVersion(false);
console.log(version); // Zarejestruje 2.1.0
```

### `getSetting(String)`

Ukrywa podane ustawienie.

```ts
const setting = await presence.getSetting("pdexID"); // Zamień pdexID z Id ustawienia
console.log(setting); // To zapisze log wartości ustawienia
```

### `hideSetting(String)`

Pokazuje podane ustawienie (działa tylko, jeśli ustawienie było już ukryte).

```ts
presence.hideSetting("pdexID"); // Zamień pdexID na id, które jest w ustawieniach
```

### `showSetting(String)`

Zwraca logi konsoli witryny.

```ts
presence.showSetting("pdexID"); // Replace pdexID with the id of the setting
```

### `getLogs()`

Returns the logs of the websites console.

```ts
const logs = await presence.getLogs();
console.log(logs); // This will log the latest 100 logs (in an array).
```

**Note:** Requires `readLogs` to be `true` in the `metadata.json` file.

### `info(String)`

Prints the given message in the console in a format based of the presence in the `info` style.

```ts
presence.info("Test") // This will log "test" in the correct styling.
```

### `success(String)`

Prints the given message in the console in a format based of the presence in the `success` style.

```ts
presence.success("Test") // This will log "test" in the correct styling.
```

### `error(String)`

Prints the given message in the console in a format based of the presence in the `error` style.

```ts
presence.error("Test") // This will log "test" in the correct styling.
```

### `getTimestampsfromMedia(HTMLMediaElement)`

Returns 2 `snowflake` timestamps in an `Array` that can be used for `startTimestamp` and `endTimestamp`.

```ts
const timestamps = presence.getTimestampsfromMedia(document.querySelector(".video"));
presenceData.startTimestamp = timestamps[0];
presenceData.endTimestamp = timestamps[1];
```

**Note:** The given `String` in querySelector is an example.

### `getTimestamps(Number, Number)`

Returns 2 `snowflake` timestamps in an `Array` that can be used for `startTimestamp` and `endTimestamp`.

```ts
const video = document.querySelector(".video"),
  timestamps = presence.getTimestamps(video.currentTime, video.duration);
presenceData.startTimestamp = timestamps[0];
presenceData.endTimestamp = timestamps[1];
```

**Note:** The given `String` in querySelector is an example.

### `timestampFromFormat(String)`

Converts a string with format `HH:MM:SS` or `MM:SS` or `SS` into an integer (Does not return snowflake timestamp).

```ts
const currentTime = presence.timestampFromFormat(document.querySelector(".video-now").textContent),
  duration = presence.timestampFromFormat(document.querySelector(".video-end").textContent),
  timestamps = presence.getTimestamps(currentTime, duration);
presenceData.startTimestamp = timestamps[0];
presenceData.endTimestamp = timestamps[1];
```

**Note:** The given `String` in querySelector is an example.

## Interfejs `presenceData`

Ten interfejs posiada następujące zmienne, wszystkie są opcjonalne.

This interface has following variables, all of them are optional.

<table>
  <thead>
    <tr>
      <th style="text-align:left">Variable</th>
      <th style="text-align:left">Opis</th>
      <th style="text-align:left">Typ</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">details</td>
      <td style="text-align:left">The first line in your presence, usually used as header.</td>
      <td style="text-align:left"><code>String</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">state</td>
      <td style="text-align:left">Second line in your presence.</td>
      <td style="text-align:left"><code>String</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">startTimestamp</td>
      <td style="text-align:left">Defines the current time.<br>
        Used if you want to display how much <code>hours:minutes:seconds</code> left.
          <br>You must convert your time to <code>timestamp</code> or you will get a wrong
          countdown.
      </td>
      <td style="text-align:left"><code>Number</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">endTimestamp</td>
      <td style="text-align:left">Defines the full duration.
        <br>Used if you want to display how much <code>hours:minutes:seconds</code> left.
          <br>You must convert your time to <code>timestamp</code> or you will get a wrong
          countdown.
      </td>
      <td style="text-align:left"><code>Number</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">largeImageKey</td>
      <td style="text-align:left">Defines the logo for the presence.</td>
      <td style="text-align:left"><code>String</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">smallImageKey</td>
      <td style="text-align:left">Defines the small icon next to presence&apos;s logo.</td>
      <td style="text-align:left"><code>String</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">smallImageText</td>
      <td style="text-align:left">Defines the text that will be shown to user when they hover over the small
        icon.</td>
      <td style="text-align:left"><code>String</code>
      </td>
    </tr>
        <tr>
      <td style="text-align:left">buttons</td>
      <td style="text-align:left">Array of buttons, max 2, label is the button text, and url is the link.</td>
      <td style="text-align:left"><code>Array&lt;Object&gt;</code>
      </td>
    </tr>
  </tbody>
</table>

```ts
const presenceData: PresenceData = {
  details: "My title",
  state: "My description",
  largeImageKey: "service_logo",
  smallImageKey: "small_service_icon",
  smallImageText: "You hovered me, and what now?",
  startTimestamp: 1564444631188,
  endTimestamp: 1564444634734,
  buttons: [
    {
            label: "Test button1",
            url: "https://premid.app/"
        },
        {
            label: "Test button2",
            url: "https://premid.app/contributors"
        }
    ]
};
```

## Events

Events allow you to detect and handle some changes or calls that were made. You can subscribe to events using the `on` method.

```ts
presence.on("UpdateData", async () => {
  // Do something when data gets updated.
});
```

To wydarzenie jest uruchamiane za każdym razem, gdy status jest aktualizowany.

#### `UpdateData`

Wystrzelony, gdy dane są odebrane ze skryptu iFrame.

#### `iFrameData`

Fired when data is received from iFrame script.
