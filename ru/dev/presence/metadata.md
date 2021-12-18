---
title: Metadata.json
description: Содержит основные данные о присутствии
published: true
date: 2021-02-07T17:12:06.799Z
tags:
editor: markdown
dateCreated: 2020-06-11T18:04:52.965Z
---

# Metadata.json

Если вы хотите опубликовать присутствие в магазине и загрузить его через расширение, вы должны создать файла `metadata.json` в папке `dist`.

Пример этого файла можно найти ниже.

```ts
{
  "$schema": "https://schemas.premid.app/metadata/1.5",
  "author": {
    "name": "ПОЛЬЗОВАТЕЛЬ",
    "id": "ID"
  },
  "contributors": [{
    "name": "ПОЛЬЗОВАТЕЛЬ",
    "id": "ID"
  }],
  "service": "СЕРВИС",
  "altnames": ["СЕРВИС"],
  "description": {
    "en": "ОПИСАНИЕ"
  },
  "url": "ССЫЛКА",
  "regExp": "REGEXP",
  "iFrameRegExp": "REGEXP",
  "version": "ВЕРСИЯ",
  "logo": "ССЫЛКА",
  "thumbnail": "ССЫЛКА",
  "color": "#45A8FC",
  "category": "КАТЕГОРИЯ",
  "tags": ["ТЕГ1", "ТЕГ2"],
  "iframe": false,
  "settings": [
    {
      "id": "ID",
      "title": "ОТОБРАЖАЕМЫЙ ЗАГОЛОВОК",
      "icon": "ИКОНКА FONTAWESOME",
      "value": true
    },
    {
      "id": "ID",
      "if": {
        "ID": true
      },
      "title": "ОТОБРАЖАЕМЫЙ ЗАГОЛОВОК",
      "icon": "ИКОНКА FONTAWESOME",
      "value": "«%song%» — %artist%",
      "placeholder": "используйте %song% или %artist%"
    },
    {
      "id": "ID",
      "title": "ОТОБРАЖАЕМЫЙ ЗАГОЛОВОК",
      "icon": "ИКОНКА FONTAWESOME",
      "value": 0,
      "values": ["1", "2", "и т. д."]
    }
  ]
}
```

## Описание файла metadata.json

Этот пример выглядит странно, да? Не волнуйтесь, это не так уж и сложно понять для чего каждая из переменных.

<table>
  <thead>
    <tr>
      <th style="text-align:left">Переменная</th>
      <th style="text-align:left">Описание</th>
      <th style="text-align:left">Тип</th>
      <th style="text-align:left">Необязательно</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>author</b></td>
      <td style="text-align:left">Должен содержать Object с <code>name</code> и <code>id</code> участника. имя пользователя Discord без идентификатора (#0000). Пользователь <code>id</code> может быть скопирован из Discord, включив разработчик
        режим и правый клик на вашем профиле.</td>
      <td style="text-align:left"><code>Object</code></td>
      <td style="text-align:left"><code>Нет</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>contributors</b></td>
      <td style="text-align:left">Должен содержать Object с <code>name</code> и <code>id</code> участника. имя пользователя Discord без идентификатора (#0000). Пользователь <code>id</code> может быть скопирован из Discord, включив разработчик
        режим и правый клик на вашем профиле.</td>
      <td style="text-align:left"><code>Array&lt;Object&gt;</code></td>
      <td style="text-align:left"><code>Да</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>service</b></td>
      <td style="text-align:left">Название услуги, которую поддерживает это присутствие.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Нет</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>altnames</b></td>
      <td style="text-align:left">Уметь искать присутствие, используя альтернативное имя.<br>
      Предназначен для использования для присутствий с разными названиями на разных языках. (e.g. Pokémon and 포켓몬스터).<br>
      Вы также можете использовать его для присутствий со специальными символами, поэтому вам не нужно их вводить (e.g. Pokémon and Pokemon).</td>
      <td style="text-align:left"><code>Array&lt;String&gt;</code></td>
      <td style="text-align:left"><code>Да</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>description</b></td>
      <td style="text-align:left">Описание сервиса <b>НЕ</b> присутствия. Ваше описание должно иметь значения пары ключей, которые указывают на язык, и описание на этом языке. Сделайте описания языков <i>, которые вы знаете</i>, наши переводчики внесут изменения в ваш файл метаданных. Можно посмотреть список категорию для языков присутствия. </td>
      <td style="text-align:left"><code>Object</code></td>
      <td style="text-align:left"><code>Нет</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>url</b></td>
      <td style="text-align:left">URL сервиса.<br><b>Пример:</b><code>vk.com</code><br>
        <b>Этот URL должен совпадать с URL сайта, так как он будет использоваться для определения сайта для вставки скрипта. Это может быть использовано в качестве массива только при наличии более URL's.</b></td>
      <td style="text-align:left"><code>String, Array&lt;String&gt;</code></td>
      <td style="text-align:left"><code>Нет</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>regExp</b></td>
      <td style="text-align:left">Строка регулярного выражения, используемая для сопоставления Url-адресов.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Да</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>version</b></td>
      <td style="text-align:left">Версия вашего присутствия.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Нет</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>logo</b></td>
      <td style="text-align:left">Ссылка на сервис&apos;с логотипом</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Нет</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>thumbnail</b></td>
      <td style="text-align:left">Ссылка на миниатюру вашего присутствия.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Нет</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>color</b></td>
      <td style="text-align:left"><code>#HEX</code> значение. Мы рекомендуем использовать основной цвет сервиса,
        что ваше присутствие поддерживает.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Нет</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>category</b></td>
      <td style="text-align:left">Строка, используемая для представления категории, под которую попадает присутствие.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Нет</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>tags</b></td>
      <td style="text-align:left">Массив с тегами, они помогут пользователям искать ваше присутствие на сайте.</td>
      <td style="text-align:left"><code>String, Array&lt;String&gt;</code></td>
      <td style="text-align:left"><code>Нет</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>iframe</b></td>
      <td style="text-align:left">Определяет, используются ли <code>iFrames</code></td>
      <td style="text-align:left"><code>Boolean</code></td>
      <td style="text-align:left"><code>Да</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>iFrameRegExp</b></td>
      <td style="text-align:left">Регулярный селектор выражений, который выбирает iframes для inject into.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Да</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>readLogs</b></td>
      <td style="text-align:left">Определяет, должно ли расширение читать журналы.</td>
      <td style="text-align:left"><code>Boolean</code></td>
      <td style="text-align:left"><code>Да</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>settings</b></td>
      <td style="text-align:left">Массив настроек, которые пользователь может изменить</td>
      <td style="text-align:left"><code>Array&lt;Object&gt;</code></td>
      <td style="text-align:left"><code>Да</code></td>
    </tr>
  </tbody>
</table>

## Регулярные выражения

Если вы хотите изучать регулярные выражения, вот несколько сайтов.

#### Обучение

• [Быстрый Стартер Видео](https://youtu.be/sXQxhojSdZM) • [RegexOne](https://regexone.com/) • [Информация о регулярных выражениях](https://www.regular-expressions.info/tutorial.html)

#### Проверка

• [Regexr](https://regexr.com/) • [Regex101](https://regex101.com/)

## Языки присутствия

PreMiD это полиглот-сервис, означающий, что существует несколько языков, доступных для подключения пользователей по всему миру. Полный список языков можно найти здесь [API конечной точке](https://api.premid.app/v2/langFile/list). Чтобы еще больше настроить свое присутствие, вы можете разрешить пользователям выбирать язык отображения своего присутствия. Видеть [`multiLanguage`](#multilanguage) для большего.

## Настройки присутствия
Настройте интерактивные настройки, чтобы пользователи могли настраивать присутствие!
```ts
"settings": [
  {
    "id": "ID",
    "multiLanguage": true //Видеть https://docs.premid.app/dev/presence/metadata#multilanguage
  },
  {
    "id": "ID",
    "title": "НАЗВАНИЕ ДИСПЛЕЯ",
    "icon": "FONTAWESOME ЗНАЧОК", //Пример "fas fa-info"
    "value": true //Логическое значение сделает его переключателем включения / выключения со значением в качестве значения по умолчанию.
  },
  {
    "id": "ID",
    "if": {
      "ID": true //Если другой параметр равен этому значению (true/false/0/1/etc.) Покажите эту кнопку
    },
    "title": "НАЗВАНИЕ ДИСПЛЕЯ",
    "icon": "FONTAWESOME ЗНАЧОК",
    "value": "\"%song%\" by %artist%", //Ввод строки сделает настройку входной, где вы можете использовать пользовательский ввод.
    "placeholder": "use %song% or %artist%" //Когда введено поле ввода пусто, оно будет показывать этот серый цвет
  },
  {
    "id": "ID",
    "title": "заглавие",
    "icon": "FONTAWESOME ICON",
    "value": 0, //Значение по умолчанию селектора
    "values": ["1", "2", "etc. ] //Выберете какой из них вы хотите
  }
]
```

### `multiLanguage`

#### Введение

Параметр `мультиЯзык` используется для того, чтобы позволить пользователям вручную выбрать язык, на котором они хотят присутствовать. Это требует использования строк из нашего [API](https://api.premid.app/v2/langFile/presence/en), для информации о том, как добавлять строки нажмите [здесь](https://docs.premid.app/dev/presence/metadata#adding-new-strings).

#### Настройки

Параметр `многоязычность` является особым случаем, не требует заголовка `` и `иконки` и не `значения` или `значения` как и другие параметры, но это требует дополнительных настроек!

Клавиша `многоязычность` может быть изменена на следующее:

`true`: используйте это, если вы собираетесь использовать только строки `общего характера. son` файл и файл `<service>.json` в [Репозиторий локализации](https://github.com/PreMiD/Localization/tree/master/src/Presence). `строка`: имя файла, исключая расширение (. son) внутри [Репозитория локализации](https://github.com/PreMiD/Localization/tree/master/src/Presence) (за исключением `общего файла`, так как он всегда загружается). Будут показаны только общие языки `общего` и введенного файла. `Array<String>`: если вы используете более одного файла внутри [Localization Repository](https://github.com/PreMiD/Localization/tree/master/src/Presence) вы можете указать все значения в массиве (за исключением `general` файл, так как он всегда загружен). Будут показаны только общие языки всех файлов.

#### Добавление новых строк

**Примечание:** Добавление настраиваемых строк для присутствия разрешено только в том случае, если у него более 1000 пользователей.

##### Клонирование проекта

1. Откройте терминал и введите команду `git clone https://github.com/PreMiD/Localization`.
2. Выберите папку по вашему выбору.
3. Откройте его в редакторе кода.

##### Создание файла

1. Перейдите в папку `src`.
2. Перейдите в папку `Presence`.
3. Создайте файл с именем `<service>.json`. (Создайте папку с **именем** (не URL) сервиса, который вы хотите поддерживать.)

##### Добавление строк

Каждый `string` является `Object` где от имени начинается с имени службы, а затем так называемого stringName с точкой между ними.

stringName — это идентификатор сообщения из 1 слова.

`Object` имеет 2 свойства; `message` и `description`. `message` - это текст, который необходимо перевести. `description` — это описание сообщения, чтобы помочь нашим переводчикам понять, что они переводят.

**Примечание:** Не добавляйте дубликаты строк. (сюда входят строки из файла `general.json`, но не из других файлов.)

Визуализация файла:

```ts
{
  "<service>.<stringName>": {
    "message": "Текст, который нужно перевести.",
    "description": "Это объясняет, что сообщение выше."
  },
  "<service>.<stringName>": {
    "message": "Текст, который нужно перевести.",
    "description": "Это объясняет, что сообщение выше."
  }
```

После того, как вы полностью сделали файл со строками, вы можете создать Pull Request в [Репозиторий локализации](https://github.com/PreMiD/Localization), в описании, которое вы **должны** включить ссылку на ваш Pull Request of the presence updated using these new strings from [Presence Repository](https://github.com/PreMiD/Presences).

#### Ключи по умолчанию
Ключи, которые вы не должны были установить, автоматически устанавливаются на следующее: `заголовок`: "Язык" **Примечание:** Это переведено на язык по умолчанию (язык браузера). `значок`: "fas fa-language" ([Предварительный просмотр](https://fontawesome.com/icons/language)) `значение`: **Установите на их язык браузера, если он доступен (100% переведен), иными словами, английский язык.** `значения`: **Установка на доступные языки (языки, на которых переводятся на 100%).**

**Примечание:** Они ни в коей мере не изменяются.

### Методы

Используйте следующие методы, чтобы получить информацию о настройках в файлах присутствия:
#### `getSetting(String)`
Возвращает значение настройки.
```ts
var setting = await presence.getSetting("pdexID"); // Заменить pdexID идентификатором параметра
console.log(setting); // Сообщается установка в логи
```

#### `hideSetting(String)`
Скрывает данную настройку.
```ts
presence.hideSetting("pdexID"); // Заменить pdexID идентификатором настройки
```

#### `showSetting(String)`
Показывают данные настройки (работает только если настройка была скрыта).
```ts
presence.showSetting("pdexID"); // Заменить pdexID идентификатором настройки
```

## Категории присутствия

При создании вашего присутствия, вы должны указать категорию, на которую попадает присутствие. Это скомпилированный список категорий, которые вы можете использовать.

<table>
  <thead>
    <tr>
      <th style="text-align:left">Категория</th>
      <th style="text-align:left">Название</th>
      <th style="text-align:left">Описание</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>anime</b></td>
      <td style="text-align:left"><b>Аниме</b></td>
      <td style="text-align:left">Все что относится к аниме, от форумов до платформ потокового видео.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>games</b></td>
      <td style="text-align:left"><b>Игры</b></td>
      <td style="text-align:left">Любой сайт, имеющий связанный с игрой контент, например <code>Kahoot</code> или <code>Skribbl.io</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>music</b></td>
      <td style="text-align:left"><b>Музыка</b></td>
      <td style="text-align:left">Это веб-сайты, которые предлагают контент, связанный с музыкой, будь то трансляция или загрузка.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>socials</b></td>
        <td style="text-align:left"><b>Соц. сети</b></td>
      <td style="text-align:left">Сайты, которые используются для создания и обмена контентом или для участия в других формах социальных сетей.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>videos</b></td>
        <td style="text-align:left"><b>Видео и Стримы</b></td>
      <td style="text-align:left">Веб-сайты, которые служат цели предоставления видео и потоков.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>other</b></td>
      <td style="text-align:left"><b>Прочее</b></td>
      <td style="text-align:left">Все, что не относится к конкретной категории, перечисленной выше.</td>
    </tr>
  </tbody>
</table>

