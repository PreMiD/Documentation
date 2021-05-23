---
title: Classe Presence
description: La classe principale pour chaque presence PreMiD
published: true
date: 2021-05-23T09:14:06.963Z
tags:
editor: markdown
dateCreated: 2021-02-21T21:13:14.449Z
---

# Classe Presence

## Introduction

La classe `Presence` est très utile car elle possède des méthodes de base dont nous avons besoin pour créer une presence.

Lorsque vous créez une classe, vous devez spécifier la propriété `clientId`.

```typescript
const presence = new Presence({
  clientId: "5141496134389561" // Exemple de clientId
});
```

### Propriétés

Il y a trois propriétés disponibles pour la classe de `Presence`.

#### `clientId`

Cette propriété est nécessaire pour que votre Presence fonctionne car elle utilise l'identifiant de votre application pour afficher son logo et ses images. Vous pouvez l'obtenir sur votre page d'[applications](https://discordapp.com/developers/applications).

#### `injectOnComplete` - *Deprecated since 2.2.4*

Quand le paramètre `injectOnComplete` est défini sur `true`, le premier évènement `UpdateData` pour les fichiers `presence.ts` et `iframe.ts` sera lancé après le chargement complet de la page.

#### `appMode` - *Deprecated since 2.2.4*

Quand le paramètre `appMode` est défini sur `true` et que la presence était censée renvoyer un `PresenceData` vide, l'app affichera l'application (image et nom) sur le profil de l'utilisateur plutôt que rien.

## Méthodes

### `getActivity()`

Retourne un objet `PresenceData` de ce que la présence affiche.

### `setActivity(PresenceData | Slideshow, Boolean)`

Définit l'activité de votre profil en fonction des données fournies.

Le premier paramètre nécessite une interface [`PresenceData`](#presencedata-interface) ou une classe [`Slideshow`](/dev/presence/slideshow) pour obtenir toutes les informations que vous souhaitez afficher dans votre profil.

Le second paramètre définit quand la présence joue quelque chose ou non. Toujours utiliser `true` si vous fournissez des timestamps dans `PresenceData`.

### `clearActivity()`

Enlève l'activité et le titre actuel.

### `setTrayTitle(String)`

> Cette méthode ne fonctionne que sur Mac OS. 
> 
> {.is-warning}

Définit le titre de la barre de menus.

### `createSlideshow()`

Crée une nouvelle classe `Slideshow`.

```typescript
const slideshow = presence.createSlideshow();
```

Il est suggéré de faire ceci directement après avoir crée la classe `Presence`:

```typescript
const presence = new Presence({
    clientId: "514271496134389561" // Exemple de clientId
  }),
  slideshow = presence.createSlideshow();
```

Vous pouvez trouver la documentation pour la classe `Slideshow` [ici](/dev/presence/slideshow).

### `getStrings(Object)`

Méthode asynchrone qui vous permet d'obtenir les chaînes traduites depuis l'extension.

Vous devez fournir `Object` avec les clés qui sont la clé de la chaîne, `keyValue` est la valeur de la chaîne. Une liste de chaînes de caractères traduites peut être trouvée ici : `https://api.premid.app/v2/langFile/presence/fr/`

```typescript
// Retourne les chaînes `Playing` et `Paused`
// depuis l'extension.
const strings = await presence.getStrings({
  play: "general.playing",
  pause: "general.paused"
});

const playString = strings.play; // Résultat: Joue
const pauseString = strings.pause; // Résultat: En pause
```

Depuis la v2.2.0 de l'extension, vous pouvez maintenant obtenir les chaînes de caractères d'une certaine langue. Cela fonctionne bien avec l'option de réglage `multiLanguage`, également nouvellement ajoutée.

Nous vous suggérons d'utiliser le code suivant afin qu'il mette à jour automatiquement PresenceData si l'utilisateur change la langue sélectionnée ;

```typescript
// Une interface de chaînes de caractères que vous obtenez (bonne pour la qualité du code et l'auto-complétion).
interface LangStrings {
  play: string;
  pause: string;
}

async function getStrings(): Promise<LangStrings> {
  return presence.getStrings(
    {
      // Les chaînes de caractères que vous obtenez, assurez-vous qu'elles correspondent à votre interface LangStrings.
      play: "general.playing",
      pause: "general.paused"
    },
    // L'ID est l'ID du paramètre multiLanguage.
    await presence.getSetting("ID").catch(() => "en");
  );
}

let strings: Promise<LangStrings> = getStrings(),
  // The ID is the ID of the multiLanguage setting.
  oldLang: string = await presence.getSetting("ID").catch(() => "en");

//! Le code suivant doit être à l'intérieur de l'événement updateData !
// L'ID est l'ID du paramètre multiLanguage.
const newLang = await presence.getSetting("ID").catch(() => "en");
if (oldLang !== newLang) {
  oldLang = newLang;
  strings = getStrings();
}

const playString = (await strings).play, // result: Playing
  pauseString = (await strings).pause; // result: Paused
```

### `getPageletiable(String)`

Retourne une variable du site web si elle existe.

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
console.log(numeric); // Affichera 210
const version = presence.getExtensionVersion(false);
console.log(version); // Affichera 2.1.0
```

### `getSetting(String)`

Retourne la valeur du paramètre.

```typescript
const setting = await presence.getSetting("pdexID"); //Remplacer pdexID avec l'id du paramètre
console.log(setting); // Cela affichera dans la console la valeur du paramètre
```

### `hideSetting(String)`

Masque le paramètre spécifié.

```typescript
presence.hideSetting("pdexID"); // Remplacer pdexID par l'id du paramètre
```

### `showSetting(String)`

Shows given setting (Only works if the setting was already hidden).

```typescript
presence.showSetting("pdexID"); // Remplacer pdexID par l'id du paramètre
```

### `getLogs()`

Returns the logs of the websites console.

```typescript
const logs = await presence.getLogs();
console.log(logs); // Cela affichera les 100 derniers logs (dans un array).
```

**Note:** Requires `readLogs` to be `true` in the `metadata.json` file.

### `info(String)`

Prints the given message in the console in a format based of the presence in the `info` style.

```typescript
presence.info("Test") // Cela va afficher "test" dans le bon style.
```

### `success(String)`

Prints the given message in the console in a format based of the presence in the `success` style.

```typescript
presence.success("Test") // Cela va afficher "test" dans le bon style.
```

### `error(String)`

Prints the given message in the console in a format based of the presence in the `error` style.

```typescript
presence.error("Test") // Cela va afficher "test" dans le bon style.
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

## Interface `PresenceData`

The `PresenceData` interface is recommended to use when you are using the `setActivity()` method.

This interface has following variables, all of them are optional.

<table>
  <thead>
    <tr>
      <th style="text-align:left">Variable</th>
      <th style="text-align:left">Description</th>
      <th style="text-align:left">Type</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">details</td>
      <td style="text-align:left">La première ligne de votre présence, généralement utilisée comme en-tête.</td>
      <td style="text-align:left"><code>String</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">state</td>
      <td style="text-align:left">Deuxième ligne de votre présence.</td>
      <td style="text-align:left"><code>String</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">startTimestamp</td>
      <td style="text-align:left">Définit le temps actuel.<br>
        Utilisé si vous voulez afficher combien d'<code>heures:minutes:secondes</code> sont restantes.
          <br>Vous devez convertir votre <code>timestamp</code> ou vous obtiendrez un compte à rebours erroné.
      </td>
      <td style="text-align:left"><code>Number</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">endTimestamp</td>
      <td style="text-align:left">Définit la durée complète.
        <br>Utilisé si vous voulez afficher combien d'<code>heures:minutes:secondes</code> sont restante.
          <br>Vous devez convertir votre <code>timestamp</code> ou vous obtiendrez un compte à rebours erroné.
      </td>
      <td style="text-align:left"><code>Number</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">largeImageKey</td>
      <td style="text-align:left">Définit le logo de la présence.</td>
      <td style="text-align:left"><code>String</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">smallImageKey</td>
      <td style="text-align:left">Définit la petite icône à côté du logo.</td>
      <td style="text-align:left"><code>String</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">smallImageText</td>
      <td style="text-align:left">Définit le texte qui sera affiché à l'utilisateur quand il survolera la petite icône
.</td>
      <td style="text-align:left"><code>String</code>
      </td>
    </tr>
        <tr>
      <td style="text-align:left">buttons</td>
      <td style="text-align:left">Tableau de boutons, maximum 2, label étant le texte du bouton et url le lien.</td>
      <td style="text-align:left"><code>Array&lt;Object&gt;</code>
      </td>
    </tr>
  </tbody>
</table>

```typescript
const presenceData: PresenceData = {
  details: "Mon titre",
  state: "Ma description",
  largeImageKey: "logo_service,
  smallImageKey: "petit_logo_service",
  smallImageText: "Vous m'avez survoler, et maintenant ?",
  startTimestamp: 1564444631188,
  endTimestamp: 1564444634734,
  buttons: [
    {
            label: "Bouton de test 1",
            url: "https://premid.app/"
        },
        {
            label: "Bouton de test 2",
            url: "https://premid.app/contributors"
        }
    ]
};
};
```

## Événements

Events allow you to detect and handle some changes or calls that were made. You can subscribe to events using the `on` method.

```typescript
presence.on("UpdateData", async () => {
  // Faire quelque chose quand les données sont mises à jour.
});
```

There are few events available:

#### `UpdateData`

This event is fired every time the presence is being updated.

#### `iFrameData`

Fired when data is received from iFrame script.
