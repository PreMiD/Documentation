---
title: Classe Presence
description: La classe principale pour chaque presence PreMiD
published: true
date: 2021-10-30T22:47:57.209Z
tags:
editor: markdown
dateCreated: 2021-09-07T01:44:50.164Z
---

# Classe Presence

## Introduction

La classe `Presence` est très utile car elle possède des méthodes de base dont nous avons besoin pour créer une presence.

Lorsque vous créez une classe, vous devez spécifier la propriété `clientId`.

```ts
const presence = new Presence({
  clientId: "5141496134389561" // Exemple de clientId
});
```

### Propriétés

Il y a trois propriétés disponibles pour la classe de `Presence`.

#### `clientId`

Cette propriété est nécessaire pour que votre Presence fonctionne car elle utilise l'identifiant de votre application pour afficher son logo et ses images. Vous pouvez l'obtenir sur votre page d'[applications](https://discordapp.com/developers/applications).

#### `injectOnComplete` - *Déconseillée depuis la version 2.2.4*

Quand le paramètre `injectOnComplete` est défini sur `true`, le premier évènement `UpdateData` pour les fichiers `presence.ts` et `iframe.ts` sera lancé après le chargement complet de la page.

#### `appMode` - *Déconseillée depuis la version 2.2.4*

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

### `setTrayTitle(String)` - *Deprecated since 2.2.3*

> Cette méthode ne fonctionne que sur Mac OS. 
> 
> {.is-warning}

Définit le titre de la barre de menus.

### `createSlideshow()`

Crée une nouvelle classe `Slideshow`.

```ts
const slideshow = presence.createSlideshow();
```

Il est suggéré de faire ceci directement après avoir crée la classe `Presence`:

```ts
const presence = new Presence({
    clientId: "514271496134389561" // Exemple de clientId
  }),
  slideshow = presence.createSlideshow();
```

Vous pouvez trouver la documentation pour la classe `Slideshow` [ici](/dev/presence/slideshow).

### `getStrings(Object)`

Méthode asynchrone qui vous permet d'obtenir les chaînes traduites depuis l'extension.

Vous devez fournir `Object` avec les clés qui sont la clé de la chaîne, `keyValue` est la valeur de la chaîne. Une liste de chaînes de caractères traduites peut être trouvée ici : `https://api.premid.app/v2/langFile/presence/fr/`

```ts
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

```ts
async function getStrings() {
return presence.getStrings(
    {
      play: "general.playing",
      pause: "general.paused"
    },
    // L'ID est l'identifiant du paramètre multiLanguage.
    await presence.getSetting("ID").catch(() => "en");
  );
}

let strings = getStrings(),
  // L'ID est à nouveau l'identifiant du paramètre multiLanguage.
  oldLang: string = await presence.getSetting("ID").catch(() => "en");

//! Le code suivant doit être à l'intérieur de l'event updateData !
// The ID is the ID of the multiLanguage setting.
const newLang = await presence.getSetting("ID").catch(() => "en");
if (oldLang !== newLang) {
  oldLang = newLang;
  strings = getStrings();
}

const playString = (await strings).play, // résultat : Lecture
  pauseString = (await strings).pause; // résultat : En pause
```

### `getPageletiable(String)`

Retourne une variable du site web si elle existe.

**Attention : cette fonction peut causer une grosse utilisation du CPU & un ralentissement du site quand elle est exécutée trop de fois.**

```ts
const pageVar = getPageletiable(".pageVar");
console.log(pageVar); // Cela permettra d'afficher le "contenu variable"
```

### `getExtensionVersion(Boolean)`

Renvoie la version de l'extension que l'utilisateur utilise.

```ts
getExtensionVersion(onlyNumeric?: boolean): string | number;

const numeric = presence.getExtensionVersion();
console.log(numeric); // Affichera 210
const version = presence.getExtensionVersion(false);
console.log(version); // Affichera 2.1.0
```

### `getSetting(String)`

Retourne la valeur du paramètre.

```ts
const setting = await presence.getSetting("pdexID"); //Remplacer pdexID avec l'id du paramètre
console.log(setting); // Cela affichera dans la console la valeur du paramètre
```

### `hideSetting(String)`

Masque le paramètre donné.

```ts
presence.hideSetting("pdexID"); // Remplacer pdexID par l'id du paramètre
```

### `showSetting(String)`

Affiche le paramètre donné (Ne marche seulement si le paramètre en question était déjà masqué).

```ts
presence.showSetting("pdexID"); // Remplacer pdexID par l'id du paramètre
```

### `getLogs()`

Retourne les logs de la console du site web.

```ts
const logs = await presence.getLogs();
console.log(logs); // Cela affichera les 100 derniers logs (dans un array).
```

**Remarque :** `readLogs` doit avoir la valeur `true` dans le fichier `metadata.json`.

### `info(String)`

Affiche le message donné dans la console dans un format basé sur la presence dans le style `info`.

```ts
presence.info("Test") // Cela va afficher "test" dans le bon style.
```

### `success(String)`

Affiche le message donné dans la console dans un format basé sur la presence dans le style `success`.

```ts
presence.success("Test") // Cela va afficher "test" dans le bon style.
```

### `error(String)`

Affiche le message donné dans la console dans un format basé sur la presence dans le style `error`.

```ts
presence.error("Test") // Cela va afficher "test" dans le bon style.
```

### `getTimestampsfromMedia(HTMLMediaElement)`

Retourne 2 `snowflake` timestamps dans un `Array` qui peut être utilisé pour `startTimestamp` et `endTimestamp`.

```ts
const timestamps = presence.getTimestampsfromMedia(document.querySelector(".video"));
presenceData.startTimestamp = timestamps[0];
presenceData.endTimestamp = timestamps[1];
```

**Note:** Le `String` donnée dans querySelector est un exemple.

### `getTimestamps(Number, Number)`

Retourne 2 timestamps sous forme de `snowflake` dans un `Array` qui peuvent être utilisé pour `startTimestamp` et `endTimestamp`.

```ts
const video = document.querySelector(".video"),
  timestamps = presence.getTimestamps(video.currentTime, video.duration);
presenceData.startTimestamp = timestamps[0];
presenceData.endTimestamp = timestamps[1];
```

**Note :** La `String` dans le querySelector n'est qu'un exemple.

### `timestampFromFormat(String)`

Convertit une string au format `HH:MM:SS` ou `MM:SS` ou `SS` en un entier (Ne retourne pas de snowflake timestamp).

```ts
const currentTime = presence.timestampFromFormat(document.querySelector(".video-now").textContent),
  duration = presence.timestampFromFormat(document.querySelector(".video-end").textContent),
  timestamps = presence.getTimestamps(currentTime, duration);
presenceData.startTimestamp = timestamps[0];
presenceData.endTimestamp = timestamps[1];
```

**Note :** La `String` dans le querySelector n'est qu'un exemple.

## Interface `PresenceData`

L'interface `PresenceData` est recommandée à l'utilisation quand vous utilisez la méthode `setActivity()`.

Cette interface contient les variables suivantes, toutes sont facultatives.

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
      <td style="text-align:left">Defines the text that will be shown to user when they hover over the small
        icon.</td>
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

```ts
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

Les événements vous permettent de détecter et de gérer quelques changements ou appels qui ont été effectués. Vous pouvez aussi suivre les événements en utilisant la méthode `on`.

```ts
presence.on("UpdateData", async () => {
  // Faire quelque chose quand les données sont mises à jour.
});
```

Il y a quelques événements disponibles :

#### `UpdateData`

Cet événement est déclenché chaque fois que la présence est mise à jour.

#### `iFrameData`

Cet événement est déclenché à chaque fois que des données sont reçues du script iFrame.
