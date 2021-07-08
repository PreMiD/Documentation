---
title: Presence-i arendamine
description:
published: true
date: 2021-07-08T19:12:34.449Z
tags:
editor: markdown
dateCreated: 2020-06-11T18:04:02.843Z
---

> Kõik presence-id on nüüd salvestatud siin: https://github.com/PreMiD/Presences 
> 
> {.is-info}

Versioon `2.x` tutvustab [presence-i poodi](https://premid.app/store). Kasutajatel on nüüd võimalus oma lemmik presence käsitsi lisada ja eemaldada [veebsaidi](https://premid.app/) kasutajaliite kaudu.

> Enne alustamist on tungivalt soovitatav tutvuda meie presence-i juhenditega. 
> 
> {.is-warning}

- [Juhised](https://docs.premid.app/dev/presence/guidelines)
{.links-list}

# Struktuur

Kõik presence-id on kodeeritud [TypeScriptis](https://www.typescriptlang.org/). [TypeScript](https://www.typescriptlang.org/)-il on JavaScripti kohal mõned eriti vürtsikad definitsioonid, nii et vigade parandamine ja tuvastamine on palju lihtsam.

## Paigaldamine

1. Installige [Git](https://git-scm.com/).
2. Installige [Node](https://nodejs.org/en/) (kaasneb [npm](https://www.npmjs.com/)).
3. Installige [TypeScript](https://www.typescriptlang.org/index.html#download-links) (avage terminal ja kirjutage `npm install -g typcript`).

## Projekti kloonimine

1. Avage terminal ja kirjutage `git clone https://github.com/PreMiD/Presences`.
2. Valige teie valikul kaust.
3. Avage see oma koodiredaktoris.

## Kaustade ja failide loomine

1. Minge kausta `websites` ja seejärel minge kausta, kus on soovitud teenuse, mida te toetada tahate **nime** (mitte URL) esimene täht.
2. Looge kaust selle teenuse **nimega**(mitte URL), mida soovite toetada.
3. Looge sees `presence.ts` ja `tsconfig.json` fail.
4. Looge sees kaust nimega `dist`.
5. Looge `metadata.json` fail kausta `dist` sisse.

## Faili tsconfig.json täitmine

Palun sisestage järgmine kood faili `tsconfig.json` sisse.

```typescript
{
  "extends": "../../../tsconfig.json",
  "compilerOptions": {
    "outDir": "./dist/"
  }
}
```

TypeScripti seadistamise kohta lisateabe saamiseks klõpsake [siia](/dev/presence/tsconfig).

## Faili metadata.json täitmine

Laiskade piilumiste jaoks oleme teinud `metadata.json` faililooja [siin](https://eggsy.xyz/projects/premid/mdcreator). Ikka soovitatakse see läbi lugeda, et teaksite, kuidas see töötab.

```json
{
  "$schema": "https://schemas.premid.app/metadata/1.3",
  "author": {
    "name": "KASUTAJA",
    "id": "ID"
  },
  "contributors": [
    {
      "name": "KASUTAJA",
      "id": "ID"
    }
  ],
  "service": "TEENUS",
  "altnames": ["TEENUS"],
  "description": {
    "en": "KIRJELDUS"
  },
  "url": "URL",
  "version": "VERSIOON",
  "logo": "URL",
  "thumbnail": "URL",
  "color": "#HEX000",
  "tags": ["TAG1", "TAG2"],
  "category": "KATEGOORIA",
  "regExp": "REGEXP",
  "iFrameRegExp": "REGEXP",
  "iframe": false,
  "readLogs": false,
  "settings": [
    {
      "id": "ID",
      "multiLanguage": true
    },
    {
      "id": "ID",
      "title": "KUVA PEALKIRI",
      "icon": "FONTAWESOME IKOON",
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

Kopeerige ülaltoodud kood ja pange see oma faili `metadata.json`. Nüüd peate atribuutide väärtusi muutma. Pange tähele, et järgmised atribuudid on valikulised failis `metadata.json`, kui te ei kavatse neid kasutada, peate need eemaldama.

- `contributors`
- `altnames`
- `regExp`
- `iframe`
- `iFrameRegExp`
- `readLogs`
- `settings`

**Mõne väärtuse eelseadistuse täpsustamine:**

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
      <td style="text-align:left">Peaks sisaldama objekti, millel on presence-i arendaja <code>nimi</code> ja <code>id</code>. <code>nimi</code> on teie Discordi kasutajanimi ilma identifikaatorita (#0000). Kasutaja <code>id</code> saab Discordist kopeerida, lubades arendaja
        režiimis ja paremklõpsake oma profiilil.</td>
      <td style="text-align:left"><code>Object</code></td>
      <td style="text-align:left"><code>Ei</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>contributors</b></td>
      <td style="text-align:left">Peaks sisaldama objekti, millel on presence-i arendaja <code>nimi</code> ja <code>id</code>. <code>nimi</code> on teie Discordi kasutajanimi ilma identifikaatorita (#0000). Kasutaja <code>id</code> saab Discordist kopeerida, lubades arendaja
        režiimis ja paremklõpsake oma profiilil.</td>
      <td style="text-align:left"><code>Array&lt;Object&gt;</code></td>
      <td style="text-align:left"><code>Jah</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>service</b></td>
      <td style="text-align:left">Teenuse pealkiri, mida see presence toetab. <br>
      (Peab olema sama nimi, kui kaust, kus kõik asub)</td>
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
      <td style="text-align:left">Väike presence-i kirjeldus. Kui teil pole ideid, võite kasutada teenuse kirjeldust. Teie kirjeldusel peavad olema võtmepaari väärtused, mis tähistavad keelt, ja kirjeldus selles konkreetses keeles. Tehke kirjeldused keeltega, mida <i>tunnete</i>, meie tõlkijad muudavad teie metaandmete faili.</td>
      <td style="text-align:left"><code>Object</code></td>
      <td style="text-align:left"><code>Ei</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>url</b></td>
      <td style="text-align:left">Teenuse URL. <br><b>Näide:</b><code>vk.com</code><br>
      <b> See URL peab vastama veebisaidi URL-ile, sest see tuvastab, kas see on veebisait, kuhu skripti süstida. </b><br><b><b> Ärge</b> lisage<code> https://</code> või<code> http://</code> URL-i sisse ega kaldkriips lõpus:
      <code>https://premid.app/</code> -> <code>premid.app</code><br>
      <b>Märkus</b>: Mõne URL-i domeeni ees võib olla <code>www.</code> või midagi muud. <b>ÄRGE</b> unustage seda lisada!<br>
      Mitu URL-i saate lisada järgmiselt:<br>
      <code>["URL1", "URL2", "JNE"]</code><br>
      Selle ülesande jaoks võite kasutada ka regExpi, tuntud ka kui Regex, mida selgitatakse allpool.</td>
      <td style="text-align:left"><code>String, Array&lt;String&gt;</code></td>
      <td style="text-align:left"><code>Ei</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>regExp</b></td>
      <td style="text-align:left">Tavalise avaldise string, mida kasutatakse URL-ide sobitamiseks.<br>
      RegExp või tuntud ka kui Regex, saab kasutada, kui veebisaidil on mitu alamdomeeni.<br>
      Selleks võite kasutada järgmist regExp-i:<br>
      <code>([a-z0-9] +) [.] domeen [.] TLD"</code><br>
      TLD tähistab tipptaseme domeeni, näiteks: .com .net (kuid ärge sisestage punkti).<br>
      <code>([a-z0-9]+)</code> tähendab kõike vahemikus a kuni z ja vahemikus 0 kuni 9.<br>
      Kiire alustaja saate selle <a href="https://youtu.be/sXQxhojSdZM">video</a> vaatamisega.<br>
      RegExp-i saate testida aadressil <a href="https://regex101.com/">Regex101</a>.</td>
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
      <td style="text-align:left">Link teenuse logole.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Ei</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>thumbnail</b></td>
      <td style="text-align:left">Link sinu presence-i pisipildile.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Ei</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>color</b></td>
      <td style="text-align:left">Väärtus <code>#HEX</code>. Soovitame kasutada teenuse põhivärvi
        mida teie presence toetab.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Ei</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>tags</b></td>
      <td style="text-align:left">Kirjuta silte, need aitavad kasutajatel otsida teie presence-it veebisaidil.</td>
      <td style="text-align:left"><code>String, Array&lt;String&gt;</code></td>
      <td style="text-align:left"><code>Ei</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>category</b></td>
      <td style="text-align:left">String, mida kasutatakse presence-i kategooria tähistamiseks. Vaadake kehtivaid kategooriaid <a href="https://docs.premid.app/dev/presence/metadata#presence-categories">siit</a>.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Ei</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>iframe</b></td>
      <td style="text-align:left">Määrab, kas <code>iFrames</code> kasutatakse.</td>
      <td style="text-align:left"><code>Boolean</code></td>
      <td style="text-align:left"><code>Jah</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>iFrameRegExp</b></td>
      <td style="text-align:left">Regulaaravaldise valija, mis valib sisestatavad iframe-id. Lisateavet leiate regExp-ist.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Jah</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>readLogs</b></td>
      <td style="text-align:left">Määrab, kas laiendus peaks logisid lugema.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Jah</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>settings</b></td>
      <td style="text-align:left">Seadete valik, mida kasutaja saab muuta.<br>
      Lisateavet presence-i kohta leiate <a href="https://docs.premid.app/dev/presence/metadata#presence-settings">siit</a>.</td>
      <td style="text-align:left"><code>Array&lt;Object&gt;</code></td>
      <td style="text-align:left"><code>Jah</code></td>
    </tr>
  </tbody>
</table>

## Alustamine

```typescript
const kohalolek = uus Presence({
    clientId: "00000000000000000000" //Rakenduse kliendi ID, mis on loodud aadressil https://discordapp.com/developers/applications
  }),
  stringid = presence.getStrings ({
    esitus: "presence. taasesitus. mängimine",
    paus: "presence.playback.paused"
    //Selle abil saate tõlkida stringe nende brauseri keeles
  });

/ *

function myOutsideHeavyLiftingFunction(){
    //Haarake ja töötlege siin kõik oma andmed

    // element haarab //
    // api kõned //
    // muutujad //
}

setInterval(myOutsideHeavyLiftingFunction, 10000);
// Käivitage funktsioon iga 10 sekundi tagant UpdateData sündmusest eraldi, et saada ja määrata muutujad, mille UpdateData korjab

*/

presence.on("UpdateData", async () = > {
  /*UpdateData käivitub alati ja seetõttu tuleks seda kasutada värskendustsüklina ehk linnukena. Seda nimetatakse võimaluse korral mitu korda sekundis.

    Soovitatav on seada väljaspool seda sündmuse funktsiooni veel üks funktsioon, mis muudab muutujate väärtusi ja teeb tugeva tõste, kui helistate andmeid API-lt.*/

  const presenceData: presenciteave = {
    largeImageKey:
      "key"/*Suure pildi võti (faili nimi) presence. Need laaditakse üles ja nimetatakse teie rakenduse jaotises Rich Presence nimega Kunstivarad*/,
    smallImageKey:
      "key"/*Presence-i juures oleva väikese pildi võti (faili nimi). Need laaditakse üles ja nimetatakse teie rakenduse jaotises Rikas Presence nimega Kunstivarad*/,
    smallImageText: "Mõned hõljutavad tekstid", //Tekst, mis kuvatakse väikese pildi kohal hõljutades
    details: "Lehe nime sirvimine", //Presence-i teksti ülemine osa
    state: "Jao A lugemine", //Presence-i teksti alumine osa
    startTimestamp: 1577232000, //Unixi ajastu ajatempel, millal loendamist alustada
    endTimestamp: 1577151472000 //Kui soovite kuvada möödunud aja asemel vasakule jääva aja, siis see on unixi ajastu ajatempel, mille abil taimer lõpeb
  }; /*Soovi korral saate siin määrata suurPiltVõti ja muuta ülejäänud muutuvate alamomadustena, näiteks presenceSata.type = "blahblah"; tüübinäited: üksikasjad, olek jne*/

  kui (presenceData.details == null) {
    //See käivitub, kui te ei määra presence-i üksikasju
    presence.setTrayTiitle (); //Kustutab salve pealkirja mac-kasutajatele
    presence.setAktiivsus (); /*Uuendage presence-i ilma andmeteta, kustutades selle ja muutes suureks pildiks Discordi rakenduse ikooni ja teksti Discordi rakenduse nimeks*/
  } muu {
    //See käivitub, kui määrate presence-i üksikasjad
    presence.setActivity (presenceData); //Värskendage presence kõigi presenceData objekti väärtustega
  }
});
```

Saate selle kopeerida oma faili `presence.ts` ja redigeerida väärtusi. Kõigi väärtuste seadistamine toimub updataData sündmuse sees.

Näidete jaoks soovitame vaadata presence-i koodi nagu: 1337x või 9GAG. Klass `Presence` kohta lisateabe saamiseks klõpsake [siia](/dev/presence/class).

Kuna v2.2.0 on nüüd slaidiseansse, võimaldab see teil intervalliga näidata mitut liidest `PresenceData`, lisateabe saamiseks klõpsake `Slideshow` klassi [siin](/dev/presence/slideshow).

## Kas te ei saa kindlaid andmeid?!

Paljud veebisaidid kasutavad [iframe'i](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe) ([Inlineframes](https://en.wikipedia.org/wiki/HTML_element#Frames)). Need Html-märgendid võivad sisaldada mitut allikat, näiteks videoid. Kuid need pole iga kord asjakohased. Mõned on peidetud või neid ei kasutata lihtsalt aktiivselt. Enne tarbetu töö tegemist kontrollige, kas saate vajaliku teabe ilma nendeta välja võtta.

1. Otsige neid oma brauserikonsoolist (veenduge, et olete vahekaardil **Elements**).
2. Otsing (<kbd>CTRL</kbd>+<kbd>F</kbd> (Windows) või <kbd>CMD</kbd>+<kbd>F</kbd> (MacOS)).
3. Käivitage `document.querySelectorAll("iframe")`.

Kui leiate, et teie andmed on iFrame-is, peate tegema järgmist:

1. Looge `iframe.ts` fail.
2. Määrake oma metaandmete failis iFrame väärtuseks `true`.
3. Täitke oma iFrame-i fail.

```typescript
const iframe = new iFrame();
iframe.on("UpdateData", async () = > {
  /*
  Hankige iFrame'ist kõik vajalikud andmed, salvestage need muutujatesse
  ja saatke need siis iframe.send abil
  */
  iframe.send ({
    //andmete saatmine
    video: video,
    aeg: video.duration
  });
});
```

4. Presence-i faili andmete vastuvõtmine iFrame failist.

```typescript
presence.on("iFrameData", (data) => {
  iFrameVideo = data.video;
  currentTime = data.time;
});
```

**Märkus:** See tuleb asetada väljaspool sündmust updateData.

## Kompileerimine

Avage kaustas konsool ja kirjutage `tsc -w`, et kompileerida `presence.ts` kausta `/dist`.

# Presence-i laadimine

1. Avage brauseris laienduse hüpikaken ja hoidke klaviatuuri nuppu <kbd>Shift</kbd>.
2. **Load Presence** kuvatakse jaotises Presences.
3. Klõpsake seda, kui hoiate endiselt nuppu <kbd>Shift</kbd>.
4. Valige oma presence-i kaust /dist.

# Mõned kasulikud asjad

## Kuum laadimine

Veebisait, millel arendate, laaditakse automaatselt uuesti iga kord, kui fail kausta salvestatakse.

## Veakõrvaldus

- Võite koodi `console.log("Test");` panna oma koodi vahele ja vaadata, kas teie brauserikonsool annab teile selle väljundi. Kui jah, siis jätkake ja proovige pärast järgmist funktsiooni uuesti. Kui ei, siis on üleval viga.
- Kui see teid ka ei aita, küsige abi meie [Discord serverist](https://discord.premid.app/) Presence-i arendajalt.

# Toimikud selgitatud

- [Presence-i klass](/dev/presence/class)
- [Slaidiseansi klass](/dev/presence/slideshow)
- [iFrame'i klass](/dev/presence/iframe)
- [Metaandmete fail](/dev/presence/metadata)
- [TypeScripti seadistamine](/dev/presence/tsconfig ""){.links-list}
