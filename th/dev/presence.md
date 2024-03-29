---
title: การพัฒนา Presence
description:
published: true
date: 2021-12-20T14:27:18.034Z
tags:
editor: markdown
dateCreated: 2020-06-11T18:04:02.843Z
---

> ตอนนี้ Presence ทั้งหมดถูกเก็บไว้ที่นี่: https://github.com/PreMiD/Presences 
> 
> {.is-info}

Version `2.x` introduces the [Presence Store](https://premid.app/store). และตอนนี้ผู้ใช้สามารถเพิ่มและลบ Presence ที่ชื่นชอบได้ผ่านทางหน้า[เว็บไซต์](https://premid.app/)

> ก่อนที่จะเริ่ม, ขอแนะนำอย่างสูงเลยว่าให้คุณไปดูแนวทางในการสร้าง Presence ของเราก่อน. 
> 
> {.is-warning}

- [แนวทาง](https://docs.premid.app/dev/presence/guidelines)
{.links-list}

# โครงสร้าง

All Presences are made using [TypeScript](https://www.typescriptlang.org/). [TypeScript](https://www.typescriptlang.org/) เป็นประเภทในการกำหนดค่ามากกว่า JavaScript, ตั้งนั้นการแก้และวินิจฉัยบัคจะเป็นอะไรที่ง่ายกว่ามาก.

## ความต้องการ

1. [Git](https://git-scm.com/)
2. [Node](https://nodejs.org/en/) (comes with [npm](https://www.npmjs.com/))

## การโคลนโปรเจ็ค

1. เปิดโปรแกรม Terminal และพิมพ์ `git clone https://github.com/PreMiD/Presences`.
2. เลือกโฟลเดอร์ที่คุณต้องการ
3. เปิดในโปรแกรมแก้ไขโค้ด

## Getting started

1. Open a new terminal in the `Presences` folder
2. Install repository dependencies using `npm i` (Or your package manager of choice)

### Creating a Presence
1. Run `npx pmd` (or run `pmd` with the package manager of your choice)
2. Select the first option
3. Fill in all prompted questions

### Compiling / Modifying a Presence
1. Run `npx pmd`
2. Select the second option
3. Enter the Presence name you want to edit > This will start a TypeScript compiler in that Presence's folder, now when you edit the `presence.ts` it will automatically compile the presence for you.
{.is-info}

For inspiration or examples on how to structure your Presence's code, take a look at existing Presences like 1337x or 9GAG

For more information about the `Presence` class click [here](/dev/presence/class).

Since v2.2.0 there are now Slideshows, this allows you to show multiple `PresenceData` interfaces on an interval, for more information click about the `Slideshow` class [here](/dev/presence/slideshow).

## Can't get certain data?!

A lot of websites are using [iframes](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe) ([Inlineframes](https://en.wikipedia.org/wiki/HTML_element#Frames)). These html tags can contain multiple sources such as videos. But they're not relevant every time. Some are hidden or just not actively used. Check if you can extract the information you need without them before you do unnecessary work.

1. Check for them in your browsers console (be sure that you are on the **Elements** tab).
2. Search (<kbd>CTRL</kbd>+<kbd>F</kbd> (Windows) or <kbd>CMD</kbd>+<kbd>F</kbd> (MacOS)).
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

# นำเข้า Presence ของคุณ

1. เปิดป๊อปอัพส่วนขยายในเบราว์เซอร์แล้วกด <kbd>Shift</kbd> ค้างไว้.
2. **นำเข้า Presence** หรือ **Load Presence** จะปรากฏขึ้นมา.
3. คลิกไปที่มันระหว่างที่คุณยังคงกดปุ่ม <kbd>Shift</kbd> อยู่.
4. เลือกโฟลเดอร์ /dist ของ Presence ของคุณ.

# สิ่งที่เป็นประโยชน์

## Hot-reloading

The website you are developing on is automatically reloading every time you save a file in your folder.

## Debugging

- You can put `console.log("Test");` between your code and see if your browser console gives you that output. If yes then go on and try again after the next function. If not then there is an error above.
- If that doesn't help you either then ask a presence developer on our [Discord server](https://discord.premid.app/) for help.

# Files explained

- [คลาส Presence](/dev/presence/class)
- [คลาส Slideshow](/dev/presence/slideshow)
- [คลาส iFrame](/dev/presence/iframe)
- [ไฟล์ Metadata](/dev/presence/metadata)
- [การกำหนดค่าไฟล์ Typescript](/dev/presence/tsconfig ""){.links-list}
