---
title: Metadata.json
description: Contient des données basique sur la Presence
published: true
date: 2021-12-20T14:27:18.034Z
tags:
editor: markdown
dateCreated: 2020-06-11T18:04:52.965Z
---

# Metadata.json

Si vous souhaitez publier une présence dans la boutique et la charger via l'extension, vous devez créer le fichier `metadata.json` dans votre dossier `dist`.

Un exemple de ce fichier se situe ci-dessous.

```json
{
  "$schema": "https://schemas.premid.app/metadata/1.7",
  "author": {
    "name": "USER",
    "id": "ID"
  },
  "contributors": [{
    "name": "USER",
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
  "category": "CATEGORY",
  "tags": ["TAG1", "TAG2"],
  "iframe": false,
  "settings": [
    {
      "id": "ID",
      "title": "DISPLAY TITLE",
      "icon": "FONTAWESOME ICON",
      "value": true
    },
    {
      "id": "ID",
      "if": {
        "ID": true
      },
      "title": "DISPLAY TITLE",
      "icon": "FONTAWESOME ICON",
      "value": "\"%song%\" by %artist%",
      "placeholder": "use %song% or %artist%"
    },
    {
      "id": "ID",
      "title": "DISPLAY TITLE",
      "icon": "FONTAWESOME ICON",
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
      <th style="text-align:left">Facultatif</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>author</b></td>
      <td style="text-align:left">Doit contenir un Objet avec le <code>nom</code> et l'<code>id</code> du développeur de la Presence. <code>name</code> est votre nom d'utilisateur Discord sans l'identifiant(#0000). L'<code>id</code> utilisateur peut être copié depuis Discord en activant le mode développeur
        et en faisant un clic droit sur votre profil.</td>
      <td style="text-align:left"><code>Object</code></td>
      <td style="text-align:left"><code>Non</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>contributors</b></td>
      <td style="text-align:left">Doit contenir un objet avec le <code>nom</code> et l'<code>id</code> du contributeur. <code>name</code> est votre nom d'utilisateur Discord sans l'identifiant(#0000). L'utilisateur <code>id</code> peut être copié depuis Discord en activant le mode développeur
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
      <td style="text-align:left">Description du service <b>PAS</b> de la présence. Votre description doit avoir des valeurs de paire de clés qui indiquent la langue, et la description dans cette langue spécifique. Faites des descriptions dans les langages <i>que vous connaissez</i>, nos traducteurs apporteront des modifications à votre fichier metadata. Voir la catégorie pour les langues de présence pour une liste. </td>
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
      <td style="text-align:left">Lien vers le logo du service.</td>
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
      <td style="text-align:left">Valeur <code>#HEX</code> (hexadécimale). Nous vous recommandons d'utiliser une des couleurs primaires du service
        pour lequel vous développez votre presence.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Non</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>category</b></td>
      <td style="text-align:left">A string used to represent the category the presence falls under.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Non</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>tags</b></td>
      <td style="text-align:left">Array with tags, they will help users to search your presence on the website.</td>
      <td style="text-align:left"><code>String, Array&lt;String&gt;</code></td>
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
      <td style="text-align:left"><code>Boolean</code></td>
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

• [Regexr](https://regexr.com/) • [Regex101](https://regex101.com/)

#### En Test

• [Regexr](https://regexr.com/) • [Regex101](https://regex101.com/)

## Langues de présence

PreMiD est un service polyglotte. Cela signifie qu'il y a un grand nombre de langues disponibles pour toucher des utilisateurs tout autour du globe. A full list of languages can be found with this [API endpoint](https://api.premid.app/v2/langFile/list). Pour personnaliser encore plus votre présence, vous pouvez permettre aux utilisateurs à sélectionner la langue d'affichage de leur présence. Voir [`multiLanguage`](#multilanguage) pour plus d'informations.

## Paramètres de présence
Configurer les paramètres interactifs pour que les utilisateurs puissent personnaliser la présence!
```json
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

Le paramètre `multiLanguage` est utilisé pour permettre aux utilisateurs de sélectionner manuellement la langue dans laquelle ils veulent que le presence leur soit montrée. Cela nécessite que vous utilisiez des chaînes de caractères de notre [API](https://api.premid.app/v2/langFile/presence/en), pour plus d'informations sur comment ajouter des chaînes de caractères cliquez [ici](https://docs.premid.app/dev/presence/metadata#adding-new-strings).

#### Configuration

La clé `multiLanguage` peut être définie comme suit :

La clé `multiLanguage` peut être définie comme suit :

`true`: utilisez ceci si vous n'allez utiliser que des chaînes de caractères du fichier `general.json` et du fichier `<service>.json` du [Dépôt de localisation](https://github.com/PreMiD/Localization/tree/master/src/Presence). `string`: nom du fichier excluant l'extension (.json) à l'intérieur du [Dépôt de localisation](https://github.com/PreMiD/Localization/tree/master/src/Presence) (excluant le fichier `general` car il est toujours chargé). Seules les langues courantes du fichier `general` et du fichier saisi seront listées. `Array<String>`: si vous utilisez plus d'un fichier à l'intérieur du [Dépôt de localisation](https://github.com/PreMiD/Localization/tree/master/src/Presence) vous pouvez spécifier toutes les valeurs dans une table (excluant le fichier `general`, car il est toujours chargé). Seules les langues courantes de tous les fichiers seront listées.

#### Ajout de nouvelles chaînes

**Note :** Ajouter des chaînes de caractère personnalisées pour une presence est autorisé seulement si elle cumule plus de 1000 utilisateurs.

##### Cloner le projet

1. Ouvrez un terminal et tapez `git clone https://github.com/PreMiD/Localization`.
2. Choisissez un dossier.
3. Ouvrez-le dans votre éditeur de code.

##### Création du fichier

1. Allez dans le dossier `src`.
2. Allez dans le dossier `Presence`.
3. Créer un fichier nommé `<service>.json`. (Le service est le **nom** (pas une URL) en minuscule du service que vous voulez supporter.)

##### Ajout de chaînes

Chaque `chaîne de caractère` est un `objet` dont le nom commence par le nom du service puis par le soi-disant stringName avec un point entre les deux.

Le stringName est un identifiant de 1 mot du message.

L'`Objet` a deux propriétés ; `message` et `description`. `message` est le texte qui a besoin d'être traduit. `description` est la description du message pour aider nos traducteurs à comprendre ce qu'ils traduisent.

**Remarque :** N'ajoutez aucune chaîne de caractères en double. (Cela inclut les chaînes de caractères en dehors du ficher `general.json` mais pas les autres fichiers.)

Visualisation du fichier :

```json
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

Après que vous ayez entièrement créé le fichier avec les chaînes de caractères, vous pouvez créer une Pull Request sur le [Dépôt de Localization](https://github.com/PreMiD/Localization), dans la description vous **devez** inclure un lien vers votre Pull Request de la presence mise à jour en utilisant ces nouvelles chaînes de caractères depuis le [Dépôt de Presence](https://github.com/PreMiD/Presences).

#### Touches par défaut
Les touches que vous n'avez pas définies seront automatiquement définies comme ceci : `title` : "Langue". **Remarque :** Ça sera traduit dans leur langue par défaut (langue du navigateur internet). `icon` : "fas fa-language" ([Aperçu](https://fontawesome.com/icons/language)) `value` : **Définies sur la langue de leur navigateur internet si c'est disponible (100% traduit), sinon en Anglais.** `values` : **Définies sur les langues disponibles (langues qui sont à 100% traduites).**

**Note :** Cela ne peut être changé dans aucun cas.

### Méthodes

Utilisez les méthodes suivantes pour obtenir des informations sur les paramètres dans votre fichier de presence :
#### `getSetting(String)`
Retourne la valeur du paramètre.
```ts
const setting = wait presence.getSetting("pdexID"); //Remplacer pdexID par l'id du paramètre
console.log(setting); // Cela affichera dans la console la valeur du paramètre
```

#### `hideSetting(String)`
Masque le paramètre spécifié.
```ts
presence.hideSetting("pdexID"); //Remplacer pdexID par l'id du paramètre
```

#### `showSetting(String)`
Montre les paramètres donnés (ne marche seulement si le paramètre était déjà caché).
```ts
presence.showSetting("pdexID"); //Remplacer pdexID par l'id du paramètre
```

## Catégories de présence

Quand vous créez votre présence, vous devez spécifier une catégorie dans laquelle votre présence s'inscrit. Ceci est une liste compilée des catégories que vous pouvez utiliser.

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

