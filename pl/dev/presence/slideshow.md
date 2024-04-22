---
title: Klasa Slideshow
description:
published: true
date: 2021-12-20T14:27:18.034Z
tags:
editor: markdown
dateCreated: 2020-12-25T00:44:42.803Z
---

# Klasa Slideshow

## Wprowadzenie

Klasa `Slideshow` jest używana do ustawiania wielu `PresenceData` i "przesuwania" przez nie co x milisekund (minimum: 5000).

Zobacz metodę [`createSlideshow`](/dev/presence/class#createslideshow) w klasie [`Presence`](/dev/presence/class) o tym, jak utworzyć klasę.

## Właściwości

### `currentSlide`

Zwraca obiekt [`PresenceData`](/dev/presence/class#presencedata-interface) z tym, co jest wyświetlane.

```ts
const currentSlide = slideshow.currentSlide
console.log(currentSlide.details) // Konsola rejestruje szczegóły PresenceData
```

## Metody

### `addSlide(String, PresenceData, Number)`

Dodaje nowy slajd do `Slideshow` zgodnie z podanymi danymi.

Pierwszy parametr wymaga `String`, który będzie używany jako unikatowy identyfikator dla slajdu.

Drugi parametr wymaga interfejsu [`PresenceData`](/dev/presence/class#presencedata-interface), aby uzyskać wszystkie informacje, które chcesz wyświetlać w slajdzie.

Trzeci parametr wymaga `Number`, który jest ilością czasu w milisekundach (minimalnie: 5000), przez którą ten slajd będzie wyświetlany.

### `getSlides()`

Zwraca wszystkie slajdy zapisane w `Slideshow` jako `Array` klasy [`SlideshowSlide`](#slideshowslide-class).

### `updateSlide(String, PresenceData, Number)`

Aktualizuje slajd podanego `id` zgodnie z podanymi danymi.

Pierwszy parametr wymaga `String`, który jest unikatowym identyfikatorem slajdu, którego chcesz zaktualizować.

Drugi parametr wymaga interfejsu [`PresenceData`](/dev/presence/class#presencedata-interface), aby uzyskać wszystkie informacje, które chcesz wyświetlać w slajdzie.

Trzeci parametr wymaga `Number`, który jest ilością czasu w milisekundach (minimalnie: 5000), przez którą ten slajd będzie wyświetlany.

### `hasSlide(String)`

Zwraca `Boolean` określający, czy slajd został dodany do `Slideshow`.

### `deleteSlide(String)`

Usuwa slajd z podanym `id` z `Slideshow`.

Pierwszy parametr wymaga `String`, który jest unikatowym identyfikatorem slajdu, którego chcesz zaktualizować.

### `deleteAllSlides()`

Usuwa wszystkie slajdy z `Slideshow`.

# Klasa SlideshowSlide

## Wprowadzenie

`SlideshowSlide` jest wewnętrzną reprezentacją każdego slajdu w `Slideshow`.

## Właściwości

### `id`

Zwraca `String` identyfikatora slajdu.

### `data`

Zwraca obiekt [`PresenceData`](/dev/presence/class#presencedata-interface) o tym, co jest wyświetlane.

## Metody

### `updateData(PresenceData)`

Ustawia dane slajdów zgodnie z podanymi danymi.

Musisz podać interfejs `PresenceData`, aby uzyskać wszystkie informacje, które chcesz wyświetlić w profilu.

### `updateInterval(Number)`

Ustawia interwał slajdu zgodnie z podanymi danymi.

Musisz podać `Number`, który jest ilością czasu w milisekundach (minimalnie: 5000), który ten slajd wyświetli.
