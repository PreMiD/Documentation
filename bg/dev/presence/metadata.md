---
title: Metadata.json
description: Съдържа основни данни за Presence
published: true
date: 2021-12-20T14:27:18.034Z
tags:
editor: markdown
dateCreated: 2020-06-11T18:04:52.965Z
---

# Metadata.json

Ако искате да публикувате presence в магазина и да го заредите чрез разширението, трябва да създадете `metadata.json` файл във вашата `dist` папка.

Пример за този файл можете да намерите по-долу.

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

## Разбиране на файла metadata.json

Този пример изглежда наистина странен, нали? Не се притеснявайте, не е толкова трудно да разберете за какво служи всяка променлива.

<table>
  <thead>
    <tr>
      <th style="text-align:left">Променлива</th>
      <th style="text-align:left">Описание</th>
      <th style="text-align:left">Вид</th>
      <th style="text-align:left">По избор</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>author</b></td>
      <td style="text-align:left">Трябва да съдържа Object с <code>името</code> и <code>ид-то</code> на разработчика на присъствие. <code>име</code> е вашето потребителско име в Discord без идентификатора(#0000). Потребителският <code>id</code> може да бъде копиран от Discord, като активирате функцията за разработчици
        и щракнете с десния бутон на мишката върху профила си.</td>
      <td style="text-align:left"><code>Object</code></td>
      <td style="text-align:left"><code>Не</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>contributors</b></td>
      <td style="text-align:left">Трябва да съдържа Object с <code>name</code> и <code>id</code> на сътрудника. <code>име</code> е вашето потребителско име в Discord без идентификатора(#0000). Потребителският <code>id</code> може да бъде копиран от Discord, като активирате функцията за разработчици
        и щракнете с десния бутон на мишката върху профила си.</td>
      <td style="text-align:left"><code>Array&lt;Object&gt;</code></td>
      <td style="text-align:left"><code>Да</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>service</b></td>
      <td style="text-align:left">Заглавието на услугата, която този presence поддържа.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Не</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>altnames</b></td>
      <td style="text-align:left">Да можете да търсите presence използвайките алтернативно име.<br>
      Предназначено за presence, които имат различни имена на различни езици. (напр.Pokémon и 포켓몬스터).<br>
      Можете да го използвате и за presence, които имат специални символи, за да не се налага да ги въвеждате (напр. Pokémon и Pokemon).</td>
      <td style="text-align:left"><code>Array&lt;String&gt;</code></td>
      <td style="text-align:left"><code>Да</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>description</b></td>
      <td style="text-align:left">Описание на услугата <b>НЕ</b> на вашия presence. Описанието ви трябва да има стойности на двойката ключове, които посочват езика и описанието на конкретния език. Направете описания с езиците, <i>които знаете</i>, нашите преводачи ще направят промени във вашия файл с метаданни. Прегледайте категорията за езици на presence, за да видите списък. </td>
      <td style="text-align:left"><code>Object</code></td>
      <td style="text-align:left"><code>Не</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>url</b></td>
      <td style="text-align:left">URL адрес на услугата.<br>
      <b>Пример:</b><code>vk.com</code><br>
      <b>Този URL адрес трябва да съвпада с URL адреса на уебсайта, тъй като ще се използва за определяне на това дали това е уебсайтът, в който да се инжектира скриптът. Това може да се използва само като Array, когато има повече от един URL адрес.</b></td>
      <td style="text-align:left"><code>String, Array&lt;String&gt;</code></td>
      <td style="text-align:left"><code>Не</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>regExp</b></td>
      <td style="text-align:left">Regular expression String използвани за съвпадение на URL адреси.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Да</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>version</b></td>
      <td style="text-align:left">Версия на вашето присъствие.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Не</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>logo</b></td>
      <td style="text-align:left">Връзка към логото на услугата.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Не</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>thumbnail</b></td>
      <td style="text-align:left">URL адрес към thumbnail-а на вашия presence.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Не</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>color</b></td>
      <td style="text-align:left"><code>#HEX</code> стойност. Препоръчваме ви да използвате основния цвят на услугата
        която вашето присъствие поддържа.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Не</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>category</b></td>
      <td style="text-align:left">Редица, използвана за представяне на категорията, в която попада вашия presence.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Не</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>tags</b></td>
      <td style="text-align:left">Array-ят с тагове ще помогне на потребителите да търсят вашия presence в уебсайта.</td>
      <td style="text-align:left"><code>String, Array&lt;String&gt;</code></td>
      <td style="text-align:left"><code>Не</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>iframe</b></td>
      <td style="text-align:left">Определя дали да се използват <code>iFrames</code></td>
      <td style="text-align:left"><code>Boolean</code></td>
      <td style="text-align:left"><code>Да</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>iFrameRegExp</b></td>
      <td style="text-align:left">Regular expression selector, който избира iframe, в който да се инжектира.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Да</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>readLogs</b></td>
      <td style="text-align:left">Определя дали разширението трябва да чете записите.</td>
      <td style="text-align:left"><code>Boolean</code></td>
      <td style="text-align:left"><code>Да</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>settings</b></td>
      <td style="text-align:left">Array от настройки, които потребителят може да промени</td>
      <td style="text-align:left"><code>Array&lt;Object&gt;</code></td>
      <td style="text-align:left"><code>Да</code></td>
    </tr>
  </tbody>
</table>

## Regular Expressions

Ако искате да научите regular expressions, ето няколко уебсайта.

#### Обучение

• [Бърз стартов видеоклип](https://youtu.be/sXQxhojSdZM) • [RegexOne](https://regexone.com/) • [Regular Expressions информация](https://www.regular-expressions.info/tutorial.html)

#### Тестване

• [Regexr](https://regexr.com/) • [Regex101](https://regex101.com/)

## Presence езици

PreMiD е полиглотска услуга, което означава, че са налични множество езици за свързване на потребители от цял свят. Пълният списък на езиците може да бъде намерен в тази [крайна точка на нашия API](https://api.premid.app/v2/langFile/list). За да персонализирате още повече вашия presence, можете да позволите на потребителите да избират езика на показване на присъствието си. Вижте [`multiLanguage`](#multilanguage) за още информация.

## Настройки на presence
Задайте интерактивни настройки, така че потребителите да могат да персонализират вашия presence!
```json
"settings": [
  {
    "id": "ID",
    "multiLanguage": true //Вижте https://docs.premid.app/dev/presence/metadata#multilanguage
  },
  {
    "id": "ID",
    "title": "ЗАГЛАВИЕ",
    "icon": "FONTAWESOME ИКОНА", //Пример: "fas fa-info"
    "value": true //Boolean стойност ще го превърне в превключвател за включване/изключване със стойността по подразбиране
  },
  {
    "id": "ИД",
    "if": {
      "ID": true //Ако друга настройка е равна на тази стойност (true/false/0/1/etc.), ще се покажете този бутон
    },
    "title": "ЗАГЛАВИЕ",
    "icon": "FONTAWESOME ИКОНА",
    "value": "\"%song%\" от %artist%", //Поставянето на string ще превърне настройката във input, където можете да използвате потребителски вход.
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

#### Introduction

The `multiLanguage` setting is used to allow users to manually select the language they want to presence to be shown in. This requires you to use strings from our [API](https://api.premid.app/v2/langFile/presence/en), for information on how to add strings click [here](https://docs.premid.app/dev/presence/metadata#adding-new-strings).

#### Setup

The `multiLanguage` setting is a special case, it doesn't require a `title` nor `icon` nor `value` or `values` like other settings but it does require you some more things to setup!

The `multiLanguage` key can be set to the following:

`true`: use this if you are only going to use strings of the `general.json` file and the `<service>.json` file of the [Localization Repository](https://github.com/PreMiD/Localization/tree/master/src/Presence). `string`: name of the file excluding the extension (.json) inside the [Localization Repository](https://github.com/PreMiD/Localization/tree/master/src/Presence) (excluding the `general` file, since it's always loaded). Only common languages of both the `general` and inputted file will be listed. `Array<String>`: if you are using more than one file inside the [Localization Repository](https://github.com/PreMiD/Localization/tree/master/src/Presence) you can specify all the values in an array (excluding the `general` file, since it's always loaded). Only common languages of all the files will be listed.

#### Adding new strings

**Note:** Adding custom strings for a presence is only allowed if it has more than 1000 users.

##### Клониране на проекта

1. Open a terminal and type `git clone https://github.com/PreMiD/Localization`.
2. Избери папка по твой избор.
3. Отвори го в твоя редактор за кодиране.

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

### Methods

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
      <th style="text-align:left">Category</th>
      <th style="text-align:left">Име</th>
      <th style="text-align:left">описание</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>anime</b></td>
      <td style="text-align:left"><b>Аниме</b></td>
      <td style="text-align:left">Anything related to anime, from forums to video streaming platforms.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>games</b></td>
      <td style="text-align:left"><b>Игри</b></td>
      <td style="text-align:left">Any website that has game related content, such as <code>Kahoot</code> or <code>Skribbl.io</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>music</b></td>
      <td style="text-align:left"><b>Музика</b></td>
      <td style="text-align:left">These are websites that offer music related content, whether that be streaming or downloading.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>socials</b></td>
        <td style="text-align:left"><b>Социални</b></td>
      <td style="text-align:left">Уебсайтове, които се използват с цел създаване и споделяне на съдържание или за участие в други форми на социални мрежи.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>videos</b></td>
        <td style="text-align:left"><b>Видеоклипове и Стриймове</b></td>
      <td style="text-align:left">Уебсайтове, които служат за предоставяне на видеоклипове и стриймове.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>other</b></td>
      <td style="text-align:left"><b>Други</b></td>
      <td style="text-align:left">Всичко, което не попада в конкретна категория, изброена по-горе.</td>
    </tr>
  </tbody>
</table>

