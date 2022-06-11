---
title: Linux
description: Ag tosú le suiteáil PreMiD ar Linux
published: true
date: 2021-12-20T14:27:18.034Z
tags:
editor: markdown
dateCreated: 2020-06-11T18:04:14.124Z
---

Tá suiteáil an iarratais an-tábhachtach mar ní féidir leis an síneadh aon rud a dhéanamh leis féin.

> Ba chóir go mbeadh úsáideoirí Aur a úsáideann pacáiste DoomLerd sábháilte mar a deir sé. Nílimid ag moladh é a úsáid, ach más mian leat gur féidir leat é a úsáid fós. Buíochas le DoomLerd as aur stór a láimhseáil fós. 
> 
> {.is-warning}

## Tábla Ábhar

- **[Faoi](#about)**
  - [Staitisticí](#stats)
  - [Riachtanais](#requirements)
  - Samplaí (go luath)
  - Ceisteanna Coitianta (go luath)
  - Foirgneamh (go luath)
  - [Tacaíocht](#support)
  - [Creidmheasanna](#credits)
  - [Ceadúnas](#license)
- **[Snapcraft](#snapcraft)** (TL;DR : _riamh_ ™️)
- **[Portable AppImage](#appimage)** (_MOLTA_)
  - [Treoracha suiteála](#appimageinstall)
  - [Nótaí breise](#appimagenotes)
- [**Red Hat Enterprise Linux (RHEL) dáiltí bunaithe**](#packagecloud)
- [**Dáiltí bunaithe ar Debian agus Ubuntu**](#packagecloud)
- [**Dáiltí bunaithe ar Arch Linux**](#arch)

<a name="about"></a>

## Faoi

**PreMiD** Is fóntais simplí, configurable é a úsáideann leabharlann LS Discord (Láithreacht Shaibhir) a ligeann duit a thaispeáint cad atá á dhéanamh agat ar an ngréasán ( agus cúpla clár ) i do phróifíl Discord mar **tás >stádas**.

<a name="stats"></a>

### Staitisticí

<table>
  <tr>
    <th>Imscaradh</th>
    <th>Iomlán na n-íoslódálacha</th>
    <th>An scaoileadh is déanaí</th>
  </tr>
  <tr>
    <td><a href="https://github.com/PreMiD/Linux/actions"><img src="https://github.com/PreMiD/Linux/workflows/CI/badge.svg?branch=master&event=push" alt="CI"></a></td>
    <td><a href="https://github.com/PreMiD/Linux/releases"><img src="https://img.shields.io/github/downloads/PreMiD/Linux/total.svg?maxAge=86400" alt="Gach eisiúint"></a></td>
    <td><a href="https://github.com/PreMiD/Linux/releases/latest"><img src="https://img.shields.io/github/v/release/PreMiD/Linux.svg?maxAge=86400" alt="An scaoileadh is déanaí"><br><img src="https://img.shields.io/github/downloads/PreMiD/Linux/latest/total.svg?maxAge=86400" alt="Scaoileadh Github"></a></td>
  </tr>
</table>

<a name="requirements"></a>

### Riachtanais

Go teicniúil gach dáileadh ar féidir leis a reáchtáil Discord's [oifigiúil](https://discordapp.com/download) **iarratas** ( ní an gréasán ná an leagan Snap ) is féidir leo PreMiD a reáchtáil freisin;</br> Mar a d'fhéadfá a thabhairt faoi deara le blianta beaga anuas, thosaigh roinnt dáiltí Linux ag titim tacaíochta don 32-giotán (ia32/i686/i386/x86) ailtireachtaí, agus mar thoradh air sin, rinneamar freisin. Is féidir leat iarracht a dhéanamh, áfach, an aip a thógáil duit féin más gá duit é a úsáid go géar ar dháileadh 32-giotán.</br> Ós rud é go n-úsáidimid Electron faoi láthair mar inneall (déanann Discord freisin!), baineann a riachtanais leis an aip seo freisin:

- Ubuntu ≥ 12.04
- Fedora ≥ 21
- Debian ≥ 8

Ní fios an dtacaíonn leaganacha níos sine de dháiltí eile leis, mar sin coinnigh do dháileadh cothrom le dáta agus bain úsáid as **TF (Tacaíocht Fhadtéarmach) ** scaoileadh má thairgeann do dháileadh iad, mar go bhfuil siad níos cobhsaí (seachain eisiúintí alfa).

<a name="support"></a>

### Tacaíocht

<div>
  <a target="_blank" href="https://discord.premid.app/" title="Tar isteach inár Discord!">
    <img height="75px" draggable="false" src="https://discordapp.com/api/guilds/493130730549805057/widget.png?style=banner2" alt="Tar isteach inár Discord!">
  </a>
</div>

<a name="credits"></a>

### Creidmheasanna

Buíochas le:

- @nattadasu, @Rubensei, @Cairo2k18, zany130, Immanuel D, Friskytrash, Alexandre (agus is beag fear eile a ndearna mé dearmad ar a n-ainmneacha) as aiseolas a sholáthar ar eisiúintí oíche.
- @apriluwu chun na tógann Gentoo a chothabháil
- @SlimShadyIAm agus naka as pacáistí Stór Úsáideoirí Arch a chothabháil roimhe seo
- An pobal Electron do phacáistí éagsúla
- Duine ar bith eile a chuir leis an tionscadal riamh ar bhealach ar bith.

<a name="license"></a>

### Ceadúnas

[![Stádas FOSSA](https://app.fossa.io/api/projects/git%2Bgithub.com%2FPreMiD%2FLinux.svg?type=large)](https://app.fossa.io/projects/git%2Bgithub.com%2FPreMiD%2FLinux?ref=badge_large)

<img src="https://i.imgur.com/ACAxtmA.png" width="100" height="100" align="right" />

<a name="snapcraft"></a>

## Portable AppImage

Is é an pacáiste AppImage an ceann molta má oibríonn Discord duit ach ní dhéanann pacáistí PreMiD eile (.deb, .rpm, srl).

<a name="appimageinstall"></a>

### Treoracha suiteála

```bash
wget https://github.com/PreMiD/Linux/releases/latest/download/PreMiD-Portable.AppImage && chmod a+x PreMiD*.AppImage
```

```bash
# Díreach cliceáil faoi dhó air nó rith
./PreMiD*.AppImage
```

<a name="appimagenotes"></a>

### Nótaí breise

Más mian leat triail a bhaint as PreMiD nó mura dteastaíonn uait é a shuiteáil, is é seo an ceann is fearr, tá sé cothrom le dáta i gcónaí ach _NÍ DHÉANANN TÚS-UATHOIBRÍOCH LEIS AN GCÓRAS!_</br>Má a bhíonn tú tuirseach de bheith agat é a oscailt gach uair, bain úsáid as na pacáistí eile (de réir do dháileadh).

<img src="https://raw.githubusercontent.com/PreMiD/Linux/master/.github/packagecloud.png" width="100" height="100" align="right" />

<a name="packagecloud"></a>

# PackageCloud

D'eisíomar pacáistí deb/rpm ag ár n-athdhéanamh packagecloud. Tabhair cuairt air ag https://packagecloud.io/PreMiD/Linux agus íoslódáil do phacáiste deb/rpm nó bain úsáid as script uathoibríoch.

Le haghaidh **Ubuntu/Debian**:

```bash
curl -s https://packagecloud.io/install/repositories/PreMiD/Linux/script.deb.sh | sudo bash
```

Le haghaidh **Fedora/CentOS/RedHat**:

```bash
curl -s https://packagecloud.io/install/repositories/PreMiD/Linux/script.rpm.sh | sudo bash
```

Mura n-oibríonn an t-ordú, íoslódáil **deb/rpm** comhad ónár socruithe athdhéanta nó sáraitheacha.

<a name="arch"></a>

<img src="https://raw.githubusercontent.com/PreMiD/Linux/86ae2fbd49499785281f388a5305b06e0d3ecfea/.github/iusearchbtw.svg" width="100" height="100" align="right" />

## Dáiltí bunaithe ar Arch Linux

Úsáidí [Taisclann Úsáideoirí Arch](https://aur.archlinux.org/packages/premid);</br> Tá dáiltí tacaithe _é féin_, Manjaro, Anarchy, Artix, Arco, ArchLabs, Endeavour, Archman, BlackArch, Liri OS agus [gach ceann a thacaíonn le suiteáil ó AUR](https://wiki.archlinux.org/index.php/Arch-based_distributions#Active).

<a name="archinstall"></a>

### Treoracha suiteála

```bash
# Ag baint úsáide as yay (molta)
yay -S premid
```

```bash
# Ag baint úsáide as pakku
pakku -S premid
```

```bash
# Ag baint úsáide as trizen
trizen -S premid
```

```bash
# Ag baint úsáide as pacaur
pacaur -S premid
```

```bash
# ... gheobhaidh tú an pointe
```

nó de láimh ón [Taisclann Úsáideoirí Arch](https://aur.archlinux.org/packages/premid) má tá a fhios agat cad atá á dhéanamh agat.

<a name="archnotes"></a>

### Nótaí breise

Má úsáideann do distro pacman pacman, ansin caithfidh tú ceann de na cúntóirí a shuiteáil ar dtús. Mura bhfuil aon cheann agat, moltar Yay, rith:

```bash
git clone https://aur.archlinux.org/yay.git && cd yay && makepkg -si
```

```bash
yay -S premid
```

Oibríonn cúntóirí eile AUR/Pacman chomh maith, cé go bhfuil feidhmiúlacht gach duine difriúil ionas go mbeidh ceisteanna agat agus iad á n-úsáid.
