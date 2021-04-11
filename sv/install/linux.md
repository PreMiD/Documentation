---
title: Linux
description: Kom igång med en PreMiD-installationen på Linux
published: true
date: 2020-11-10T18:06:56.520Z
tags:
editor: markdown
dateCreated: 2020-06-11T18:04:14.124Z
---

Installationen av programmet är mycket viktigt eftersom tillägget inte kan göra något av sig själv.

> Användare av Aur som använder DoomLerd's package bör vara okej som han säger. Vi rekommenderar inte att använda det, men om du vill så kan du ändå. Thanks to DoomLerd for handling aur repo still. 
> 
> {.is-warning}

## Innehållsförteckning

- **[Om](#about)**
  - [Statistik](#stats)
  - [Krav](#requirements)
  - Exempel (kommer snart)
  - Vanliga frågor (kommer snart)
  - Byggning (kommer snart)
  - [Hjälp](#support)
  - [Tack till](#credits)
  - [Licens](#license)
- **[Snapcraft](#snapcraft)** (TL;DR : _aldrig_ ™️)
- **[Portable AppImage](#appimage)** (_REKOMMENDERAS_)
  - [Installationsinstruktioner](#appimageinstall)
  - [Ytterliggare anteckningar](#appimagenotes)
- [**Red Hat Enterprise Linux (RHEL) baserade distributioner**](#packagecloud)
- [**Debian och Ubuntu baserade distributioner**](#packagecloud)
- [**Arch Linux baserade distributioner**](#arch)

<a name="about"></a>

## Om oss

**PreMiD** är en enkel, konfigurerbart verktyg som använder Discords RP ( Rich Presence ) bibliotek vilket låter dig visa vad du gör på webben ( och några program ) i din Discord profil som **spelar status**.

<a name="stats"></a>

### Statistik

<table>
  <tr>
    <th>Utplacering</th>
    <th>Totala nedladdningar</th>
    <th>Senaste versionen</th>
  </tr>
  <tr>
    <td><a href="https://github.com/PreMiD/Linux/actions"><img src="https://github.com/PreMiD/Linux/workflows/CI/badge.svg?branch=master&event=push" alt="CI"></a></td>
    <td><a href="https://github.com/PreMiD/Linux/releases"><img src="https://img.shields.io/github/downloads/PreMiD/Linux/total.svg?maxAge=86400" alt="All releases"></a></td>
    <td><a href="https://github.com/PreMiD/Linux/releases/latest"><img src="https://img.shields.io/github/v/release/PreMiD/Linux.svg?maxAge=86400" alt="Senaste versionen"><br><img src="https://img.shields.io/github/downloads/PreMiD/Linux/latest/total.svg?maxAge=86400" alt="Github releases"></a></td>
  </tr>
</table>

<a name="requirements"></a>

### Krav

Tekniskt sett kan varje distribution som kan köra Discords [officiella](https://discordapp.com/download) **app** ( inte webb eller snap versionen ) köra PreMiD med;</br> Som du kan ha märkt de senaste åren, så har några Linux distributioner börjat avsluta stödet för 32-bit (ia32/i686/i386/x86) arkitekturerna, och som resultat, så gjorde vi också det. Du kan dock själv försöka bygga appen om du desperat behöver använda den på en 32-bit distribution.</br> Eftersom vi just nu använder Electron som vår motor (Discord gör också det!), dessa krav gäller även för denna app :

- Ubuntu ≥ 12.04
- Fedora ≥ 21
- Debian ≥ 8

Det är okänt ifall äldre versioner av andra distributioner stöder det, så håll bara din distribution uppdaterad och använd **LTS (Long-Term Support)** utgåvor om din distribution erbjuder de, eftersom de är mer stabila (undvik alpha-utgåvor).

<a name="support"></a>

### Support

<div>
  <a target="_blank" href="https://discord.premid.app/" title="Join our Discord!">
    <img height="75px" draggable="false" src="https://discordapp.com/api/guilds/493130730549805057/widget.png?style=banner2" alt="Join our Discord!">
  </a>
</div>

<a name="credits"></a>

### Tack till

Tack till :

- @nattadasu, @Rubensei, @Cairo2k18, zany130, Immanuel D, Friskytrash, Alexandre (och några andra som jag glömde namnet på) för feedback på nattliga utgåvor.
- @apriluwu för hanteringen av Gentoo byggen
- @SlimShadyIAm och naka för tidigare underhåll av vårt Arch User Repository paket
- Electron gemenskapen för olika paket
- Alla andra som någonsin bidragit till projektet på något sätt.

<a name="license"></a>

### Licens

[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bgithub.com%2FPreMiD%2FLinux.svg?type=large)](https://app.fossa.io/projects/git%2Bgithub.com%2FPreMiD%2FLinux?ref=badge_large)

<img src="https://i.imgur.com/ACAxtmA.png" width="100" height="100" align="right"></img>
<a name="snapcraft"></a>

## Portable AppImage

AppImage paketet är det rekommenderade paketet om Discord fungerar för dig men andra PreMiD-paket (.deb, .rpm, etc) gör det inte.

<a name="appimageinstall"></a>

### Installationsinstruktioner

```bash
wget https://github.com/PreMiD/Linux/releases/latest/download/PreMiD-Portable.AppImage && chmod a+x PreMiD*.AppImage
```

```bash
# Dubbel-klicka bara eller kör
./PreMiD*.AppImage
```

<a name="appimagenotes"></a>

### Ytterliggare anteckningar

Either if you want to try PreMiD or just don't want to install it, this one's the best, it's always up to date but _DOESN'T AUTO-START WITH THE SYSTEM!_</br>If you get tired of having to open it each time, use the other packages (according to your distribution).

<img src="https://raw.githubusercontent.com/PreMiD/Linux/master/.github/packagecloud.png" width="100" height="100" align="right"></img>
<a name="packagecloud"></a>

# PackageCloud

We released deb/rpm packages at our packagecloud repo. Please visit it at https://packagecloud.io/PreMiD/Linux and download your deb/rpm package or use automatic script.

For **Ubuntu/Debian**:

```bash
curl -s https://packagecloud.io/install/repositories/PreMiD/Linux/script.deb.sh | sudo bash
```

For **Fedora/CentOS/RedHat**:

```bash
curl -s https://packagecloud.io/install/repositories/PreMiD/Linux/script.rpm.sh | sudo bash
```

If command doesn't work, download **deb/rpm** file from our packagecloud repo or override settings.

<a name="arch"></a>
<img src="https://raw.githubusercontent.com/PreMiD/Linux/86ae2fbd49499785281f388a5305b06e0d3ecfea/.github/iusearchbtw.svg" width="100" height="100" align="right"></img>

## Arch Linux baserade distributioner

Uses [Arch User Repository](https://aur.archlinux.org/packages/premid);</br> Supported distributions are _itself_, Manjaro, Anarchy, Artix, Arco, ArchLabs, Endeavour, Archman, BlackArch, Liri OS and [every one that supports installing from AUR](https://wiki.archlinux.org/index.php/Arch-based_distributions#Active).

<a name="archinstall"></a>

### Installationsinstruktioner

```bash
# Using yay (recommended)
yay -S premid
```

```bash
# Using pakku
pakku -S premid
```

```bash
# Using trizen
trizen -S premid
```

```bash
# Using pacaur
pacaur -S premid
```

```bash
# ... you get the point
```

or manually from the [Arch User Repository](https://aur.archlinux.org/packages/premid) if you know what you're doing.

<a name="archnotes"></a>

### Ytterliggare anteckningar

If your distro uses pacman, then you have to install one of the helpers first. If you don't have any, Yay is recommended, run :

```bash
git clone https://aur.archlinux.org/yay.git && cd yay && makepkg -si
```

```bash
yay -S premid
```

Other AUR/Pacman helpers work as well, although each one's functionality is different so you may face issues while using them.