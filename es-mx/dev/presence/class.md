---
title: Clase de Presence
description: La clase principal para cada presence de PreMiD
published: true
date: 2021-02-26T20:42:26.910Z
tags:
editor: markdown
dateCreated: 2021-02-21T21:13:14.449Z
---

# Clase de Presence

## Introducción

La clase de `Presence` es útil dado que contiene métodos básicos para construir una presence.

Cuando creas una clase has de especificar apropiadamente el campo `clientId`.

```typescript
const presence = new Presence({
  clientId: "514271496134389561" // clientId de ejemplo
});
```

### Propiedades

Hay tres propiedades disponibles para la clase `Presence`.

#### `clientId`

Esta propiedad es necesaria para que funcione, ya que utiliza el id de aplicación para mostrar su logotipo entre otras imágenes. Puedes obtenerlo en tu [página de aplicaciones](https://discordapp.com/developers/applications).

#### `injectOnComplete`

Al configurar `injectOnComplete` a `true` el primer evento `UpdateData` se lanzará, en ambos archivos `presence.ts` y `iframe.ts`, una vez haya terminado de cargar completamente la página.

#### `appMode`

Al establecer `appMode` a `true` si la presence enviara un `PresenceData` vacío, la app mostrará la imagen y nombre de la aplicación en el perfil del usuario.

## Métodos

### `getActivity()`

Devuelve un objeto `PresenceData` con los datos que se están mostrando en la presence.

### `setActivity(PresenceData | Slideshow, Boolean)`

Establece la actividad de tu perfil de acuerdo a los datos proporcionados.

El primer parámetro requiere una interfaz [`PresenceData`](#presencedata-interface) o una clase [`Slideshow`](/dev/presence/slideshow) para obtener toda la información que deseas mostrar en tu perfil.

El segundo parámetro indica si la presence está reproduciendo algo o no. El segundo parámetro indica si la presence está reproduciendo algo o no. Utiliza siempre `true` si proporcionas marcas de tiempo (timestamps) en `PresenceData`.

### `clearActivity()`

Elimina la actividad actual y el titulo de la bandeja de trabajo.

### `setTrayTitle(String)`

> Este método funciona sólo en Mac OS. 
> 
> {.is-warning}

Establece el título de la bandeja en la barra de menús.

### `createSlideshow()`

Crea una nueva instancia de la clase `Slideshow`.

```typescript
const slideshow = presence.createSlideshow();
```

Se sugiere hacer esto al instanciar la clase `Presence`:

```typescript
const presence = new Presence({
    clientId: "514271496134389561" // clientId de ejemplo
  }),
  slideshow = presence.createSlideshow();
```

Puedes encontrar la documentación para la clase `Slideshow` [aquí](/dev/presence/slideshow).

### `getStrings(Object)`

Un método asíncrono que te permite obtener strings traducidas de la extensión.

Debes proporcionar un `Object` donde las claves son la clave del string, `valorClave` es el valor del string. Puedes encontrar una lista de strings traducidas aquí: `https://api.premid.app/v2/langFile/presence/en/`

```typescript
// Devuelve las strings `Playing` y `Paused`
// desde la extensión.
const strings = await presence.getStrings({
  reproduciendo: "general.playing",
  pausado: "general.paused"
}, "en");

const playString = strings.reproduciendo; // resultato: Playing
const pauseString = strings.pausado; // resultado: Paused
```

Desde la versión 2.2.0 de la extensión ahora puedes obtener strings dado un idioma. Esto funciona bien en conjunto de la configuración `multiLanguage` recientemente añadida.

Sugerimos que utilices el siguiente código para que se actualice automáticamente PresenceData si el usuario cambia el idioma;

```typescript
// Una interfaz de strings que estás obteniendo obtienes (buena para calidad del código y autocompletado).
interface LangStrings {
  play: string;
  pause: string;
}

async function getStrings(): Promise<LangStrings> {
  return presence.getStrings(
    {
      // Las strings que estás obteniendo, asegurate de que concuerdan con la interfaz LangStrings.
      play: "general.playing",
      pause: "general.paused"
    },
    // El ID es el ID del campo multiLanguage establecido en los ajustes.
    await presence.getSetting("ID")
  );
}

let strings: Promise<LangStrings> = getStrings(),
  // El ID es el ID del campo multiLanguage establecido en los ajustes.
  oldLang: string = await presence.getSetting("ID");

//! ¡El siguiente código debe estar dentro del evento updateData!
// El ID es el ID del campo multiLanguage establecido en los ajustes.
const newLang = await presence.getSetting("ID");
if (oldLang !== newLang) {
  oldLang = newLang;
  strings = getStrings();
}

const playString = (await strings).play, // result: Playing
  pauseString = (await strings).pause; // result: Paused
```

### `getPageletiable(String)`

Returns a variable from the website if it exists.

```typescript
const pageVar = getPageletiable(".pageVar");
console.log(pageVar); // This will log the "Variable content"
```

### `getExtensionVersion(Boolean)`

Returns version of the extension the user is using.

```typescript
getExtensionVersion(onlyNumeric?: boolean): string | number;

const numeric = presence.getExtensionVersion();
console.log(numeric); // Will log 210
const version = presence.getExtensionVersion(false);
console.log(version); // Will log 2.1.0
```

### `getSetting(String)`

Obtén el valor del ajuste.

```typescript
const setting = await presence.getSetting("pdexID"); //Reemplaza pdexID con el id de tu ajuste
console.log(setting); // Esto mostrará el valor del ajuste
```

### `hideSetting(String)`

Oculta la configuración dada.

```typescript
presence.hideSetting("pdexID"); // Replace pdexID with the id of the setting
```

### `showSetting(String)`

Muestra la configuración dada (Solo funciona si el ajuste ya estaba oculto).

```typescript
presence.showSetting("pdexID"); // Replace pdexID with the id of the setting
```

### `getLogs()`

Returns the logs of the websites console.

```typescript
const logs = await presence.getLogs();
console.log(logs); // This will log the latest 100 logs (in an array).
```

**Note:** Requires `readLogs` to be `true` in the `metadata.json` file.

### `info(String)`

Prints the given message in the console in a format based of the presence in the `info` style.

```typescript
presence.info("Test") // This will log "test" in the correct styling.
```

### `success(String)`

Prints the given message in the console in a format based of the presence in the `success` style.

```typescript
presence.success("Test") // This will log "test" in the correct styling.
```

### `error(String)`

Prints the given message in the console in a format based of the presence in the `error` style.

```typescript
presence.error("Test") // This will log "test" in the correct styling.
```

### `getTimestampsfromMedia(HTMLMediaElement)`

Returns 2 `snowflake` timestamps in an `Array` that can be used for `startTimestamp` and `endTimestamp`.

```typescript
const timestamps = getTimestampsfromMedia(document.querySelector(".video"));
presenceData.startTimestamp = timestamps[0];
presenceData.endTimestamp = timestamps[1];
```

**Note:** The given `String` in querySelector is an example.

### `getTimestamps(Number, Number)`

Returns 2 `snowflake` timestamps in an `Array` that can be used for `startTimestamp` and `endTimestamp`.

```typescript
const video = document.querySelector(".video"),
  timestamps = getTimestamps(video.currentTime, video.duration);
presenceData.startTimestamp = timestamps[0];
presenceData.endTimestamp = timestamps[1];
```

**Note:** The given `String` in querySelector is an example.

### `timestampFromFormat(String)`

Converts a string with format `HH:MM:SS` or `MM:SS` or `SS` into an integer (Does not return snowflake timestamp).

```typescript
const currentTime = timestampFromFormat(document.querySelector(".video-now").textContent),
  duration = timestampFromFormat(document.querySelector(".video-end").textContent),
  timestamps = getTimestamps(currentTime, duration);
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
      <th style="text-align:left">Variable</th>
      <th style="text-align:left">Descripción</th>
      <th style="text-align:left">Tipo</th>
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
      <td style="text-align:left">Defines the text that will be shown to user when he will hover the small
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

```typescript
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

```typescript
presence.on("UpdateData", async () => {
  // Do something when data gets updated.
});
```

There are few events available:

#### `UpdateData`

This event is fired every time the presence is being updated.

#### `iFrameData`

Fired when data is received from iFrame script.
