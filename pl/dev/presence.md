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

Wersja `2.x` wprowadza [sklep z aktywnościami Presence](https://premid.app/store). Użytkownicy mają teraz możliwość ręcznego dodawania lub usuwania ich ulubionych statusów za pośrednictwem interfejsu użytkownika z [strony](https://premid.app/).

> Zanim zaczniesz, należy przyjrzeć się naszym wytycznym dotyczącym tworzenia Presence. 
> 
> {.is-warning}

- [Wytyczne](https://docs.premid.app/dev/presence/guidelines)
{.links-list}

# Struktura

Wszystkie statusy są wykonywane za pomocą [TypeScript](https://www.typescriptlang.org/). [TypeScript](https://www.typescriptlang.org/) ma kilka dodatkowych definicji nad JavaScriptem, więc naprawianie i identyfikowanie błędów jest o wiele prostsze.

## Wymagania

1. [Git](https://git-scm.com/)
2. Zainstaluj program [Node.js](https://nodejs.org/en/) (instaluje się z [npm](https://www.npmjs.com/)).

## Klonowanie projektu

1. Otwórz terminal i wpisz `git clone https://github.com/PreMiD/Presences`.
2. Wybierz wybrany przez siebie folder.
3. Otwórz go w twoim edytorze kodu.

## Pierwsze kroki

1. Otwórz nowy terminal w folderze `Presences`
2. Zainstaluj zależności repozytorium używając `npm i` (Lub wybrany menedżer pakietów)

### Tworzenie Presence
1. Run `npx pmd` (or run `pmd` with the package manager of your choice)
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
3. Wykonaj `document.querySelectorAll("iframe")`.

Jeśli okaże się, że Twoje dane znajdują się w ramce iFrame, wykonaj następujące czynności:

1. Stwórz plik `iframe.ts`.
2. Ustaw iFrame na `true` w twoim pliku metadanych.
3. Wypełnianie w twoim pliku iFrame.

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

4. Zrobienie, by plik Statusu odbierał dane z pliku iFrame.

```ts
presence.on("iFrameData", (data) => {
  iFrameVideo = data.video;
  currentTime = data.time;
});
```

**Uwaga:** To musi być umieszczone poza zdarzeniem updateData.

# Ładowanie Presence

1. Otwórz okno rozszerzenia i przytrzymaj klawisz <kbd>Shift</kbd> na twojej klawiaturze.
2. **Load Presence** pojawi się w sekcji Presences.
3. Kliknij to, cały czas przytrzymując klawisz <kbd>Shift</kbd>.
4. Wybierz folder /dist z swojego presence.

# Kilka pomocnych rzeczy

## Szybkie odświeżanie

Strona, którą tworzysz, jest automatycznie odświeżana za każdym razem, gdy zapiszesz plik w folderze.

## Debugowanie

- Możesz umieścić `console.log("Test");` między swoim kodem i zobaczyć czy w konsoli w przeglądarce zwraca Ci taki wynik. Jeżeli tak, kontynuuj i spróbuj ponownie po następnej funkcji. Jeśli nie, oznacza to błąd powyżej.
- Jeżeli to nie pomoże, poproś o pomoc jednego z programistów na [serwerze discord](https://discord.premid.app/).

# Wyjaśnienie plików

- [Klasa Presence](/dev/presence/class)
- [Klasa Slideshow](/dev/presence/slideshow)
- [Klasa iFrame](/dev/presence/iframe)
- [Metadane Pliku](/dev/presence/metadata)
- [Konfiguracja TypeScript](/dev/presence/tsconfig ""){.links-list}
