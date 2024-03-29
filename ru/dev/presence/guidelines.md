---
title: Руководство по Presence
description: Правила, которым должны следовать все разработчики presence, чтобы добавить свое presence.
published: true
date: 2021-12-20T14:27:18.034Z
tags:
editor: markdown
dateCreated: 2021-09-07T01:44:53.883Z
---

<div align="center">
    <img src="https://github.com/PreMiD.png?size=2048" width="128px" style="max-width:100%;">
    <h3 style="font-size: 2rem; margin-bottom: 0">Руководство по созданию Presence</h3>
    <h4 style="margin-top: 0">Редакция 3</h4>
    <br />
</div>

# Рекомендации

При публикации Presence в [репозиторий Presences](https://github.com/PreMiD/Presences/), мы требуем, чтобы вы следовали набору правил. Для некоторых эти строгие правила могут показаться суровыми. Однако следование этим правилам может уберечь нас и наших пользователей от каких-либо проблем.

# Создание

Основные правила разработки Presence заключаются в следующем:

- Presences **должны** быть связанным с выбранным веб-сайтом.
- Presences **не могут** быть сделаны для незаконных веб-сайтов. (например, раздражители, продажа наркотиков, детская порнография и т.д.)
- Структура файла должна быть чистой и управляемой, не включать файлы, которые не указаны. (например, папки vscode и git, файлы изображений и текста и т. д.)
- Presences для веб-сайтов (`.onion` TLD) или веб-сайтов с бесплатными доменами/хостами (для примера, `TK` [все бесплатные домены Freenom], `.RF`, `GD` и т.д.) **не разрешены**, исключения могут быть сделаны, если представлено доказательство того, что они заплатили за домен.
- Возраст домена Presence должен быть не менее 2 месяцев.
- Presences, которые нацелены на внутренние страницы браузера (например, веб-магазин Chrome, ` chrome: // `, ` about: ` и т.д.) **не разрешены**, поскольку они требуют, чтобы экспериментальный флаг был включен на стороне пользователей, и это возможно может нанести вред их браузерам.
- Presences с поддержкой только одного поддомена ** не будет** разрешено, так как они могут быть нерабочими для других страниц (например, домашняя страница), исключения могут быть сделаны для политики конфиденциальности и контактных страниц (контент, который используется не часто) или сайтов, где имеется прочий несвязанный контент. (например, страницы википедии)
- Presence для онлайн-радио разрешено только в том случае, если у радио есть не менее 100 еженедельных слушателей и 15 одновременных, также оно должно иметь прочие особенности, кроме простого отображения альбома/названия песни и т.д.
- Presence не имеет разрешения для запуска JS кода со своей собственной функцией для получения переменных. Если Firefox имеет проблемы со встроенной функцией внутри класса `Presence`, вам разрешено сделать свою собственную функцию, и вы должны сообщить нам об этом в описании Pull Request.
- Присутствия c низким качеством (или с небольшим контекстом) **не** допускается (например, только показ логотипа и текста, и без дальнейшего его изменения).
- Presences для таких сервисов, как Discord-бот или списки серверов, должны соответствовать этим дополнительным требованиям:
  - Возраст домена должен быть не менее **6 месяцев**.
  - Уникальные посетители в день:
    - Для доменов возрастом от 6 до 12 месяцев: **20,000 уникальных посетителей в день**.
    - Для доменов возрастом более 12 месяцев: **45,000 уникальных посетителей в день**.
  - Веб-сайт не может находиться на дешёвом домене, подобных `.xyz`, `.club` и т.д.
  - Сам сайт должен иметь очень хорошее качество, дизайн и т. Д.
- Presence должен использовать [общую информацию](https://api.premid.app/v2/langFile/presence/en) (строки, начинающиеся с "general."). Вы можете добиться этого, используя `multiLanguage` с предоставленными строками. Если ваш Presence требует пользовательских строк, то вы не должны использовать `multiLanguage` до тех пор, пока Presence не получит 1000 пользователей. Вы можете найти пример [здесь](https://docs.premid.app/dev/presence/class#getstringsobject).
- Присутствие должно обязательно иметь папку `dist`, а также файлы `presence.ts`, `iframe.ts` и `metadata.json`. В конечном итоге директория должна выглядеть вот так:

```bash
presence
├── dist
│   └── metadata.json
├── presence.ts
└── tsconfig.json
```

или если вы используете `iframe.ts` файл:

```bash
presence
├── dist
│   └── metadata.json
├── presence.ts
├── iframe.ts
└── tsconfig.json
```

## [**metadata.json**](https://docs.premid.app/dev/presence/metadata)

> Для удобства наших разработчиков presence, мы предоставили схему, которую вы можете использовать для проверки целостности вашего `metadata` файла. Это совершенно необязательно и не требуется в процессе проверки.

> Настоятельно рекомендуется организовать ваш `metadata` файл в формате, показанном ниже, и вы должны иметь грамматически правильные названия служб, описания, теги и поля настроек. Все, что не соответствует спецификациям, ** не будет ** разрешено.

> Presence сайтов с откровенным содержанием **обязаны** иметь тег `nsfw` и логотип или иконка **не** должны содержать этот контент.

Каждый Presence имеет файл дескриптора с названием ` metadata.json`, метаданные имеют строгий стандарт, и пример этого файла может быть представлен ниже:

```json
{
  "$schema": "https://schemas.premid.app/metadata/1.6",
  "author": {
    "name": "ПОЛЬЗОВАТЕЛЬ",
    "id": "ID"
  },
  "contributors": [
    {
      "name": "ПОЛЬЗОВАТЕЛЬ",
      "id": "ID"
    }
  ],
  "service": "УСЛУГА",
  "altnames": ["УСЛУГА"],
  "description": {
    "en": "ОПИСАНИЕ"
  },
  "url": "URL",
  "version": "ВЕРСИЯ",
  "logo": "URL",
  "thumbnail": "URL",
  "color": "#HEX000",
  "tags": ["ЯРЛЫК1", "ЯРЛЫК2"],
  "category": "КАТЕГОРИЯ",
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
      "title": "ОТОБРАЖАЕМЫЙ ЗАГОЛОВОК",
      "icon": "FONTAWESOME ЗНАЧОК",
      "value": true
    },
    {
      "id": "ID",
      "if": {
        "ID": true
      },
      "title": "ОТОБРАЖАЕМЫЙ ЗАГОЛОВОК",
      "icon": "FONTAWESOME ЗНАЧОК",
      "value": "\"%song%\" by %artist%",
      "placeholder": "use %song% or %artist%"
    },
    {
      "id": "ID",
      "title": "ОТОБРАЖАЕМЫЙ ЗАГОЛОВОК",
      "icon": "FONTAWESOME ЗНАЧОК",
      "value": 0,
      "values": ["1", "2", "и т. д."]
    }
  ]
}
```

> Если поле указано как дополнительное в [документации](https://docs.premid.app/dev/presence/metadata) или рядом с ключом стоит `*`, а ваш Presence использует для него значение по умолчанию, не включайте его в файл `metadata`. (например, presence без поддержки iframe не потребует поле `iframe`.)

> Все изображения в файле `metadata` должны быть загружены на `i.imgur.com`. Использование контента, размещенного на сайте **не** разрешено, так как на нём могут измениться пути и файлы.

Список полей и их правил перечислены ниже:

### **`$schema`**

- Ключ _схемы_ **должен** содержать знак доллара в начале его действия, это предупредит ваш текстовый редактор, что вы хотите проверить ваш JSON-файл на модель. _Как указывалось ранее, вам не нужно включать схему, но если вы включите её, то вы должны принять это во внимание_

### **`author`**

- ID _значение_ **должно** быть вашим Discord snowflake ID. Вы можете получить это включив [режим разработчика](https://support.discord.com/hc/en-us/articles/206346498-Where-can-I-find-my-User-Server-Message-ID-). _ Пожалуйста ** не** путайте это с ID приложения, который предназначен только для вашего presence._

### **`*contributors`**

- **Не** добавляйте себя или кого-нибудь, если только они не помогли с Presence, в качестве участника.

### **`service`**

- Название службы **должно** быть названием каталога Presence. Например, если presence находится на `/websites/Y/YouTube/`, название сервиса должно быть `YouTube`.
- Вы **не можете** использовать url в качестве названия сервиса, если сайт не использует его в качестве официального названия. Если название не является описательным и может считаться расплывчатым, то использование url является **обязательным**. (например, `YouTube` разрешен, потому что это официальное, описательное название, в то время как `youtube.com` не является таковым. `Top` это не описательное название, поэтому **требуется** использование url `top.gg`)
- Если у службы есть некоторые прямые правила брендинга их имени, вы должны следовать им.

### **`*altnames`**

- Используйте это **только** тогда, когда веб-сайт имеет несколько официальных названий (например, Pokémon и 포켓몬스터). _Сокращённые_ версии названий сервисов вписываются в `tags`.

### **`description`**

- Для **всех** Presence **необходимо** иметь описание на английском языке независимо от предпочитаемого языка сайта.
- **Не** пробуйте перевести описание самостоятельно, если вы не знаете этого языка, переводчики откорректируют ваш `metadata.json` и поменяют описание при необходимости.

### **`url`**

- Ссылка ** должна ** быть строкой, если веб-сайт использует только один домен. Если веб-сайт использует множество, сделайте это массивом и укажите каждый из них.
- **Не** включайте в ссылку протоколы (например, `http` или `https`) и параметры запроса (например,`www.google.com/search?gws_rd=ssl`, который должен быть `www.google.com`)

### **`version`**

- Всегда следите за тем, чтобы номер версии соблюдался [стандартам семантического версионирования](https://semver.org), что переводится в следующую схему: `<MAJOR>.<MINOR>.<PATCH>`. Что-то похожее на `1.0.0.1`, `1.0`, `1`, `1.0.0-BETA` или изменение `1.0.0` на `2.0.0` при исправлении ошибки/небольшом изменении **не** разрешено.
- Версия **должна** всегда начинаться с `1.0.0`, если не указано иное, другие версии **не** будут разрешены.

### **`logo`**

- Логотип ** должен ** быть квадратным изображением с соотношением сторон ` 1:1`.
- Изображение **обязательно** должно иметь разрешение `512x512` пикселей. Вы можете изменить его размер с помощью такого инструмента, как [imageresizer](https://imageresizer.com/).

### **`thumbnail`**

- Миниатюра предпочтительно **должна** быть [широкой рекламной карточкой](https://i.imgur.com/3QfIc5v.jpg) или [скриншотом](https://i.imgur.com/OAcBmwW.png), если карточка **не имеется**.

### **`color`**

- Цвет **должен** быть шестнадцатеричным значением между `#000000` и `#FFFFFF`.
- Цветная строка ** должна ** начинаться с символа #.

### **`tags`**

- **Все** presences должны иметь по крайней мере _один_ тег.
- Теги должны **не** включать пробелы, косые черты, одинарные/двойные кавычки, символы Unicode и всегда должны быть в нижнем регистре.
- Теги предпочтительно **должны** включать альтернативные названия сервисов, чтобы облегчить поиск (например, если Presence Amazon включало поддержку AWS, то у него были бы такие теги: `amazon-web-services` и `aws`)
- Вам **необходимо** добавить тег ` NSFW `, если Presence предназначен для веб-сайта с NSFW-контентом.

### **`category`**

- Категория **должна** быть одной из следующих, перечисленных в [документации](https://docs.premid.app/dev/presence/metadata#presence-categories).
- Presence должен принадлежать к категории, которая соответствует содержанию веб-сайта. (например, не используйте `anime`, когда вебсайт не имеет отношения к аниме).

### **`*regExp`** <br /> **`*iFrameRegExp`**

- Регулярные выражения **должны** быть рабочими. Пожалуйста, протестируйте свои выражения с инструментами, перечисленными в [документации](https://docs.premid.app/dev/presence/metadata#testing).

### **`readLogs`**

- Значение должно быть `boolean` (`true` или `false`).
- Включает журналы для вашего присутствия.

### **`warning`**

- Включает предупреждающий значок для запроса пользователю, что этому Presence требуется больше действий, чем только добавление Presence.
- Пример Presence, использующего эту переменную метаданных – `VLC`.

### **`settings`**

- Если вы решите сделать форматированную строку (например: `%song% от %artist%`), то вам необходимо иметь переменные окружённые знаком процента с любой стороны. Переменные, такие как `%var`, `var%`, или `%%var%%` и всё что между ними, являются **не** допускаемым в целях стандартизации.
- Название настроек **не** должны быть полностью в верхнем регистре. Например, такие имена как `SHOW BROWSING STATUS` **не** разрешены; однако такие имена, как `Show Browsing Status` или `Show browsing status` разрешены.
- Если вы используете опцию `multiLanguage`, она имеет следующие типы:
  - Значение типа **Boolean** будет включать только строки из [`general.json`](https://github.com/PreMiD/Localization/blob/master/src/Presence/general.json) в репозитории локализации или из файла Presence (к примеру, если название Presence – YouTube, то расширение будет получать строки из `youtube.json`)
  - В значение типа **String** (например, `youtube`) указывается имя файла, из которого вы хотите получать строки.
  - В значение типа **Array<String>** (например `["youtube", "discord"]`) указывается массив из названий файлов, из которых вы хотите получать строки.

## [**presence.ts**](https://docs.premid.app/dev/presence/class)

> Ваш код **должен** быть _хорошо написанным_ и _ читабельным_, все строки должны быть грамматически правильными (грамматические ошибки на сайтах можно игнорировать).

> Каждый Presence соблюдает строгий набор правил анализа, который будет проверяться в процессе рассматривания. Несколько предложений можно найти ниже. [Рекомендации плагина TypeScript для проверки строгих типов](https://github.com/typescript-eslint/typescript-eslint/tree/master/packages/eslint-plugin/docs/rules). [ESlint Рекомендации](https://eslint.org/docs/rules). [Prettier](https://prettier.io/).

Вот список правил, которые вы должны соблюдать при написании файла `presence.ts`:

- **Всегда** объявляйте новый экземпляр класса `Presence` перед любой другой переменной, чтобы избежать редких проблем, которые могут возникнуть; это не является обязательным требованием по дизайну, поэтому оно может быть удалено в будущем.
- **Никогда** не используйте собственные функции, когда [доступны нативные варианты](https://docs.premid.app/dev/presence#files-explained); это гарантирует, что исправления на уровне расширения также применимы к вашим Presence. Вы можете использовать всё, что вам нужно, если вы не найдете их в документации.
- **Запрещается** создавать Presence для сайта без добавления поддержки его основного языка (например, Presence для YouTube написано с поддержкой только португальского и японского языков, но без основного – английского)
- Поле `smallImageKey` и `smallImageText` предназначено для вывода дополнительного/второстепенного контекста (например, `playing/paused` для видео-сайтов, `browsing` для обычных сайтов и других случаев), не для рекламы профиля Discord или чего-либо, не связанного с PreMiD.
- Вам **не** разрешено получать доступ к `localStorage`.
- При доступе к сохранённым данным в cookie, пожалуйста, добавляйте префикс `PMD_` к ключам.
- Вы можете делать HTTP/HTTPS запросы только к `premid.app` или API веб-сайта, для которого создаётся Presence. Если вы используете внешние домены, вам нужно будет объяснить, почему это необходимо. Единственным разрешенным API для выполнения запроса является [`Fetch API`](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API).
- **Не** присваивайте значение undefined для полей в объекте presenceData после его объявления, вместо этого используйте ключевое слово `delete`. (например, используйте `delete data.startTimestamp` вместо `data.startTimestamp = undefined`)
- Вам **не** разрешено писать Presence, который изменяет функциональность сайта. Имеется ввиду добавление, удаление или модификация элементов DOM.
- Presences, использующие кнопки, должны соответствовать дополнительным требованиям:
  - Перенаправление на главную страницу запрещено.
  - Рекламирование сайтов запрещено.
  - Нельзя отображать информацию, которую вы не смогли бы уместить в других полях.
  - Перенаправление непосредственно на аудио/видео поток запрещено.


## [**tsconfig.json**](https://docs.premid.app/dev/presence/tsconfig)

> **Не** пишите собственный файл `tsconfig.json`, используйте то, что предоставлено в [документации](https://docs.premid.app/dev/presence/tsconfig).

## Модификация

> Вы **должны** изменить версию в **metadata** на более высокое значение, чем в предыдущей версии, при внесении изменений в **presence.ts**, **iframe.ts** или **metadata.json**.

В некоторых ситуациях presence может вести себя неожиданно или использовать незначительные изменения для улучшения своей функциональности. Вот список правил, которым вы **должны** следовать при изменении presences.

- Если автор Presence не выходил на связь более месяца, вы можете связаться с проверяющим, чтобы узнать, можете ли вы изменить Presence.
- Если вы вносите изменения в presence и изменяете не менее **четверти** кодовой базы presence's, вы можете добавить себя в качестве участника. Проконсультируйтесь с рецензентом для получения дополнительной информации по этой теме.
- Кто угодно может создавать PR для исправления ошибок. **Не** изменяйте изображение, если оно не устарело и соответствует требованиям.

# Верификация

> **Весь** код, добавленный в магазин, будет лицензирован в соответствии с `Mozilla Public License 2.0`.

> Если вам нужно связаться с кем-либо, пожалуйста, используйте наш официальный сервер Discord. Все проверяющие имеют роль `Reviewer` в их профиле.

> Обратите внимание, что проверяющие участвуют в работе добровольно и управляют другими репозиториями в дополнение к этому, ваш запрос на добавление может быть не рассмотрен в течение нескольких часов или дней после его создания.

> **Всегда** имейте актуальную ветвь перед созданием запроса. Это поможет ограничить количество ложных срабатываний от автоматических проверок.

Самым важным процессом разработки Presence является добавление вашего Presence в магазин. Это делается путем создания [запроса на добавление](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/creating-a-pull-request) в репозиторий `PreMiD/Presences` на GitHub. Наши рецензенты проверят ваш Presence на соответствие стандартам и добавят его в магазин.

<div>
  <h2 style="font-size: 2rem; margin-bottom: 0;">Проверяющие Presence</h2>
  <a href="https://github.com/Bas950"><img src="https://github.com/Bas950.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
  <a href="https://github.com/EncryptedDev"><img src="https://github.com/EncryptedDev.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
</div>

## `Ограничения`

Повторяющиеся нарушения, такие как несоблюдение рекомендаций, спам запросами на добавление, угрозы или несоответствующее поведение, приведут к запрету на создание Presence.

В этом сценарии происходят следующие изменения:

- Presences под вашим управлением будут переданы боту PreMiD или другому пользователю (решается проверяющим). Идентификатор для каждого Presence пересоздаётся под новым именем владельца.
- Все ваши вопросы и запросы на добавление (создание нового Presence, изменение существующего Presence и т.д.), созданные после запрета, будут немедленно закрыты.
- Заявки для разработки Presence, созданные под вашим именем, будут удалены.

## `Проверка`

Несколько вещей, которые вы должны знать после открытия запроса:

- Требуется 2 проверяющих, чтобы выполнить слияние с вашим запросом на добавление.
- Если запрос неактивен в течение 7 дней, он будет незамедлительно закрыт.
- Все автоматические проверки **должны** быть пройдены для слияния.
- ⚠️ Вы **должны** предоставить новые, без изменений скриншоты (сделанные вами), показывающие параллельное сравнение вашего профиля и веб-сайта, чтобы доказать, что ваше presence работает. _Вам разрешено склеивать скриншоты для удобства просмотра_ Это относится как к созданию, так и к модификации.
- ⚠️Также от вас **требуется** добавление скриншотов настроек Presence в расширении, если они имеются. Пример можно увидеть [здесь](https://imgur.com/a/OD3sj5R).

## `Автоматические проверки`

![Примеры проверок](https://i.imgur.com/vF7QpBH.png)

В настоящее время presence проходит 3 отдельных этапа проверки. Все эти автоматические проверки помогают проверяющим определить, подходит ли ваш Presence для развертывания.

- `DeepScan` это бот, который проверяет качество кода. Если вы получаете ошибки в связи с появлением новых проблем, вам **необходимо** их исправить. *Предупреждение: DeepScan не всегда дает вам ошибки. Взгляните на предупреждения CodeFactor.*
- `CodeFactor` - это бот, который проверяет качество кода. Если вы получаете ошибки в связи с появлением новых проблем, вам **необходимо** их исправить.
- `Schema Validation` просканирует ваш `metadata.json` на наличие любых ошибок (например, отсутствующие поля, неверные типы значений и т.д.). Если вы видите новые проблемы, то вам также **необходимо** их исправить. Добавление поля схемы в файл `metadata.json` позволит вашему текстовому редактору (если поддерживается) показать вам эти ошибки во время разработки.

## `Дополнительные правила`

- **Всегда** будьте уверены в том, что вы запускаете ваш Presence в наиболее подходящей папке, если его название начинается с _любой_ латинской буквы, то он должен находиться в соответствии с алфавитом (например, `D/dアニメストア` или `G/Google`). Любые другие Unicode / нелатинские символы **должны** находиться в папке `#` (например, `#/巴哈姆特`) и номера в папке `0-9` (например, `0-9/4anime`).

После того как все рекомендации будут соблюдены с соответствующими проверками, ваш Presence будет добавлен в магазин.

# Предложения

Если у вас есть предложения по нашим правилам, вы можете связаться с нами в @[Discord сервере PreMiD](https://discord.premid.app), и мы проверим их!

# Вклад

`Редакция 3` руководства была написана и представлена следующими лицами:

<div>
<a href="https://github.com/PreMiD"><img src="https://github.com/PreMiD.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
</div>

`Редакция 2` руководства была написана и представлена следующими лицами:

<div>
<a href="https://github.com/CobyPowers"><img src="https://github.com/CobyPowers.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
</div>

`Редакция 1` руководства была утверждена следующими лицами:

<div>
<a href="https://github.com/CobyPowers"><img src="https://github.com/CobyPowers.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
<a href="https://github.com/Bas950"><img src="https://github.com/Bas950.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
<a href="https://github.com/i1u5"><img src="https://github.com/i1u5.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
</div>
