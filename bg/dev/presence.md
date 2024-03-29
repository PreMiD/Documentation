---
title: Разработване на Presence
description:
published: true
date: 2021-12-20T14:27:18.034Z
tags:
editor: markdown
dateCreated: 2020-06-11T18:04:02.843Z
---

> Всички presence вече се съхраняват тук: https://github.com/PreMiD/Presences 
> 
> {.is-info}

Версия `2.x` въвежда [магазина за presences](https://premid.app/store). Потребителите вече имат възможност ръчно да добавят и премахват любимите си presences чрез потребителския интерфейс на [уебсайта](https://premid.app/).

> Преди да започнете, ви препоръчваме да се запознаете с нашите presence насоки. 
> 
> {.is-warning}

- [Насоки](https://docs.premid.app/dev/presence/guidelines)
{.links-list}

# Структура

Всички presence са кодирани на [TypeScript](https://www.typescriptlang.org/). [TypeScript](https://www.typescriptlang.org/) има някои допълнителни пикантни дефиниции на types в сравнение с JavaScript, така че поправянето и идентифицирането на грешки е много по-лесно.

## Изисквания

1. [Git](https://git-scm.com/)
2. Изтегли [Node](https://nodejs.org/en/) (идва със [npm](https://www.npmjs.com/)).

## Клониране на проекта

1. Отворете терминал и напишете `git clone https://github.com/PreMiD/Presences`.
2. Избери папка по твой избор.
3. Отвори го в твоя редактор на код.

## Създаване на папки и файлове

1. Отворете нов терминал в папката `Presences`
2. Инсталирайте repository dependencies с помощта на `npm i` (Или вашия пакетен мениджър по избор)

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

# Зареждане на Presence

1. Open the extension popup in the browser and hold the <kbd>Shift</kbd> button on your keyboard.
2. **Load Presence** will appear in the Presences section.
3. Click on it while you are still holding the <kbd>Shift</kbd> button.
4. Select the /dist folder of your presence.

# Някои полезни неща

## Горещо презареждане

The website you are developing on is automatically reloading every time you save a file in your folder.

## Отстраняване на грешки

- You can put `console.log("Test");` between your code and see if your browser console gives you that output. If yes then go on and try again after the next function. If not then there is an error above.
- If that doesn't help you either then ask a presence developer on our [Discord server](https://discord.premid.app/) for help.

# Обяснение на файловете

- [Presence клас](/dev/presence/class)
- [Slideshow клас](/dev/presence/slideshow)
- [iFrame клас](/dev/presence/iframe)
- [Metadata File](/dev/presence/metadata)
- [TypeScript Конфигурация](/dev/presence/tsconfig ""){.links-list}
