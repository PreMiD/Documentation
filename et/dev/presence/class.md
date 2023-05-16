---
title: Presence-i klass
description: Iga PreMiD-i presence-i põhiklass
published: true
date: 2022-05-26T18:03:00.000Z
tags:
editor: markdown
dateCreated: 2021-09-07T01:44:50.164Z
---

# Presence-i klass

## Sissejuhatus

Klass `Presence` on väga kasulik, sest sellel on põhilised meetodid, mida me vajame presence-i loomiseks.

Klassi loomisel tuleb määrata `clientId` omadus.

```ts
const presence = new Presence({
  clientId: "514271496134389561" // Näide clientId
});
```

### Omadused

Klassil `Presence` on kolm omadust.

#### `clientId`

See omadus on vajalik, et teie presence toimiks, sest see kasutab teie rakenduse id-d oma logo ja varade kuvamiseks. Selle saate oma [rakenduste lehel](https://discordapp.com/developers/applications).

#### `injectOnComplete` - *Vähendatud alates 2.2.4*

Kui määrata `injectOnComplete` väärtuseks `true`, käivitub esimene `UpdateData` sündmus nii `presence.ts` kui ka `iframe.ts` failide puhul alles siis, kui leht on täielikult laetud.

#### `appMode` - *Välistatud alates 2.2.4*

Kui seadistada `appMode` väärtuseks `true` ja kui presence peaks saatma tühja `PresenceData`, näitab rakendus rakenduse (pilt ja nimi) kasutaja profiilil, mitte midagi asemel.

## Meetodid

### `getActivity()` - *Välistatud alates 2.2.4*

Tagastab `PresenceData` objekti selle kohta, mida presence kuvab.

### `setActivity(PresenceData | Slideshow, Boolean)`

Seadistab teie profiili aktiivsuse vastavalt esitatud andmetele.

Esimene parameeter nõuab [`PresenceData`](#presencedata-interface) liidest või [`Slideshow`](/dev/presence/slideshow) klassi, et saada kogu teave, mida soovite oma profiilis kuvada.

Teine parameeter määrab, kas presence mängib midagi või mitte. Kasutage alati `true`, kui esitate ajatempleid `PresenceData`-s.

### `clearActivity()`

Tühjendab teie praeguse tegevuse ja salve pealkirja.

### `setTrayTitle(String)` - *Välistatud alates 2.2.3*

> See meetod töötab ainult Mac OS-is. 
> 
> {.is-warning}

Määrab Menubar salve pealkirja.

### `createSlideshow()`

Loob uue `Slideshow` klassi.

```ts
const slideshow = presence.createSlideshow();
```

Seda soovitatakse teha kohe pärast klassi `Presence` loomist:

```ts
const presence = new Presence({
    clientId: "514271496134389561" // Näide clientId
  }),
  slideshow = presence.createSlideshow();
```

Klassi `Slideshow` dokumentatsiooni leiate [siit](/dev/presence/slideshow).

### `getStrings(Object)`

Asünkroonne meetod, mis võimaldab saada tõlgitud stringid laiendusest.

Sa pead esitama `Object`, kusjuures võtmed on stringi võti, `keyValue` on stringi väärtus. Tõlgitud stringide nimekiri on leitav sellest lõpp-punktist: `https://api.premid.app/v2/langFile/presence/en/`

```ts
// Tagastab stringid `Playing` ja `Paused`
// laiendusest.
const strings = await presence.getStrings({
  play: "general.playing",
  pause: "general.paused"
});

const playString = strings.play; // tulemus: Playing
const pauseString = strings.pause; // tulemus: Paused
```

Alates laienduse v2.2.0 versioonist saate nüüd teatud keele stringid kätte. See töötab hästi koos samuti äsja lisatud `multiLanguage` seadistusvõimalusega.

Soovitame kasutada järgmist koodi, et see uuendaks automaatselt PresenceData, kui kasutaja muudab valitud keelt;

```ts
async function getStrings() {
  return presence.getStrings(
    {
      play: "general.playing",
      pause: "general.paused"
    },
    // ID on multiLanguage-i seadistuse ID.
    await presence.getSetting("ID").catch(() => "en");
  );
}

let strings = getStrings(),
  // ID on multiLanguage-i seadistuse ID.
  oldLang: string = await presence.getSetting("ID").catch(() => "en");

//! Järgmine kood peab olema updateData sündmuse sees!
// The ID is the ID of the multiLanguage setting.
const newLang = await presence.getSetting("ID").catch(() => "en");
if (oldLang !== newLang) {
  oldLang = newLang;
  strings = getStrings();
}

const playString = (await strings).play, // tulemus: Playing
  pauseString = (await strings).pause; // tulemus: Paused
```

### `getPageletiable(String)`

Tagastab veebilehe muutuja, kui see on olemas.

**Hoiatus: See funktsioon võib põhjustada suurt protsessorikasutust & saidi mahajäämus, kui seda on teostatud liiga palju kordi.**

```ts
const pageVar = presence.getPageletiable("pageVar");
console.log(pageVar); // See logib "Muutuva sisu"
```

### `getExtensionVersion(Boolean)`

Tagastab kasutaja kasutatava laienduse versiooni.

```ts
getExtensionVersion(onlyNumeric?: boolean): string | number;

const numeric = presence.getExtensionVersion();
console.log(numeric); // Logib 210
const version = presence.getExtensionVersion(false);
console.log(version); // Logib 2.1.0
```

### `getSetting(String)`

Tagastab sätte väärtuse.

```ts
const setting = await presence.getSetting("pdexID"); //Asenda pdexID seadistuse id-ga.
console.log(setting); // See logib seadistuse väärtuse
```

### `hideSetting(String)`

Peidab antud sätte.

```ts
presence.hideSetting("pdexID"); // Asendab pdexID seadistuse id-ga
```

### `showSetting(String)`

Näitab antud seadistust (Töötab ainult siis, kui seade oli juba peidetud).

```ts
presence.showSetting("pdexID"); // Asendab pdexID seadistuse id-ga
```

### `getLogs()`

Tagastab veebisaitide konsooli logid.

```ts
const logs = await presence.getLogs();
console.log(logs); // See logib viimased 100 logi (reas).
```

**Märkus:** Nõuab, et `readLogs` oleks `true` failis `metadata.json`.

### `info(String)`

Trükib antud teate konsoolis presence-i formaadis, mis põhineb `info` stiilil.

```ts
presence.info("Test") // See logib "test" õiges stiilis.
```

### `success(String)`

Trükib antud teate konsoolis presence-i formaadis, mis põhineb `success` stiilil.

```ts
presence.success("Test") // See logib "test" õiges stiilis.
```

### `error(String)`

Trükib antud teate konsoolis presence-i formaadis, mis põhineb `error` stiilil.

```ts
presence.error("Test") // See logib "test" õiges stiilis.
```

### `getTimestampsfromMedia(HTMLMediaElement)`

Tagastab 2 `snowflake` ajatemplit `Array`-na, mida saab kasutada `startTimestamp` ja `endTimestamp` jaoks.

```ts
const timestamps = presence.getTimestampsfromMedia(document.querySelector(".video"));
presenceData.startTimestamp = timestamps[0];
presenceData.endTimestamp = timestamps[1];
```

**Märkus:** Antud `String` querySelector-is on näide.

### `getTimestamps(Number, Number)`

Tagastab 2 `snowflake` ajatemplit `Array`-na, mida saab kasutada `startTimestamp` ja `endTimestamp` jaoks.

```ts
const video = document.querySelector(".video"),
  timestamps = presence.getTimestamps(video.currentTime, video.duration);
presenceData.startTimestamp = timestamps[0];
presenceData.endTimestamp = timestamps[1];
```

**Märkus:** Antud `String` querySelector-is on näide.

### `timestampFromFormat(String)`

Teisendab stringi formaadiga `HH:MM:SS` või `MM:SS` või `SS` täisarvuks (ei tagasta snowflake ajatemplit).

```ts
const currentTime = presence.timestampFromFormat(document.querySelector(".video-now").textContent),
  duration = presence.timestampFromFormat(document.querySelector(".video-end").textContent),
  timestamps = presence.getTimestamps(currentTime, duration);
presenceData.startTimestamp = timestamps[0];
presenceData.endTimestamp = timestamps[1];
```

**Märkus:** Antud `String` querySelector-is on näide.

## `PresenceData` Liides

`PresenceData` liideset on soovitatav kasutada, kui kasutate `setActivity()` meetodit.

Sellel liidesel on järgmised muutujad, mis kõik on valikulised.

<table>
  <thead>
    <tr>
      <th style="text-align:left">Muutuja</th>
      <th style="text-align:left">Kirjeldus</th>
      <th style="text-align:left">Tüüp</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">details</td>
      <td style="text-align:left">Esimene rida teie presence-is, mida tavaliselt kasutatakse pealkirjana.</td>
      <td style="text-align:left"><code>String</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">state</td>
      <td style="text-align:left">Teine rida teie presence-is.</td>
      <td style="text-align:left"><code>String</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">startTimestamp</td>
      <td style="text-align:left">Määratleb praeguse aja.<br>
        Kasutatakse, kui soovite kuvada, mitu <code>tundi:minutit:sekundit</code> on jäänud.
          <br>Sa pead oma aja teisendama <code>timestamp</code>-iks või sa saad vale
          tagasiarvestuse.
      </td>
      <td style="text-align:left"><code>Number</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">endTimestamp</td>
      <td style="text-align:left">Määrab kogu kestuse.
        <br>Kasutatakse, kui soovite kuvada, mitu <code>tundi:minutit:sekundit</code> on jäänud.
          <br>Sa pead oma aja teisendama <code>timestamp</code>-iks või sa saad vale
          tagasiarvestuse.
      </td>
      <td style="text-align:left"><code>Number</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">largeImageKey</td>
      <td style="text-align:left">Määrab presence-i logo.</td>
      <td style="text-align:left"><code>String</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">smallImageKey</td>
      <td style="text-align:left">Määratleb väikese ikooni presence-i logo kõrval.</td>
      <td style="text-align:left"><code>String</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">smallImageText</td>
      <td style="text-align:left">Määrab teksti, mida näidatakse kasutajale, kui ta viib hiire üle väikse
        ikooni.</td>
      <td style="text-align:left"><code>String</code>
      </td>
    </tr>
        <tr>
      <td style="text-align:left">buttons</td>
      <td style="text-align:left">Nuppude array, maksimaalselt 2, label on nupu tekst ja url on link.</td>
      <td style="text-align:left"><code>Array&lt;Object&gt;</code>
      </td>
    </tr>
  </tbody>
</table>

```ts
const enum Assets {
  Logo = ""
}

const presenceData: PresenceData = {
  details: "My title",
  state: "My description",
  largeImageKey: Assets.Logo,
  smallImageKey: Assets.Reading, //Other Assets can be found in index.d.ts
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

## Sündmused

Sündmused võimaldavad tuvastada ja käsitleda mõningaid muudatusi või tehtud kõnesid. Sündmusi saab tellida meetodi `on` abil.

```ts
presence.on("UpdateData", async () => {
  // Teeb midagi, kui andmeid uuendatakse.
});
```

Saadaval on vähe sündmusi:

#### `UpdateData`

See sündmus käivitub iga kord, kui presence-it uuendatakse.

#### `iFrameData`

Käivitub, kui iFrame'i skriptist saadakse andmeid.
