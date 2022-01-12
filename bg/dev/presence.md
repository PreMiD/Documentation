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

## Инсталация

1. Изтегли [Git](https://git-scm.com/).
2. Изтегли [Node](https://nodejs.org/en/) (идва със [npm](https://www.npmjs.com/)).
3. Инсталиране на [TypeScript](https://www.typescriptlang.org/index.html#download-links) (отворете терминал и напишете `npm install -g typescript`).

## Клониране на проекта

1. Отворете терминал и напишете `git clone https://github.com/PreMiD/Presences`.
2. Избери папка по твой избор.
3. Отвори го в твоя редактор на код.

## Създаване на папки и файлове

1. Отидете в папката `websites` след това, отидете в папката с първата буква на **името** (не URL) на сервиза които искате да поддържате.
2. Създайте папка с **името** (не URL адрес) на услугата която искате да поддържате.
3. Създайте `presence.ts` и `tsconfig.json` файлове вътре.
4. Създайте папка кръстена `dist` вътре.
5. Създайте `metadata.json` файл в `dist` папката.

## Попълване на tsconfig.json файла

Моля, поставете следния код във файла `tsconfig.json`.

```json
{
  "extends": "../../../tsconfig.json",
  "compilerOptions": {
    "outDir": "./dist/"
  }
}
```

За да научите повече за конфигурацията на TypeScript, кликнете [тук](/dev/presence/tsconfig).

## Попълване на metadata.json файла

Направихме създател на `metadata.json` файла за мързеливите хора [тук](https://eggsy.xyz/projects/premid/mdcreator). Все пак ви препоръчваме да прочетете това, за да знаете как работи.

```json
{
  "$schema": "https://schemas.premid.app/metadata/1.6",
  "author": {
    "name": "ЧОВЕК",
    "id": "ИД"
  },
  "contributors": [
    {
      "name": "ЧОВЕК",
      "id": "ИД"
    }
  ],
  "service": "УСЛУГА",
  "altnames": ["УСЛУГА"],
  "description": {
    "en": "ОПИСАНИЕ"
  },
  "url": "URL АДРЕС",
  "version": "ВЕРСИЯ",
  "logo": "URL АДРЕС",
  "thumbnail": "URL АДРЕС",
  "color": "#HEX000",
  "tags": ["ТАГ1", "ТАГ2"],
  "category": "КАТЕГОРИЯ",
  "regExp": "REGEXP",
  "iFrameRegExp": "REGEXP",
  "iframe": false,
  "readLogs": false,
  "settings": [
    {
      "id": "ИД",
      "multiLanguage": true
    },
    {
      "id": "ИД",
      "title": "ПОКАЗАНО ЗАГЛАВИЕ",
      "icon": "FONTAWESOME ИКОНА",
      "value": true
    },
    {
      "id": "ИД",
      "if": {
        "ИД": true
      },
      "title": "ПОКАЗНО ЗАГЛАВИЕ",
      "icon": "FONTAWESOME ИКОНА",
      "value": "\"%song%\" от %artist%",
      "placeholder": "използвай %song% или %artist%"
    },
    {
      "id": "ИД",
      "title": "ПОКАЗАНО ЗАГЛАВИЕ",
      "icon": "FONTAWESOME ИКОНА",
      "value": 0,
      "values": ["1", "2", "подобни..."]
    }
  ]
}
```

Копирайте горния код и го поставете във вашия `metadata.json` файл. Сега трябва да редактирате стойностите на свойствата. Обърнете внимание, че следните свойства не са задължителни във вашия `metadata.json` файл, ако не планирате да ги използвате, трябва да ги премахнете.

- `contributors`
- `altnames`
- `regExp`
- `iframe`
- `iFrameRegExp`
- `readLogs`
- `settings`

**Изясняване на някои предварително зададени стойности:**

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
      <td style="text-align:left">Трябва да съдържа Object с <code>името</code> и <code>ид-то</code> на разработчика на присъствие. <code>име</code> е вашето потребителско име в Discord без идентификатора(#0000). Потребителското <code>id</code> може да бъде копирано от Discord, като активирате функцията за разработчици и щракнете с десния бутон на мишката върху профила си.</td>
      <td style="text-align:left"><code>Object</code></td>
      <td style="text-align:left"><code>Не</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>contributors</b></td>
      <td style="text-align:left">Трябва да съдържа Object с <code>името</code> и <code>ид-то</code> на разработчика на присъствие. <code>име</code> е вашето потребителско име в Discord без идентификатора(#0000). Потребителското <code>id</code> може да бъде копирано от Discord, като активирате функцията за разработчици и щракнете с десния бутон на мишката върху профила си.</td>
      <td style="text-align:left"><code>Array&lt;Object&gt;</code></td>
      <td style="text-align:left"><code>Да</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>service</b></td>
      <td style="text-align:left">Заглавие на услугата, която това presence поддържа.<br>
    (Трябва да е същото име като папката, в която се намира всичко)</td>
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
      <td style="text-align:left">Малко описание на presence, можете да използвате описание на услугата, ако ви липсват идеи. Описанието ви трябва да има стойности на двойката ключове, които посочват езика и описанието на конкретния език. Направете описания с <i>езиците, които знаете</i>, нашите преводачи ще направят промени във вашия файл с метаданни.</td>
      <td style="text-align:left"><code>Object</code></td>
      <td style="text-align:left"><code>Не</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>url</b></td>
      <td style="text-align:left">URL адрес на услугата.<br><b>Пример:</b><code>vk.com</code><br>
      <b>Този URL адрес трябва да съвпада с URL адреса на уебсайта, тъй като той ще определи дали това е уебсайтът, в който да се инжектира скриптът.</b><br> <b>НЕ</b> добавяйте <code>https://</code> или <code>http://</code> в URL адреса, нито наклонена черта в края:
      <code>https://premid.app/</code> -> <code>premid.app</code><br>
      <b>Бележка:</b>: Някои URL адреси могат да имат <code>www.</code> или нещо друго пред домейна си. <b>НЕ</b> забравяйте да го добавите!<br>
      Можете да добавите няколко URL адреса, като направите следното:<br>
      <code>["URL1", "URL2", "и други..."]</code><br>
      Можете също така да използвате regExp, известен също като Regexз, за тази задача, както е обяснено по-долу.</td>
      <td style="text-align:left"><code>String, Array&lt;String&gt;</code></td>
      <td style="text-align:left"><code>Не</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>regExp</b></td>
      <td style="text-align:left">Regular expression изрази са използвани за съвпадение на URL адреси.<br>
      RegExp или известен още като Regex, може да се използва, ако даден уебсайт има множество поддомейни.<br>
      За целта можете да използвате следния regExp:<br>
      <code>([a-z0-9]+)[.]domain[.]TLD"</code><br>
      TLD означава домейн от най-високо ниво, например: .com .net (но не въвеждайте точката).<br>
      <code>([a-z0-9]+)</code> означава всичко от a до z и от 0 до 9.<br>
      Можете да получите бърз начален опит, като гледате това <a href="https://youtu.be/sXQxhojSdZM">видео</a>.<br>
      Можете да тествате своя regExp на <a href="https://regex101.com/">Regex101</a>.</td>
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
      <td style="text-align:left"><b>tags</b></td>
      <td style="text-align:left">Array-ят с тагове ще помогне на потребителите да търсят вашия presence в уебсайта.</td>
      <td style="text-align:left"><code>String, Array&lt;String&gt;</code></td>
      <td style="text-align:left"><code>Не</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>category</b></td>
      <td style="text-align:left">Редица, използвана за представяне на категорията, в която попада вашия presence. Вижте валидните категории <a href="https://docs.premid.app/dev/presence/metadata#presence-categories">тук</a>.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Не</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>iframe</b></td>
      <td style="text-align:left">Определя дали да се използват <code>iFrames</code>.</td>
      <td style="text-align:left"><code>Boolean</code></td>
      <td style="text-align:left"><code>Да</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>iFrameRegExp</b></td>
      <td style="text-align:left">Regular expression selector, който избира iframe, в който да се инжектира. Вижте regExp за повече информация.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Да</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>readLogs</b></td>
      <td style="text-align:left">Определя дали разширението трябва да чете записите.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Да</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>settings</b></td>
      <td style="text-align:left">Масив от настройки, които потребителят може да промени.<br>
      Прочетете повече за настройките за presence <a href="https://docs.premid.app/dev/presence/metadata#presence-settings">тук</a>.</td>
      <td style="text-align:left"><code>Array&lt;Object&gt;</code></td>
      <td style="text-align:left"><code>Да</code></td>
    </tr>
  </tbody>
</table>

## Започване на работа

```ts
const presence = new Presence({
  //Идентификаторът на клиента на приложението, създадено в https://discordapp.com/developers/applications
  clientId: "000000000000000000"
  }),
  //Можете да използвате това, за да получите преведени strings на езика на браузъра
  strings = presence.getStrings({
    play: "presence.playback.playing",
    pause: "presence.playback.paused"
  });

/*
function myOutsideHeavyLiftingFunction(){
    //Вземете и обработете всичките си данни тук

    // грабвания на елементи //
    // повиквания на api //
    // набори от променливи //
}

setInterval(myOutsideHeavyLiftingFunction, 10000);
//Изпълнявайте функцията, отделно от event-a UpdateData, на всеки 10 секунди, за да получите и зададете променливите, които UpdateData взема.
*/

presence.on("UpdateData", async () => {
  /*UpdateData се изпълнява винаги и затова трябва да се използва като цикъл на обновяване или `tick`. Това се прави няколко пъти в секунда, когато е възможно.

    Препоръчително е да създадете друга функция извън тази функция на събитието, която ще променя стойностите на променливите и ще извършва тежката работа, ако извиквате данни от API.*/

  const presenceData: PresenceData = {
    //Голямото изображение на вашия presence. Това може да бъде ключ на изображение, качено в портала за разработчици на Discord - Rich Presence - Art Assets, или URL адрес на изображение.
    largeImageKey: "key",
    //Малкото изображение на присъствието. Това може да бъде ключ на изображение, качено в портала за разработчици на Discord - Rich Presence - Art Assets, или URL адрес на изображение.
    smallImageKey: "https://mycrazywebsite.com/coolImage.png",
    //Текстът, който се показва при преминаване с мишката над малкото изображение
    smallImageText: "Some hover text",
     //Горната част на текста за presence
    details: "Име на страницата за разглеждане",
    //Долната част на текста за presence
    състояние: "Reading section A",
    //Епохалният времеви печат на Unix за начало на броенето от
    startTimestamp: 3133657200000,
    //Ако искате да показвате оставащото време вместо изтеклото, това е епохалната времева марка на Unix, при която таймерът приключва
    endTimestamp: 3133700400000
    //По избор можете да зададете тук largeImageKey и да промените останалото като променливи подсвойства, например presenceData.type = "blahblah"; примери за тип: детайли, състояние и т.н.
  };
  //Актуализиране на presece с всички стойности от обекта presenceData
  if (presenceData.details) presence.setActivity(presenceData);
  //Актуализирайте presence без данни, като го изчистите и превърнете голямото изображение в иконата на приложението Discord, а текста - в името на приложението Discord
  else presence.setActivity();
});
```

Можете да го копирате във вашия файл `presence.ts` и да редактирате стойностите. Задаването на всички стойности се извършва в event-а updataData.

За примери предлагаме да разгледате кода на присъствия като: 1337x или 9GAG. За повече информация относно `Presence` класа кликнете [тук](/dev/presence/class).

От версия 2.2.0 вече има слайдшоу, което ви позволява да покажете няколко `PresenceData` интерфейси на определен интервал, за повече информация щракнете върху `Slideshow` класа [тук](/dev/presence/slideshow).

## Не можете да получите определени данни?!

Много уебсайтове използват [iframes](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe) ([Inlineframes](https://en.wikipedia.org/wiki/HTML_element#Frames)). Тези html тагове могат да съдържат множество източници, например видеоклипове. Но те не са от значение всеки път. Някои от тях са скрити или просто не се използват активно. Проверете дали можете да извлечете необходимата ви информация без тях, преди да вършите излишна работа.

1. Проверете за тях в конзолата на браузъра (уверете се, че сте в раздела **Елементи**).
2. Потърсете (<kbd>CTRL</kbd>+<kbd>F</kbd> (Windows) или <kbd>CMD</kbd>+<kbd>F</kbd> (MacOS)).
3. Изпълнете `document.querySelectorAll("iframe")`.

Ако откриете, че данните ви се намират в iFrame, трябва да направите следното:

1. Създайте файл `iframe.ts`.
2. Задайте iFrame на `true` във вашия файл с метаданни.
3. Попълване на файла iFrame.

```ts
const iframe = new iFrame();
iframe.on("UpdateData", async () => {
  //Получете всички необходими данни от iFrame, запазете ги в променливи и след това ги изпратете с помощта на iframe.send
  iframe.send({
    //изпращане на данни
    video: video,
    time: video.duration
  });
});
```

4. Направете така, че вашият файл за presence да получава данни от файла iFrame.

```ts
presence.on("iFrameData", (data) => {
  iFrameVideo = data.video;
  currentTime = data.time;
});
```

**Забележка:** Това трябва да се постави извън event-а updateData.

## Компилиране

Отворете терминала във вашата папка и въведете `tsc -w` за компилиране на `presence.ts` в папката `/dist`.

# Зареждане на presence

1. Отворете изскачащия прозорец на разширението в браузъра и задръжте бутона <kbd>Shift</kbd> на клавиатурата.
2. **Зареждане на presence** ще се появи в раздела Presences.
3. Щракнете върху него, докато все още държите бутона <kbd>Shift</kbd>.
4. Изберете папката /dist на вашия presence.

# Някои полезни неща

## Горещо зареждане

Уебсайтът, в който разработвате, се презарежда автоматично всеки път, когато запазвате файл в папката си.

## Отстраняване на грешки

- Можете да поставите `console.log("Test");` между кода си и да видите дали конзолата на браузъра ви дава този резултат. Ако е така, продължете и опитайте отново след следващата функция. Ако не, тогава е налице грешка по-горе.
- Ако и това не ви помогне, попитайте разработчик на presence в нашия [Discord сървър](https://discord.premid.app/) за помощ.

# Обяснение на файловете

- [Presence клас](/dev/presence/class)
- [Slideshow клас](/dev/presence/slideshow)
- [iFrame клас](/dev/presence/iframe)
- [Metadata файл](/dev/presence/metadata)
- [Typescript конфигурация](/dev/presence/tsconfig ""){.links-list}
