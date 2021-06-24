---
title: Metadata.json
description: Enthält grundlegende Daten zur Presence
published: true
date: 2021-02-07T17:12:06.799Z
tags:
editor: markdown
dateCreated: 2020-06-11T18:04:52.965Z
---

# Metadata.json

Wenn du eine Presence im Shop veröffentlichen und über die Erweiterung laden möchten, solltest du die `metadata.json`-Datei in deinem `dist` Ordner erstellen.

Ein Beispiel für diese Datei, kannst du unten finden.

```typescript
{
  "author": {
    "name": "USER",
    "id": "ID"
  },
  "contributors": [{
    "name": "USER",
    "id": "ID"
  }],
  "Service": "SERVICE",
  "Altnamen": ["SERVICE"],
  "description": {
    "de": "DESCRIPTION"
  },
  "url": "URL",
  "regExp": "REGEXP",
  "iFrameRegExp": "REGEXP",
  "version": "VERSION",
  "Logo": "URL",
  "thumbnail": "URL",
  "color": "#45A8FC",
  "tag": ["TAG1", "TAG2"],
  "category": "CATEGORY",
  "iframe": falsch,
  "settings": [
    {
      "id": "ID",
      "title": "VORSCHAU TITEL",
      "icon": "FONTAWESOME ICON",
      "Wert": true
    },
    {
      "id": "ID",
      "if": {
        "ID": true
      },
      "title": "VORSCHAU TITEL",
      "icon": "FONTAWESOME ICON",
      "Wert": "\"%song%\" von %artist%",
      "Platzhalter": "benutze %song% oder %artist%"
    },
    {
      "id": "ID",
      "title": "VORSCHAU TITEL",
      "icon": "FONTAWESOME ICON",
      "value": 0,
      "values": ["1", "2", "etc. ]
    }
  ]
}
```

## Grundlegendes zur metadata.json Datei

Das Beispiel sieht wirklich seltsam aus, oder? Keine Sorge, es ist nicht so schwer zu verstehen, wofür jede Variable gedacht ist.

<table>
  <thead>
    <tr>
      <th style="text-align:left">Variable</th>
      <th style="text-align:left">Beschreibung</th>
      <th style="text-align:left">Type</th>
      <th style="text-align:left">Optional</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>author</b></td>
      <td style="text-align:left">Sollte ein Objekt mit dem <code>name</code> und <code>id</code> des Presence-Entwickler enthalten. <code>name</code> ist dein Discord-Benutzername ohne den Identifikator (#0000). User <code>id</code> can be copied from Discord by enabling developer
        mode and right-clicking on your profile.</td>
      <td style="text-align:left"><code>Object</code></td>
      <td style="text-align:left"><code>Nein</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>contributors</b></td>
      <td style="text-align:left">Sollte ein Objekt mit dem <code>name</code> und der <code>id</code> des Mitwirkenden enthalten. <code>name</code> ist dein Discord-Benutzername ohne den Identifikator (#0000). User <code>id</code> can be copied from Discord by enabling developer
        mode and right-clicking on your profile.</td>
      <td style="text-align:left"><code>Array&lt;Object&gt;</code></td>
      <td style="text-align:left"><code>Ja</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>service</b></td>
      <td style="text-align:left">Der Titel des Dienstes, den diese Presence unterstützt.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Nein</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>altnames</b></td>
      <td style="text-align:left">Erlaubt es die Presence mit einem alternativen Namen zu suchen.<br>
      Soll für Presences, die verschiedene Namen in verschiedenen Sprachen haben, verwendet werden (z.B.: Pokémon und 포켓몬스터).<br>
      Dies kann auch genutzt werden für Presences, die spezielle Zeichen  haben, sodass diese nicht eingegeben werden müssen (z.B.: Pokémon und Pokemon).</td>
      <td style="text-align:left"><code>Array&lt;String&gt;</code></td>
      <td style="text-align:left"><code>Ja</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>description</b></td>
      <td style="text-align:left">Beschreibung des Dienstes <b>NICHT</b> der Presence. Your description must have key pair values which indicate the language, and the description in that specific language. Make descriptions with the languages <i>that you know</i>, our translators will make changes to your metadata file. Siehe die Kategorie für Presence-Sprachen für eine Liste. </td>
      <td style="text-align:left"><code>Object</code></td>
      <td style="text-align:left"><code>Nein</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>url</b></td>
      <td style="text-align:left">URL des Dienstes.<br>
<b>Beispiel:</b><code>vk.com</code><br>
<b>Diese URL muss der URL der Webseite gleichen, da sie genutzt wird um zu erkenne, ob es sich um die richtige Webseite handelt, in der das Script injiziert wird. Dies darf nur als Array benutzt werden, wenn es mehr als nur eine URL gibt.</b></td>
      <td style="text-align:left"><code>String, Array&lt;String&gt;</code></td>
      <td style="text-align:left"><code>Nein</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>regExp</b></td>
      <td style="text-align:left">Ein Regex-String, welcher benutzt wird, um URLs zu vergleichen.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Ja</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>version</b></td>
      <td style="text-align:left">Version deiner Presence.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Nein</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>logo</b></td>
      <td style="text-align:left">Link to service&apos;s logotype.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Nein</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>thumbnail</b></td>
      <td style="text-align:left">Link zu deinem Presence-Vorschaubild.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Nein</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>color</b></td>
      <td style="text-align:left"><code>#HEX</code> Wert. We recommend to use a primary color of the service
        that your presence supports.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Nein</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>tags</b></td>
      <td style="text-align:left">Array with tags, they will help users to search your presence on the website.</td>
      <td style="text-align:left"><code>String, Array&lt;String&gt;</code></td>
      <td style="text-align:left"><code>Nein</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>category</b></td>
      <td style="text-align:left">Eine Zeichenfolge, die die Kategorie darstellt, unter die die Presence fällt.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Nein</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>iframe</b></td>
      <td style="text-align:left">Legt fest, ob <code>iFrames</code> verwendet werden</td>
      <td style="text-align:left"><code>Boolean</code></td>
      <td style="text-align:left"><code>Ja</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>iFrameRegExp</b></td>
      <td style="text-align:left">Ein Selektor für reguläre Ausdrücke, der iframes auswählt, in die injiziert werden soll.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Ja</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>readLogs</b></td>
      <td style="text-align:left">Legt fest, ob die Erweiterung Logs lesen soll.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Ja</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>settings</b></td>
      <td style="text-align:left">Eine Reihe von Einstellungen, die der Nutzer ändern kann.</td>
      <td style="text-align:left"><code>Array&lt;Object&gt;</code></td>
      <td style="text-align:left"><code>Ja</code></td>
    </tr>
  </tbody>
</table>

## Reguläre Ausdrücke

Wenn Sie reguläre Ausdrücke lernen möchten, finden Sie hier einige Websites.

#### Lernen

• [Schnellstarter Video](https://youtu.be/sXQxhojSdZM) • [RegexOne](https://regexone.com/) • [Reguläre-Ausdrücke Info](https://www.regular-expressions.info/tutorial.html)

#### Testen

• [Regexr](https://regexr.com/) • [Regex101](https://regex101.com/)

## Presence-Sprachen

PreMiD is a polyglot service, meaning that there are multiple languages available to connect users around the globe. Eine vollständige Liste von Sprachen können mithilfe dieses [API-Endpunkts](https://api.premid.app/v2/langFile/list) gefunden werden. Um deine Presence noch mehr anzupassen, kannst Du Benutzern erlauben, die Sprache ihrer Presence auszuwählen. Siehe [`multiLanguage`](#multilanguage) für mehr Informationen.

## Presence-Einstellungen
Richte interaktive Einstellungen ein, sodass die Presence benutzerdefiniert eingestellt werden kann.
```typescript
"settings": [
  {
    "id": "ID",
    "multiLanguage": true //Siehe https://docs.premid.app/dev/presence/metadata#multilanguage
  },
  {
    "id": "ID" 
    "title": "DISPLAY TITLE",
    "icon": "FONTAWESOME ICON", //Beispiel: "fas fa-info"
    "value": true //Boolean Wert wird daraus eine On/Off Switch machen, mit dem Wert als Voreinstellung
  },
  {
    "id": "ID",
    "if": {
      "ID": true //Wenn eine andere Einstellung diesem Wert entspricht (true/false/0/1/etc.), wird der Button angzeigt
    },
    "title": "DISPLAY TITLE",
    "icon": "FONTAWESOME ICON",
    "value": "\"%song%\" by %artist%", //Wenn ein String eingeben wird, wird die Einstellung zu einer Eingabe, in die eine benutzerdefinierte Eingabe verwenden kann.
    "Platzhalter": "Benutze %song% oder %artist%" //Wenn die Eingabe leer ist, wird dies ausgegraut
  },
  {
    "id": "ID",
    "title": "BEISPIEL TITLE",
    "icon": "FONTAWESOME ICON",
    "value": 0, //Standardwert des Selektors
    "values": ["1", "2", "etc. ] //Wird die Einstellung zu einem Selektor machen, in dem Du wählst welches Du auswählst
  }
]
```

### `multiLanguage`

#### Einführung

Die `multiLanguage` Einstellung erlaubt es Benutzern die manuelle Auswahl der Sprache, die in der Presence angezeigt werden soll. This requires you to use strings from our [API](https://api.premid.app/v2/langFile/presence/en), for information on how to add strings click [here](https://docs.premid.app/dev/presence/metadata#adding-new-strings).

#### Einrichtung

Die `multiLanguage` Einstellung ist ein Sonderfall, es benötigt weder einen `title` noch `icon`, `value` oder `values`, wie die anderen Einstellungen, aber es benötigt mehr Dinge zum einrichten!

Die `multiLanguage` Einstellung kann in die folgenden Werte gesetzt werden:

`true`: Nutze diesen Wert, wenn du nur Strings aus der `general.json` Datei und der `<service>.json` Datei verwendest aus der [Lokalisierungs-Repository](https://github.com/PreMiD/Localization/tree/master/src/Presence). `string`: Name der Datei ohne Dateiendung (.json) in der [Lokalisierungs-Repository](https://github.com/PreMiD/Localization/tree/master/src/Presence) (ausgenommen der `general` Datei, da diese immer geladen wird). Es werden nur gebräuchliche Sprachen sowohl der `general` als auch der eingegebenen Datei angezeigt. `Array<String>`: Wenn du mehr als eine Datei innerhalb der [Lokalisierung-Repository](https://github.com/PreMid/Localization/tree/master/src/Presence) verwendest, kannst du alle Werte in einem Array angeben (ausgenommen der `general` Datei, da diese immer geladen wird). Nur gebräuchliche Sprachen aller Dateien werden aufgelistet.

#### Neue Stings hinzufügen

**Note:** Adding custom strings for a presence is only allowed if it has more than 1000 users.

##### Klont das Projekt

1. Öffne ein Terminal und gib `git clone https://github.com/PreMiD/Localization` ein.
2. Wähle einen Ordner deiner Wahl.
3. Öffne es in deinem Code-Editor.

##### Erstellt die Datei

1. Gehe in den Ordner `src`.
2. Gehe in den `Presence` Ordner.
3. Erstelle eine Datei namens `<service>.json`. (Service ist der **Name** (keine URL) in Kleinbuchstaben des Dienstes, den Du unterstützen möchtest.)

##### Hinzufügen der Strings

Each `string` is an `Object` where from the name starts with the service name and then the so called stringName with a dot in between them.

The stringName is a 1 word identifier of the message.

The `Object` has 2 properties; `message` and `description`. `message` is the text that needs to be translated. `description` is a description of the message to help our translators understand what they are translating.

**Note:** Do not add any duplicate strings. (This includes strings out of the `general.json` file but not the other files.)

Visualization of the file:

```typescript
{
  "<service>.<stringName>": {
    "message": "Text, der übersetzt werden muss.",
    "description": "Erklärt die Nachricht darüber."
  },
  "<service>.<stringName>": {
    "message": "Text, der übersetzt werden muss.",
    "description": "Erklärt die Nachricht darüber."
  }
}
```

After you have fully made the file with strings you can create a Pull Request on the [Localization Repository](https://github.com/PreMiD/Localization), in the description you **must** include a link to your Pull Request of the presence updated using these new strings from the [Presence Repository](https://github.com/PreMiD/Presences).

#### Standard-Tasten
The keys you didn't have to set are automatically set to the following: `title`: "Language" **Note:** This is translated into their default language (browser language). `icon`: "fas fa-language" ([Preview](https://fontawesome.com/icons/language)) `value`: **Set to their browser language if it is available (100% translated), otherwise English.** `values`: **Set to the available languages (languages that have it 100% translated).**

**Note:** These are in no way changeable.

### Methoden

Use the following methods to get settings info in your presence files:
#### `getSetting(String)`
Returns value of setting.
```typescript
const setting = await.presence.getSetting("pdexID"); // Ersetze pdexID mit der ID der Einstellung
console.log(setting); // Dies loggt den Wert der Einstellung
```

#### `hideSetting(String)`
Hides given setting.
```typescript
presence.hideSetting("pdexID"); // pdexID mit der ID von der Einstellung ersetzen
```

#### `showSetting(String)`
Gibt die Protokolle der Webseiten-Konsole wieder.
```typescript
presence.showSetting("pdexID"); // pdexID mit der ID von der Einstellung ersetzen
```

## Presence-Kategorien

When making your presence, you must specify a category which the presence falls under. This is a compiled list of the categories that you can use.

<table>
  <thead>
    <tr>
      <th style="text-align:left">Kategorie</th>
      <th style="text-align:left">Name</th>
      <th style="text-align:left">Beschreibung</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>anime</b></td>
      <td style="text-align:left"><b>Anime</b></td>
      <td style="text-align:left">Alles, was mit Anime zu tun hat, von Foren bis zu Video-Streaming-Plattformen.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>games</b></td>
      <td style="text-align:left"><b>Spiele</b></td>
      <td style="text-align:left">Jede Website mit spielbezogenen Inhalten, z. B. <code>Kahoot</code> oder <code>Skribbl.io</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>music</b></td>
      <td style="text-align:left"><b>Musik</b></td>
      <td style="text-align:left">Hierbei handelt es sich um Websites, die musikbezogene Inhalte anbieten, unabhängig davon, ob diese gestreamt oder heruntergeladen werden.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>socials</b></td>
        <td style="text-align:left"><b>Soziale Netzwerke</b></td>
      <td style="text-align:left">Websites, die zum Erstellen und Teilen von Inhalten oder zur Teilnahme an anderen Formen sozialer Netzwerke verwendet werden.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>videos</b></td>
        <td style="text-align:left"><b>Videos & Livestreams</b></td>
      <td style="text-align:left">Websites, die dem Zweck dienen, Videos und Streams bereitzustellen.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>other</b></td>
      <td style="text-align:left"><b>Sonstiges</b></td>
      <td style="text-align:left">Alles, was nicht unter eine der oben aufgeführten Kategorien fällt.</td>
    </tr>
  </tbody>
</table>

