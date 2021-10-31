---
title: Presence ডেভেলপমেন্ট
description: 
published: true
date: 2021-10-30T23:13:21.192Z
tags: 
editor: markdown
dateCreated: 2021-09-07T01:23:15.835Z
---

> সব Presences এখন রাখা আছে এখানে: https://github.com/PreMiD/Presences 
> 
> {.is-info}

ভার্সন `2.x` পরিচয় করিয়ে দেয় [Presence স্টোরকে](https://premid.app/store)। ইউজাররা এখন ম্যানুয়ালি অ্যাড ও রিমুভ করতে পারে তাদের প্রিয় Presences [ওয়েবসাইটের](https://premid.app/) ইউজার ইন্টারফেস দ্বারা।

> শুরু করার আগে, এটা পরামর্শিত যে তুমি আমাদের Presence - এর বিধি দেখো। 
> 
> {.is-warning}

- [বিধি](https://docs.premid.app/dev/presence/guidelines)
{.links-list}

# গঠন

সব Presence কোড করা হয়েছে [TypeScript](https://www.typescriptlang.org/) - এ। [TypeScript](https://www.typescriptlang.org/) has some extra spicy type definitions over JavaScript, so fixing and identifying bugs is way easier.

## ইন্সটলেশন

1. ইন্সটল করো [Git](https://git-scm.com/).
2. ইন্সটল করো [Node](https://nodejs.org/en/) (সাথে আসে [npm](https://www.npmjs.com/)).
3. ইন্সটল করো [TypeScript](https://www.typescriptlang.org/index.html#download-links) (একটি টার্মিনাল ওপেন করো এবং টাইপ করো `npm install -g typescript`).

## প্রোজেক্টটিকে ক্লোন করা

1. একটি টার্মিনাল ওপেন করো এবং টাইপ করো `git clone https://github.com/PreMiD/Presences`.
2. তোমার পছন্দের একটি ফোল্ডার বাছাই করো।
3. তোমার কোড এডিটর দিয়ে এটিকে ওপেন করো।

## ফোল্ডার এবং ফাইল তৈরি করা

1. `websites` ফোল্ডারে যাও এবং যে Presence তুমি তৈরি করতে চাও তার **নামের** (URL না) প্রথম অক্ষরের ফোল্ডারে যাও।
2. যে Presence তুমি তৈরি করতে চাও তার **নাম** (URL না) দিয়ে একটি ফোল্ডার তৈরি করো।
3. ভিতরে একটি `presence.ts` এবং একটি `tsconfig.json` ফাইল তৈরি করো।
4. `dist` নামের একটি ফোল্ডার তৈরি করো।
5. একটি `metadata.json` ফাইল তৈরি করো `dist` ফোল্ডার এর ভিতরে।

## tsconfig.json ফাইলটি পূরণ করা

নিচের কোডটি `tsconfig.json` ফাইলে দাও।

```typescript
{
  "extends": "../../../tsconfig.json",
  "compilerOptions": {
    "outDir": "./dist/"
  }
}
```

TypeScript কনফিগারেশন সম্পর্কে আরো জানতে ক্লিক করো [এখানে](/dev/presence/tsconfig)।

## metadata.json ফাইলটি পূরণ করা

অলস মানুষদের জন্য আমরা তৈরি করেছি `metadata.json` ফাইল তৈরিকারক [এখানে](https://eggsy.xyz/projects/premid/mdcreator)। তবুও এটা পড়া উচিত তাহলে তুমি বুঝবে এটা কীভাবে কাজ করে।

```json
{
  "$schema": "https://schemas.premid.app/metadata/1.5",
  "author": {
    "name": "USER",
    "id": "ID"
  },
  "contributors": [
    {
      "name": "USER",
      "id": "ID"
    }
  ],
  "service": "SERVICE",
  "altnames": ["SERVICE"],
  "description": {
    "en": "DESCRIPTION"
  },
  "url": "URL",
  "version": "VERSION",
  "logo": "URL",
  "thumbnail": "URL",
  "color": "#HEX000",
  "tags": ["TAG1", "TAG2"],
  "category": "CATEGORY",
  "regExp": "REGEXP",
  "iFrameRegExp": "REGEXP",
  "iframe": false,
  "readLogs": false,
  "settings": [
    {
      "id": "ID",
      "multiLanguage": true
    },
    {
      "id": "ID",
      "title": "DISPLAY TITLE",
      "icon": "FONTAWESOME ICON",
      "value": true
    },
    {
      "id": "ID",
      "if": {
        "ID": true
      },
      "title": "DISPLAY TITLE",
      "icon": "FONTAWESOME ICON",
      "value": "\"%song%\" by %artist%",
      "placeholder": "use %song% or %artist%"
    },
    {
      "id": "ID",
      "title": "DISPLAY TITLE",
      "icon": "FONTAWESOME ICON",
      "value": 0,
      "values": ["1", "2", "etc."]
    }
  ]
}
```

উপরের কোডটি কপি করো এবং তোমার `metadata.json` ফাইলে পেস্ট করো। তোমাকে এখন প্রপার্টিগুলোর মানগুলো এডিট করতে হবে। মনে রাখো যে নিচের প্রপার্টিগুলো অপশনাল তোমার `metadata.json` ফাইলে, যদি তুমি সেগুলো না ব্যবহার করার চিন্তা করো তাহলে তোমাকে সেগুলো রিমুভ করতে হবে।

- `contributors`
- `altnames`
- `regExp`
- `iframe`
- `iFrameRegExp`
- `readLogs`
- `settings`

**কিছু মান প্রিসেটগুলোকে স্পষ্ট করা:**

<table>
  <thead>
    <tr>
      <th style="text-align:left">ভ্যারিয়েবল</th>
      <th style="text-align:left">বিবরণ</th>
      <th style="text-align:left">ধরন</th>
      <th style="text-align:left">অপশনাল</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>author</b></td>
      <td style="text-align:left">একটি অবজেক্ট হতে হবে যার মধ্যে Presence ডেভেলপারের <code>name</code> এবং <code>id</code> থাকবে। <code>name</code> হচ্ছে তোমার Discord ইউজারনেম আইডেন্টিফায়ার (#0000) ছাড়া। ইউজার <code>আইডি</code> কপি করা যাবে Discord থেকে ডেভেলপার মোড
        অন করে এবং তোমার প্রোফাইলের উপর মাউসের ডান পাশের বাটন ক্লিক করে।</td>
      <td style="text-align:left"><code>Object</code></td>
      <td style="text-align:left"><code>না</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>contributors</b></td>
      <td style="text-align:left">একটি অবজেক্ট হতে হবে যার মধ্যে Presence ডেভেলপারের <code>name</code> এবং <code>id</code> থাকবে। <code>name</code> হচ্ছে তোমার Discord ইউজারনেম আইডেন্টিফায়ার (#0000) ছাড়া। ইউজার <code>আইডি</code> কপি করা যাবে Discord থেকে ডেভেলপার মোড
        অন করে এবং তোমার প্রোফাইলের উপর মাউসের ডান পাশের বাটন ক্লিক করে।</td>
      <td style="text-align:left"><code>Array&lt;Object&gt;</code></td>
      <td style="text-align:left"><code>হ্যাঁ</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>service</b></td>
      <td style="text-align:left">The title of the service that this presence supports.<br>
      (Must be the same name as the folder where everything is in)</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>না</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>altnames</b></td>
      <td style="text-align:left">Be able to search the presence using an alternative name.<br>
      Meant to be used for presences that have different names in different languages (e.g. Pokémon and 포켓몬스터).<br>
      You can also use it for presences that have special characters so you don't have to type those (e.g. Pokémon and Pokemon).</td>
      <td style="text-align:left"><code>Array&lt;String&gt;</code></td>
      <td style="text-align:left"><code>হ্যাঁ</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>description</b></td>
      <td style="text-align:left">Small description of the presence, you can use description of the service if you are out of ideas. Your description must have key pair values which indicate the language, and the description in that specific language. Make descriptions with the languages <i>that you know</i>, our translators will make changes to your metadata file.</td>
      <td style="text-align:left"><code>Object</code></td>
      <td style="text-align:left"><code>না</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>url</b></td>
      <td style="text-align:left">URL of the service.<br><b>Example:</b><code>vk.com</code><br>
      <b>This URL must match the URL of the website as it will detect whether or not this is the website to inject the script to.</b><br> Do <b>NOT</b> add <code>https://</code> or <code>http://</code> inside of the URL nor a slash at the end:
      <code>https://premid.app/</code> -> <code>premid.app</code><br>
      <b>Note</b>: Some URLs may have <code>www.</code> or something else in front of their domain. Do <b>NOT</b> forget to add it!<br>
      You can add multiple URLs by doing the following:<br>
      <code>["URL1", "URL2", "ETC."]</code><br>
      You could also use regExp also known as Regex for this task, explained further below.</td>
      <td style="text-align:left"><code>String, Array&lt;String&gt;</code></td>
      <td style="text-align:left"><code>না</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>regExp</b></td>
      <td style="text-align:left">A regular expression string used to match urls.<br>
      regExp or also known as Regex, can be used if a website has multiple subdomains.<br>
      You could use the following regExp for that:<br>
      <code>([a-z0-9]+)[.]domain[.]TLD"</code><br>
      TLD standing for Top Level Domain for example: .com .net (but do not enter the dot).<br>
      <code>([a-z0-9]+)</code> means anything from a to z and from 0 to 9.<br>
      You can get a quick starter by watching this <a href="https://youtu.be/sXQxhojSdZM">video</a>.<br>
      You can test your regExp at <a href="https://regex101.com/">Regex101</a>.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>হ্যাঁ</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>version</b></td>
      <td style="text-align:left">Version of your presence.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>না</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>logo</b></td>
      <td style="text-align:left">Link to service&apos;s logotype.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>না</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>thumbnail</b></td>
      <td style="text-align:left">Link to your presence thumbnail.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>না</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>color</b></td>
      <td style="text-align:left"><code>#HEX</code> value. We recommend to use a primary color of the service
        that your presence supports.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>না</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>tags</b></td>
      <td style="text-align:left">Array with tags, they will help users to search your presence on the website.</td>
      <td style="text-align:left"><code>String, Array&lt;String&gt;</code></td>
      <td style="text-align:left"><code>না</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>category</b></td>
      <td style="text-align:left">A string used to represent the category the presence falls under. See the valid catergories <a href="https://docs.premid.app/dev/presence/metadata#presence-categories">here</a>.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>না</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>iframe</b></td>
      <td style="text-align:left">Defines whether <code>iFrames</code> are used.</td>
      <td style="text-align:left"><code>Boolean</code></td>
      <td style="text-align:left"><code>হ্যাঁ</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>iFrameRegExp</b></td>
      <td style="text-align:left">A regular expression selector that selects iframes to inject into. See regExp for more info.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>হ্যাঁ</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>readLogs</b></td>
      <td style="text-align:left">Defines whether the extension should be reading logs.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>হ্যাঁ</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>settings</b></td>
      <td style="text-align:left">An array of settings the user can change.<br>
      Read more about presence settings <a href="https://docs.premid.app/dev/presence/metadata#presence-settings">here</a>.</td>
      <td style="text-align:left"><code>Array&lt;Object&gt;</code></td>
      <td style="text-align:left"><code>হ্যাঁ</code></td>
    </tr>
  </tbody>
</table>

## শুরু করা যাক

```typescript
const presence = new Presence({
    clientId: "000000000000000000" //অ্যাপ্লিকেশন এর ক্লায়েন্ট আইডি যেটা তৈরি করা হয়েছে https://discordapp.com/developers/applications - তে
  }),
  strings = presence.getStrings({
    play: "presence.playback.playing",
    pause: "presence.playback.paused"
    //তুমি এটা ব্যবহার করতে পারো অনুবাদ করা স্ট্রিংগুলো পেতে ইউজারের ব্রাউজারের ভাষা অনুযায়ী
  });

/*

function myOutsideHeavyLiftingFunction(){
    //নাও এবং তোমার সব ডাটা এখানে প্রসেস করো

    // এলিমেন্ট নেয় //
    // API কল করে //
    // ভ্যারিয়েবল সেট করে //
}

setInterval(myOutsideHeavyLiftingFunction, 10000);
//ফাংশনটিকে UpdateData ইভেন্ট থেকে আলাদা চালাও প্রতি 10 সেকেন্ড অন্তর ভেরিয়েবলগুলো সেট করতে যেগুলো UpdateData নেয়

*/

presence.on("UpdateData", async () => {
  /*UpdateData সবসময় কাজ করছে, এবং সুতরাং তোমার রিফ্রেশ চক্র হিসেবে কাজ করবে। This is called several times a second where possible.

    এটি পরামর্শিত যে অন্য একটি ফাংশন সেট করতে হবে এই ইভেন্ট ফাংশন এর বাইরে যা 
ভ্যারিয়েবলের মানগুলো পরিবর্তন করবে এবং কঠিন কাজগুলো করবে যদি তুমি একটি API থেকে ডাটা কল করো।*/

  const presenceData: PresenceData = {
    largeImageKey:
      "key" /*Key (ফাইলের নাম) Presence - এর বড় ছবিটির। These are uploaded and named in the Rich Presence section of your application, called Art Assets*/,
    smallImageKey:
      "key" /*The key (file name) of the Small Image on the presence. These are uploaded and named in the Rich Presence section of your application, called Art Assets*/,
    smallImageText: "Some hover text", //The text which is displayed when hovering over the small image
    details: "Browsing Page Name", //The upper section of the presence text
    state: "Reading section A", //The lower section of the presence text
    startTimestamp: 1577232000, //The unix epoch timestamp for when to start counting from
    endTimestamp: 1577151472000 //If you want to show Time Left instead of Elapsed, this is the unix epoch timestamp at which the timer ends
  }; /*Optionally you can set a largeImageKey here and change the rest as variable subproperties, for example presenceSata.type = "blahblah"; type examples: details, state, etc.*/

  if (!presenceData.details) presence.setActivity(); /*Update the presence with no data, therefore clearing it and making the large image the Discord Application icon, and the text the Discord Application name*/
  else presence.setActivity(presenceData); //Update the presence with all the values from the presenceData object
});
```

তুমি এটা কপি করতে পারো তোমার `presence.ts` ফাইলে এবং মানগুলো এডিট করতে পারো। Setting all the values is done inside of the updataData event.

উদাহরণের জন্য আমরা পরামর্শ দেই Presences - এর কোড দেখতে যেমন: 1337x বা 9GAG. আরও তথ্যের জন্য `Presence` ক্লাস সম্বন্ধে, ক্লিক করো [এখানে](/dev/presence/class)।

Since v2.2.0 there are now Slideshows, this allows you to show multiple `PresenceData` interfaces on an interval, for more information click about the `Slideshow` class [here](/dev/presence/slideshow).

## নির্দিষ্ট ডাটা পাচ্ছ না?!

বেশ কিছু ওয়েবসাইট বর্তমানে [iframes](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe) ([Inlineframes](https://en.wikipedia.org/wiki/HTML_element#Frames)) ব্যবহার করছে। এসব HTML ট্যাগগুলোর মধ্যে একাধিক উৎস থাকতে পারে যেমন ভিডিও। কিন্তু সেগুলো সবসময় একই থাকে না। কিছু গোপন করা থাকে অথবা শুধু সক্রিয়ভাবে ব্যবহার করা হয় না। চেক করো যদি তুমি তথ্যটিকে এক্সট্রাক্ট করতে পারো যা তোমার প্রয়োজন সেগুলো ছাড়া কোনো অপ্রয়োজনীয় কাজ করার আগে।

1. সেগুলো চেক করো তোমার ব্রাউজারের কনসোলে (নিশ্চিত হও যে তুমি **Elements** ট্যাবে রয়েছ)।
2. সার্চ করো (<kbd>CTRL</kbd>+<kbd>F</kbd> (উইন্ডোজ) অথবা <kbd>CMD</kbd>+<kbd>F</kbd> (ম্যাক ওএস))।
3. দাও `document.querySelectorAll("iframe")`.

যদি তুমি দেখো যে তোমার প্রয়োজনীয় ডাটা একটি iFrame - এ রয়েছে, তাহলে তোমাকে ধাপগুলো অনুসরণ করতে হবে:

1. একটি `iframe.ts` ফাইল তৈরি করো।
2. তোমার মেটাডাটা ফাইলে iFrame - কে সেট করো `true` - তে।
3. তোমার iFrame ফাইল পূরণ করো।

```typescript
const iframe = new iFrame();
iframe.on("UpdateData", async () => {
  /*
  পাও তোমার প্রয়োজনীয় সমস্ত ডাটা iFrame থেকে এবং সেগুলোকে ভ্যারিয়েবলে সেভ করো
  এবং সেগুলোকে পাঠাও iframe.send ব্যবহার করে
  */
  iframe.send({
    //ডাটা পাঠানো
    video: video,
    time: video.duration
  });
});
```

4. তোমার Presence ফাইলটিকে iFrame ফাইল থেকে ডাটা নেওয়ার সিস্টেম তৈরি করা।

```typescript
presence.on("iFrameData", (data) => {
  iFrameVideo = data.video;
  currentTime = data.time;
});
```

**বিঃদ্রঃ** এটাকে updateData ইভেন্ট এর বাইরে স্থাপন করতে হবে।

## কম্পাইলিং

`presence.ts` ফাইলটিকে `/dist` ফোল্ডারে কম্পাইল করার জন্য একটি কনসোল ওপেন করো তোমার ফোল্ডারে এবং টাইপ করো `tsc -w`

# Presence - টিকে লোড করা

1. এক্সটেনশনটি ওপেন করো ব্রাউজারে এবং <kbd>Shift</kbd> বাটনটি চেপে রাখো তোমার কীবোর্ডের।
2. **Presence লোড করাও** আসবে Presences সেকশনে।
3. <kbd>Shift</kbd> বাটনটিতে চেপে রাখা অবস্থাতেই এটিতে ক্লিক করো।
4. /dist ফোল্ডারটি সিলেক্ট করো তোমার Presence - এর।

# কিছু সহায়ক জিনিস

## হট রিলোডিং

যে ওয়েবসাইট এর উপর ভিত্তি করে Presence - টি তৈরি করছ সেটি অটোমেটিকভাবে রিলোড হচ্ছে প্রত্যেক সময় তুমি একটি ফাইল সেভ করো তোমার ফোল্ডারে।

## ডিবাগিং

- তুমি তোমার কোড এর মাঝখানে `console.log("Test");` দিতে পারো এবং দেখতে পারো যদি তোমার ব্রাউজার কনসোল তোমাকে সেই আউটপুটটি দেয়। যদি দেয়, তাহলে পরের ফাংশনের পরে আবার চেষ্টা করো। যদি না দেয়, তাহলে উপরে একটি সমস্যা আছে।
- যদি তাও তোমাকে সাহায্য না করে তাহলে একজন Presence ডেভেলপারকে জিজ্ঞেস করতে পারো আমাদের [Discord সার্ভারে](https://discord.premid.app/) সাহায্যের জন্যে।

# ফাইলগুলো ব্যাখ্যা করা

- [Presence ক্লাস](/dev/presence/class)
- [স্লাইডশো ক্লাস](/dev/presence/slideshow)
- [iFrame ক্লাস](/dev/presence/iframe)
- [মেটাডাটা ফাইল](/dev/presence/metadata)
- [TypeScript কনফিগারেশন](/dev/presence/tsconfig ""){.links-list}
