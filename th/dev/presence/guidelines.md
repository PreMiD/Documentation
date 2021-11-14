---
title: แนวทางในการสร้าง Presence
description: Rules that all presence developers must follow to have their presence added.
published: true
date: 2021-10-18T16:26:36.089Z
tags:
editor: markdown
dateCreated: 2021-09-07T01:44:53.883Z
---

<div align="center">
    <img src="https://github.com/PreMiD.png?size=2048" width="128px" style="max-width:100%;">
    <h3 style="font-size: 2rem; margin-bottom: 0">แนวทางในการสร้าง Presence</h3>
    <h4 style="margin-top: 0">Revision 3</h4>
    <br />
</div>

# แนวทาง

เพื่อที่จะเผยแพร่ Presence ไปยัง [ที่เก็บของ Presence ทั้งหมด](https://github.com/PreMiD/Presences/), เราต้องการให้คุณปฏิบัติตามหลักเกณฑ์ที่กำหนด. สำหรับบางคนกฎนี้อาจเข้มงวดและรุนแรงเกินไป อย่างไรก็ตามการดำเนินการตามกฎเหล่านี้จะทำให้เราและผู้ใช้จะไม่พบเจอปัญหาใด ๆ

# การสร้าง

กฏทั่วไปสําหรับการพัฒนา Presence มีดังนี้

- Presence **ต้อง**มีความเกี่ยวข้องกับเว็ปไซต์ที่คุณเลือก
- คุณ**ไม่สามารถ**สร้าง Presences สำหรับเว็บไซต์ที่ผิดกฎหมายได้ (เช่น เกี่ยวกับความเครียด, การขายยาเสพติด, การอนาจารเด็ก, และอื่นๆ)
- โครงสร้างไฟล์ต้องบริสุทธิ์เเละมีการจัดการ, อย่าใส่ไฟล์ที่ไม่เกี่ยวข้อง (เช่น vscode เเละโฟลเดอร์ git, รูปภาพเเละไฟล์ต่างๆ)
- คุณต้องมีโครงสร้างไฟล์ที่เหมาะสม, สําหรับการร่าง **ไม่**อนุญาติ
- คุณ**ไม่สามารถ**สร้าง Presences สำหรับเว็บไซต์ที่ใช้ Domains หรือ Hosts ฟรีได้ (ตัวอย่างเช่น, `.TK` [Domains บน Freenom ทั้งหมด], `.RF`, `GD`, และอื่นๆ) มีข้อยกเว้นได้หากคุณมีหลักฐานว่าคุณจ่ายเงินเพื่อที่จะได้ Domain มา
- Domain ของ Presence ต้องมีอายุอย่างน้อย 2 เดือน
- Presence ที่เล็งการพัฒนาด้วยเบราว์เซอร์ภายในเช่น (Chrome Web Store, `chrome://`, `about:` หรือหน้าอื่นๆนั้น) **ไม่อนุญาติ** เนื่องจากต้องเปิดโหมดทดลองของเบราว์เซอร์นั้นๆ เเละอาจะเกิดความเสียหายของเบราว์เซอร์ได้
- Presence ที่มีเพียง Domain เดียวจะ**ไม่อนุญาติ**, เนื่องจากอาจจะทําให้หน้าอื่นขัดข้องได้เช่น (หน้าหลัก), เเต่สามารถทําได้เเค่นโยบายเเละหน้าติดต่อ (เนื้อหาที่ไม่ได้ใช้บ่อยๆ) หรือ เนื้อหาที่ไม่เกี่ยวข้อง (เช่น หน้า Wiki)
- Presences for online radios are only allowed if the radio has at least 100 weekly listeners and 15 concurrent and must have some features other than just showing album/song title, etc.
- Presences are not allowed to run JS code with their own function to get variables. If Firefox has issues with built-in function inside `Presence` class, you are allowed to do your own function and you need to tell us about it in Pull Request description.
- Low quality presences (or ones with little context) are **not** allowed (for e.g., only showing a logo and text but never changing it again).
- Presences for services like Discord Bot/Server Lists must follow these extra requirements:
  - The domain should be at least **6 months** old.
  - Unique visitors per day:
    - For 6 to 12 month old domains: **20,000 unique visitors/day**.
    - For 12+ month old domains: **45,000 unique visitors/day**.
  - The website can't be on a cheap domain like `.xyz`, `.club` and so on.
  - The website itself must have a very good quality, design, etc.
- Presences should use [common details](https://api.premid.app/v2/langFile/presence/en) (strings starting with "general."). You can achieve this using `multiLanguage` with the provided strings. If your presence requires custom strings, then you shouldn't use `multiLanguage` until the presence gets 1000 users. You can find an example [here](https://docs.premid.app/dev/presence/class#getstringsobject).
- Including the `dist` folder, `presence.ts` file, `iframe.ts` file, and `metadata.json` file is mandatory so the result would be what is represented in the following schema:

```bash
presence
├── dist
│   └── metadata.json
├── presence.ts
└── tsconfig.json
```

หรือถ้าคุณใช้ไฟล์ `iframe.ts`:

```bash
presence
├── dist
│   └── metadata.json
├── presence.ts
├── iframe.ts
└── tsconfig.json
```

## [**metadata.json**](https://docs.premid.app/dev/presence/metadata)

> เพื่อความสะดวกสําหรับการพัฒนา, เรามีโครงสร้างให้ ซึงคุณสามารถใช้เพื่อตรวจสอบความสมบูรณ์ของไฟล์ `metadata`ได้ นี้เป็นทางเลือกทั้งหมด เเละไม่จําเป็นระหว่างการตรวจสอบ

> ขอแนะนำให้คุณจัดระเบียบไฟล์ `metadata` ในรูปเเบบข้างล่างนี้, และคุณต้องมีชื่อบริการที่ถูกต้องตามหลักไวยากรณ์, คําอธิบาย, เเท๊ก, เเละ การตั่งค่าต่างๆ สิ่งที่ไม่ได้จัดระเบียบการข้อกําหนดจะ**ไม่ผ่านการอนุมัติ**

> Presence สําหรับเว็บไซต์ที่มีเนื้อหาที่ 18+ **ต้องมี **`nsfw เเท๊ก`, เเละ โลโก้หรือภาพย่อต้อง **ไม่เกี่ยวกับเนื้อหาพวกนี้**

เเต่ละ Presence มีตัวบอกไฟล์ เรียกว่า `metadata.json`, metadata ต้องได้มาตรฐานและตัวอย่างของไฟล์นี้สามารถดูได้ด้านล่าง:

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
      "id": "multiLanguage",
      "multiLanguage": true
    }
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

> If a field is listed as optional on the [documentation](https://docs.premid.app/dev/presence/metadata) or there is a `*` next to the key, and your presence uses the default value for it, do not include it in the `metadata` file. (เช่น Presence ไม่ต้องการ iframe ไม่ต้องใส่ `iframe`ลงไป)

> รูปภาพในไฟล์ `metadata` ต้องเป็นลิงค์จาก `i.imgur.com` Using content hosted on the website is **not** permitted as they can change the paths and files unwillingly.

A list of fields and their rules are listed below:

### **`$schema`**

- The schema _key_ **must** include a dollar sign at the beginning of it, this will signal your text editor that you want to validate your JSON file against a model. _As stated earlier, you do not need to include a schema, but if you include it you must take this into account._

### **`author`**

- The ID _value_ **must** be your Discord snowflake ID. You can get it by enabling [developer mode](https://support.discord.com/hc/en-us/articles/206346498-Where-can-I-find-my-User-Server-Message-ID-). _Please do **not** confuse this with your application ID, which is only for your presence._

### **`*contributors`**

- Do **not** add yourself as a contributor, and do not add someone else as a contributor unless they have helped with the presence.

### **`service`**

- The service name **must** be the name of the presence directory. For example, if the presence is located at `/websites/Y/YouTube/`, the service name must be `YouTube`.
- You **cannot** use the url as the service name unless the website uses the url as its official name. If the name is not descriptive and can be considered vague, using the url is **required**. (for e.g., `YouTube` is permitted because that is the official name and is descriptive, while `youtube.com` is not. `Top` is a non-descriptive name, so using the url `top.gg` is **required**.)
- If service has some explicit branding rules of their name, you should follow them.

### **`*altnames`**

- **Only** use this in scenarios where a website goes under multiple official names (e.g. Pokémon and 포켓몬스터). _Shortened_ versions of service names go under `tags`.

### **`description`**

- **All** presences are **required** to have an English description regardless of the website's prefered language.
- Do **not** try and translate the description yourself unless you know that language, translators will modify your `metadata.json` and change the descriptions if necessary.

### **`url`**

- The url **must** be a string if the website only uses one domain. If the website uses multiple, make this an array and specify each one.
- Do **not** include protocols in the url (for e.g., `http` or `https`), and do not include query parameters in the url (for e.g., `www.google.com/search?gws_rd=ssl` which should be `www.google.com`)

### **`version`**

- Always make sure the version number follows [semantic versioning standards](https://semver.org), which translates to the following scheme: `<NEW-FEATURE>.<HUGE-BUGFIX>.<SMALL-BUGFIX-OR-METADATA-CHANGES>`. Anything else like `1.0.0.1`, `1.0`, `1`, `1.0.0-BETA` or changing `1.0.0` to `2.0.0` on a bug fix/small change is **not** permitted.
- The version **must** always start at `1.0.0` unless told otherwise, other versions will **not** be permitted.

### **`logo`**

- The logo **must** be a square image with a `1:1` aspect ratio.
- The image is **required** to have a minimum resolution of `512x512` pixels. You can upsize it using a tool like [waifu2x](http://waifu2x.udp.jp/).

### **`thumbnail`**

- The thumbnail **should** preferably be a [wide promotional card](https://i.imgur.com/3QfIc5v.jpg) or a [screenshot](https://i.imgur.com/OAcBmwW.png) if the first is **not** available.

### **`color`**

- The color **must** be a hexadecimal value between `#000000` and `#FFFFFF`.
- The color string **must** be prepended with a hash symbol.

### **`tags`**

- **All** presences are required to have at least _one_ tag.
- Tags must **not** include any spaces, slashes, single/double quotation marks, Unicode characters, and should always be lowercase.
- Tags **should** preferably include alternate service names to make searching easier (for e.g., if an Amazon presence had included AWS support, it would have its tags like `amazon-web-services` and `aws`)
- You are **required** to add an `NSFW` tag if the presence is for an NSFW website.

### **`category`**

- The category **must** be one of the following listed on the [documentation](https://docs.premid.app/dev/presence/metadata#presence-categories).
- The presence must use a category that matches the content of the website. (for e.g., don't use `anime` when the website isn't related to anime).

### **`*regExp`** <br /> **`*iFrameRegExp`**

- Regular expressions **must** be valid. Please test your expressions with the tools listed on the [documentation](https://docs.premid.app/dev/presence/metadata#testing).

### **`readLogs`**

- Must be `boolean` value (e.g. `true` or `false`).
- Enables logs for your presence.

### **`warning`**

- Enables warning icon for prompting user that this presence needs more steps than only adding presence.
- Example of presence using this metadata variable is `VLC`.

### **`settings`**

- If you decide to make a format string (for e.g., `%song% by %artist%`), you must have the variables surrounded by a percent sign on either side. Variables like `%var`, `var%`, or `%%var%%` and anything in between are **not** permitted for the sake of standardization.
- The name of the settings must **not** be in all capital letters. For example, names such as `SHOW BROWSING STATUS` will **not** be permitted; however, names such as `Show Browsing Status` or `Show browsing status` are permitted.
- If you are using the `multiLanguage` option it can have the following types:
  - **Boolean** type which will only enable strings from [`general.json`](https://github.com/PreMiD/Localization/blob/master/src/Presence/general.json) from the Localization repo or from the presence file (e.g. when the name of the presence is YouTube, the extension will get strings from `youtube.json` too.)
  - **String** type (e.g. `youtube`) which will specify the name of the files that you want to get strings from.
  - **Array<String>** type (e.g. `["youtube", "discord"]`) which will specify the name of the files that you want to get strings from.

## [**presence.ts**](https://docs.premid.app/dev/presence/class)

> The code you write **must** be _well-written_ and **must** be _readable_ and all strings must be grammatically correct (grammar errors on websites can be ignored).

> Each presence follows a strict linting ruleset which will be checked during the review process. A couple of recommendations can be seen below. [TypeScript Plugin Recommendations for Strict Type Checking](https://github.com/typescript-eslint/typescript-eslint/tree/master/packages/eslint-plugin/docs/rules). [ESlint Recommendations](https://eslint.org/docs/rules). [Prettier](https://prettier.io/).

Here is a list of rules you must follow when writing your `presence.ts` file:

- **Always** declare a new instance of the `Presence` class before any other variable to avoid rare issues that may occur; this is not a requirement by design so it could be removed in the future.
- **Never** use custom functions when [native variants are available](https://docs.premid.app/dev/presence#files-explained); this makes sure fixes on the extension level also apply to your presences. You're free to use whatever you need if you do not find them listed in the docs.
- It is **forbidden** to code presences for a site without adding support to its primary language (for e.g., a YouTube presence coded with support only for Portueguese and Japanese, but not English itself.)
- The `smallImageKey` and `smallImageText` fields are intended to provide additional/secondary context (such as `playing/paused` for video sites, `browsing` for regular sites, and other cases) not to promote Discord profiles or anything unrelated to PreMiD.
- You are **not** allowed to access `localStorage`.
- When accessing cookies for stored data, please prefix the key with `PMD_`.
- You may only make HTTP/HTTPS requests to `premid.app` or the presence website API. If you are using external domains, you will be required to explain why it is necessary. Only allowed API to make request is [`Fetch API`](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API).
- Do **not** set fields in the presenceData object to undefined after it has been declared, use the `delete` keyword instead. (for e.g., use `delete data.startTimestamp` instead of `data.startTimestamp = undefined`)
- You are **not** allowed to write presences that change the functionality of a given website. This includes the addition, deletion, or modification of DOM elements.
- Presences that use buttons should follow extra requirements:
  - Redirects to main page are prohibited.
  - Promoting websites by them is prohibited.
  - They can't display information you couldn't fit in other fields.
  - Redirecting directly to audio/video stream is prohibited.


## [**tsconfig.json**](https://docs.premid.app/dev/presence/tsconfig)

> Do **not** write your own `tsconfig.json` file, use what has been provided on [documentation](https://docs.premid.app/dev/presence/tsconfig).

## Modification

> You **must** change the version in the **metadata** to be a higher value from the previous version when making changes to either the **presence.ts**, **iframe.ts** or **metadata.json**.

In some situations, presences may behave unexpectedly or could use some minor changes to improve their functionality. นี่คือกฎทั้งหมดทีคุณจะ**ต้อง**ปฏิบัติตามระหว่างการปรับเปลี่ยน Presences.

- คุณ**ไม่**ได้รับอนุญาตในการเขียน Presence ใหม่หรือเปลี่ยนแปลงผู้เขียนของมัน. If the presence author was banned from the official server or hasn't made the required changes within a month, you may contact a reviewer to see if you can to rewrite the presence.
- If you make modifications to a presence and change at least a **quarter** of the presence's codebase, you are allowed to add yourself as a contributor. Contact a reviewer for more information about this subject.
- Anyone may provide hotfixes to fix bugs; however, try **not** to make changes that are **not** required. Valid modifications include general fixes (code and typos), additions (descriptions and tags), missing files, etc. Do **not** change images if they are not outdated and are in specifications.

# Verification

> **All** code contributed to the store will be licensed under the `Mozilla Public License 2.0`.

> If you need to contact someone, please use our official Discord server. All reviewers will have the `Reviewer` role on their profile.

> Please keep in mind that the reviewers work voluntarily and manage other repositories in addition to this one, your pull request may not get reviewed until hours or even days after it has been created.

> **Always** have an up-to-date fork before creating your pull request. This will help limit false positives from the checks.

The most important process of presence development is getting your presence on the store. This is done by making a [pull request](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/creating-a-pull-request) on GitHub on the `PreMiD/Presences` repository. Our reviewers will confirm that your presence is up to standards and will push it onto the store.

<div>
  <h2 style="font-size: 2rem; margin-bottom: 0;">Presence Reviewers</h2>

  <a href="https://github.com/Bas950"><img src="https://github.com/Bas950.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
  <a href="https://github.com/Slowlife01"><img src="https://github.com/Slowlife01.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
  <a href="https://github.com/EncryptedDev"><img src="https://github.com/EncryptedDev.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
  <br />
</div>

## `Restrictions`

Repetitive offenses such as breaking guidelines, spamming pull requests, threats, or innapropriate behavior will get you banned from creating presences.

In this scenario, the following changes will occur:

- Presences under your management will be transferred to the PreMiD bot or another user (reviewer decision). The application id for each presence will be recreated under the new owner's name.
- All of your issues and pull requests (presence creation, presence contribution, etc) created following the ban will be prompty closed.
- Tickets created under your name regarding presence development will be deleted.

## `Reviewing`

บางสิ่งที่คุณควรรู้หลังจากที่เปิด pull request:

- It takes 2 reviewers to merge a pull request.
- ถ้า pull request ไม่มีการเคลื่อนไหวเป็นระยะเวลา 7 วัน pull request จะถูกปิดทันที.
- All checks **must** be passed in order to merge.
- ⚠️ You **must** provide new, unaltered screenshots (taken by you) showing a side-by-side comparison of your profile and the website to prove that your presence works. _You are allowed to stitch screenshots together for viewing pleasure_ This applies for both creation and modification.
- ⚠️ You are also **required** to include screenshots of the presence settings in the extension if supplied. An example can be seen [here](https://imgur.com/a/OD3sj5R).

## `Checks`

![Example of checks](https://i.imgur.com/T8agbnB.png)

ปัจจุบัน, Presence จะต้องผ่านการตรวจสอบ 3 ขั้นตอน. All of these checks help the reviewers determine whether your presence is suitable for deployment.

- `Codacy` คือบอทที่จะตรวจสอบคุณภาพของโค้ด. หากคุณพบว่ามีข้อผิดพลาดเกิดขี้น, คุณ**จำเป็น**ต้องแก้ไขพวกมัน. *Warning: Codacy doesn't always give you errors. Please look at CodeFactor warnings instead.*
- `CodeFactor` is a bot that checks for code quality. หากคุณพบว่ามีข้อผิดพลาดเกิดขี้น, คุณ**จำเป็น**ต้องแก้ไขพวกมัน.
- `Schema Validation` will scan your `metadata.json` file for any errors (for e.g., missing fields, invalid value types, etc.). If you ever see any new issues, you are also **required** to fix those. Adding a schema field to your `metadata.json` file will allow your text editor (if supported) to show you these errors during development.

## `กฎเพิ่มเติม`

- **Always** make sure to start your presence in the most appropriate folder, if its name starts with _any_ Latin letter then it must be under its alphabetical match (for e.g., `D/dアニメストア` or `G/Google`). Any other Unicode/non-Latin characters **must** be under the `#` folder (for e.g., `#/巴哈姆特`) and numbers under the `0-9` folder (for e.g., `0-9/4anime`).

After meeting all of the guidelines with the proper reviews and checks, your presence will be merged with the store.

# ข้อเสนอแนะ

If you have some suggestions about our guidelines, you should contact us @ [PreMiD's discord server](https://discord.premid.app) and we will check them!

# ผู้ที่มีส่วนช่วยเหลือทั้งหมด

`Revision 3` of the guidelines was written and was contributed to by the following individuals:

<div>
<a href="https://github.com/ririxidev"><img src="https://github.com/ririxidev.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
</div>

`Revision 2` of the guidelines was written and was contributed to by the following individuals:

<div>
<a href="https://github.com/CobyPowers"><img src="https://github.com/CobyPowers.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
</div>

`Revision 1` was maintained by the following individuals:

<div>
<a href="https://github.com/CobyPowers"><img src="https://github.com/CobyPowers.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
<a href="https://github.com/Bas950"><img src="https://github.com/Bas950.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
<a href="https://github.com/doomlerd"><img src="https://github.com/doomlerd.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
</div>
