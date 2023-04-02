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

Kui soovid avaldata presence-it poes ja laadida seda laienduse kaudu, tuleb luua `metadata.json` fail oma `dist` kausta.

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
      <th style="text-align:left">Muutuja</th>
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
      <td style="text-align:left">Selle teenuse pealkiri, mida see presence toetab.</td>
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
      <td style="text-align:left">Teenuse kirjeldus <b>MITTE</b> presence-i. Teie kirjeldusel peavad olema võtmepaari väärtused, mis näitavad keelt ja kirjeldust selles konkreetses keeles. Tehke kirjeldused keeltega, <i>mis te oskate</i>, meie tõlkijad teevad muudatused teie metaandmefaili. Vaadake presence-i keelte kategooriat, et saada nimekiri. </td>
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

PreMiD on polüglottne teenus, mis tähendab, et kasutajate ühendamiseks üle maailma on saadaval mitu keelt. Täielik keelte nimekiri on leitav selle [API lõpp-punkti](https://api.premid.app/v2/langFile/list) kaudu. Kui soovite oma presence-it veelgi rohkem kohandada, saate lubada kasutajatel valida oma presence-i kuvamise keele. Vaata [`multiLanguage`](#multilanguage), et saada rohkem teavet.

## Presence-i seaded
Seadistage interaktiivsed seaded, et kasutajad saaksid presence-it kohandada!
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

Seade `multiLanguage` võimaldab kasutajatel käsitsi valida keele, milles nad soovivad, et presence näidataks. Selleks on vaja kasutada meie stringe [API](https://api.premid.app/v2/langFile/presence/en)-st, teabe saamiseks stringide lisamise kohta klõpsake [siia](https://docs.premid.app/dev/presence/metadata#adding-new-strings).

#### Seadistamine

Seade `multiLanguage` on erijuhtum, see ei nõua `title` ega `icon` ega `value` ega `values` nagu teised seaded, aga see nõuab, et sa seadistasid mõningaid asju lisaks!

Võtme `multiLanguage` saab määrata järgmiselt:

`true`: kasutage seda, kui kavatsete kasutada ainult `general.json` faili ja `<service>.json` faili [Lokaliseerimise hoidla](https://github.com/PreMiD/Localization/tree/master/src/Presence) stringidest. `string`: [Lokaliseerimise hoidla](https://github.com/PreMiD/Localization/tree/master/src/Presence) sees oleva faili nimi ilma laiendita (.json) (välja arvatud `üldine` fail, kuna see laaditakse alati). Loetletakse ainult nii `general` kui ka sisestatud faili ühised keeled. `Array<String>`: kui kasutate rohkem kui ühte faili [Lokaliseerimise hoidla](https://github.com/PreMiD/Localization/tree/master/src/Presence) sees, saate määrata kõik väärtused ritta (välja arvatud `üldine` fail, kuna see laaditakse alati). Loetletakse ainult kõigi failide ühised keeled.

#### Uute stringide lisamine

**Märkus:** Kohandatud stringide lisamine on lubatud ainult siis, kui presence-il on rohkem kui 1000 kasutajat.

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

Kasutage järgmisi meetodeid, et saada seadete teavet oma presence-i failide kohta:
#### `getSetting(String)`
Tagastab seadistuse väärtuse.
```ts
const setting = await presence.getSetting("pdexID"); //Asenda pdexID seadistuse id-ga.
console.log(setting); // See logib seadistuse väärtuse
```

#### `hideSetting(String)`
Peidab antud seadistuse.
```ts
presence.hideSetting("pdexID"); //Asenda pdexID seadistuse id-ga
```

#### `showSetting(String)`
Näitab antud seadistust (töötab ainult siis, kui seade oli juba peidetud).
```ts
presence.showSetting("pdexID"); //Asenda pdexID seadistuse id-ga
```

## Presence-i kategooriad

Presence-i tegemisel peate määrama kategooria, mille alla presence kuulub. See on koostatud loetelu kategooriatest, mida saate kasutada.

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
      <td style="text-align:left">Kõik, mis on seotud animega, alates foorumitest kuni video voogedastusplatvormideni.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>games</b></td>
      <td style="text-align:left"><b>Mängud</b></td>
      <td style="text-align:left">Mis tahes veebisait, millel on mänguga seotud sisu, näiteks <code>Kahoot</code> või <code>Skribbl.io</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>music</b></td>
      <td style="text-align:left"><b>Muusika</b></td>
      <td style="text-align:left">Need on veebisaidid, mis pakuvad muusikaga seotud sisu, olgu see siis voogedastus või allalaadimine.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>socials</b></td>
        <td style="text-align:left"><b>Sotsiaalmeedia</b></td>
      <td style="text-align:left">Veebilehed, mida kasutatakse sisu loomiseks ja jagamiseks või muudes suhtlusvõrgustikes osalemiseks.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>videos</b></td>
        <td style="text-align:left"><b>Videod & Otseülekanded</b></td>
      <td style="text-align:left">Veebilehed, mille eesmärk on pakkuda videoid ja voogedastusi.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>other</b></td>
      <td style="text-align:left"><b>Muud</b></td>
      <td style="text-align:left">Kõik, mis ei kuulu eespool loetletud konkreetsesse kategooriasse.</td>
    </tr>
  </tbody>
</table>

