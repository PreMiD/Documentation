---
title: Linux
description: PreMiD installimisega Linuxis alustamine
published: true
date: 2021-12-20T14:27:18.034Z
tags:
editor: markdown
dateCreated: 2020-06-11T18:04:14.124Z
---

Rakenduse installimine on väga oluline, kuna laiendus ei saa ise midagi teha.

> Aur kasutajad, kes kasutavad DoomLerdi paketti, peaksid olema turvalised, nagu ta ütleb. Me ei soovita seda kasutada, kuid kui soovite, saate seda siiski kasutada. Aitäh DoomLerdile aur repo käsitsemise eest. 
> 
> {.is-warning}

## Sisukord

- **[Info](#about)**
  - [Statistika](#stats)
  - [Nõuded](#requirements)
  - Näited (varsti)
  - KKK (varsti)
  - Ehitus (varsti)
  - [Klienditugi](#support)
  - [Tunnustus](#credits)
  - [Litsents](#license)
- **[Snapcraft](#snapcraft)** (TL;DR : _mitte kunagi_ ™️)
- ** [Kaasaskantav AppImage](#appimage)** (_SOOVITATAV_)
  - [Installeerimise juhised](#appimageinstall)
  - [Lisamärkused](#appimagenotes)
- [**Red Hat Enterprise Linuxi (RHEL) põhised jaotused**](#packagecloud)
- [**Debiani ja Ubuntu põhised jaotused**](#packagecloud)
- [**Arch Linuxi põhised jaotused**](#arch)

<a name="about"></a>

## Info

** PreMiD ** on lihtne, konfigureeritav utiliit, mis kasutab Discordi RP (Rich Presence) teeki, mis võimaldab teil veebis (ja mõnedes programmides) näidata, mida teete teie Discordi profiil ** olekuna **.

<a name="stats"></a>

### Statistika

<table>
  <tr>
    <th>Paigaldamine</th>
    <th>Allalaadimisi kokku</th>
    <th>Viimane väljaanne</th>
  </tr>
  <tr>
    <td><a href="https://github.com/PreMiD/Linux/actions"><img src="https://github.com/PreMiD/Linux/workflows/CI/badge.svg?branch=master&event=push" alt="CI"></a></td>
    <td><a href="https://github.com/PreMiD/Linux/releases"><img src="https://img.shields.io/github/downloads/PreMiD/Linux/total.svg?maxAge=86400" alt="Kõik väljaanded"></a></td>
    <td><a href="https://github.com/PreMiD/Linux/releases/latest"><img src="https://img.shields.io/github/v/release/PreMiD/Linux.svg?maxAge=86400" alt="Viimane väljaanne"><br><img src="https://img.shields.io/github/downloads/PreMiD/Linux/latest/total.svg?maxAge=86400" alt="GitHubi väljaanded"></a></td>
  </tr>
</table>

<a name="requirements"></a>

### Nõuded

Tehniliselt iga jaotus, mis suudab joosta Discordi [ ametlikku ](https://discordapp.com/download) ** rakendust ** (mitte veebi ega snapi versioon) saab joosta ka PreMiD-i; </br> Nagu olete viimastel aastatel märganud, hakkasid mõned Linuxi distributsioonid 32-bitiste (ia32 / i686 / i386 / x86) arhitektuuride tuge kaotama ja selle tulemusena tegime seda ka meie. Võite siiski proovida rakendust ise ehitada, kui peate seda hädasti 32-bitises jaotises kasutama. </br> Kuna praegu kasutame mootorit Electron (ka Discord kasutab!), Kehtivad selle nõuded ka selle rakenduse kohta:

- Ubuntu ≥ 12.04
- Fedora ≥ 21
- Debian ≥ 8

Pole teada, kas teiste jaotuste vanemad versioonid seda toetavad, nii et hoidke oma jaotus värskena ja kasutage väljaandeid ** LTS (Long-Term Support) **, kui teie jaotus neid pakub, nad on stabiilsemad (vältige alpha väljaandeid).

<a name="support"></a>

### Klienditugi

<div>
  <a target="_blank" href="https://discord.premid.app/" title="Liitu meie Discordiga!">
    <img height="75px" draggable="false" src="https://discordapp.com/api/guilds/493130730549805057/widget.png?style=banner2" alt="Liitu meie Discordiga!">
  </a>
</div>

<a name="credits"></a>

### Tunnustus

Tänu :

- @nattadasu, @Rubensei, @ Cairo2k18, zany130, Immanuel D, Friskytrash, Alexandre (ja vähesed teised, kelle nime unustasin) beetaversioonide kohta tagasiside andmise eest.
- @apriluwu Gentoo järkude hooldamise eest
- @SlimShadyIAm ja naka varem Archi kasutajahoidla pakettide hooldamise eest
- Electroni kogukond mitmesuguste pakettide eest
- Kõik teised, kes on projekti kuidagi kaasa aidanud.

<a name="license"></a>

### Litsents

[![FOSSA staatus](https://app.fossa.io/api/projects/git%2Bgithub.com%2FPreMiD%2FLinux.svg?type=large)](https://app.fossa.io/projects/git%2Bgithub.com%2FPreMiD%2FLinux?ref=badge_large)

<img src="https://i.imgur.com/ACAxtmA.png" width="100" height="100" align="right" />

<a name="snapcraft"></a>

## Portable AppImage

AppImage pakett on soovitatav, kui Discord töötab teie jaoks, kuid teised PreMiD paketid (.deb, .rpm jne) mitte.

<a name="appimageinstall"></a>

### Installeerimise juhised

```bash
wget https://github.com/PreMiD/Linux/releases/latest/download/PreMiD-Portable.AppImage && chmod a+x PreMiD*.AppImage
```

```bash
# Lihtsalt topeltklõpsake seda või käivitage
./PreMiD*.AppImage
```

<a name="appimagenotes"></a>

### Lisamärkused

Kui soovite proovida PreMiD-i või lihtsalt ei soovi seda installida, on see parim, see on alati ajakohane, kuid _EI AUTO-KÄIVITA SÜSTEEMIGA! _</br> Kui te olete väsinud sellest, et peate selle iga kord avama, kasutage teisi pakette (vastavalt teie jaotusele).

<img src="https://raw.githubusercontent.com/PreMiD/Linux/master/.github/packagecloud.png" width="100" height="100" align="right" />

<a name="packagecloud"></a>

# PackageCloud

Avaldasime debag / rpm paketid meie packagecloudi repos. Külastage seda aadressil https://packagecloud.io/PreMiD/Linux ja laadige alla deb / rpm pakett või kasutage automaatset skripti.

** Ubuntu / Debiani ** jaoks:

```bash
curl -s https://packagecloud.io/install/repositories/PreMiD/Linux/script.deb.sh | sudo bash
```

** Fedora / CentOS / RedHat ** jaoks:

```bash
curl -s https://packagecloud.io/install/repositories/PreMiD/Linux/script.rpm.sh | sudo bash
```

Kui käsk ei tööta, laadige ** deb / rpm ** fail alla meie packagecloudi repost või alistage seaded.

<a name="arch"></a>

<img src="https://raw.githubusercontent.com/PreMiD/Linux/86ae2fbd49499785281f388a5305b06e0d3ecfea/.github/iusearchbtw.svg" width="100" height="100" align="right" />

## Arch Linuxi põhised jaotused

Kasutab [ Archi kasutajahoidlat ](https://aur.archlinux.org/packages/premid); </br> Toetatud jaotused on _ itself</ em >, Manjaro, Anarhia, Artix, Arco, ArchLabs, Endeavour, Archman, BlackArch, Liri OS ja [ kõik teised, mis toetavad installimist AUR-ist ](https://wiki.archlinux.org/index.php/Arch-based_distributions#Active).</p>

<a name="archinstall"></a>

### Installeerimise juhised

```bash
# Yay kasutamine (soovitatav)
yay -S premid
```

```bash
# Pakku kasutamine
pakku -S premid
```

```bash
# Trizeni kasutamine
trizen -S premid
```

```bash
# Pacauri kasutamine
pacaur -S premid
```

```bash
# ... saate aru
```

või käsitsi [Archi kasutajahoidlast](https://aur.archlinux.org/packages/premid), kui teate, mida teete.

<a name="archnotes"></a>

### Lisamärkused

Kui teie distro kasutab pacmani, peate kõigepealt installima ühe abistaja. Kui teil pole ühtegi, Yay on soovitatav, käivitage:

```bash
git clone https://aur.archlinux.org/yay.git && cd yay && makepkg -si
```

```bash
yay -S premid
```

Töötavad ka teised AUR / Pacmani abistajad, ehkki igaühe funktsionaalsus on erinev, nii et nende kasutamisel võib tekkida probleeme.
