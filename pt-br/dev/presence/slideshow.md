---
title: Classe de Slideshow
description: 
published: true
date: 2021-09-18T14:41:04.543Z
tags: 
editor: markdown
dateCreated: 2021-09-07T01:56:12.012Z
---

# Classe de Slideshow

## Introdução

The `Slideshow` class is used to set multiple `PresenceData` and "slide" through them every x milliseconds (minimum: 5000).

See the [`createSlideshow`](/dev/presence/class#createslideshow) method in the [`Presence`](/dev/presence/class) class on how to create a `Slideshow`.

## Propriedades

### `currentSlide`

Returns a [`PresenceData`](/dev/presence/class#presencedata-interface) object of what the presence/current slide is displaying.

```typescript
const currentSlide = slideshow.currentSlide
console.log(currentSlide.details) // Will console log the details of the PresenceData
```

## Métodos

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

# SlideshowSlide Class

## Introdução

Um `SlideshowSlide` é a representação interna de cada slide em um `Slideshow`.

## Propriedades

### `id`

Retorna uma `String` do id do slide.

### `data`

Retorna um objeto [`PresenceData`](/dev/presence/class#presencedata-interface) do `PresenceData` salvo no slide.

## Métodos

### `updateData(PresenceData)`

Define os dados dos slides de acordo com os dados fornecidos.

Você deve fornecer uma interface `PresenceData` para obter todas as informações que por fim você deseja exibir em seu perfil.

### `updateInterval(Number)`

Define o intervalo do slide de acordo com os dados fornecidos.

Você deve fornecer um `Número` que é a quantidade de tempo em milissegundos (mínimo: 5000) que este slide irá mostrar.