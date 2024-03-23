---
title: Класс присутствия
description: Основной класс для каждого Presence в PreMiD
published: true
date: 2022-05-26T18:03:00.000Z
tags:
editor: markdown
dateCreated: 2021-09-07T01:44:50.164Z
---

# Класс Presence

## Введение

Класс `Presence` очень полезен, так как он содержит базовые методы, необходимые для создания Presence.

Когда Вы создаёте класс, Вам необходимо указать свойство `clientId`.

```ts
const presence = new Presence({
  clientId: "514271496134389561" // Пример clientId
});
```

### Свойства

Доступны три свойства для класса `Presence`.

#### `clientId`

Это свойство необходимо для того, чтобы ваш Presence работал, поскольку оно использует идентификатор вашего приложения для отображения своего логотипа и ресурсов. Вы можете получить это на свой [страница приложений](https://discordapp.com/developers/applications).

#### `injectOnComplete` — *устарел с 2.2.4*

При установке на `injectOnComplete` в `true` первое событие `UpdateData` для обоих `присутствия. ,` и `iframe.ts` файлы будут запущены только при полной загрузке страницы.

#### `appMode` — *устарел с 2.2.4*

При установке `appMode` на `true` и наличии для отправки пустой `PresenceData`, приложение будет показывать приложение (изображение и имя) в профиле пользователя, а не ничего.

## Методы

### `getActivity()` — *устарел с 2.2.4*

Возвращает объект `PresenceData` о том, что отображает Presence.

### `setActivity(PresenceData | Slideshow, Boolean)`

Устанавливает активность профиля в соответствии с полученными данными.

Первый параметр требует интерфейс [`PresenceData`](#presencedata-interface) или класс [`Slideshow`](/dev/presence/slideshow) , чтобы получить всю информацию, которую вы хотите отобразить в вашем профиле.

Второй параметр определяет, воспроизводит Presence что-нибудь или нет. Всегда используйте `true` , если вы предоставляете временные метки в `PresenceData`.

### `clearActivity()`

Очищает вашу текущую активность и заголовок в трее.

### `setTrayTitle(tring)` - *Устарел с 2.2.3*

> Этот метод работает только на Mac OS. 
> 
> {.is-warning}

Устанавливает заголовок в Menubar.

### `createSlideshow()`

Создает новый класс `слайд-шоу`.

```ts
const slideshow = presence.createSlideshow();
```

Предлагается сделать это при создании экземпляра класса `Presence`:

```ts
const presence = new Presence({
    clientId: "514271496134389561" // Пример clientId
  }),
  slideshow = presence.createSlideshow();
```

Вы можете найти документацию по классу `Slideshow` [здесь](/dev/presence/slideshow).

### `getStrings(Object)`

Асинхронный метод, который позволяет извлекать переведенные строки из расширения.

Вам нужно передавать `Object` с ключами строк, `keyValue` - строковое значение. Список переведённых строк можно найти в этом endpoint'е: `https://api.premid.app/v2/langFile/presence/en`

```ts
// Возвращает `Playing` и `Paused` строки
// из расширения.
const strings = await presence.getStrings({
  play: "general.playing",
  pause: "general.paused"
});

const playString = strings.play; // result: Играет
const pauseString = strings.pause; // result: Остановлен
```

Начиная с версии 2.2.0 расширения вы можете получить строки для определенного языка. Это хорошо работает с недавно добавленной опцией `multiLanguage`.

Мы предлагаем вам использовать следующий код, чтобы он автоматически обновлял PresenceData, если пользователь меняет язык:

```ts
async function getStrings() {
  return presence.getStrings(
    {
      play: "general.playing",
      pause: "general.paused"
    },
    // ID — идентификатор настройки multiLanguage.
    await presence.getSetting("ID").catch(() => "en");
  );
}

let strings = getStrings(),
  // ID — идентификатор настройки multiLanguage.
  oldLang: string = await presence.getSetting("ID").catch(() => "en");

//! await presence.getSetting("ID").catch(() => "en");
  );
}

let strings: Promise<LangStrings> = getStrings(),
  // ID — идентификатор настройки multiLanguage.
// The ID is the ID of the multiLanguage setting.
const newLang = await presence.getSetting("ID").catch(() => "en");
if (oldLang !== newLang) {
  oldLang = newLang;
  strings = getStrings();
}

const playString = (await strings).play, // результат: Playing
  pauseString = (await strings).pause; // результат: Paused
```

### `getPageletiable(String)`

Возвращает переменную с сайта, если она существует.

**Предупреждение: Эта функция может привести к высокой загрузке процессора и лагам сайта, если она была вызвана слишком много раз.**

```ts
const pageVar = presence.getPageletiable("pageVar");
console.log(pageVar); // Выведет "Содержимое переменной"
```

### `getExtensionVersion(Boolean)`

Возвращает версию расширения, которое использует пользователь.

```ts
getExtensionVersion(onlyNumeric?: boolean): string | number;

const numeric = presence.getExtensionVersion();
console.log(numeric); // Выведет 210
const version = presence.getExtensionVersion(false);
console.log(version); // Выведет 2.1.0
```

### `getSetting(String)`

Возвращает значение настройки.

```ts
var setting = await presence.getSetting("pdexID"); // Замените pdexID идентификатором настройки
console.log(setting); // Выведет значение настройки
```

### `hideSetting(String)`

Скрывает указанные настройки.

```ts
presence.hideSetting("pdexID"); // Замените pdexID идентификатором настройки
```

### `showSetting(String)`

Показывают данные настройки (работает только если настройка была скрыта).

```ts
presence.showSetting("pdexID"); // Замените pdexID идентификатором настройки
```

### `getLogs()`

Возвращает журналы консоли веб-сайтов.

```ts
const logs = await presence.getLogs();
console.log(logs); // Журнал последних 100 логов (в массиве).
```

**Примечание:** Требует `readLogs` со значением `true` в файле `metadata.json`.

### `info(String)`

Выводит данное сообщение в консоли в формате, основанном на присутствии в стиле `info`.

```ts
presence.info("Test") // Выведет "test" в правильном стиле.
```

### `success(String)`

Выводит введённое сообщение в консоли в формате, основанном на присутствии в стиле `success`.

```ts
presence.success("Test") // Выведет "test" в правильном стиле.
```

### `error(String)`

Выводит введённое сообщение в консоли в формате, основанном на присутствии в стиле `ошибки`.

```ts
presence.error("Test") // Выведет "test" в правильном стиле.
```

### `getTimestampsfromMedia(HTMLMediaElement)`

Возвращает 2 временные метки `snowflake` в `Array`, которые могут быть использованы для `startTimestamp` и `endTimestamp`.

```ts
const timestamps = presence.getTimestampsfromMedia(document.querySelector(".video"));
presenceData.startTimestamp = timestamps[0];
presenceData.endTimestamp = timestamps[1];
```

**Заметка:** Данный `String` в querySelector является примером.

### `getTimestamps(Number, Number)`

Возвращает 2 временные метки `snowflake` в `Array`, которые могут быть использованы для `startTimestamp` и `endTimestamp`.

```ts
const video = document.querySelector(".video"),
  timestamps = presence.getTimestamps(video.currentTime, video.duration);
presenceData.startTimestamp = timestamps[0];
presenceData.endTimestamp = timestamps[1];
```

**Заметка:** Данный `String` в querySelector является примером.

### `timestampFromFormat(String)`

Преобразует string с форматом `HH:MM:SS` или `MM:SS`, или `SS` в integer (не возвращает временную метку snowflake).

```ts
const currentTime = presence.timestampFromFormat(document.querySelector(".video-now").textContent),
  duration = presence.timestampFromFormat(document.querySelector(".video-end").textContent),
  timestamps = presence.getTimestamps(currentTime, duration);
presenceData.startTimestamp = timestamps[0];
presenceData.endTimestamp = timestamps[1];
```

**Заметка:** Данный `String` в querySelector является примером.

## Интерфейс `PresenceData`

Интерфейс `PresenceData` рекомендуется использовать, когда вы используете метод `setActivity()`.

Этот интерфейс имеет следующие переменные, все они являются необязательными.

<table>
  <thead>
    <tr>
      <th style="text-align:left">Переменная</th>
      <th style="text-align:left">Описание</th>
      <th style="text-align:left">Тип</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">details</td>
      <td style="text-align:left">Первая строка в вашем presence, обычно используется в качестве заголовка.</td>
      <td style="text-align:left"><code>String</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">state</td>
      <td style="text-align:left">Вторая линия вашего presence.</td>
      <td style="text-align:left"><code>String</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">startTimestamp</td>
      <td style="text-align:left">Определяет текущее время.<br>
        Используется, если вы хотите отобразить, сколько <code>часов:минут:секунд</code> осталось.
          <br>Вы должны преобразовать ваше время в <code>временную метку</code> или вы получите неправильный обратный отсчёт.
      </td>
      <td style="text-align:left"><code>Number</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">endTimestamp</td>
      <td style="text-align:left">Определяет полную продолжительность.
        <br>Используется если вы хотите отображать сколько <code>часов:минут:секунды</code> осталось.
          <br>Вы должны преобразовать ваше время в <code>временную метку</code> или вы получите неправильный обратный отсчёт.
      </td>
      <td style="text-align:left"><code>Number</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">largeImageKey</td>
      <td style="text-align:left">Определяет логотип для presence.</td>
      <td style="text-align:left"><code>String</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">smallImageKey</td>
      <td style="text-align:left">Определяет маленький значок рядом с логотипом presence.</td>
      <td style="text-align:left"><code>String</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">smallImageText</td>
      <td style="text-align:left">Определяет текст, который будет отображаться пользователю при наведении курсора на небольшой
        значок.</td>
      <td style="text-align:left"><code>String</code>
      </td>
    </tr>
        <tr>
      <td style="text-align:left">buttons</td>
      <td style="text-align:left">Массив кнопок, макс. 2, метка является текстом кнопки, а url это ссылка.</td>
      <td style="text-align:left"><code>Array&lt;Object&gt;</code>
      </td>
    </tr>
  </tbody>
</table>

```ts
const presenceData: PresenceData = {
  details: "Моё название",
  state: "Моё описание",
  largeImageKey: Assets.Logo,
  smallImageKey: Assets.Reading, // Другие ассеты можно найти в index.d.ts
  smallImageText: "Ты навёлся на меня, что дальше?" ,
  startTimestamp: 1564444631188,
  endTimestamp: 1564444634734,
  buttons: [
    {
            label: "Тестовая кнопка1",
            url: "https://premid. app/"
        },
        {
            label: "Тестовая кнопка2",
            url: "https://premid.app/contributors"
        }
    ]
};
```

## События

События позволяют обнаруживать и обрабатывать некоторые внесённые изменения или вызовы. Вы можете подписаться на события с помощью метода `on`.

```ts
presence.on("UpdateData", async () => {
    // Выполняйте что-то, когда данные обновляются.
});
```

Доступно несколько событий:

#### `UpdateData`

Это событие запускается каждый раз, когда Presence обновляется.

#### `iFrameData`

Срабатывает при получении данных из скрипта iFrame.
