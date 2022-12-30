---
title: Rozwój statusów
description:
published: true
date: 2021-12-20T14:27:18.034Z
tags:
editor: markdown
dateCreated: 2020-06-11T18:04:02.843Z
---

> Wszystkie statusy są trzymane tutaj: https://github.com/PreMiD/Presences 
> 
> {.is-info}

Version `2.x` introduces the [Presence Store](https://premid.app/store). Użytkownicy mają teraz możliwość ręcznego dodawania lub usuwania ich ulubionych statusów za pośrednictwem interfejsu użytkownika z [strony](https://premid.app/).

> Zanim zaczniesz, należy przyjrzeć się naszym wytycznym dotyczącym tworzenia Presence. 
> 
> {.is-warning}

- [Wytyczne](https://docs.premid.app/dev/presence/guidelines)
{.links-list}

# Struktura

All Presences are made using [TypeScript](https://www.typescriptlang.org/). [TypeScript](https://www.typescriptlang.org/) ma kilka dodatkowych definicji nad JavaScriptem, więc naprawianie i identyfikowanie błędów jest o wiele prostsze.

## Wymagania

1. [Git](https://git-scm.com/)
2. Zainstaluj program [Node.js](https://nodejs.org/en/) (instaluje się z [npm](https://www.npmjs.com/)).

## Klonowanie projektu

1. Otwórz terminal i wpisz `git clone https://github.com/PreMiD/Presences`.
2. Wybierz wybrany przez siebie folder.
3. Otwórz go w twoim edytorze kodu.

## Getting started

1. Otwórz nowy terminal w folderze `Presences`
2. Zainstaluj zależności repozytorium używając `npm i` (Lub wybrany menedżer pakietów)

### Creating a Presence
1. Uruchom `npx pmd` (lub uruchamiając `pmd` w wybranym menedżerze pakietów)
2. Wybierz pierwszą opcję
3. Wypełnij wszystkie pytania

### Kompilacja / Modyfikacja obecności
1. Uruchom `npx pmd`
2. Wybierz drugą opcję
3. Wpisz nazwę Presence, którą chcesz edytować > Uruchomi wtedy kompilator TypeScript w folderze Presence, od teraz gdy zaczniesz edytować `presence.ts` będzie to automatycznie kompilowane.
{.is-info}

Dla inspiracji lub przykładów na temat struktury kodu Presence zajrzyj do istniejących Presences takich jak 1337x lub 9GAG

Aby uzyskać więcej informacji o klasie `Presence`, kliknij [tutaj](/dev/presence/class).

Od v2.2.0 istnieją Slideshows, pozwala Ci to na wyświetlanie wielu interfejsów `PresenceData` w odstępach czasowych, więcej informacji znajdziesz klikając w klasę `Slideshow` [tutaj](/dev/presence/slideshow).

## Nie można uzyskać pewnych danych?!

Wiele stron używa [iframes](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe) ([Inlineframes](https://en.wikipedia.org/wiki/HTML_element#Frames)). Te tagi html mogą zawierać wiele źródeł, takich jak filmy. Lecz nie są one istotne za każdym razem. Niektóre z nich są ukryte lub po prostu nie są aktywnie wykorzystywane. Sprawdź, czy możesz uzyskać informacje, których potrzebujesz, zanim wykonasz zbędna pracę.

1. Sprawdź je w konsoli przeglądarki (upewnij się, że jesteś na karcie **Elementy**).
2. Szukaj (<kbd>CTRL</kbd>+<kbd>F</kbd> (Windows) albo <kbd>CMD</kbd>+<kbd>F</kbd> (MacOS)).
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

# Kilka pomocnych rzeczy

## Hot-reloading

The website you are developing on is automatically reloading every time you save a file in your folder.

## Debugging

- You can put `console.log("Test");` between your code and see if your browser console gives you that output. If yes then go on and try again after the next function. If not then there is an error above.
- If that doesn't help you either then ask a presence developer on our [Discord server](https://discord.premid.app/) for help.

# Wyjaśnienie plików

- [Presence Class](/dev/presence/class)
- [Slideshow Class](/dev/presence/slideshow)
- [Klasa iFrame](/dev/presence/iframe)
- [Metadata File](/dev/presence/metadata)
- [TypeScript Configuration](/dev/presence/tsconfig ""){.links-list}
