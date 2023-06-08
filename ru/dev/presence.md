---
title: Разработка Presence
description:
published: true
date: 2021-12-20T14:27:18.034Z
tags:
editor: markdown
dateCreated: 2020-06-11T18:04:02.843Z
---

> Все presences теперь хранятся здесь: https://github.com/PreMiD/Presences 
> 
> {.is-info}

Версия `2.x` представляет [магазин Presence](https://premid.app/store). Теперь у пользователей есть возможность вручную добавлять и удалять свои любимые presences через [сайт](https://premid.app/).

> Прежде чем приступить, настоятельно рекомендуем ознакомиться с нашим руководством по разработке pressence. 
> 
> {.is-warning}

- [Рекомендации](https://docs.premid.app/dev/presence/guidelines)
{.links-list}

# Структура

Все Presences написаны на [TypeScript](https://www.typescriptlang.org/). В отличие от JavaScript, [TypeScript](https://www.typescriptlang.org/) имеет несколько дополнительных определений типов, поэтому выявлять и исправлять ошибки намного проще.

## Требования

1. [Git](https://git-scm.com/)
2. [Node](https://nodejs.org/en/) (в комплекте с [npm](https://www.npmjs.com/))

## Клонирование проекта

1. Откройте терминал и введите команду `git clone https://github.com/PreMiD/Presences`.
2. Выберите папку по вашему выбору.
3. Откройте его в редакторе кода.

## Подготовка

1. Откройте новый терминал в папке `Presences`
2. Установите зависимости репозитория с помощью `npm i` (или вашего менеджера пакетов по выбору)

### Создание Presence
1. Запустите `npx pmd` (или запустите `pmd` с помощью менеджера пакетов по вашему выбору)
2. Выберите первый вариант
3. Заполните все предложенные вопросы

### Компиляция / Модификация Presence
1. Запустите `npx pmd`
2. Выберите второй вариант
3. Введите название Presence, которое вы хотите отредактировать > это запустит компилятор TypeScript в папке этого Presence, теперь, если вы измените файл `presence.ts`, то это запустит автоматическую компиляцию Presence для вас.
{.is-info}

Для вдохновения или изучения примеров того, как правильно структурировать код вашего Presence, посмотрите на существующие Presence, например: 1337x или 9GAG

Для получения дополнительной информации о классе `Presence` нажмите [здесь](/dev/presence/class).

Начиная с версии 2.2.0 появились слайд-шоу, позволяющие показывать несколько интерфейсов `PresenceData` с интервалом, подробнее о классе `Slideshow` [здесь](/dev/presence/slideshow).

## Не удается получить нужные данные?!

Многие веб-сайты используют [iframes](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe) ([Inlineframes](https://en.wikipedia.org/wiki/HTML_element#Frames)). Данные HTML-теги могут содержать несколько источников, например, видео. Однако не всегда являются полезными. Некоторые из них скрыты или просто не используются. Пожалуйста, проверьте, сможете ли вы извлечь нужную информацию без них, чтобы не выполнять лишнюю работу.

1. Проверьте их в консоли браузера (убедитесь, что вы находитесь на вкладке **Элементы**).
2. Поиск (<kbd>CTRL</kbd>+<kbd>F</kbd> (Windows) или <kbd>CMD</kbd>+<kbd>F</kbd> (MacOS)).
3. Выполните `document.querySelectorAll("iframe")`.

Если вы заметили, что необходимые данные находятся в iFrame, вам нужно выполнить следующее:

1. Создайте файл `iframe.ts`.
2. Установите для iFrame значение `true` в файле метаданных.
3. Заполните ваш файл iFrame.

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

4. Сделайте так, чтобы ваш файл Presence получал данные из файла iFrame.

```ts
presence.on("iFrameData", (data) => {
  iFrameVideo = data.video;
  currentTime = data.time;
});
```

**Примечание:** Это должно быть размещено вне события updateData.

# Загрузка вашего присутствия

1. Откройте панель расширения в вашем браузере и зажмите кнопку <kbd>Shift</kbd> на вашей клавиатуре.
2. **Загрузить Presence** появится в разделе Presences.
3. Нажмите на кнопку, удерживая клавишу <kbd>Shift</kbd>.
4. Выберите папку /dist вашего Presence.

# Полезные советы

## Быстрая перезагрузка

Веб-сайт, разрабатываемый вами, будет автоматически перезагружаться при каждом сохранении файла.

## Отладка

- Вы можете разместить `console.log("Test");` между строками вашего кода и проверить наличие вывода в консоли браузера. Если выводится, то продолжайте и повторите попытку после следующей функции. Если нет, то ошибка выше.
- Если вам это не поможет, вы можете задать вопрос разработчику Presence на нашем [Discord сервере](https://discord.premid.app/).

# Описание файлов

- [Класс Presence](/dev/presence/class)
- [Класс Slideshow](/dev/presence/slideshow)
- [Класс iFrame](/dev/presence/iframe)
- [Файл метаданных](/dev/presence/metadata)
- [Настройка TypeScript](/dev/presence/tsconfig ""){.links-list}
