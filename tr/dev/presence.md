---
title: Presence Geliştirme
description:
published: true
date: 2021-12-20T14:27:18.034Z
tags:
editor: markdown
dateCreated: 2020-06-11T18:04:02.843Z
---

> Tüm presenceler artık burada depolanıyor: https://github.com/PreMiD/Presences 
> 
> {.is-info}

Versiyon `2.x` [Presence Mağazası](https://premid.app/store)'nı sunar. Kullanıcılar bundan sonra kendi oluşturdukları servisleri [mağazaya](https://premid.app/store) ekletebilecek ve diğer kullanıcıların kullanımına sunabilecek.

> Başlamadan önce servis kılavuzlarına uymanız şiddetle tavsiye edilir. 
> 
> {.is-warning}

- [Kurallar](https://docs.premid.app/dev/presence/guidelines)
{.links-list}

# Yapı

Tüm Presence'ler [TypeScript](https://www.typescriptlang.org/) kullanılarak yapılmıştır. [TypeScript](https://www.typescriptlang.org/)'in içerisinde bulundurduğu bir çok tanımlamalar ile kodunuzdaki hataları bulmak çok daha kolay olacaktır.

## Gereksinimler

1. [Git](https://git-scm.com/)
2. [Node](https://nodejs.org/en/) ([npm](https://www.npmjs.com/) ile birlikte gelir)

## Projeyi klonlama

1. Bir konsol açın ve `git clone https://github.com/PreMiD/Presences` yazın.
2. Bir klasör seçin.
3. Klasörü kullandığınız editör ile açın.

## Başlarken

1. Open a new terminal in the `Presences` folder
2. Install repository dependencies using `npm i` (Or your package manager of choice)

### Bir Presence yaratmak
1. Run `npx pmd` (or run `pmd` with the package manager of your choice)
2. Birinci opsiyonu seçin
3. Verilen bütün soruları doldurun

### Bir Presence Derlemek / Üzerinde Değişiklik Yapmak
1. `npx pmd` yürütün
2. İkinci opsiyonu seçin
3. Düzenlemek istedğiniz Presence adını giriniz > Bu Presence'in klasöründe bir TypeScript derleyicisi başlatacak, artık `presence.ts`'i düzenlediğinizde kendisi sizin için presence'i otomatik bir şekilde derleyecek.
{.is-info}

For inspiration or examples on how to structure your Presence's code, take a look at existing Presences like 1337x or 9GAG

For more information about the `Presence` class click [here](/dev/presence/class).

v2.0.0'dan beri artık Slayt Gösterileri var, bu sizin bir arada birden fazla `PresenceData` arayüzü göstermenize olanak sağlar, daha fazla bilgi için `Slayt Gösterisi` hakkındaya [buradan](/dev/presence/slideshow) tıklayın.

## Belirli veriyi alamıyor musunuz?!

A lot of websites are using [iframes](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe) ([Inlineframes](https://en.wikipedia.org/wiki/HTML_element#Frames)). These html tags can contain multiple sources such as videos. But they're not relevant every time. Bazıları gizli ya da yalnızca aktif olarak kullanılmıyor. Gereksiz iş yapmadan önce onlar olmadan ihtiyacınız olan bilgiyi çıkarıp çıkaramadığınızı kontol edin.

1. Onları tarayıcınızın konsolundan kontrol ediniz (**Öğeler** sekmesinde olduğunuzdan emin olun).
2. Arayın (<kbd>CTRL</kbd>+<kbd>F</kbd> (Windows) ya da <kbd>CMD</kbd>+<kbd>F</kbd> (MacOS)).
3. `document.querySelectorAll("iframe")` yürütün.

Eğere verinizin bir iFrame içerisinde olduğunu öğrenirseniz yapmanız gerekenler:

1. Bir `iframe.ts` dosyası oluşturun.
2. metadata dosyanızda iFrame'i `true` olarak ayarlayın.
3. iFrame dosyanızın içini doldurmak.

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

4. Presence dosyanızın iFrame dosyanızdan veri almasını sağlamak.

```ts
presence.on("iFrameData", (data) => {
  iFrameVideo = data.video;
  currentTime = data.time;
});
```

**Not:** Bu updateEvent etkinliğinin dışına yerleştirilmeli.

# Servisi test etme

1. Tarayıcınızdan uzantı açılır penceresini açın ve klavyenizden <kbd>Shift</kbd> butonuna basılı tutun.
2. **Presence Yükle** Presence'ler bölümünde belirecektir.
3. Click on it while you are still holding the <kbd>Shift</kbd> button.
4. Select the /dist folder of your presence.

# Bazı yararlı şeyler

## Hot-reloading

The website you are developing on is automatically reloading every time you save a file in your folder.

## Hata ayıklamak

- You can put `console.log("Test");` between your code and see if your browser console gives you that output. If yes then go on and try again after the next function. If not then there is an error above.
- If that doesn't help you either then ask a presence developer on our [Discord server](https://discord.premid.app/) for help.

# Dosyaların açıklamaları

- [Presence Sınıfı](/dev/presence/class)
- [Slideshow Sınıfı](/dev/presence/slideshow)
- [iFrame Sınıfı](/dev/presence/iframe)
- [Metadata File](/dev/presence/metadata)
- [TypeScript Konfigürasyonu](/dev/presence/tsconfig ""){.links-list}
