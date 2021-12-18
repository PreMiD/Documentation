---
title: Linux
description: Tải PreMiD trên Linux
published: true
date: 2020-11-10T18:06:56.520Z
tags:
editor: markdown
dateCreated: 2020-06-11T18:04:14.124Z
---

Việc cài đặt tiện ích rất quan trọng vì ứng dụng không thể hoạt động một mình.

> Người dùng Aur sử dụng gói của DoomLerd sẽ được an toàn như anh ấy nói. Chúng tôi không khuyến khích sử dụng nó, nhưng nếu bạn muốn, bạn vẫn có thể sử dụng nó. Cảm ơn DoomLerd vì vẫn đang quản lý kho lưu trữ aur. 
> 
> {.is-warning}

## Mục lục

- **[Về](#about)**
  - [Thông tin](#stats)
  - [Yêu cầu hệ thống](#requirements)
  - Ví dụ (Sắp có)
  - Câu hỏi thường gặp (Sắp có)
  - Xây dựng (Sắp có)
  - [Hỗ trợ](#support)
  - [Đóng góp](#credits)
  - [Giấy phép](#license)
- **[Snapcraft](#snapcraft)** (Tóm gọn : _Không bao giờ_ ™️)
- **[Portable AppImage](#appimage)** (_KHUYẾN NGHỊ_)
  - [Hướng dẫn cài đặt](#appimageinstall)
  - [Ghi chú bổ sung](#appimagenotes)
- [**Hệ điều hành dựa trên Red Hat Enterprise Linux (RHEL)**](#packagecloud)
- [**Hệ điều hành dựa trên Debian và Ubuntu**](#packagecloud)
- [**Hệ điều hành dựa trên Arch Linux**](#arch)

<a name="about"></a>

## Giới thiệu

**PreMiD** là một công cụ sử dụng thư viện RP (Rich Presence) của Discord để cho phép bạn chia sẻ những thứ bạn đang làm trên web (và một vài chương trình) trên profile Discord của bạn dưới dạng **đang chơi**.

<a name="stats"></a>

### Thông tin

<table>
  <tr>
    <th>Triển khai phần mềm</th>
    <th>Tổng lượt tải</th>
    <th>Phiên bản mới nhất</th>
  </tr>
  <tr>
    <td><a href="https://github.com/PreMiD/Linux/actions"><img src="https://github.com/PreMiD/Linux/workflows/CI/badge.svg?branch=master&event=push" alt="CI"></a></td>
    <td><a href="https://github.com/PreMiD/Linux/releases"><img src="https://img.shields.io/github/downloads/PreMiD/Linux/total.svg?maxAge=86400" alt="Tất cả phiên bản"></a></td>
    <td><a href="https://github.com/PreMiD/Linux/releases/latest"><img src="https://img.shields.io/github/v/release/PreMiD/Linux.svg?maxAge=86400" alt="Phiên bản mới nhất"><br><img src="https://img.shields.io/github/downloads/PreMiD/Linux/latest/total.svg?maxAge=86400" alt="Các phiên bản trên GitHub"></a></td>
  </tr>
</table>

<a name="requirements"></a>

### Yêu cầu hệ thống

Technically every distribution that can run Discord's [official](https://discordapp.com/download) **app** ( not the web or the snap version ) can run PreMiD too;</br> As you may have noticed in the recent years, some Linux distributions started dropping support for the 32-bit (ia32/i686/i386/x86) architectures, and as a result, we did too. You can, however, try to build the app yourself if you desperately need to use it on a 32-bit distribution.</br> Since we currently use Electron as an engine (Discord does too!), its requirements also apply to this app :

- Ubuntu ≥ 12.04
- Fedora ≥ 21
- Debian ≥ 8

It is unknown whether older versions of other distributions support it, so just keep your distribution updated and use **LTS (Long-Term Support)** releases if your distribution offers them, as they're more stable (avoid alpha releases).

<a name="support"></a>

### Hỗ trợ

<div>
  <a target="_blank" href="https://discord.premid.app/" title="Tham gia Discord của chúng tôi!">
    <img height="75px" draggable="false" src="https://discordapp.com/api/guilds/493130730549805057/widget.png?style=banner2" alt="Tham gia Discord của chúng tôi!">
  </a>
</div>

<a name="credits"></a>

### Đóng góp

Thanks to :

- @nattadasu, @Rubensei, @Cairo2k18, zany130, Immanuel D, Friskytrash, Alexandre (and few other guys whom I forgot their names) for providing feedback on nightly releases.
- @apriluwu for maintaining the Gentoo builds
- @SlimShadyIAm and naka for formerly maintaining the Arch User Repository packages
- The Electron community for various packages
- Anyone else who has ever contributed to the project in any way.

<a name="license"></a>

### Giấy phép

[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bgithub.com%2FPreMiD%2FLinux.svg?type=large)](https://app.fossa.io/projects/git%2Bgithub.com%2FPreMiD%2FLinux?ref=badge_large)

<img src="https://i.imgur.com/ACAxtmA.png" width="100" height="100" align="right"></img>
<a name="snapcraft"></a>

## Portable AppImage

The AppImage package is the recommended one if Discord works for you but other PreMiD packages (.deb, .rpm, etc) don't.

<a name="appimageinstall"></a>

### Hướng dẫn cài đặt

```bash
wget https://github.com/PreMiD/Linux/releases/latest/download/PreMiD-Portable.AppImage && chmod a+x PreMiD*.AppImage
```

```bash
# Just double-click it or run
./PreMiD*.AppImage
```

<a name="appimagenotes"></a>

### Ghi chú bổ sung

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

## Hệ điều hành dựa trên Arch Linux

Uses [Arch User Repository](https://aur.archlinux.org/packages/premid);</br> Supported distributions are _itself_, Manjaro, Anarchy, Artix, Arco, ArchLabs, Endeavour, Archman, BlackArch, Liri OS and [every one that supports installing from AUR](https://wiki.archlinux.org/index.php/Arch-based_distributions#Active).

<a name="archinstall"></a>

### Hướng dẫn cài đặt

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

### Ghi chú bổ sung

If your distro uses pacman, then you have to install one of the helpers first. If you don't have any, Yay is recommended, run :

```bash
git clone https://aur.archlinux.org/yay.git && cd yay && makepkg -si
```

```bash
yay -S premid
```

Other AUR/Pacman helpers work as well, although each one's functionality is different so you may face issues while using them.