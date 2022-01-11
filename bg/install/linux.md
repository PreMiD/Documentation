---
title: Linux
description: Започване на работа с инсталация на PreMiD на Linux
published: true
date: 2021-12-20T14:27:18.034Z
tags:
editor: markdown
dateCreated: 2020-06-11T18:04:14.124Z
---

Инсталирането на приложението е много важно, тъй като разширението не може да направи нищо само по себе си.

> Потребителите на Aur, които използват пакета на DoomLerd, трябва да са в безопасност, както казва той. Не ви препоръчваме да го използвате, но ако искате, все пак можете да го използвате. Благодаря на DoomLerd за обработката на repo-то. 
> 
> {.is-warning}

## Съдържание

- **[Относно](#about)**
  - [Статистики](#stats)
  - [Изисквания](#requirements)
  - Примери (скоро)
  - Често задавани въпроси (скоро)
  - Изграждане (скоро)
  - [Поддръжка](#support)
  - [Кредити](#credits)
  - [Лиценз](#license)
- **[Snapcraft](#snapcraft)** (TL;DR : _никога_ ™️)
- **[Преносим AppImage](#appimage)** (_ПРЕПОРЪЧАНО_)
  - [Инструкции за инсталиране](#appimageinstall)
  - [Допълнителни бележки](#appimagenotes)
- [**Red Hat Enterprise Linux (RHEL) на базата на разпределения**](#packagecloud)
- [**Дистрибуции, базирани на Debian и Ubuntu**](#packagecloud)
- [**Дистрибуции, базирани на Arch Linux**](#arch)

<a name="about"></a>

## Относно

**PreMiD** е проста, конфигурируема програма, която използва библиотеката RP ( Rich Presence ) на Discord, която ви позволява да показвате това, което правите в мрежата ( и няколко програми ), в профила си в Discord като **състояние на игра**.

<a name="stats"></a>

### Статистики

<table>
  <tr>
    <th>Внедряване</th>
    <th>Общо изтегляния</th>
    <th>Последна версия</th>
  </tr>
  <tr>
    <td><a href="https://github.com/PreMiD/Linux/actions"><img src="https://github.com/PreMiD/Linux/workflows/CI/badge.svg?branch=master&event=push" alt="CI"></a></td>
    <td><a href="https://github.com/PreMiD/Linux/releases"><img src="https://img.shields.io/github/downloads/PreMiD/Linux/total.svg?maxAge=86400" alt="Всички издания"></a></td>
    <td><a href="https://github.com/PreMiD/Linux/releases/latest"><img src="https://img.shields.io/github/v/release/PreMiD/Linux.svg?maxAge=86400" alt="Последна версия"><br><img src="https://img.shields.io/github/downloads/PreMiD/Linux/latest/total.svg?maxAge=86400" alt="Публикации в Github"></a></td>
  </tr>
</table>

<a name="requirements"></a>

### Изисквания

Технически всяка дистрибуция, която може да стартира [официалното](https://discordapp.com/download) **приложение** на Discord (не уеб или snap версията) може да стартира и PreMiD;</br> Както може би сте забелязали през последните години, някои дистрибуции на Linux започнаха да се отказват от поддръжката на 32-битови (ia32/i686/i386/x86) архитектури и в резултат на това ние също го направихме. Можете обаче да се опитате да създадете приложението сами, ако отчаяно се нуждаете да го използвате в 32-битова дистрибуция.</br> Тъй като в момента използваме Electron като основа (Discord също го прави!), неговите изисквания се отнасят и за това приложение:

- Ubuntu ≥ 12.04
- Fedora ≥ 21
- Debian ≥ 8

Не е известно дали по-старите версии на други дистрибуции я поддържат, затова просто поддържайте дистрибуцията си актуализирана и използвайте **LTS (Long-Term Support)** издания, ако дистрибуцията ви ги предлага, тъй като те са по-стабилни (избягвайте алфа версиите).

<a name="support"></a>

### Поддръжка

<div>
  <a target="_blank" href="https://discord.premid.app/" title="Присъединете се към нашия Discord сървър!">
    <img height="75px" draggable="false" src="https://discordapp.com/api/guilds/493130730549805057/widget.png?style=banner2" alt="Присъединете се към нашия Discord сървър!">
  </a>
</div>

<a name="credits"></a>

### Кредити

Благодарим на:

- @nattadasu, @Rubensei, @Cairo2k18, zany130, Immanuel D, Friskytrash, Alexandre (и няколко други момчета, на които забравих имената) за предоставяне на обратна връзка за нощните версии.
- @apriluwu за поддържане на компилациите на Gentoo
- @SlimShadyIAm и naka за предишното поддържане на пакетите на Arch User Repository
- Общността на Electron за различни пакети
- Всеки друг, който някога е допринесъл за проекта по някакъв начин.

<a name="license"></a>

### Лиценз

[![Статус на FOSSA](https://app.fossa.io/api/projects/git%2Bgithub.com%2FPreMiD%2FLinux.svg?type=large)](https://app.fossa.io/projects/git%2Bgithub.com%2FPreMiD%2FLinux?ref=badge_large)

<img src="https://i.imgur.com/ACAxtmA.png" width="100" height="100" align="right"></img>
<a name="snapcraft"></a>

## Portable AppImage

Пакетът AppImage е препоръчителен, ако Discord работи за вас, но други пакети PreMiD (.deb, .rpm и т.н.) не работят.

<a name="appimageinstall"></a>

### Инструкции за инсталиране

```bash
wget https://github.com/PreMiD/Linux/releases/latest/download/PreMiD-Portable.AppImage && chmod a+x PreMiD*.AppImage
```

```bash
# Просто кликнете два пъти върху него или го стартирайте
./PreMiD*.AppImage
```

<a name="appimagenotes"></a>

### Допълнителни бележки

Ако искате да изпробвате PreMiD или просто не искате да го инсталирате, този е най-добрият, той е винаги актуален, но _НЕ СТАРТИРА АВТОМАТИЧНО СЪС СИСТЕМАТА!_</br>Ако ви омръзне да го отваряте всеки път, използвайте другите пакети (според вашата дистрибуция).

<img src="https://raw.githubusercontent.com/PreMiD/Linux/master/.github/packagecloud.png" width="100" height="100" align="right"></img>
<a name="packagecloud"></a>

# PackageCloud

Издадохме пакети deb/rpm в нашето хранилище packagecloud. Моля, прегледайте URL адреса https://packagecloud.io/PreMiD/Linux и изтеглете своя deb/rpm пакет или използвайте автоматичен скрипт.

За **Ubuntu/Debian**:

```bash
curl -s https://packagecloud.io/install/repositories/PreMiD/Linux/script.deb.sh | sudo bash
```

За **Fedora/CentOS/RedHat**:

```bash
curl -s https://packagecloud.io/install/repositories/PreMiD/Linux/script.rpm.sh | sudo bash
```

Ако командата не работи, изтеглете **deb/rpm** файл от нашето хранилище packagecloud или отменете настройките.

<a name="arch"></a>
<img src="https://raw.githubusercontent.com/PreMiD/Linux/86ae2fbd49499785281f388a5305b06e0d3ecfea/.github/iusearchbtw.svg" width="100" height="100" align="right"></img>

## Дистрибуции, базирани на Arch Linux

Uses [Arch User Repository](https://aur.archlinux.org/packages/premid);</br> Supported distributions are _itself_, Manjaro, Anarchy, Artix, Arco, ArchLabs, Endeavour, Archman, BlackArch, Liri OS and [every one that supports installing from AUR](https://wiki.archlinux.org/index.php/Arch-based_distributions#Active).

<a name="archinstall"></a>

### Инструкции за инсталиране

```bash
# Използване на yay (препоръчително)
yay -S premid
```

```bash
# Използване на pakku
pakku -S premid
```

```bash
# Използване на trizen
trizen -S premid
```

```bash
# Използване на pacaur
pacaur -S premid
```

```bash
# ... разбирате смисъла
```

или ръчно от [Хранилището на потребителите на Arch](https://aur.archlinux.org/packages/premid), ако знаете какво правите.

<a name="archnotes"></a>

### Допълнителни бележки

Ако вашата дистрибуция използва pacman, първо трябва да инсталирате един от помощниците. Ако не разполагате с такива, Yay е препоръчително, стартирайте:

```bash
git clone https://aur.archlinux.org/yay.git && cd yay && makepkg -si
```

```bash
yay -S premid
```

Други помощници на AUR/Pacman също работят, въпреки че функционалността на всеки от тях е различна, така че може да срещнете проблеми при използването им.
