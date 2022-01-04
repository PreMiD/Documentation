---
title: স্লাইডশো ক্লাস
description:
published: true
date: 2021-12-20T14:27:18.034Z
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

```ts
const currentSlide = slideshow.currentSlide
console.log(currentSlide.details) // কনসোল লগ করবে PresenceData এর বিস্তারিত
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

# SlideshowSlide ক্লাস

## পরিচিতি

A `SlideshowSlide` is the internal representation of each slide in a `Slideshow`.

## প্রপার্টি

### `id`

একটি `String` রিটার্ন করে স্লাইডটির আইডি এর।

### `data`

স্লাইডটিতে সংরক্ষিত `PresenceData` এর একটি [`PresenceData`](/dev/presence/class#presencedata-interface) অবজেক্ট রিটার্ন করে।

## মেথড

### `updateData(PresenceData)`

প্রদান করা ডাটা অনুযায়ী স্লাইড ডাটাকে সেট করে।

You must provide a `PresenceData` interface to get all information that you ultimately want to display in your profile.

### `updateInterval(Number)`

Sets the interval of the slide according to provided data.

You must provide a `Number` which is the amount of time in milliseconds (minimum: 5000) that this slide will show.
