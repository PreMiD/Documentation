---
title: Presence Development
description:
published: true
date: 2021-12-20T14:27:18.034Z
tags:
editor: markdown
dateCreated: 2020-06-11T18:04:02.843Z
---

> All presences are now stored here: https://github.com/PreMiD/Presences 
> 
> {.is-info}

Version `2.x` introduces the [Presence Store](https://premid.app/store). Users now have the ability to manually add and remove their favourite presences through the user interface of the [website](https://premid.app/).

> Before getting started, it is highly recommended that you look at our presence guidelines. 
> 
> {.is-warning}

- [הנחיות](https://docs.premid.app/dev/presence/guidelines)
{.links-list}

# Structure

All Presences are made using [TypeScript](https://www.typescriptlang.org/). [TypeScript](https://www.typescriptlang.org/) has some extra spicy type definitions over JavaScript, so fixing and identifying bugs is way easier.

## Requirements

1. [Git](https://git-scm.com/)
2. [Node](https://nodejs.org/en/) (comes with [npm](https://www.npmjs.com/))

## שכפל את הפרויקט

1. Open a terminal and type `git clone https://github.com/PreMiD/Presences`.
2. בחר תיקיה לפי בחירתך.
3. פתח אותו בעורך הקוד שלך.

## Getting started

1. Open a new terminal in the `Presences` folder
2. Install repository dependencies using `npm i` (Or your package manager of choice)

### יצירת נוכחות
1. Run `npx pmd` (or run `pmd` with the package manager of your choice)
2. בחר באפשרות הראשונה
3. Fill in all prompted questions

### Compiling / Modifying a Presence
1. Run `npx pmd`
2. בחר באפשרות השנייה
3. הזן את שם הנוכחות שברצונך לערוך > זה יתחיל מהדר TypeScript בתיקיה של אותה נוכחות, כעת כאשר אתה עורך את ה-`presence.ts` הוא יקמפל את הנוכחות עבורך באופן אוטומטי.
{.is-info}

For inspiration or examples on how to structure your Presence's code, take a look at existing Presences like 1337x or 9GAG

For more information about the `Presence` class click [here](/dev/presence/class).

Since v2.2.0 there are now Slideshows, this allows you to show multiple `PresenceData` interfaces on an interval, for more information click about the `Slideshow` class [here](/dev/presence/slideshow).

## Can't get certain data?!

A lot of websites are using [iframes](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe) ([Inlineframes](https://en.wikipedia.org/wiki/HTML_element#Frames)). These html tags can contain multiple sources such as videos. But they're not relevant every time. חלקם מוסתרים או פשוט לא בשימוש פעיל. בדוק אם אתה יכול לחלץ את המידע שאתה צריך בלעדיהם לפני שאתה עושה עבודה מיותרת.

1. Check for them in your browsers console (be sure that you are on the **Elements** tab).
2. Search (<kbd>CTRL</kbd>+<kbd>F</kbd> (Windows) or <kbd>CMD</kbd>+<kbd>F</kbd> (MacOS)).
3. Execute `document.querySelectorAll("iframe")`.

אם אתה מגלה שהנתונים שלך נמצאים ב-iFrame, עליך לבצע את הפעולות הבאות:

1. Create a `iframe.ts` file.
2. הגדר את iFrame ל-`true` בקובץ המטא נתונים שלך.
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

4. גורם לקובץ הנוכחות שלך לקבל נתונים מקובץ iFrame.

```ts
presence.on("iFrameData", (data) => {
  iFrameVideo = data.video;
  currentTime = data.time;
});
```

**Note:** This needs to be placed outside of the updateData event.

# Loading your Presence

1. פתח את התוסף הקופץ בדפדפן והחזק את כפתור <kbd>Shift</kbd> במקלדת שלך.
2. **Load Presence** will appear in the Presences section.
3. לחץ עליו בזמן שאתה עדיין מחזיק את הלחצן <kbd>Shift</kbd>.
4. Select the /dist folder of your presence.

# Some helpful things

## Hot-reloading

The website you are developing on is automatically reloading every time you save a file in your folder.

## Debugging

- You can put `console.log("Test");` between your code and see if your browser console gives you that output. If yes then go on and try again after the next function. If not then there is an error above.
- If that doesn't help you either then ask a presence developer on our [Discord server](https://discord.premid.app/) for help.

# Files explained

- [Presence Class](/dev/presence/class)
- [Slideshow Class](/dev/presence/slideshow)
- [iFrame Class](/dev/presence/iframe)
- [Metadata File](/dev/presence/metadata)
- [TypeScript Configuration](/dev/presence/tsconfig ""){.links-list}
