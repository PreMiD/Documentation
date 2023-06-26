---
title: Dezvoltator Prezență
description:
published: true
date: 2021-12-20T14:27:18.034Z
tags:
editor: markdown
dateCreated: 2020-06-11T18:04:02.843Z
---

> Toate prezențele sunt acum stocate aici: https://github.com/PreMiD/Presences 
> 
> {.is-info}

Versiunea `2.x` introduce [magazin de prezență](https://premid.app/store). Utilizatorii au acum capacitatea de a adăuga și elimina manual prezența lor preferată prin interfața de utilizator a [site-ului web](https://premid.app/).

> Înainte de a începe, este foarte recomandat să vă uitați la regulile noastre de prezență. 
> 
> {.is-warning}

- [Instrucțiuni](https://docs.premid.app/dev/presence/guidelines)
{.links-list}

# Structură

Toate prezența sunt codificate în [TypeScript](https://www.typescriptlang.org/). [TypeScript](https://www.typescriptlang.org/) are câteva definiții de tip extra picante față de JavaScript, așa că repararea și identificarea erorilor este mult mai ușoară.

## Cerințe

1. [Git](https://git-scm.com/)
2. [Node](https://nodejs.org/en/) (vine cu [npm](https://www.npmjs.com/))

## Clonarea proiectului

1. Deschideți un terminal și tastați `git clone https://github.com/PreMiD/Presences`.
2. Alegeți un folder la alegere.
3. Deschideți-l în editorul de cod.

## Pentru a începe

1. Open a new terminal in the `Presences` folder
2. Install repository dependencies using `npm i` (Or your package manager of choice)

### Creating a Presence
1. Run `npx pmd` (or run `pmd` with the package manager of your choice)
2. Select the first option
3. Fill in all prompted questions

### Compiling / Modifying a Presence
1. Run `npx pmd`
2. Select the second option
3. Enter the Presence name you want to edit > This will start a TypeScript compiler in that Presence's folder, now when you edit the `presence.ts` it will automatically compile the presence for you.
{.is-info}

For inspiration or examples on how to structure your Presence's code, take a look at existing Presences like 1337x or 9GAG

For more information about the `Presence` class click [here](/dev/presence/class).

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

**Notă:** Acesta trebuie să fie plasat în afara evenimentului updateData.

# Încărcarea prezenței

1. Deschideți extensia popup în motorul de căutare și țineți apăsat butonul <kbd>Shift</kbd> butonul de pe tastatură.
2. **Încărcarea prezenței** va apărea în secțiunea Prezențe.
3. Faceți click pe el în timp ce încă țineți mâna pe butonul <kbd>Shift</kbd>.
4. Selectați folderul /dist al prezenței dumneavoastră.

# Câteva sfaturi ajutătoare

## Hot-reloading

Site-ul web pe care vă dezvoltați se reîncarcă automat de fiecare dată când salvați un fișier în folderul dumneavoastră.

## Depanare

- Poți să pui `console.log("Test");` între codul dumneavoastră și vedeți dacă consola motorului de căutare vă oferă acea ieșire. Dacă da, continuați și încercați din nou după următoarea funcție. Dacă nu, atunci există o eroare mai sus.
- Dacă acest lucru nu te ajută fie să întrebi un dezvoltator de prezență pe serverul nostru [Discord server](https://discord.premid.app/) pentru ajutor.

# Explicația Fișierelor

- [Clasă prezență](/dev/presence/class)
- [Slideshow Class](/dev/presence/slideshow)
- [Clasă iFrame](/dev/presence/iframe)
- [Fișier Metadata](/dev/presence/metadata)
- [Configurare TypeScript](/dev/presence/tsconfig ""){.links-list}
