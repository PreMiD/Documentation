---
title: Класс присутствия
description: Основной класс для каждого присутствия PreMiD
published: true
date: 2021-05-23T09:14:06.963Z
tags:
editor: markdown
dateCreated: 2021-02-21T21:13:14.449Z
---

# Класс Состояния

## Введение

Класс `Presence` очень полезен, так как он содержит базовые методы, необходимые для создания присутствия.

Когда Вы создаёте класс, Вам необходимо указать свойство `clientId`.

```typescript
const presence = new Presence({
  clientId: "514271496134389561" // Пример clientId
});
```

### Свойства

Доступны три свойства для класса `Presence`.

#### `clientId`

Это свойство необходимо для того, чтобы ваше присутствие работало, поскольку оно использует идентификатор вашего приложения для отображения своего логотипа и ресурсов. Вы можете получить это на свой [страница приложений](https://discordapp.com/developers/applications).

#### `injectOnComplete` — *устарел с 2.2.4*

При установке на `injectOnComplete` в `true` первое событие `UpdateData` для обоих `присутствия. ,` и `iframe.ts` файлы будут запущены только при полной загрузке страницы.

#### `appMode` — *устарел с 2.2.4*

При установке `appMode` на `true` и наличии для отправки пустой `PresenceData`, приложение будет показывать приложение (изображение и имя) в профиле пользователя, а не ничего.

## Методы

### `getActivity()`

Возвращает объект `PresenceData` о том, что отображает присутствие.

### `setActivity(PresenceData | Slideshow, Boolean)`

Устанавливает активностью профиля с соответствии с предоставленными данными.

Первый параметр требует интерфейс [`PresenceData`](#presencedata-interface) или класс [`Slideshow`](/dev/presence/slideshow) , чтобы получить всю информацию, которую вы хотите отобразить в вашем профиле.

Второй параметр определяет, что-нибудь presence играет или нет. Всегда используйте `true` , если вы предоставляете временные метки в `PresenceData`.

### `clearActivity()`

Очищает вашу текущую активность и заголовок в трее.

### `setTrayTitle(String)`

> Этот метод работает только на Mac OS. 
> 
> {.is-warning}

Устанавливает заголовок в идентификатор.

### `createSlideshow()`

Создает новый класс `слайд-шоу`.

```typescript
const slideshow = presence.createSlideshow();
```

Предлагается сделать это при создании экземпляра класса `Presence`:

```typescript
const presence = new Presence({
    clientId: "514271496134389561" // Пример clientId
  }),
  слайдшоу = presence.createSlideshow();
```

Вы можете найти документацию по `Slideshow` class [here](/dev/presence/slideshow).

### `getStrings(Object)`

Асинхронный метод, который позволяет извлекать переведенные строки из расширения.

Вы должны указывать ключами `Object` как ключ для строки, `keyValue` - строковое значение. С помощью этой конечной точки можно найти сборку переведенных строк: `https://api.premid.app/v2/langFile/presence/en`

```typescript
// Возвращает `Playing` и `Paused` строки
// из расширения.
const strings = await presence.getStrings({
  play: "general.playing",
  pause: "general.paused"
});

const playString = strings.play; // result: Играет
const pauseString = strings.pause; // result: Остановлен
```

Начиная с версии 2.2.0 расширения вы можете получить строки для определенного языка. Это хорошо работает с недавно добавленными `multiLanguage` вариант настройки.

Мы предлагаем вам использовать следующий код, чтобы он автоматически обновлял PresenceData, если пользователь меняет выбранный язык;

```typescript
async function getStrings() {
  return presence.getStrings(
    {
      play: "general.playing",
      pause: "general.paused"
    },
    // The ID is the ID of the multiLanguage setting.
    await presence.getSetting("ID").catch(() => "en");
  );
}

let strings = getStrings(),
  // The ID is the ID of the multiLanguage setting.
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

const playString = (await strings).play, // result: Playing
  pauseString = (await strings).pause; // result: Paused
```

### `getPageletiable(String)`

Возвращает переменную с сайта, если она существует.

**Предупреждение: Эта функция может привести к высокой загрузке процессора и лагам сайта, если она была вызвана слишком много раз.**

```typescript
const pageVar = presence.getPageletiable("pageVar");
console.log(pageVar); // Это зарегистрирует "Переменное содержимое"
```

### `getExtensionVersion(Boolean)`

Возвращает версию расширения, которое использует пользователь.

```typescript
getExtensionVersion(onlyNumeric?: boolean): строка | number;

const numeric = presence.getExtensionVersion();
консоль. og(numeric); // Журнал 210
const версия = presence.getExtensionVersion(false);
console.log(версия); // Журнал 2.1.0
```

### `getSetting(String)`

Возвращает значение настройки.

```typescript
var setting = await presence.getSetting("pdexID"); // Заменить pdexID идентификатором параметра
console.log(setting); // Сообщается установка в логи
```

### `hideSetting(String)`

Скрывает указанные настройки.

```typescript
presence.hideSetting("pdexID"); // Заменить pdexID идентификатором настройки
```

### `showSetting(String)`

Показывают данные настройки (работает только если настройка была скрыта).

```typescript
presence.showSetting("pdexID"); // Заменить pdexID идентификатором настройки
```

### `getLogs()`

Возвращает журналы консоли веб-сайтов.

```typescript
const logs = await presence.getLogs();
console.log(logs); // Журнал последних 100 логов (в массиве).
```

**Примечание:** Требует `readLogs` к быть `true` в `metadata.json` файл.

### `info(String)`

Выводит данное сообщение в консоли в формате, основанном на присутствии в стиле `info`.

```typescript
presence.info("Test") // Это протоколирует "test" в правильном стиле.
```

### `success(String)`

Печатает данное сообщение в консоли в формате основанном на присутствии в стиле `success`.

```typescript
presence.success("Test") // Это протоколирует "test" в правильном стиле.
```

### `error(String)`

Выводит данное сообщение в консоли в формате, основанном на присутствии в стиле `ошибки`.

```typescript
presence.error("Test") // Это протоколирует "test" в правильном стиле.
```

### `getTimestampsfromMedia(HTMLMediaElement)`

Возвращает 2 `snowflake` timestamps в `Array`, которые могут быть использованы для `startTimestamp` и `endTimestamp`.

```typescript
const timestamps = presence.getTimestampsfromMedia(document.querySelector(".video"));
presenceData.startTimestamp = timestamps[0];
presenceData.endTimestamp = timestamps[1];
```

**Заметка:** Данный `String` в querySelector является примером.

### `getTimestamps(Number, Number)`

Возвращает 2 `snowflake` отметки времени в `Array` это может быть использовано для `startTimestamp` и `endTimestamp`.

```typescript
const video = document.querySelector(".video"),
  timestamps = presence.getTimestamps(video.currentTime, video.duration);
presenceData.startTimestamp = timestamps[0];
presenceData.endTimestamp = timestamps[1];
```

**Заметка:** Данный `String` в querySelector является примером.

### `timestampFromFormat(String)`

Преобразует строку в формат `HH:MM:SS` или `MM:SS` или `SS` в целое (не возвращает snowflake timestamp).

```typescript
const currentTime = presence.timestampFromFormat(document.querySelector(".video-now").textContent),
  duration = presence.timestampFromFormat(document.querySelector(".video-end").textContent),
  timestamps = presence.getTimestamps(currentTime, duration);
presenceData.startTimestamp = timestamps[0];
presenceData.endTimestamp = timestamps[1];
```

**Заметка:** Данный `String` в querySelector является примером.

## `PresenceData` Интерфейс

При использовании метода `setActivity()` рекомендуется использовать интерфейса `presenceData`.

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
        <br>Используется если вы хотите отображать сколько <code>часов:минут:секунды</code> слева.
          <br>Вы должны преобразовать ваше время в <code>временную метку</code> или вы получите неправильный обратный отсчёт.
      </td>
      <td style="text-align:left"><code>Number</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">largeImageKey</td>
      <td style="text-align:left">Определяет логотип для присутствия.</td>
      <td style="text-align:left"><code>String</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">smallImageKey</td>
      <td style="text-align:left">Определяет маленький значок рядом с наличием&apos;с логотипа.</td>
      <td style="text-align:left"><code>String</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">smallImageText</td>
      <td style="text-align:left">Определяет текст, который будет показан пользователю, когда он наведет маленький значок
.</td>
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

```typescript
const presenceData: PresenceData = {
  details: "Моё название",
  state: "Мое описание",
  largeImageKey: "service_logo",
  smallImageKey: "small_service_icon",
  smallImageText: "Вы меня подогнали, и что сейчас? ,
  startTimestamp: 1564444631188,
  endTimestamp: 1564444634734,
  кнопок: [
    {
            ярлык: "Test button1",
            url: "https://premid. pp/"
        },
        {
            метка: "Кнопка тестирования2",
            url: "https://premid. pp/contributors"
        }
    ]
};
```

## События

События позволяют обнаруживать и обрабатывать некоторые внесённые изменения или вызовы. Вы можете подписаться на события с помощью метода `on`.

```typescript
presence.on("Данные обновить", асинхронный () => {
    // Выполняйте что-то, когда данные обновляются.
});
```

Доступно несколько событий:

#### `UpdateData`

Это событие запускается каждый раз, когда присутствие обновляется.

#### `iFrameData`

Срабатывает при получении данных из iFrame script.
