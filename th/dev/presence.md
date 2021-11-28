---
title: การพัฒนา Presence
description:
published: true
date: 2021-07-08T19:12:34.449Z
tags:
editor: markdown
dateCreated: 2020-06-11T18:04:02.843Z
---

> ตอนนี้ Presence ทั้งหมดถูกเก็บไว้ที่นี่: https://github.com/PreMiD/Presences 
> 
> {.is-info}

เวอร์ชัน `2.x` แนะนำให้ใช้ Presence จาก[ร้านค้า](https://premid.app/store) และตอนนี้ผู้ใช้สามารถเพิ่มและลบ Presence ที่ชื่นชอบได้ผ่านทางหน้า[เว็บไซต์](https://premid.app/)

> ก่อนที่จะเริ่ม, ขอแนะนำอย่างสูงเลยว่าให้คุณไปดูแนวทางในการสร้าง Presence ของเราก่อน. 
> 
> {.is-warning}

- [แนวทาง](https://docs.premid.app/dev/presence/guidelines)
{.links-list}

# โครงสร้าง

โค้ดของ presence ทั้งหมดเขียนอยู่ในภาษา [TypeScript](https://www.typescriptlang.org/). [TypeScript](https://www.typescriptlang.org/) เป็นประเภทในการกำหนดค่ามากกว่า JavaScript, ตั้งนั้นการแก้และวินิจฉัยบัคจะเป็นอะไรที่ง่ายกว่ามาก.

## การติดตั้ง

1. ติดตั้ง [Git](https://git-scm.com/).
2. ติดตั้ง [Nodejs](https://nodejs.org/en/) (พร้อมกับ [npm](https://www.npmjs.com/))
3. ติดตั้ง [TypeScript](https://www.typescriptlang.org/index.html#download-links) (เปิดเทอร์มินัลแล้วพิมพ์ `npm install -g typescript`)

## การโคลนโปรเจ็ค

1. เปิดโปรแกรม Terminal และพิมพ์ `git clone https://github.com/PreMiD/Presences`.
2. เลือกโฟลเดอร์ที่คุณต้องการ
3. เปิดในโปรแกรมแก้ไขโค้ด

## การสร้างโฟลเดอร์และไฟล์

1. ไปที่โฟลเดอร์ `websites` จากนั้นไปที่ โฟลเดอร์ ที่มีอักษรตัวแรกเหมือนกับ **ชื่อ** ( ไม่ใช่ URL) เซอร์วิสที่คุณอยากเพิ่ม.
2. สร้างโฟลเดอร์และตั้งชื่อให้เหมือนกับ**ชื่อ** (ไม่ใช่ URL) ของบริการที่คุณอยากจะเพิ่ม
3. สร้างไฟล์ `presence.ts` และ `tsconfig.json` ข้างใน
4. สร้างโฟลเดอร์ชื่อว่า `dist` ข้างใน
5. สร้างไฟล์ `metadata.json` ข้างในโฟลเดอร์ `dist`

## ป้อนข้อมูลในไฟล์ tsconfig.json

โปรดใส่โค้คต่อไปนี้ภายในไฟล์ `tsconfig.json`

```ts
{
  "extends": "../../../tsconfig.json",
  "compilerOptions": {
    "outDir": "./dist/"
  }
}
```

ถ้าต้องการที่จะเรียนรู้เพิ่มเติมเกี่ยวกับ Typescript คลิก [ที่นี่](/dev/presence/tsconfig)

## ป้อนข้อมูลในไฟล์ metadata.json

เราได้ทำตัวสร้างไฟล์ `metadata.json` ไว้สำหรับคนขี้เกียจแล้ว [กดตรงนี้เลย](https://eggsy.xyz/projects/premid/mdcreator) แต่เราก็ยังคงแนะนำให้อ่านทั้งหมดนี้, เพื่อที่คุณจะได้รู้ว่ามันทำงานอย่างไร.

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

โปรดคัดลอกโค้ดด้านบนและใส่ไปในไฟล์ `metadata.json`. และตอนนี้คุณก็สามารถเปลี่ยนค่าต่างๆได้แล้ว. โปรดทราบไว้ว่าค่าด้านล่างทั้งหมดนี้ไม่จำเป็นต้องมีในไฟล์ `metadata.json` ของคุณ, ถ้าคุณไม่คิดที่จะใช้พวกมันคุณต้องนำพวกมันออก.

- `contributors`
- `altnames`
- `regExp`
- `iframe`
- `iFrameRegExp`
- `readLogs`
- `settings`

**รู้จักกับค่าต่างๆ:**

<table>
  <thead>
    <tr>
      <th style="text-align:left">ตัวแปร</th>
      <th style="text-align:left">คำอธิบาย</th>
      <th style="text-align:left">ชนิด</th>
      <th style="text-align:left">ไม่บังคับ</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>author</b></td>
      <td style="text-align:left">Should contain an Object with the <code>name</code> and <code>id</code> of the presence developer. <code>name</code> คือชื่อผู้ใช้ดิสคอร์ดของคุณที่ไม่มีแท็ก (#0000) Id <code>ผู้ใช้</code> สามารถคัดลอกได้จากดิสคอร์ดโดยการเปิด
        โหมดผู้พัฒนาและคลิกขวาบนโปรไฟล์ของคุณ</td>
      <td style="text-align:left"><code>Object</code></td>
      <td style="text-align:left"><code>ไม่</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>contributors</b></td>
      <td style="text-align:left">Should contain an Object with the <code>name</code> and <code>id</code> of the presence developer. <code>name</code> คือชื่อผู้ใช้ดิสคอร์ดของคุณที่ไม่มีแท็ก (#0000) Id <code>ผู้ใช้</code> สามารถคัดลอกได้จากดิสคอร์ดโดยการเปิด
        โหมดผู้พัฒนาและคลิกขวาบนโปรไฟล์ของคุณ</td>
      <td style="text-align:left"><code>Array&lt;Object&gt;</code></td>
      <td style="text-align:left"><code>ใช่</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>service</b></td>
      <td style="text-align:left">The title of the service that this presence supports.<br>
      (Must be the same name as the folder where everything is in)</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>ไม่</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>altnames</b></td>
      <td style="text-align:left">Be able to search the presence using an alternative name.<br>
      Meant to be used for presences that have different names in different languages (e.g. Pokémon and 포켓몬스터).<br>
      You can also use it for presences that have special characters so you don't have to type those (e.g. Pokémon and Pokemon).</td>
      <td style="text-align:left"><code>Array&lt;String&gt;</code></td>
      <td style="text-align:left"><code>ใช่</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>description</b></td>
      <td style="text-align:left">Small description of the presence, you can use description of the service if you are out of ideas. คำอธิบายของคุณต้องมีค่าคีย์ที่ระบุภาษาและคำอธิบายในภาษานั้น ๆ สร้างคำอธิบายด้วยภาษา <i>ที่คุณเข้าใจ </i>, ผู้แปลภาษาของเราจะทำการแปลไฟล์ metadata ของคุณ</td>
      <td style="text-align:left"><code>Object</code></td>
      <td style="text-align:left"><code>ไม่</code></td>
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
      <td style="text-align:left"><code>ไม่</code></td>
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
      <td style="text-align:left"><code>ใช่</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>version</b></td>
      <td style="text-align:left">เวอร์ชั่น presence ของคุณ</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>ไม่</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>logo</b></td>
      <td style="text-align:left">ลิ้งโลโก้ของบริการ</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>ไม่</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>thumbnail</b></td>
      <td style="text-align:left">ลิ้งไปยังภาพขนาดย่อของ presence ของคุณ</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>ไม่</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>color</b></td>
      <td style="text-align:left">ค่า <code>#HEX</code> เราแนะนำให้ใช้สีหลักของบริการ
        ที่ presence ของคุณรองรับ</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>ไม่</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>tags</b></td>
      <td style="text-align:left">Array ของแท็กทั้งหมด, จะช่วยให้ผู้ใช้ ค้นหา presence ของคุณ บนเว็บไซต์ได้ง่ายขึ้น</td>
      <td style="text-align:left"><code>String, Array&lt;String&gt;</code></td>
      <td style="text-align:left"><code>ไม่</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>category</b></td>
      <td style="text-align:left">String ที่ใช้แสดงหมวดหมู่ที่ได้รับอิทธิพลจาก presence See the valid catergories <a href="https://docs.premid.app/dev/presence/metadata#presence-categories">here</a>.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>ไม่</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>iframe</b></td>
      <td style="text-align:left">กำหนดว่าจะใช้ <code>iFrames</code>.</td>
      <td style="text-align:left"><code>Boolean</code></td>
      <td style="text-align:left"><code>ใช่</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>iFrameRegExp</b></td>
      <td style="text-align:left">นิพจน์ทั่วไปที่ใช้ตรวจหา iframe ที่จะแทรก See regExp for more info.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>ใช่</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>readLogs</b></td>
      <td style="text-align:left">Defines whether the extension should be reading logs.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>ใช่</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>settings</b></td>
      <td style="text-align:left">An array of settings the user can change.<br>
      Read more about presence settings <a href="https://docs.premid.app/dev/presence/metadata#presence-settings">here</a>.</td>
      <td style="text-align:left"><code>Array&lt;Object&gt;</code></td>
      <td style="text-align:left"><code>ใช่</code></td>
    </tr>
  </tbody>
</table>

## เริ่มต้นกันเลย

```ts
const presence = new Presence({
  //The client ID of the Application created at https://discordapp.com/developers/applications
  clientId: "000000000000000000"
  }),
  //You can use this to get translated strings in their browser language
  strings = presence.getStrings({
    play: "presence.playback.playing",
    pause: "presence.playback.paused"
  });

/*
function myOutsideHeavyLiftingFunction(){
    //Grab and process all your data here

    // element grabs //
    // api calls //
    // variable sets //
}

setInterval(myOutsideHeavyLiftingFunction, 10000);
//Run the function separate from the UpdateData event every 10 seconds to get and set the variables which UpdateData picks up
*/

presence.on("UpdateData", async () => {
  /*UpdateData is always firing, and therefore should be used as your refresh cycle, or `tick`. This is called several times a second where possible.

    It is recommended to set up another function outside of this event function which will change variable values and do the heavy lifting if you call data from an API.*/

  const presenceData: PresenceData = {
    //The key (file name) of the Large Image on the presence. These are uploaded and named in the Rich Presence section of your application, called Art Assets
    largeImageKey: "key",
    //The key (file name) of the Small Image on the presence. These are uploaded and named in the Rich Presence section of your application, called Art Assets
    smallImageKey: "key",
    //The text which is displayed when hovering over the small image
    smallImageText: "Some hover text",
     //The upper section of the presence text
    details: "Browsing Page Name",
    //The lower section of the presence text
    state: "Reading section A",
    //The unix epoch timestamp for when to start counting from
    startTimestamp: 3133657200000,
    //If you want to show Time Left instead of Elapsed, this is the unix epoch timestamp at which the timer ends
    endTimestamp: 3133700400000
    //Optionally you can set a largeImageKey here and change the rest as variable subproperties, for example presenceData.type = "blahblah"; type examples: details, state, etc.
  };
  //Update the presence with all the values from the presenceData object
  if (presenceData.details) presence.setActivity(presenceData);
  //Update the presence with no data, therefore clearing it and making the large image the Discord Application icon, and the text the Discord Application name
  else presence.setActivity(); 
});
```

You can copy this into your `presence.ts` file and edit the values. Setting all the values is done inside of the updataData event.

For examples we suggest to look at the code of presences like: 1337x or 9GAG. For more information about the `Presence` class click [here](/dev/presence/class).

Since v2.2.0 there are now Slideshows, this allows you to show multiple `PresenceData` interfaces on an interval, for more information click about the `Slideshow` class [here](/dev/presence/slideshow).

## รับข้อมูลบางอย่างไม่ได้?!

A lot of websites are using [iframes](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe) ([Inlineframes](https://en.wikipedia.org/wiki/HTML_element#Frames)). These html tags can contain multiple sources such as videos. But they're not relevant every time. Some are hidden or just not actively used. Check if you can extract the information you need without them before you do unnecessary work.

1. Check for them in your browsers console (be sure that you are on the **Elements** tab).
2. ค้นหา (<kbd>CTRL</kbd>+<kbd>F</kbd> (Windows) หรือ <kbd>CMD</kbd>+<kbd>F</kbd> (MacOS)).
3. Execute `document.querySelectorAll("iframe")`.

If you find that your data is in a iFrame you need to do the following:

1. Create a `iframe.ts` file.
2. Set iFrame to `true` in your metadata file.
3. Filling in your iFrame file.

```ts
const iframe = new iFrame();
iframe.on("UpdateData", async () => {
  //Get all the data you need out of the iFrame save them in variables and then send them using iframe.send
  iframe.send({
    //sending data
    video: video,
    time: video.duration
  });
});
```

4. Making your presence file receive data from the iFrame file.

```ts
presence.on("iFrameData", (data) => {
  iFrameVideo = data.video;
  currentTime = data.time;
});
```

**Note:** This needs to be placed outside of the updateData event.

## Compiling

Open a console in your folder and type `tsc -w` to compile the `presence.ts` into the `/dist` folder.

# นำเข้า Presence

1. เปิดส่วนขยายใน Broswer แล้วกด <kbd>Shift</kbd> ค้างไว้
2. **นำเข้า Presence** หรือ **Load Presence** จะปรากฏขึ้นมา.
3. คลิกไปที่มันระหว่างที่คุณยังคงกดปุ่ม <kbd>Shift</kbd> อยู่.
4. เลือกโฟลเดอร์ /dist ของ Presence ของคุณ.

# Some helpful things

## Hot-reloading

The website you are developing on is automatically reloading every time you save a file in your folder.

## การแก้ไขจุดบกพร่อง

- คุณสามารถใส่ `console.log("Test");`  ภายในโค้ดของคุณและดูว่า Console Browser ของคุณให้ผลลัพธ์นั้นหรือไม่ ถ้าใช่ให้ไปลองอีกครั้งหลังฟังก์ชันถัดไป ถ้าไม่ใช่แสดงว่ามีข้อผิดพลาดอยู่ด้านบน
- If that doesn't help you either then ask a presence developer on our [Discord server](https://discord.premid.app/) for help.

# Files explained

- [คลาส Presence](/dev/presence/class)
- [คลาส Slideshow](/dev/presence/slideshow)
- [คลาส iFrame](/dev/presence/iframe)
- [ไฟล์ metadata](/dev/presence/metadata)
- [การกำหนดค่าไฟล์ Typescript](/dev/presence/tsconfig ""){.links-list}
