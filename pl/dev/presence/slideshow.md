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

Returns a [`PresenceData`](/dev/presence/class#presencedata-interface) object of what the presence/current slide is displaying.

```ts
const currentSlide = slideshow.currentSlide
console.log(currentSlide.details) // Will console log the details of the PresenceData
```

## Metody

### `addSlide(String, PresenceData, Number)`

Add a new slide to the `Slideshow` according to provided data.

First parameter requires a `String` that will be used as a unique identifier for the slide.

Second parameter requires a [`PresenceData` interface](/dev/presence/class#presencedata-interface) to get all information that you want to display in the slide.

Third parameter requires a `Number` which is the amount of time in milliseconds (minimum: 5000) that this slide will show.

### `getSlides()`

Returns all slides saved in the `Slideshow` as an `Array` of [`SlideshowSlide`](#slideshowslide-class).

### `updateSlide(String, PresenceData, Number)`

Updates the slide of the given `id` according to provided data.

First parameter requires a `String` that is the unique identifier of the slide you want to update.

Second parameter requires a [`PresenceData` interface](/dev/presence/class#presencedata-interface) to get all information that you want to display in the slide.

Third parameter requires a `Number` which is the amount of time in milliseconds (minimum: 5000) that this slide will show.

### `hasSlide(String)`

Returns a `Boolean` stating whether the slide is added to the `Slideshow`.

### `deleteSlide(String)`

Deletes the slide with the given `id` from the `Slideshow`.

First parameter requires a `String` that is the unique identifier of the slide you want to delete.

### `deleteAllSlides()`

Deletes all slides from the `Slideshow`.

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
