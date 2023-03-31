---
title: Presence-i arendamine
description:
published: true
date: 2021-12-20T14:27:18.034Z
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

## Nõuded

1. [Git](https://git-scm.com/)
2. Paigaldage [Node](https://nodejs.org/en/) (kaasneb [npm](https://www.npmjs.com/))

## Projekti kloonimine

1. Avage terminal ja kirjutage `git clone https://github.com/PreMiD/Presences`.
2. Valige teie valikul kaust.
3. Avage see oma koodiredaktoris.

## Alustamine

1. Avage uus terminal kaustas `Presences`
2. Paigalda repositooriumi sõltuvused, kasutades `npm i` (või oma valitud paketihaldurit)

### Presence-i loomine
1. Käivitage `npx pmd` (või käivitage `pmd` oma valitud paketihalduriga)
2. Valige esimene valik
3. Täitke kõik küsitud küsimused

### Presence-i koostamine/muutmine
1. Käivita `npx pmd`
2. Valige teine valik
3. Sisestage Presence-i nimi, mida soovite muuta > See käivitab TypeScripti kompilaatori selles Presence'i kaustas, nüüd, kui te redigeerite `presence.ts`, kompileerib see automaatselt presence'i teie eest.
{.is-info}

Inspiratsiooni või näiteid selle kohta, kuidas oma Presence-i koodi struktureerida, leiate olemasolevatest Presence-itest, nagu 1337x või 9GAG

Lisateavet klassi `Presence` kohta leiate [siit](/dev/presence/class).

Alates v2.2.0 on nüüd olemas Slideshow'd, see võimaldab teil näidata mitu `PresenceData` liidest intervalliga, lisateabe saamiseks klõpsake klassi `Slideshow` kohta [siit](/dev/presence/slideshow).

## Teatud andmeid ei saa?!

Paljud veebisaidid kasutavad [ifraame](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe) ([Inlineframe](https://en.wikipedia.org/wiki/HTML_element#Frames)). Need html-tähed võivad sisaldada mitmeid allikaid, näiteks videoid. Kuid need ei ole iga kord asjakohased. Mõned neist on peidetud või neid lihtsalt ei kasutata aktiivselt. Kontrollige, kas saate vajaliku teabe kätte ilma nendeta, enne kui teete asjatut tööd.

1. Kontrollige neid oma brauseri konsoolist (veenduge, et olete **Elemendid** vahekaardil).
2. Otsi (<kbd>CTRL</kbd>+<kbd>F</kbd> (Windows) või <kbd>CMD</kbd>+<kbd>F</kbd> (MacOS)).
3. Käivita `document.querySelectorAll("iframe")`.

Kui leiate, et teie andmed on iFrame'is, peate tegema järgmist:

1. Loo fail `iframe.ts`.
2. Määra iFrame'ile oma metaandmefailis väärtuseks `true`.
3. Täitke oma iFrame-i fail.

```ts
const iframe = new iFrame();
iframe.on("UpdateData", async () => {
  //Get all the data you need out of the iFrame save them in variables and then send them using iframe.send
  iframe.send({
    //sending data
    video: video,
    time: video.duration
  });
});
```

4. Presence-i faili andmete vastuvõtmine iFrame failist.

```ts
presence.on("iFrameData", (data) => {
  iFrameVideo = data.video;
  currentTime = data.time;
});
```

**Märkus:** See tuleb asetada väljaspool sündmust updateData.

# Presence-i laadimine

1. Avage brauseris laienduse hüpikaken ja hoidke klaviatuuri nuppu <kbd>Shift</kbd>.
2. **Load Presence** kuvatakse jaotises Presences.
3. Klõpsake seda, kui hoiate endiselt nuppu <kbd>Shift</kbd>.
4. Valige oma presence-i kausta /dist.

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
