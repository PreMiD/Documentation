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

Since v2.2.0 there are now Slideshows, this allows you to show multiple `PresenceData` interfaces on an interval, for more information click about the `Slideshow` class [here](/dev/presence/slideshow).

## Can't get certain data?!

A lot of websites are using [iframes](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe) ([Inlineframes](https://en.wikipedia.org/wiki/HTML_element#Frames)). These html tags can contain multiple sources such as videos. But they're not relevant every time. Some are hidden or just not actively used. Check if you can extract the information you need without them before you do unnecessary work.

1. Check for them in your browsers console (be sure that you are on the **Elements** tab).
2. Search (<kbd>CTRL</kbd>+<kbd>F</kbd> (Windows) or <kbd>CMD</kbd>+<kbd>F</kbd> (MacOS)).
3. Execute `document.querySelectorAll("iframe")`.

If you find that your data is in a iFrame you need to do the following:

1. Create a `iframe.ts` file.
2. Set iFrame to `true` in your metadata file.
3. Filling in your iFrame file.

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

4. Making your presence file receive data from the iFrame file.

```ts
presence.on("iFrameData", (data) => {
  iFrameVideo = data.video;
  currentTime = data.time;
});
```

**Note:** This needs to be placed outside of the updateData event.

# Loading your Presence

1. Open the extension popup in the browser and hold the <kbd>Shift</kbd> button on your keyboard.
2. **Load Presence** will appear in the Presences section.
3. Click on it while you are still holding the <kbd>Shift</kbd> button.
4. Select the /dist folder of your presence.

# Mõned kasulikud asjad

## Hot-reloading

The website you are developing on is automatically reloading every time you save a file in your folder.

## Debugging

- You can put `console.log("Test");` between your code and see if your browser console gives you that output. If yes then go on and try again after the next function. If not then there is an error above.
- If that doesn't help you either then ask a presence developer on our [Discord server](https://discord.premid.app/) for help.

# Toimikud selgitatud

- [Presence Class](/dev/presence/class)
- [Slideshow Class](/dev/presence/slideshow)
- [iFrame Class](/dev/presence/iframe)
- [Metadata File](/dev/presence/metadata)
- [TypeScript Configuration](/dev/presence/tsconfig ""){.links-list}
