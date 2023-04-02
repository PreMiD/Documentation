---
title: Slaidiseansi klass
description:
published: true
date: 2021-12-20T14:27:18.034Z
tags:
editor: markdown
dateCreated: 2020-12-25T00:44:42.803Z
---

# Slaidiseansi klass

## Sissejuhatus

Klassiga `Slideshow` kasutatakse mitmete `PresenceData` seadistamist ja nende libistamist iga x millisekundi järel (vähemalt: 5000).

Vaadake [`createSlideshow`](/dev/presence/class#createslideshow) meetodit jaotises [`Presence`](/dev/presence/class) klass `Slideshow` loomise kohta.

## Atribuudid

### `currentSlide`

Tagastab objekti [`PresenceData` ](/dev/presence/class#presencedata-interface) oleku/praeguse slaidi kuvamise.

```ts
const currentSlide = slideshow.currentSlide
console.log(currentSlide.details) // Logib konsoolil PresenceData üksikasjad
```

## Meetodid

### `addSlide(String, PresenceData, Number)`

Lisage vastavalt esitatud andmetele `Slideshow`-i uus slaid.

Esimene parameeter nõuab `String`-i, mida kasutatakse slaidi kordumatu identifikaatorina.

Teine parameeter nõuab kogu slaidis kuvatava teabe saamiseks [`PresenceData` liidet](/dev/presence/class#presencedata-interface).

Kolmas parameeter nõuab `Number`-it, mis on selle slaidi kuvamise aeg millisekundites (vähemalt: 5000).

### `getSlides()`

Tagastab kõik `Slideshow` salvestatud slaidid `Array`-na kujul [`SlideshowSlide`](#slideshowslide-class).

### `updateSlide(String, PresenceData, Number)`

Värskendab antud `id` slaidis vastavalt esitatud andmetele.

Esimene parameeter nõuab `String`-i, mis on värskendatava slaidi kordumatu tunnus.

Teine parameeter nõuab kogu slaidis kuvatava teabe saamiseks [`PresenceData` liidet](/dev/presence/class#presencedata-interface).

Kolmas parameeter nõuab `Number`-it, mis on selle slaidi kuvamise aeg millisekundites (vähemalt: 5000).

### `hasSlide(String)`

Tagastab `Boolean`-i, mis näitab, kas slaid on lisatud `Slideshow`-i.

### `deleteSlide(String)`

Kustutab slaidi etteantud `id`` Slideshow`-st.

Esimene parameeter nõuab `String`-i, mis on kustutatava slaidi kordumatu tunnus.

### `deleteAllSlides()`

Kustutab kõik slaidid `Slideshow`-st.

# SlideshowSlide-i klass

## Sissejuhatus

`SlideshowSlide` on `Slideshow` iga slaidi sisemine esitus.

## Atribuudid

### `id`

Tagastab slaidi Id `String`-ina.

### `data`

Tagastab slaidile salvestatud `PresenceData` objekti [`PresenceData`](/dev/presence/class#presencedata-interface).

## Meetodid

### `updateData(PresenceData)`

Määrab slaidide andmed vastavalt esitatud andmetele.

Kogu teabe saamiseks, mida soovite lõpuks oma profiilil kuvada, peate lisama liidese `PresenceData`.

### `updateInterval(Number)`

Määrab slaidi intervalli vastavalt esitatud andmetele.

Peate esitama `Number`-i, mis on millisekundites (vähemalt: 5000) antud slaidi kuvamise aeg.
