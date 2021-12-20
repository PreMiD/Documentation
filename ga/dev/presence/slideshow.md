---
title: Rang Taispeántas Sleamhnán
description:
published: true
date: 2021-12-20T14:27:18.034Z
tags:
editor: markdown
dateCreated: 2020-12-25T00:44:42.803Z
---

# Rang Taispeántas Sleamhnán

## Réamhrá

Úsáidtear an rang `Slideshow` chun iolraí ` PresenceData ` agus "sleamhnán" a shocrú trí gach x milleasoicind (íosmhéid: 5000).

Féach an modh [ ` createSlideshow ` ](/dev/presence/class#createslideshow) sa mhodh [ `Presence` ](/dev/presence/class) aicme ar conas ` Slideshow` a chruthú.

## Airíonna

### `currentSlide`

Filleann sé réad [ `PresenceData`](/dev/presence/class#presencedata-interface) ar a bhfuil an sleamhnán láithreachta/reatha á thaispeáint.

```ts
const currentSlide = slideshow.currentSlide
console.log(currentSlide.details) // Déanfaidh consól sonraí an PresenceData a logáil
```

## Modhanna

### `addSlide(String, PresenceData, Number)`

Cuir sleamhnán nua leis an `Slideshow` de réir na sonraí a cuireadh ar fáil.

Éilíonn an chéad pharaiméadar ` Teaghrán ` a úsáidfear mar aitheantóir uathúil don sleamhnán.

Éilíonn an dara paraiméadar comhéadan [ ` PresenceData ` ](/dev/presence/class#presencedata-interface) chun gach faisnéis a theastaíonn uait a thaispeáint sa sleamhnán a fháil.

Éilíonn an tríú paraiméadar ` Uimhir ` arb é an méid ama i milleasoicindí (íosmhéid: 5000) a thaispeánfaidh an sleamhnán seo.

### `getSlides()`

Seoltar gach sleamhnán a sábháladh sa ` Slideshow` ar ais mar ` Array ` de [ ` SlideshowSlide ` ](#slideshowslide-class).

### `updateSlide(String, PresenceData, Number)`

Nuashonraíonn sé sleamhnán an ` id ` a thugtar de réir na sonraí a cuireadh ar fáil.

Éilíonn an chéad pharaiméadar ` Teaghrán ` arb é aitheantóir uathúil an sleamhnáin is mian leat a nuashonrú.

Éilíonn an dara paraiméadar comhéadan [ ` PresenceData ` ](/dev/presence/class#presencedata-interface) chun gach faisnéis a theastaíonn uait a thaispeáint sa sleamhnán a fháil.

Éilíonn an tríú paraiméadar ` Uimhir ` arb é an méid ama i milleasoicindí (íosmhéid: 5000) a thaispeánfaidh an sleamhnán seo.

### `hasSlide(String)`

Seoltar ` Boole ` ar ais ag rá an gcuirtear an sleamhnán leis an ` Slideshow`.

### `deleteSlide(String)`

Scriosann an sleamhnán leis an ` id ` tugtha ón ` Slideshow`.

Éilíonn an chéad pharaiméadar ` Teaghrán ` arb é aitheantóir uathúil an sleamhnáin is mian leat a scriosadh.

### `deleteAllSlides()`

Scriosann sé gach sleamhnán ón ` Slideshow`.

# Rang SlideshowSlide

## Réamhrá

Is é atá i ` SlideshowSlide ` léiriú inmheánach gach sleamhnáin i Taispeántas `Slideshow`.

## Airíonna

### `id`

Filleann ` Teaghrán ` de id an sleamhnáin.

### `data`

Filleann sé réad [ ` PresenceData ` ](/dev/presence/class#presencedata-interface) den réad ` PresenceData ` a sábháladh sa sleamhnán.

## Modhanna

### `updateData(PresenceData)`

Socraigh na sonraí sleamhnán de réir na sonraí a chuirtear ar fáil.

Caithfidh tú comhéadan ` PresenceData ` a sholáthar chun gach faisnéis a theastaíonn uait a thaispeáint i do phróifíl sa deireadh.

### `updateInterval(Number)`

Socraíonn eatramh an sleamhnáin de réir na sonraí a chuirtear ar fáil.

Ní mór duit ` Uimhir ` a sholáthar arb é an méid ama i milleasoicindí (íosmhéid: 5000) a thaispeánfaidh an sleamhnán seo.
