---
title: Metadata.json
description: Contient des données basique sur la Presence
published: true
date: 2021-02-07T17:12:06.799Z
tags:
editor: markdown
dateCreated: 2020-06-11T18:04:52.965Z
---

# Metadata.json

Si vous souhaitez publier une présence dans la boutique et la charger via l'extension, vous devez créer le fichier ` metadata.json ` dans votre dossier ` dist `.

Un exemple de ce fichier se situe ci-dessous.

```typescript
{
  "author": {
    "name": "UTILISATEUR",
    "id": "ID"
  },
  "contributors": [{
    "name": "UTILISATEUR",
    "id": "ID"
  }],
  "service": "SERVICE",
  "altnames": ["SERVICE"],
  "description": {
    "en": "DESCRIPTION"
  },
  "url": "URL",
  "regExp": "REGEXP",
  "iFrameRegExp": "REGEXP",
  "version": "VERSION",
  "logo": "URL",
  "thumbnail": "URL",
  "color": "#45A8FC",
  "tags": ["TAG1", "TAG2"],
  "category": "CATÉGORIE",
  "iframe": false,
  "settings": [
    {
      "id": "ID",
      "title": "TITRE AFFICHÉ",
      "icon": "ICÔNE FONTAWESOME",
      "value": true
    },
    {
      "id": "ID",
      "if": {
        "ID": true
      },
      "title": "TITRE AFFICHÉ",
      "icon": "ICÔNE FONTAWESOME",
      "value": "\"%song%\" par %artist%",
      "placeholder": "utilisez %song% ou %artist%"
    },
    {
      "id": "ID",
      "title": "TITRE AFFICHÉ",
      "icon": "ICÔNE FONTAWESOME",
      "value": 0,
      "values": ["1", "2", "etc."]
    }
  ]
}
```

## Comprendre le fichier metadata.json

Cet exemple semble vraiment étrange, hein? Ne vous inquiétez pas, ce n'est pas si difficile de comprendre à quoi sert chaque variable.

<table>
  <thead>
    <tr>
      <th style="text-align:left">Variable</th>
      <th style="text-align:left">Description</th>
      <th style="text-align:left">Type</th>
      <th style="text-align:left">Optionnel</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>author</b></td>
      <td style="text-align:left">Doit contenir un Objet avec le <code>nom</code> et l'<code>id</code> du développeur de la Presence. <code>name</code> est votre nom d'utilisateur Discord sans l'identifiant(#0000). L'utilisateur <code>id</code> peut être copié depuis Discord en activant le mode développeur
        et en faisant un clic droit sur votre profil.</td>
      <td style="text-align:left"><code>Object</code></td>
      <td style="text-align:left"><code>Non</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>contributors</b></td>
      <td style="text-align:left">Doit contenir un objet avec le <code>nom</code> et l'<code>id</code> du contributeur. <code>name</code> est votre nom d'utilisateur Discord sans l'identifiant(#0000). L'<code>id</code> utilisateur peut être copié depuis Discord en activant le mode développeur
        et en faisant un clic droit sur votre profil.</td>
      <td style="text-align:left"><code>Array&lt;Object&gt;</code></td>
      <td style="text-align:left"><code>Oui</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>service</b></td>
      <td style="text-align:left">Le titre du service que cette présence supporte.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Non</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>altnames</b></td>
      <td style="text-align:left">Soyez en mesure de rechercher la presence en utilisant un nom alternatif.<br>
      Destiné à être utilisé pour les presences qui ont des noms différents dans des langues différentes (par ex. Pokémon et 포켓몬스터).<br>
      Vous pouvez également l'utiliser pour les presences qui ont des caractères spéciaux afin que vous n'ayez pas à les taper (par ex. Pokémon et Pokemon).</td>
      <td style="text-align:left"><code>Array&lt;String&gt;</code></td>
      <td style="text-align:left"><code>Oui</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>description</b></td>
      <td style="text-align:left">Description du service <b>PAS</b> de la présence. Votre description doit avoir des valeurs de paire de clés qui indiquent la langue, et la description dans cette langue spécifique. Faites des descriptions avec les langues <i>que vous connaissez</i>, nos traducteurs apporteront des modifications à votre fichier de métadonnées. Voir la catégorie pour les langues de présence pour une liste. </td>
      <td style="text-align:left"><code>Object</code></td>
      <td style="text-align:left"><code>Non</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>url</b></td>
      <td style="text-align:left">URL du service.<br>
<b>Exemple :</b><code>vk. om</code><br>
        <b>Cette url doit correspondre à l'url du site web car elle sera utilisée pour détecter où que ce soit ou non le site web où injecter le script. Ceci ne peut être utilisé comme un tableau que s'il y a plus d'une urls.</b></td>
      <td style="text-align:left"><code>String, Array&lt;String&gt;</code></td>
      <td style="text-align:left"><code>Non</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>regExp</b></td>
      <td style="text-align:left">Une chaîne d'expression régulière utilisée pour faire correspondre les URLs.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Oui</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>version</b></td>
      <td style="text-align:left">Version de votre présence.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Non</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>logo</b></td>
      <td style="text-align:left">Lien vers le logo du service&apos;.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Non</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>thumbnail</b></td>
      <td style="text-align:left">Lien vers votre miniature de présence.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Non</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>color</b></td>
      <td style="text-align:left">valeur <code>#HEX</code>. Nous vous recommandons d'utiliser une couleur primaire du service
        que votre présence supporte.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Non</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>tags</b></td>
      <td style="text-align:left">Tableau avec des tags, ils aideront les utilisateurs à rechercher votre présence sur le site Web.</td>
      <td style="text-align:left"><code>String, Array&lt;String&gt;</code></td>
      <td style="text-align:left"><code>Non</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>category</b></td>
      <td style="text-align:left">Une chaîne utilisée pour représenter la catégorie sous laquelle tombe la présence.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Non</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>iframe</b></td>
      <td style="text-align:left">Définit si <code>iFrames</code> sont utilisés</td>
      <td style="text-align:left"><code>Boolean</code></td>
      <td style="text-align:left"><code>Oui</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>iFrameRegExp</b></td>
      <td style="text-align:left">Un sélecteur d'expression régulière qui sélectionne les iframes à injecter.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Oui</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>readLogs</b></td>
      <td style="text-align:left">Définit si l'extension doit lire les logs.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Oui</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>settings</b></td>
      <td style="text-align:left">Un tableau de paramètres que l'utilisateur peut modifier</td>
      <td style="text-align:left"><code>Array&lt;Object&gt;</code></td>
      <td style="text-align:left"><code>Oui</code></td>
    </tr>
  </tbody>
</table>

## Expressions régulières

Si vous voulez apprendre les expressions régulières, voici quelques sites web.

#### Apprentissage

- [ Vidéo de démarrage rapide](https://youtu.be/sXQxhojSdZM) - [RegexOne](https://regexone.com/) - [Information sur les expressions régulières](https://www.regular-expressions.info/tutorial.html)

#### En Test

• [Regexr](https://regexr.com/) • [Regex101](https://regex101.com/)

## Langues de présence

PreMiD est un service polyglotte. Cela signifie qu'il y a un grand nombre de langues disponibles pour toucher des utilisateurs tout autour du globe. Une liste complète des langues peut être trouvée avec ce [point de terminaison de l'API](https://api.premid.app/v2/langFile/list). Pour personnaliser encore plus votre présence, vous pouvez permettre aux utilisateurs à sélectionner la langue d'affichage de leur présence. Voir [`multiLanguage`](#multilanguage) pour plus d'informations.

## Paramètres de présence
Configurer les paramètres interactifs pour que les utilisateurs puissent personnaliser la présence!
```typescript
"settings": [
  {
    "id": "ID",
    "multiLanguage": true //Voir https://docs.premid.app/dev/presence/metadata#multilanguage
  },
  {
    "id": "ID",
    "title": "TITRE AFFICHÉ",
    "icon": "ICÔNE FONTAWESOME", //Exemple : "fas fa-info"
    "value": true //Les valeurs booléennes vont faire apparaître un bouton "on/off" avec cette valeur comme valeur par défaut  },
  {
    "id": "ID",
    "if": {
      "ID": true //Si un autre paramètre équivaut à cette valeur (true/false/0/1/etc.) alors affichez ce bouton.
    },
    "title": "TITRE AFFICHÉ",
    "icon": "ICÔNE FONTAWESOME",
    "value": "\"%song%\" par %artist%", //Mettre une string va créer un paramètre avec un champ de saisie où vous pourrez mettre une saisie personnalisée.
    "placeholder": "utilisez %song% par %artist%" //Lorsque l'entrée est vide, elle s'affiche en grisé
        },
        {
            "id": "ID",
            "title": "TITRE AFFICHÉ",
            "icon": "ICÔNE GRATUITE FONTAWESOME",
            "value": 0, //Valeur par défaut du sélecteur
            "values": ["1", "2", "etc."] //Fera du réglage un sélecteur où vous sélectionnez celui que vous voulez
        }
]
```

### `multiLanguage`

#### Introduction

Le paramètre `multiLanguage` est utilisé pour permettre aux utilisateurs de sélectionner manuellement la langue dans laquelle ils veulent que le presence leur soit montrée. This requires you to use strings from our [API](https://api.premid.app/v2/langFile/presence/en), for information on how to add strings click [here](https://docs.premid.app/dev/presence/metadata#adding-new-strings).

#### Configuration

Le paramètre `multiLanguage` est un cas spécial, il ne nécessite ni de `titre` ni d' `icône` ni de `valeur` ou `valeurs` comme d'autres paramètres, mais, il demande encore plus de choses à configurer !

La clé `multiLanguage` peut être définie comme suit :

`true`: utilisez ceci si vous n'allez utiliser que des chaînes de caractères du fichier `general.json` et du fichier `<service>.json` du [Dépôt de localisation](https://github.com/PreMiD/Localization/tree/master/src/Presence). `string`: nom du fichier excluant l'extension (.json) à l'intérieur du [Dépôt de localisation](https://github.com/PreMiD/Localization/tree/master/src/Presence) (excluant le fichier `general` car il est toujours chargé). Seules les langues courantes du fichier `general` et du fichier saisi seront listées. `Array<String>`: si vous utilisez plus d'un fichier à l'intérieur du [Dépôt de localisation](https://github.com/PreMiD/Localization/tree/master/src/Presence) vous pouvez spécifier toutes les valeurs dans une table (excluant le fichier `general`, car il est toujours chargé). Seules les langues courantes de tous les fichiers seront listées.

#### Ajout de nouvelles chaînes

**Note:** Adding custom strings for a presence is only allowed if it has more than 1000 users.

##### Cloner le projet

1. Ouvrez un terminal et tapez `git clone https://github.com/PreMiD/Localization`.
2. Choisissez un dossier.
3. Ouvrez-le dans votre éditeur de code.

##### Création du fichier

1. Allez dans le dossier `src`.
2. Allez dans le dossier `Presence`.
3. Créer un fichier nommé `<service>.json`. (Le service est le **nom** (pas une URL) en minuscule du service que vous voulez supporter.)

##### Ajout de chaînes

Each `string` is an `Object` where from the name starts with the service name and then the so called stringName with a dot in between them.

The stringName is a 1 word identifier of the message.

The `Object` has 2 properties; `message` and `description`. `message` is the text that needs to be translated. `description` is a description of the message to help our translators understand what they are translating.

**Note:** Do not add any duplicate strings. (This includes strings out of the `general.json` file but not the other files.)

Visualization of the the file:

```typescript
{
  "<service>.<stringName>": {
    "message": "Texte qui doit être traduit. ,
    "description": "Ceci explique ce que le message ci-dessus est."
  },
  "<service>.<stringName>": {
    "message": "Texte qui doit être traduit. ,
    "description": "Ceci explique ce que le message ci-dessus est."
  }
}
```

After you have fully made the file with strings you can create a Pull Request on the [Localization Repository](https://github.com/PreMiD/Localization), in the description you **must** include a link to your Pull Request of the presence updated using these new strings from the [Presence Repository](https://github.com/PreMiD/Presences).

#### Touches par défaut
The keys you didn't have to set are automatically set to the following: `title`: "Language" **Note:** This is translated into their default language (browser language). `icon`: "fas fa-language" ([Preview](https://fontawesome.com/icons/language)) `value`: **Set to their browser language if it is available (100% translated), otherwise English.** `values`: **Set to the available languages (languages that have it 100% translated).**

**Note:** These are in no way changeable.

### Méthodes

Use the following methods to get settings info in your presence files:
#### `getSetting(String)`
Returns value of setting.
```typescript
const setting = wait presence.getSetting("pdexID"); //Remplacer pdexID par l'id du paramètre
console.log(setting); // Cela affichera dans la console la valeur du paramètre
```

#### `hideSetting(String)`
Hides given setting.
```typescript
presence.hideSetting("pdexID"); //Remplacer pdexID par l'id du paramètre
```

#### `showSetting(String)`
Affiche le paramètre spécifié (Ne fonctionne que si le paramètre est déjà masqué).
```typescript
presence.showSetting("pdexID"); //Remplacer pdexID par l'id du paramètre
```

## Catégories de présence

When making your presence, you must specify a category which the presence falls under. This is a compiled list of the categories that you can use.

<table>
  <thead>
    <tr>
      <th style="text-align:left">Catégorie</th>
      <th style="text-align:left">Nom</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>anime</b></td>
      <td style="text-align:left"><b>Animé</b></td>
      <td style="text-align:left">Tout ce qui est en rapport à l'animation, des forums aux plateformes de streaming vidéo.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>games</b></td>
      <td style="text-align:left"><b>Jeux</b></td>
      <td style="text-align:left">N'importe quel site web qui a un contenu lié au jeu, comme <code>Kahoot</code> ou <code>Skribbl.io</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>music</b></td>
      <td style="text-align:left"><b>Musique</b></td>
      <td style="text-align:left">Ce sont des sites Web qui offrent des contenus liés à la musique, que ce soit en streaming ou en téléchargement.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>socials</b></td>
        <td style="text-align:left"><b>Réseaux sociaux</b></td>
      <td style="text-align:left">Les sites Web qui sont utilisés dans le but de créer et de partager du contenu ou de participer à d'autres formes de réseau social.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>videos</b></td>
        <td style="text-align:left"><b>Vidéos & Streams</b></td>
      <td style="text-align:left">Sites Web qui servent à fournir des vidéos et des streams.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>other</b></td>
      <td style="text-align:left"><b>Autre</b></td>
      <td style="text-align:left">Tout ce qui ne relève pas d'une catégorie spécifique énumérée ci-dessus.</td>
    </tr>
  </tbody>
</table>

