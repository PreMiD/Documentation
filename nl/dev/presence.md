---
title: Presenceontwikkeling
description:
published: true
date: 2021-12-20T14:27:18.034Z
tags:
editor: markdown
dateCreated: 2020-06-11T18:04:02.843Z
---

> Alle presences worden hier opgeslagen: https://github.com/PreMiD/Presences 
> 
> {.is-info}

Versie `2.x` introduceert de [presencebibliotheek](https://premid.app/store). Gebruikers kunnen nu handmatig hun favoriete presences toevoegen en verwijderen via de gebruikersinterface op de [website](https://premid.app/).

> Voordat je aan de slag gaat, is het zeer aan te raden om onze presence richtlijnen te bekijken. 
> 
> {.is-warning}

- [Richtlijnen](https://docs.premid.app/dev/presence/guidelines)
{.links-list}

# Structuur

Alle presences zijn gecodeerd in [TypeScript](https://www.typescriptlang.org/). [TypeScript](https://www.typescriptlang.org/) heeft een paar extra type definities, dus het oplossen en vinden van bugs is veel eenvoudiger.

## Vereisten

1. [Git](https://git-scm.com/)
2. [Node](https://nodejs.org/en/) (komt met [npm](https://www.npmjs.com/))

## Het project klonen

1. Open een terminal en typ `git clone https://github.com/PreMiD/Presences`.
2. Kies een map van je keuze.
3. Open het in je code editor.

## Aan de slag

1. Open een nieuwe terminal in de map `Presences`
2. Install repository dependencies using `npm i` (Or your package manager of choice)

### Creating a Presence
1. Run `npx pmd` (or run `pmd` with the package manager of your choice)
2. Select the first option
3. Fill in all prompted questions

### Compileren / Wijzigen ven een Presence
1. Run `npx pmd`
2. Select the second option
3. Enter the Presence name you want to edit > This will start a TypeScript compiler in that Presence's folder, now when you edit the `presence.ts` it will automatically compile the presence for you.
{.is-info}

For inspiration or examples on how to structure your Presence's code, take a look at existing Presences like 1337x or 9GAG

Voor meer informatie over de `Presence-klas` klik [hier](/dev/presence/class).

Sinds v2.2.0 zijn er nu Slideshows, dit stelt je in staat om meerdere `PresenceData` interfaces op een interval weer te geven, voor meer informatie over de `Slideshow` klasse klik [hier](/dev/presence/slideshow).

## Kan bepaalde data niet krijgen?!

Veel websites gebruiken [iframes](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe) ([Inlineframes](https://en.wikipedia.org/wiki/HTML_element#Frames)). Deze html-tags kunnen meerdere bronnen bevatten, zoals video's. Maar ze zijn niet altijd relevant. Sommige zijn verborgen of worden niet vaak gebruikt. Controleer of je de informatie die je nodig hebt, kan verkrijgen zonder dat je onnodig werk doet.

1. Controleer ze met de console van je browser (zorg dat je op de **Elements**-tab zit).
2. Zoeken (<kbd>CTRL</kbd>+<kbd>F</kbd> (Windows) of <kbd>CMD</kbd>+<kbd>F</kbd> (MacOS)).
3. Voer `document.querySelectorAll("iframe")` uit.

Als je vindt dat je gegevens zich in iFrame bevinden, moet je het volgende doen:

1. Maak een `iframe.ts` bestand aan.
2. Stel iFrame in op `true` in je metadata bestand.
3. Vul je iFrame bestand in.

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

4. Je presence-bestand gegevens laten ontvangen van het iFrame-bestand.

```ts
presence.on("iFrameData", (data) => {
  iFrameVideo = data.video;
  currentTime = data.time;
});
```

**Opmerking:** Dit moet buiten de updateData event worden geplaatst.

# Laden van de presence

1. Open de extensie pop-up in de browser en houd <kbd>Shift</kbd> knop op je toetsenbord ingedrukt.
2. **Laad Presence** verschijnt in de Presence's sectie.
3. Klik erop terwijl je nog steeds de <kbd>Shift</kbd> knop ingedrukt houdt.
4. Selecteer de map /dist van je presence.

# Enkele nuttige dingen

## Hot-herladen

De website waar je mee bezig bent wordt automatisch herladen wanneer je een bestand in je map opslaat.

## Foutopsporing

- Je kunt `console.log("Test");` tussen je code zetten en kijken of je browserconsole je die uitvoer geeft. Zo ja, ga dan verder en probeer het opnieuw na de volgende functie. Zo niet, dan is er een fout hierboven.
- Als dat je ook niet helpt, vraag dan een presence-ontwikkelaar op onze [Discord-server](https://discord.premid.app/) voor hulp.

# Uitleg van bestanden

- [Presence Klasse](/dev/presence/class)
- [Slideshow Klasse](/dev/presence/slideshow)
- [iFrame Klasse](/dev/presence/iframe)
- [Metadata Bestand](/dev/presence/metadata)
- [TypeScript configuratie](/dev/presence/tsconfig ""){.links-list}
