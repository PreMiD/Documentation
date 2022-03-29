---
title: Metadata.json
description: Presence টি সম্বন্ধে প্রাথমিক ডাটা থাকে
published: true
date: 2021-12-20T14:27:18.034Z
tags:
editor: markdown
dateCreated: 2020-06-11T18:04:52.965Z
---

# Metadata.json

তুমি যদি স্টোরে একটি Presence পাবলিশ করতে এবং এক্সটেনশনটি দ্বারা লোড করাতে চাও, তোমাকে `metadata.json` ফাইলটি তৈরি করতে হবে তোমার `dist` ফোল্ডারে।

সেই ফাইলের একটি উদাহরণ পাওয়া যাবে নিচে।

```json
{
  "$schema": "https://schemas.premid.app/metadata/1.7",
  "author": {
    "name": "USER",
    "id": "ID"
  },
  "contributors": [{
    "name": "USER",
    "id": "ID"
  }],
  "service": "SERVICE",
  "altnames": ["SERVICE"],
  "description": {
    "en": "DESCRIPTION"
  },
  "url": "URL",
  "regExp": "REGEXP",
  "iFrameRegExp": "REGEXP",
  "version": "VERSION",
  "logo": "URL",
  "thumbnail": "URL",
  "color": "#45A8FC",
  "category": "CATEGORY",
  "tags": ["TAG1", "TAG2"],
  "iframe": false,
  "settings": [
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

## metadata.json কে বোঝা

সেই উদাহরণটি দেখতে বেশ অদ্ভুত, তাই না? চিন্তা করবে না, এটা বোঝা এতো কঠিন নয় যে প্রত্যেক ভ্যারিয়েবল কীসের জন্য।

<table>
  <thead>
    <tr>
      <th style="text-align:left">ভেরিয়েবল</th>
      <th style="text-align:left">ডেসক্রিপশন</th>
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
      <td style="text-align:left">একটি অবজেক্ট হতে হবে যার মধ্যে কন্ট্রিবিউটরের <code>name</code> এবং <code>id</code> থাকবে। <code>name</code> হচ্ছে তোমার Discord ইউজারনেম আইডেন্টিফায়ার (#0000) ছাড়া। ইউজার <code>আইডি</code> কপি করা যাবে Discord থেকে ডেভেলপার মোড
        অন করে এবং তোমার প্রোফাইলের উপর মাউসের ডান পাশের বাটন ক্লিক করে।</td>
      <td style="text-align:left"><code>Array&lt;Object&gt;</code></td>
      <td style="text-align:left"><code>হ্যাঁ</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>service</b></td>
      <td style="text-align:left">The title of the service that this presence supports.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>না</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>altnames</b></td>
      <td style="text-align:left">Presence টিকে যেন সার্চ করতে পারো একটি বিকল্প নাম ব্যবহার করে।<br>
      ব্যবহার করতে হবে সেসব Presences এর জন্য যেগুলোর ভিন্ন নাম রয়েছে ভিন্ন ভাষায়
(যেমন Pokémon এবং 포켓몬스터).<br>
      তুমি এটাকে ব্যবহার করতে পারো সেসব Presence এর জন্য যেগুলোর বিশেষ অক্ষর রয়েছে যাতে তোমাকে আর সেগুলো টাইপ না করতে হয় (যেমন Pokémon এবং Pokemon).</td>
      <td style="text-align:left"><code>Array&lt;String&gt;</code></td>
      <td style="text-align:left"><code>হ্যাঁ</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>description</b></td>
      <td style="text-align:left">Description of the service <b>NOT</b> the presence. Your description must have key pair values which indicate the language, and the description in that specific language. Make descriptions with the languages <i>that you know</i>, our translators will make changes to your metadata file. View the category for presence languages for a list. </td>
      <td style="text-align:left"><code>Object</code></td>
      <td style="text-align:left"><code>না</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>url</b></td>
      <td style="text-align:left">URL of the service.<br>
      <b>Example:</b><code>vk.com</code><br>
      <b>This url must match the url of the website as it will be used to detect wherever or not this is the website to inject the script to. This may only be used as an array when there are more than one urls.</b></td>
      <td style="text-align:left"><code>String, Array&lt;String&gt;</code></td>
      <td style="text-align:left"><code>না</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>regExp</b></td>
      <td style="text-align:left">A regular expression string used to match urls.</td>
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
      <td style="text-align:left"><b>category</b></td>
      <td style="text-align:left">A string used to represent the category the presence falls under.</td>
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
      <td style="text-align:left"><b>iframe</b></td>
      <td style="text-align:left">Defines whether <code>iFrames</code> are used</td>
      <td style="text-align:left"><code>Boolean</code></td>
      <td style="text-align:left"><code>হ্যাঁ</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>iFrameRegExp</b></td>
      <td style="text-align:left">A regular expression selector that selects iframes to inject into.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>হ্যাঁ</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>readLogs</b></td>
      <td style="text-align:left">Defines whether the extension should be reading logs.</td>
      <td style="text-align:left"><code>Boolean</code></td>
      <td style="text-align:left"><code>হ্যাঁ</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>settings</b></td>
      <td style="text-align:left">An array of settings the user can change</td>
      <td style="text-align:left"><code>Array&lt;Object&gt;</code></td>
      <td style="text-align:left"><code>হ্যাঁ</code></td>
    </tr>
  </tbody>
</table>

## Regular Expressions

If you want to learn regular expressions, here are a few websites.

#### Learning

• [Quick Starter Video](https://youtu.be/sXQxhojSdZM) • [RegexOne](https://regexone.com/) • [Regular Expressions Info](https://www.regular-expressions.info/tutorial.html)

#### Testing

• [Regexr](https://regexr.com/) • [Regex101](https://regex101.com/)

## Presence languages

PreMiD is a polyglot service, meaning that there are multiple languages available to connect users around the globe. A full list of languages can be found with this [API endpoint](https://api.premid.app/v2/langFile/list). To customize your presence even more, you can allow users to select their presence display language. See [`multiLanguage`](#multilanguage) for more.

## Presence settings
Setup interactive settings so users can customize the presence!
```json
"settings": [
  {
    "id": "ID",
    "multiLanguage": true //See https://docs.premid.app/dev/presence/metadata#multilanguage
  },
  {
    "id": "ID",
    "title": "DISPLAY TITLE",
    "icon": "FONTAWESOME ICON", //Example "fas fa-info"
    "value": true //Boolean value will make it an on/off switch with the value as the default value
  },
  {
    "id": "ID",
    "if": {
      "ID": true //If another setting equals this value (true/false/0/1/etc.) then show this button
    },
    "title": "DISPLAY TITLE",
    "icon": "FONTAWESOME ICON",
    "value": "\"%song%\" by %artist%", //Putting in a string will make the setting an input one, where you can use a custom input.
    "placeholder": "use %song% or %artist%" //When input is empty it will show this grayed out
  },
  {
    "id": "ID",
    "title": "DISPLAY TITLE",
    "icon": "FONTAWESOME ICON",
    "value": 0, //Default value of the selector
    "values": ["1", "2", "etc."] //Will make the setting a selector where you select which one you want
  }
]
```

### `multiLanguage`

#### পরিচিতি

The `multiLanguage` setting is used to allow users to manually select the language they want to presence to be shown in. This requires you to use strings from our [API](https://api.premid.app/v2/langFile/presence/en), for information on how to add strings click [here](https://docs.premid.app/dev/presence/metadata#adding-new-strings).

#### Setup

The `multiLanguage` setting is a special case, it doesn't require a `title` nor `icon` nor `value` or `values` like other settings but it does require you some more things to setup!

The `multiLanguage` key can be set to the following:

`true`: use this if you are only going to use strings of the `general.json` file and the `<service>.json` file of the [Localization Repository](https://github.com/PreMiD/Localization/tree/master/src/Presence). `string`: name of the file excluding the extension (.json) inside the [Localization Repository](https://github.com/PreMiD/Localization/tree/master/src/Presence) (excluding the `general` file, since it's always loaded). Only common languages of both the `general` and inputted file will be listed. `Array<String>`: if you are using more than one file inside the [Localization Repository](https://github.com/PreMiD/Localization/tree/master/src/Presence) you can specify all the values in an array (excluding the `general` file, since it's always loaded). Only common languages of all the files will be listed.

#### Adding new strings

**Note:** Adding custom strings for a presence is only allowed if it has more than 1000 users.

##### প্রোজেক্টটিকে ক্লোন করা

1. Open a terminal and type `git clone https://github.com/PreMiD/Localization`.
2. তোমার পছন্দের একটি ফোল্ডার বাছাই করো।
3. তোমার কোড এডিটর দিয়ে এটিকে ওপেন করো।

##### Creating the file

1. Go into the `src` folder.
2. Go into the `Presence` folder.
3. Make a file named `<service>.json`. (Service is the **name** (not an URL) in lowercase of the service you want to support.)

##### Adding the strings

Each `string` is an `Object` where from the name starts with the service name and then the so called stringName with a dot in between them.

The stringName is a 1 word identifier of the message.

The `Object` has 2 properties; `message` and `description`. `message` is the text that needs to be translated. `description` is a description of the message to help our translators understand what they are translating.

**Note:** Do not add any duplicate strings. (This includes strings out of the `general.json` file but not the other files.)

Visualization of the file:

```json
{
  "<service>.<stringName>": {
    "message": "Text that needs to be translated.",
    "description": "This explains what the message above is."
  },
  "<service>.<stringName>": {
    "message": "Text that needs to be translated.",
    "description": "This explains what the message above is."
  }
}
```

After you have fully made the file with strings you can create a Pull Request on the [Localization Repository](https://github.com/PreMiD/Localization), in the description you **must** include a link to your Pull Request of the presence updated using these new strings from the [Presence Repository](https://github.com/PreMiD/Presences).

#### Default keys
The keys you didn't have to set are automatically set to the following: `title`: "Language" **Note:** This is translated into their default language (browser language). `icon`: "fas fa-language" ([Preview](https://fontawesome.com/icons/language)) `value`: **Set to their browser language if it is available (100% translated), otherwise English.** `values`: **Set to the available languages (languages that have it 100% translated).**

**Note:** These are in no way changeable.

### মেথডগুলো

Use the following methods to get settings info in your presence files:
#### `getSetting(String)`
Returns value of setting.
```ts
const setting = await presence.getSetting("pdexID"); //Replace pdexID with the id of the setting
console.log(setting); // This will log the value of the setting
```

#### `hideSetting(String)`
Hides given setting.
```ts
presence.hideSetting("pdexID"); //Replace pdexID with the id of the setting
```

#### `showSetting(String)`
Shows given setting (Only works if the setting was already hidden).
```ts
presence.showSetting("pdexID"); //Replace pdexID with the id of the setting
```

## Presence categories

When making your presence, you must specify a category which the presence falls under. This is a compiled list of the categories that you can use.

<table>
  <thead>
    <tr>
      <th style="text-align:left">ক্যাটাগরি</th>
      <th style="text-align:left">নাম</th>
      <th style="text-align:left">ডেসক্রিপশন</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>anime</b></td>
      <td style="text-align:left"><b>অ্যানিমে</b></td>
      <td style="text-align:left">যেকোনো কিছু যা অ্যানিমে সম্পর্কিত, ফোরাম থেকে ভিডিও স্ট্রিমিং প্লাটফর্ম।</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>games</b></td>
      <td style="text-align:left"><b>গেমস</b></td>
      <td style="text-align:left">যেকোনো ওয়েবসাইট যার মধ্যে গেম সম্পর্কিত কন্টেন্ট রয়েছে, যেমন <code>Kahoot</code> বা <code>Skribbl.io</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>music</b></td>
      <td style="text-align:left"><b>মিউজিক</b></td>
      <td style="text-align:left">These are websites that offer music related content, whether that be streaming or downloading.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>socials</b></td>
        <td style="text-align:left"><b>সোশ্যাল</b></td>
      <td style="text-align:left">Websites that are used for the purpose of creating and sharing content or for participating in other forms of social networking.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>videos</b></td>
        <td style="text-align:left"><b>ভিডিও & স্ট্রিম</b></td>
      <td style="text-align:left">Websites that serve the purpose of providing videos and streams.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>other</b></td>
      <td style="text-align:left"><b>অন্যান্য</b></td>
      <td style="text-align:left">Anything that does not fall under a specific category listed above.</td>
    </tr>
  </tbody>
</table>

