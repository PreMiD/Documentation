---
title: স্লাইডশো ক্লাস
description:
published: true
date: 2020-12-25T00:47:38.111Z
tags:
editor: markdown
dateCreated: 2020-12-25T00:44:42.803Z
---

# স্লাইডশো ক্লাস

## পরিচিতি

`Slideshow` ক্লাসটি ব্যবহৃত হয় একাধিক `PresenceData` এবং "স্লাইড" সেট করতে প্রতি x মিলিসেসেন্ডে (কমপক্ষে: 5000).

[`createSlideshow`](/dev/presence/class#createslideshow) মেথডটি দেখো [`Presence`](/dev/presence/class) ক্লাসের কীভাবে একটি `স্লাইডশো` তৈরি করতে হয়।

## প্রপার্টি

### `currentSlide`

একটি [`PresenceData`](/dev/presence/class#presencedata-interface) অবজেক্ট রিটার্ন করে যার মধ্যে থাকে presence/বর্তমান স্লাইডটি কী দেখাচ্ছে।

```typescript
const currentSlide = slideshow.currentSlide
console.log(currentSlide.details) // Will console log the details of the PresenceData
```

## মেথড

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

## পরিচিতি

A `SlideshowSlide` is the internal representation of each slide in a `Slideshow`.

## প্রপার্টি

### `id`

Returns a `String` of the id of the slide.

### `data`

Returns a [`PresenceData`](/dev/presence/class#presencedata-interface) object of the `PresenceData` saved in the slide.

## মেথড

### `updateData(PresenceData)`

Sets the slides data according to provided data.

You must provide a `PresenceData` interface to get all information that you ultimately want to display in your profile.

### `updateInterval(Number)`

Sets the interval of the slide according to provided data.

You must provide a `Number` which is the amount of time in milliseconds (minimum: 5000) that this slide will show.