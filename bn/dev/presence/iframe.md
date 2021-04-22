---
title: iFrame ক্লাস
description:
published: true
date: 2020-05-03T20:17:51.982Z
tags:
---

# iFrame ক্লাস
> PreMiD এর সাথে iframe সিস্টেমটি সমস্যাযুক্ত এবং অপ্রত্যাশিত ব্যবহার করতে পারে, সতর্কতার সাথে ব্যবহার করো। 
> 
> {.is-danger}

## পরিচিতি

কিছু পরিস্থিতিতে, তোমার Presence - এর প্রয়োজন হতে পারে `iframes` - এর ভিতরের এলিমেন্টগুলো অ্যাক্সেস করার।

যে কোডটি তুমি লেখো `iframe.ts` ফাইলের ভিতর সেটি পেজের প্রত্যেকটি iframe - এর মধ্যে কাজ করে।

Presences এর মতো, `iframes` - এর নিজস্ব ক্লাস রয়েছে অটোমেটিকভাবে ডাটা আপডেট করার জন্য।

```typescript
let iframe = new iFrame();

iframe.on("UpdateData", async () => {
    // কোড এখানে হবে...
});
```

## মেথোড

### `send(Object)`
Presence - এ ডাটা পাঠায়। এই মেথোডটি ব্যবহার করলে Presence - টি একটি `iFrameData` ইভেন্ট পাঠাবে।

### `getUrl()`
`iframe` - টির URL রিটার্ন করে।

## ইভেন্ট
`iframes` - এ, ইভেন্টগুলো কাজ করে যেভাবে সেগুলো কাজ করে `presence` ক্লাসে।

```typescript
iframe.on("UpdateData", async () => {
    // কোড এখানে হবে...
});
```

সবগুলো ইভেন্টের একটি তালিকা এখানে:

#### `UpdateData`

এই ইভেন্টটি প্রত্যেকবার কাজ করে যখন iframe - টি আপডেট হচ্ছে।