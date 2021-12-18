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

Trên lý thuyết, các hệ điều hành có thể chạy **ứng dụng** Discord [chính thức](https://discordapp.com/download) ( không phải phiên bản web hay bản snap ) thì cũng có thể chạy PreMiD;</br> Trong vài năm trở lại đây, một số Distro của Linux đã dừng hỗ trợ cấu trúc 32-bit (ia32/i686/i386/x86) và như một hệ quả, chúng tôi cũng làm thế. Bạn có thể tự dựng lại phần mềm nếu bạn thực sự cần phải sử dụng trên distro 32-bit.</br> Vì chúng tôi sử dụng môi trường phát triển ứng dụng Electron (Discord cũng vậy!), các yêu cầu của nó cũng được áp dụng cho PreMiD :

- Ubuntu ≥ 12.04
- Fedora ≥ 21
- Debian ≥ 8

Khó thể biết các phiên bản cũ hơn của các distro khác có hỗ trợ không, vì vậy luôn cập nhật distro của bạn và sử dụng các phiên bản **LTS (Hỗ trợ dài hạn)** nếu có, vì chúng ổn định hơn (tránh phiên bản alpha).

<a name="support"></a>

### Hỗ trợ

<div>
  <a target="_blank" href="https://discord.premid.app/" title="Tham gia Discord của chúng tôi!">
    <img height="75px" draggable="false" src="https://discordapp.com/api/guilds/493130730549805057/widget.png?style=banner2" alt="Tham gia Discord của chúng tôi!">
  </a>
</div>

<a name="credits"></a>

### Đóng góp

Xin cảm ơn :

- @nattadasu, @Rubensei, @Cairo2k18, zany130, Immanuel D, Friskytrash, Alexandre (và một số người khác mà tôi không nhớ tên) vì đã cung cấp phản hồi về các bản phát hành nightly.
- @apriluwu đã duy trì các bản dựng Gentoo
- @SlimShadyIAm và naka vì trước đây đã duy trì các gói Kho lưu trữ người dùng Arch
- Cộng đồng Electron cho các gói khác nhau
- Bất kỳ ai khác đã từng đóng góp cho dự án theo bất kỳ cách nào.

<a name="license"></a>

### Giấy phép

[![Tình trạng FOSSA](https://app.fossa.io/api/projects/git%2Bgithub.com%2FPreMiD%2FLinux.svg?type=large)](https://app.fossa.io/projects/git%2Bgithub.com%2FPreMiD%2FLinux?ref=badge_large)

<img src="https://i.imgur.com/ACAxtmA.png" width="100" height="100" align="right"></img>
<a name="snapcraft"></a>

## Portable AppImage

Gói AppImage là gói được khuyến nghị nếu Discord hoạt động nhưng các gói PreMiD khác (.deb, .rpm, v.v.) thì không.

<a name="appimageinstall"></a>

### Hướng dẫn cài đặt

```bash
wget https://github.com/PreMiD/Linux/releases/latest/download/PreMiD-Portable.AppImage && chmod a+x PreMiD*.AppImage
```

```bash
# Chỉ cần nhấp đúp vào nó hoặc chạy
./PreMiD*.AppImage
```

<a name="appimagenotes"></a>

### Ghi chú bổ sung

Hoặc nếu bạn muốn thử PreMiD hoặc không muốn cài đặt nó, thì đây là cách tốt nhất, nó luôn được cập nhật nhưng _KHÔNG KHỞI ĐỘNG CÙNG HỆ THỐNG!_ </br> Nếu bạn cảm thấy mệt mỏi vì phải mở nó nhiều lần, vui lòng sử dụng các phiên bản khác (theo distro của bạn).

<img src="https://raw.githubusercontent.com/PreMiD/Linux/master/.github/packagecloud.png" width="100" height="100" align="right"></img>
<a name="packagecloud"></a>

# PackageCloud

Chúng tôi đã phát hành các gói deb / rpm tại kho lưu trữ packagecloud của chúng tôi. Vui lòng truy cập nó tại https://packagecloud.io/PreMiD/Linux và tải xuống gói deb / rpm của bạn hoặc sử dụng tập lệnh tự động.

Đối với **Ubuntu/Debian**:

```bash
curl -s https://packagecloud.io/install/repositories/PreMiD/Linux/script.deb.sh | sudo bash
```

Đối với **Fedora/CentOS/RedHat**:

```bash
curl -s https://packagecloud.io/install/repositories/PreMiD/Linux/script.rpm.sh | sudo bash
```

Nếu lệnh không hoạt động, hãy tải xuống tệp **deb/rpm** từ kho lưu trữ packagecloud của chúng tôi hoặc ghi đè các cài đặt.

<a name="arch"></a>
<img src="https://raw.githubusercontent.com/PreMiD/Linux/86ae2fbd49499785281f388a5305b06e0d3ecfea/.github/iusearchbtw.svg" width="100" height="100" align="right"></img>

## Hệ điều hành dựa trên Arch Linux

Sử dụng [Kho lưu trữ Người dùng Arch](https://aur.archlinux.org/packages/premid);</br> Các distro được hỗ trợ bao gồm _bản thân Arch_, Manjaro, Anarchy, Artix, Arco, ArchLabs, Endeavour, Archman, BlackArch, Liri OS và [mọi distro hỗ trợ cài đặt từ AUR](https://wiki.archlinux.org/index.php/Arch-based_distributions#Active).

<a name="archinstall"></a>

### Hướng dẫn cài đặt

```bash
# Sử dụng yay (khuyến nghị)
yay -S premid
```

```bash
# Sử dụng pakku
pakku -S premid
```

```bash
#Sử dụng trizen
trizen -S premid
```

```bash
# Sử dụng pacaur
pacaur -S premid
```

```bash
# ... bạn hiểu rồi đấy
```

hoặc theo cách thủ công từ [Kho lưu trữ người dùng Arch](https://aur.archlinux.org/packages/premid) nếu bạn biết mình đang làm gì.

<a name="archnotes"></a>

### Ghi chú bổ sung

Nếu distro của bạn sử dụng pacman, thì trước tiên bạn phải cài đặt một trong các trình trợ giúp. Nếu bạn chưa cài, Yay được khuyến nghị, hãy chạy :

```bash
git clone https://aur.archlinux.org/yay.git && cd yay && makepkg -si
```

```bash
yay -S premid
```

Các trình trợ giúp AUR/Pacman khác cũng hoạt động, mặc dù chức năng chúng khác nhau nên bạn có thể gặp sự cố khi sử dụng chúng.