---
title: Metadata.json
description: Sisaldab põhiandmeid Presence-i kohta
published: true
date: 2021-12-20T14:27:18.034Z
tags:
editor: markdown
dateCreated: 2020-06-11T18:04:52.965Z
---

# Metadata.json

If you want to publish a presence to the store and load it via the extension, you should create the `metadata.json` file in your `dist` folder.

Selle faili näite leiate allpool.

```json
{
  "$schema": "https://schemas.premid.app/metadata/1.7",
  "author": {
    "name": "KASUTAJA",
    "id": "ID"
  },
  "contributors": [{
    "name": "KASUTAJA",
    "id": "ID"
  }],
  "service": "TEENUS",
  "altnames": ["TEENUS"],
  "description": {
    "en": "KIRJELDUS"
  },
  "url": "URL",
  "regExp": "REGEXP",
  "iFrameRegExp": "REGEXP",
  "version": "VERSIOoN",
  "logo": "URL",
  "thumbnail": "URL",
  "color": "#45A8FC",
  "category": "KATEGOORIA",
  "tags": ["TAG1", "TAG2"],
  "iframe": false,
  "settings": [
    {
      "id": "ID",
      "title": "KUVA PEALKIRI",
      "icon": "FONTAWESOME IkoON",
      "value": true
    },
    {
      "id": "ID",
      "if": {
        "ID": true
      },
      "title": "KUVA PEALKIRI",
      "icon": "FONTAWESOME IKOON",
      "value": "\"%song%\" by %artist%",
      "placeholder": "use %song% or %artist%"
    },
    {
      "id": "ID",
      "title": "KUVA PEALKIRI",
      "icon": "FONTAWESOME IKOON",
      "value": 0,
      "values": ["1", "2", "etc."]
    }
  ]
}
```

## Metadata.json-i mõistmine

See näide näeb tõesti imelik välja? Ärge muretsege, ei ole nii raske aru saada, milleks iga muutuja on mõeldud.

<table>
  <thead>
    <tr>
      <th style="text-align:left">Variable</th>
      <th style="text-align:left">Kirjeldus</th>
      <th style="text-align:left">Tüüp</th>
      <th style="text-align:left">Valikuline</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>author</b></td>
      <td style="text-align:left">Peaks sisaldama objekti, millel on presence-i arendaja <code>nimi</code> ja <code>id</code>. <code>nimi</code> on teie Discordi kasutajanimi ilma identifikaatorita (#0000). Kasutaja <code>id</code> saab kopeerida Discordist, lubades arendaja
        režiimi ja tehes oma profiilil parempoolse hiireklõpsu.</td>
      <td style="text-align:left"><code>Object</code></td>
      <td style="text-align:left"><code>Ei</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>contributors</b></td>
      <td style="text-align:left">Peab sisaldama objekti, mis sisaldab panustaja <code>nime</code> ja <code>id-ed</code>. <code>nimi</code> on teie Discordi kasutajanimi ilma identifikaatorita (#0000). Kasutaja <code>id</code> saab kopeerida Discordist, lubades arendaja
        režiimi ja tehes oma profiilil parempoolse hiireklõpsu.</td>
      <td style="text-align:left"><code>Array&lt;Object&gt;</code></td>
      <td style="text-align:left"><code>Jah</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>service</b></td>
      <td style="text-align:left">The title of the service that this presence supports.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Ei</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>altnames</b></td>
      <td style="text-align:left">Saate presence-i otsida alternatiivse nime abil. <br>
      Mõeldud kasutamiseks presence-i puhul, millel on erinevates keeltes erinev nimi (nt Pokémon ja 포켓 몬스터). <br>
      Saate seda kasutada ka presence-ite jaoks, millel on erimärgid, nii et te ei pea neid kirjutama (nt Pokémon ja Pokemon).</td>
      <td style="text-align:left"><code>Array&lt;String&gt;</code></td>
      <td style="text-align:left"><code>Jah</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>description</b></td>
      <td style="text-align:left">Description of the service <b>NOT</b> the presence. Teie kirjeldusel peavad olema võtmepaari väärtused, mis näitavad keelt ja kirjeldust selles konkreetses keeles. Tehke kirjeldused keeltega, <i>mis te oskate</i>, meie tõlkijad teevad muudatused teie metaandmefaili. View the category for presence languages for a list. </td>
      <td style="text-align:left"><code>Object</code></td>
      <td style="text-align:left"><code>Ei</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>url</b></td>
      <td style="text-align:left">Teenuse URL.<br>
      <b>Näide:</b><code>vk.com</code><br>
      <b>See url peab vastama veebilehe url-ile, sest selle järgi tuvastatakse, kuhu see veebileht kuhu skripti süstida või mitte. Seda võib kasutada ainult array-na, kui on rohkem kui üks url.</b></td>
      <td style="text-align:left"><code>String, Array&lt;String&gt;</code></td>
      <td style="text-align:left"><code>Ei</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>regExp</b></td>
      <td style="text-align:left">Regulaaravaldise string, mida kasutatakse urlide sobitamiseks.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Jah</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>version</b></td>
      <td style="text-align:left">Teie presence-i versioon.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Ei</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>logo</b></td>
      <td style="text-align:left">Link teenuse logotüübile.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Ei</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>thumbnail</b></td>
      <td style="text-align:left">Link oma presence-i thumbnailile.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Ei</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>color</b></td>
      <td style="text-align:left">Väärtus <code>#HEX</code>. Soovitame kasutada teenuse põhivärvi, mida teie presence toetab.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Ei</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>category</b></td>
      <td style="text-align:left">Kirjuta silte, need aitavad kasutajatel otsida teie presence-it veebisaidil.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Ei</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>tags</b></td>
      <td style="text-align:left">String, mida kasutatakse presence-i kategooria tähistamiseks.</td>
      <td style="text-align:left"><code>String, Array&lt;String&gt;</code></td>
      <td style="text-align:left"><code>Ei</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>iframe</b></td>
      <td style="text-align:left">Määrab, kas <code>iFrames</code> kasutatakse</td>
      <td style="text-align:left"><code>Boolean</code></td>
      <td style="text-align:left"><code>Jah</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>iFrameRegExp</b></td>
      <td style="text-align:left">Regulaaravaldise selektor, mis valib iframe'id, kuhu süstida.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Jah</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>readLogs</b></td>
      <td style="text-align:left">Määrab, kas laiendus peaks logisid lugema.</td>
      <td style="text-align:left"><code>Boolean</code></td>
      <td style="text-align:left"><code>Jah</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>settings</b></td>
      <td style="text-align:left">Seadete array, mida kasutaja saab muuta</td>
      <td style="text-align:left"><code>Array&lt;Object&gt;</code></td>
      <td style="text-align:left"><code>Jah</code></td>
    </tr>
  </tbody>
</table>

## Regulaaravaldised

Kui soovite õppida regulaaravaldisi, siis siin on mõned veebisaidid.

#### Õppimine

• [Quick Starter Video](https://youtu.be/sXQxhojSdZM) • [RegexOne](https://regexone.com/) • [Regular Expressions Info](https://www.regular-expressions.info/tutorial.html)

#### Testimine

• [Regexr](https://regexr.com/) • [Regex101](https://regex101.com/)

## Presence-i keeled

PreMiD on polüglottne teenus, mis tähendab, et kasutajate ühendamiseks üle maailma on saadaval mitu keelt. Täielik keelte nimekiri on leitav selle [API lõpp-punkti](https://api.premid.app/v2/langFile/list) kaudu. To customize your presence even more, you can allow users to select their presence display language. Vaata [`multiLanguage`](#multilanguage), et saada rohkem teavet.

## Presence-i seaded
Setup interactive settings so users can customize the presence!
```json
"settings": [
  {
    "id": "ID",
    "multiLanguage": true //Vaata https://docs.premid.app/dev/presence/metadata#multilanguage
  },
  {
    "id": "ID",
    "title": "DISPLAY TITLE",
    "icon": "FONTAWESOME IKOON", //Näide "fas fa-info"
    "value": true //Boolean väärtus teeb sellest sisse/välja lüliti, mille väärtus on vaikimisi väärtus.
  },
  {
    "id": "ID",
    "if": {
      "ID": true //Kui mõni muu seadistus on võrdne selle väärtusega (true/false/0/1/etc.), siis näita seda nuppu.
    },
    "title": "DISPLAY TITLE",
    "icon": "FONTAWESOME IKOON",
    "value": "\"%song%\" by %artist%", //Sõnumi sisestamine muudab seadistuse sisendiks, kus saab kasutada kohandatud sisendit.
    "placeholder": "use %song% or %artist%" //Kui sisend on tühi, siis kuvatakse see hallis.
  },
  {
    "id": "ID",
    "title": "DISPLAY TITLE",
    "icon": "FONTAWESOME IKOON",
    "value": 0, //Valikuri vaikeväärtus
    "values": ["1", "2", "etc."] //See teeb seadistuse selektoriks, kus saab valida, millist soovite
  }
]
```

### `multiLanguage`

#### Sissejuhatus

The `multiLanguage` setting is used to allow users to manually select the language they want to presence to be shown in. Selleks on vaja kasutada meie stringe [API](https://api.premid.app/v2/langFile/presence/en)-st, teabe saamiseks stringide lisamise kohta klõpsake [siia](https://docs.premid.app/dev/presence/metadata#adding-new-strings).

#### Seadistamine

Seade `multiLanguage` on erijuhtum, see ei nõua `title` ega `icon` ega `value` ega `values` nagu teised seaded, aga see nõuab, et sa seadistasid mõningaid asju lisaks!

Võtme `multiLanguage` saab määrata järgmiselt:

`true`: kasutage seda, kui kavatsete kasutada ainult `general.json` faili ja `<service>.json` faili [Lokaliseerimise hoidla](https://github.com/PreMiD/Localization/tree/master/src/Presence) stringidest. `string`: [Lokaliseerimise hoidla](https://github.com/PreMiD/Localization/tree/master/src/Presence) sees oleva faili nimi ilma laiendita (.json) (välja arvatud `üldine` fail, kuna see laaditakse alati). Loetletakse ainult nii `general` kui ka sisestatud faili ühised keeled. `Array<String>`: kui kasutate rohkem kui ühte faili [Lokaliseerimise hoidla](https://github.com/PreMiD/Localization/tree/master/src/Presence) sees, saate määrata kõik väärtused ritta (välja arvatud `üldine` fail, kuna see laaditakse alati). Loetletakse ainult kõigi failide ühised keeled.

#### Uute stringide lisamine

**Note:** Adding custom strings for a presence is only allowed if it has more than 1000 users.

##### Projekti kloonimine

1. Avage terminal ja kirjutage `git clone https://github.com/PreMiD/Localization`.
2. Valige enda valikul kaust.
3. Avage see oma koodiredaktoris.

##### Faili loomine

1. Mine kausta `src`.
2. Mine kausta `Presence`.
3. Tee fail nimega `<service>.json`. (Service on **nimi** (mitte URL), mis on kirjutatud väikse tähtedega ja mida soovite toetada.)

##### Stringide lisamine

Iga `string` on `Objekt`, mille nimest algab teenuse nimi ja seejärel nn stringName, mille vahel on punkt.

StringName on sõnumi 1-sõnaline identifikaator.

`Objektil` on 2 omadust; `sõnum` ja `kirjeldus`. `message` on tekst, mis tuleb tõlkida. `description` on sõnumi kirjeldus, mis aitab meie tõlkijatel mõista, mida nad tõlkivad.

**Märkus:** Ärge lisage duplikaatseid stringisid. (See hõlmab stringid failist `general.json`, kuid mitte muud failid.)

Faili visualiseerimine:

```json
{
  "<service>.<stringName>": {
    "message": "Tõlkimist vajav tekst.",
    "description": "See selgitab, mis on ülaltoodud sõnum."
  },
  "<service>.<stringName>": {
    "message": "Tekst, mis tuleb tõlkida.",
    "description": "See selgitab, mis on ülaltoodud sõnum."
  }
}
```

Pärast seda, kui olete faili täielikult stringidega teinud, saate luua Pull Request'i [Lokaliseerimise hoidlas](https://github.com/PreMiD/Localization), kirjelduses **peate** lisama lingi oma Pull Request'ile presence-ile, mida on uuendatud nende uute stringide abil [Presence Repository](https://github.com/PreMiD/Presences)-is.

#### Vaikimisi võtmed
Klahvid, mida te ei pidanud seadistama, on automaatselt seadistatud järgmiselt: `title`: "Language" **Märkus:** See tõlgitakse nende vaikimisi keelde (brauseri keel). `ikoon`: "fa-language" ([Eelvaade](https://fontawesome.com/icons/language)) `väärtus`: **Määrata oma brauseri keel, kui see on olemas (100% tõlgitud), muidu inglise keel.** `väärtused`: **Määrata olemasolevad keeled (keeled, mis on 100% tõlgitud).**

**Märkus:** Need ei ole kuidagi muudetavad.

### Meetodid

Use the following methods to get settings info in your presence files:
#### `getSetting(String)`
Returns value of setting.
```ts
const setting = await presence.getSetting("pdexID"); //Replace pdexID with the id of the setting
console.log(setting); // This will log the value of the setting
```

#### `hideSetting(String)`
Hides given setting.
```ts
presence.hideSetting("pdexID"); //Replace pdexID with the id of the setting
```

#### `showSetting(String)`
Shows given setting (Only works if the setting was already hidden).
```ts
presence.showSetting("pdexID"); //Replace pdexID with the id of the setting
```

## Presence categories

When making your presence, you must specify a category which the presence falls under. This is a compiled list of the categories that you can use.

<table>
  <thead>
    <tr>
      <th style="text-align:left">Kategooria</th>
      <th style="text-align:left">Nimi</th>
      <th style="text-align:left">Kirjeldus</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>anime</b></td>
      <td style="text-align:left"><b>Anime</b></td>
      <td style="text-align:left">Anything related to anime, from forums to video streaming platforms.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>games</b></td>
      <td style="text-align:left"><b>Mängud</b></td>
      <td style="text-align:left">Any website that has game related content, such as <code>Kahoot</code> or <code>Skribbl.io</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>music</b></td>
      <td style="text-align:left"><b>Muusika</b></td>
      <td style="text-align:left">These are websites that offer music related content, whether that be streaming or downloading.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>socials</b></td>
        <td style="text-align:left"><b>Sotsiaalmeedia</b></td>
      <td style="text-align:left">Websites that are used for the purpose of creating and sharing content or for participating in other forms of social networking.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>videos</b></td>
        <td style="text-align:left"><b>Videod & Otseülekanded</b></td>
      <td style="text-align:left">Websites that serve the purpose of providing videos and streams.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>other</b></td>
      <td style="text-align:left"><b>Muud</b></td>
      <td style="text-align:left">Anything that does not fall under a specific category listed above.</td>
    </tr>
  </tbody>
</table>

