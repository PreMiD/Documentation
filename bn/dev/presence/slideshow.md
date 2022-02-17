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

## প্রপার্টিগুলো

### `currentSlide`

একটি [`PresenceData`](/dev/presence/class#presencedata-interface) অবজেক্ট রিটার্ন করে যার মধ্যে থাকে presence/বর্তমান স্লাইডটি কী দেখাচ্ছে।

```ts
const currentSlide = slideshow.currentSlide
console.log(currentSlide.details) // কনসোল লগ করবে PresenceData এর বিস্তারিত
```

## মেথডগুলো

### `addSlide(String, PresenceData, Number)`

প্রদত্ত ডাটা অনুযায়ী একটি নতুন স্লাইড যোগ করে `Slideshow` টিতে।

প্রথম প্যারামিটারে একটি `String` প্রয়োজন যা ব্যবহার করা হবে স্লাইডটির জন্য একটি ইউনিক আইডেন্টিফায়ার হিসেবে।

দ্বিতীয় প্যারামিটারে একটি [`PresenceData` ইন্টারফেস](/dev/presence/class#presencedata-interface) প্রয়োজন সকল তথ্য পেতে যা তুমি দেখাতে চাও স্লাইডটিতে।

Third parameter requires a `Number` which is the amount of time in milliseconds (minimum: 5000) that this slide will show.

### `getSlides()`

Returns all slides saved in the `Slideshow` as an `Array` of [`SlideshowSlide`](#slideshowslide-class).

### `updateSlide(String, PresenceData, Number)`

Updates the slide of the given `id` according to provided data.

First parameter requires a `String` that is the unique identifier of the slide you want to update.

দ্বিতীয় প্যারামিটারে একটি [`PresenceData` ইন্টারফেস](/dev/presence/class#presencedata-interface) প্রয়োজন সকল তথ্য পেতে যা তুমি দেখাতে চাও স্লাইডটিতে।

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

## প্রপার্টিগুলো

### `id`

একটি `String` রিটার্ন করে স্লাইডটির আইডি এর।

### `data`

স্লাইডটিতে সংরক্ষিত `PresenceData` এর একটি [`PresenceData`](/dev/presence/class#presencedata-interface) অবজেক্ট রিটার্ন করে।

## মেথডগুলো

### `updateData(PresenceData)`

প্রদান করা ডাটা অনুযায়ী স্লাইড ডাটাকে সেট করে।

তোমাকে একটি `PresenceData` ইন্টারফেস দিতে হবে সব তথ্য পেতে যা তুমি শেষ পর্যন্ত তোমার প্রোফাইলে দেখাতে চাও।

### `updateInterval(Number)`

প্রদান করা ডাটা অনুযায়ী স্লাইডটির ইন্টারভাল সেট করে।

তোমাকে একটি `Number` দিতে হবে যা হবে সময়ের পরিমাণ মিলিসেকেন্ডে (কমপক্ষে: 5000) যেটি এই স্লাইডটি দেখাবে।
