---
title: Linux
description: শুরু করা যাক PreMiD ইন্সটলেশন লিনাক্সে
published: true
date: 2021-09-18T14:12:58.772Z
tags: 
editor: markdown
dateCreated: 2021-09-07T01:23:27.177Z
---

অ্যাপ্লিকেশনটির ইন্সটলেশন খুবই গুরুত্বপূর্ণ কেননা এক্সটেনশনটি নিজ থেকে কিছুই করতে পারেনা।

> Aur ইউজারগুলো যারা DoomLerd - এর প্যাকেজ ব্যবহার করে তারা নিরাপদ থাকবে যেমন তিনি বলেছেন। আমরা এটা ব্যবহার করার পরামর্শ দিচ্ছি না, কিন্তু তুমি যদি চাও তাহলে তুমি ব্যবহার করতে পারো। DoomLerd - কে ধন্যবাদ এখনো Aur রিপোজিটরি মেইনটেইন করার জন্যে। 
> 
> {.is-warning}

## সূচীপত্র

- **[পরিচিতি](#about)**
  - [পরিসংখ্যান](#stats)
  - [রিকোয়ারমেন্টগুলো](#requirements)
  - উদাহরণ (শীঘ্রই আসছে)
  - সচরাচর জিজ্ঞাস্য প্রশ্নগুলো (শীঘ্রই আসছে)
  - তৈরি করা (শীঘ্রই আসছে)
  - [সাপোর্ট](#support)
  - [কৃতিত্ব](#credits)
  - [লাইসেন্স](#license)
- **[Snapcraft](#snapcraft)** (ছোট কথায়: _কখনই না_ ™️)
- **[Portable AppImage](#appimage)** (_পরামর্শিত_)
  - [ইন্সটলেশন নির্দেশাবলী](#appimageinstall)
  - [অতিরিক্ত নোট](#appimagenotes)
- [**রেড হ্যাট এন্টারপ্রাইজ লিনাক্স (RHEL) ভিত্তিক ডিস্ট্রিবিউশনগুলো**](#packagecloud)
- [**Debian এবং Ubuntu ভিত্তিক ডিস্ট্রিবিউশনগুলো**](#packagecloud)
- [**Arch Linux ভিত্তিক ডিস্ট্রিবিউশনগুলো**](#arch)

<a name="about"></a>

## পরিচিতি

**PreMiD** হচ্ছে একটি সহজ, কনফিগারযোগ্য ইউটিলিটি যা Discord - এর RP (Rich Presence) লাইব্রেরি ব্যবহার করে দেখায় তুমি কী করছ ইন্টারনেটে (এবং কিছু প্রোগ্রাম) তোমার Discord প্রোফাইলে **প্লেয়িং স্ট্যাটাস** হিসেবে।

<a name="stats"></a>

### পরিসংখ্যান

<table>
  <tr>
    <th>ডেপ্লয়মেন্ট</th>
    <th>মোট ডাউনলোড</th>
    <th>সর্বশেষ রিলিজ</th>
  </tr>
  <tr>
    <td><a href="https://github.com/PreMiD/Linux/actions"><img src="https://github.com/PreMiD/Linux/workflows/CI/badge.svg?branch=master&event=push" alt="CI"></a></td>
    <td><a href="https://github.com/PreMiD/Linux/releases"><img src="https://img.shields.io/github/downloads/PreMiD/Linux/total.svg?maxAge=86400" alt="সব রিলিজগুলো"></a></td>
    <td><a href="https://github.com/PreMiD/Linux/releases/latest"><img src="https://img.shields.io/github/v/release/PreMiD/Linux.svg?maxAge=86400" alt="সর্বশেষ রিলিজ"><br><img src="https://img.shields.io/github/downloads/PreMiD/Linux/latest/total.svg?maxAge=86400" alt="গিটহাব রিলিজগুলো"></a></td>
  </tr>
</table>

<a name="requirements"></a>

### রিকোয়ারমেন্টগুলো

মূলত যেসব ডিস্ট্রিবিউশন Discord - এর [অফিসিয়াল](https://discordapp.com/download) **অ্যাপ্লিকেশন** (ওয়েব বা স্ন্যাপ ভার্সন না) চালাতে পারে সেগুলো PreMiD - ও চালাতে পারে;</br> যেমন তুমি খেয়াল করেছ বিগত বছরগুলোতে, কিছু লিনাক্স ডিস্ট্রিবিউশনগুলো সাপোর্ট বন্ধ করতে শুরু করেছে 32-bit (ia32/i686/i386/x86) আর্কিটেকচারগুলোর জন্য, তেমনি ফলাফলস্বরূপ, আমরাও তাই করেছি। তুমি চালাতে পারবে, তবে, চেষ্টা করবে নিজ থেকে অ্যাপ্লিকেশানটা তৈরি করতে যদি তোমার গুরুতরভাবে এটি ব্যবহার করতে হয় 32-bit ডিস্ট্রিবিউশনে।</br> যেহেতু আমরা বর্তমানে Electron ব্যবহার করি ইঞ্জিন হিসেবে (Discord - ও করে!), এর রিকোয়ারমেন্টগুলোও এই অ্যাপ্লিকেশানের সাথে সংযুক্ত হয়:

- Ubuntu ≥ 12.04
- Fedora ≥ 21
- Debian ≥ 8

অন্যান্য ডিস্ট্রিবিউশনগুলোর পুরাতন ভার্সনগুলো এটি সাপোর্ট করে কিনা এটা এখনও অজানা, তাই নিজের ডিস্ট্রিবিউশন আপডেটেড রাখো এবং **LTS (Long-Term Support)** রিলিজগুলো ব্যবহার করো যদি তোমার ডিস্ট্রিবিউশন সেগুলো দেয়, কেননা সেগুলো আরো স্থিতিশীল (আলফা রিলিজগুলো এড়াও)।

<a name="support"></a>

### সাপোর্ট

<div>
  <a target="_blank" href="https://discord.premid.app/" title="জয়েন করো আমাদের Discord!">
    <img height="75px" draggable="false" src="https://discordapp.com/api/guilds/493130730549805057/widget.png?style=banner2" alt="জয়েন করো আমাদের Discord!">
  </a>
</div>

<a name="credits"></a>

### কৃতিত্ব

ধন্যবাদ জানাই:

- @nattadasu, @Rubensei, @Cairo2k18, zany130, Immanuel D, Friskytrash, Alexandre - কে (এবং আরো অন্যান্য কয়েকজনকে যাদের নাম আমি ভুলে গেছি) ফিডব্যাক দেওয়ার জন্যে।
- @apriluwu - কে Gentoo বিল্ডগুলোকে মেইনটেইন করার জন্যে
- @SlimShadyIAm এবং naka - কে পূর্বে Arch User রিপোজিটরি প্যাকেজগুলোকে মেইনটেইন করার জন্যে
- Electron কমিউনিটিকে বিভিন্ন ধরণের প্যাকেজ দেওয়ার জন্যে
- অন্য কেউ যে প্রোজেক্টটিকে যেকোনোভাবে কন্ট্রিবিউট করেছে।

<a name="license"></a>

### লাইসেন্স

[![FOSSA স্ট্যাটাস](https://app.fossa.io/api/projects/git%2Bgithub.com%2FPreMiD%2FLinux.svg?type=large)](https://app.fossa.io/projects/git%2Bgithub.com%2FPreMiD%2FLinux?ref=badge_large)

<img src="https://i.imgur.com/ACAxtmA.png" width="100" height="100" align="right"></img>
<a name="snapcraft"></a>

## Portable AppImage

AppImage প্যাকেজটি পরামর্শিত যদি Discord তোমার জন্য কাজ করে কিন্তু অন্যান্য PreMiD প্যাকেজগুলো (.deb, .rpm, etc) না করে।

<a name="appimageinstall"></a>

### ইন্সটলেশন নির্দেশাবলী

```bash
wget https://github.com/PreMiD/Linux/releases/latest/download/PreMiD-Portable.AppImage && chmod a+x PreMiD*.AppImage
```

```bash
ডাবল ক্লিক করো অথবা রান করো
./PreMiD*.AppImage
```

<a name="appimagenotes"></a>

### অতিরিক্ত নোট

হয় তুমি যদি PreMiD পরীক্ষা করতে চাও অথবা শুধু তুমি এটাকে ইন্সটল করতে চাও না, এটাই হচ্ছে সেরাটা, এটা সবসময় আপ টু ডেট কিন্তু _কখনো অটো স্টার্ট হয় না সিস্টেমের সাথে!_</br>যদি তুমি ক্লান্ত হয়ে যাও প্রত্যেকবার এটাকে ওপেন করার জন্যে, ব্যবহার করো অন্যান্য প্যাকেজগুলো (তোমার ডিস্ট্রিবিউশন অনুযায়ী)।

<img src="https://raw.githubusercontent.com/PreMiD/Linux/master/.github/packagecloud.png" width="100" height="100" align="right"></img>
<a name="packagecloud"></a>

# PackageCloud

আমরা deb/rpm প্যাকেজগুলো রিলিজ করেছি আমাদের PackageCloud রিপোজিটরিতে। যাও https://packagecloud.io/PreMiD/Linux - তে এবং ডাউনলোড করো তোমার deb/rpm প্যাকেজ অথবা ব্যবহার করো অটোমেটিক স্ক্রিপ্ট।

**Ubuntu/Debian** - এর জন্য:

```bash
curl -s https://packagecloud.io/install/repositories/PreMiD/Linux/script.deb.sh | sudo bash
```

**Fedora/CentOS/RedHat** - এর জন্য:

```bash
curl -s https://packagecloud.io/install/repositories/PreMiD/Linux/script.rpm.sh | sudo bash
```

যদি কমান্ড কাজ না করে, ডাউনলোড করো **deb/rpm** ফাইল আমাদের PackageCloud রিপোজিটরি থেকে অথবা সেটিংস ওভাররাইড করো।

<a name="arch"></a>
<img src="https://raw.githubusercontent.com/PreMiD/Linux/86ae2fbd49499785281f388a5305b06e0d3ecfea/.github/iusearchbtw.svg" width="100" height="100" align="right"></img>

## Arch Linux ভিত্তিক ডিস্ট্রিবিউশনগুলো

[Arch User রিপোজিটরি](https://aur.archlinux.org/packages/premid) ব্যবহার করে;</br> সাপোর্টেড ডিস্ট্রিবিউশনগুলো হলো _নিজেই_, Manjaro, Anarchy, Artix, Arco, ArchLabs, Endeavour, Archman, BlackArch, Liri OS এবং [সবকটি যেগুলো AUR থেকে ইন্সটল করা সাপোর্ট করে](https://wiki.archlinux.org/index.php/Arch-based_distributions#Active)।

<a name="archinstall"></a>

### ইন্সটলেশন নির্দেশাবলী

```bash
# yay ব্যবহার করা (পরামর্শিত)
yay -S premid
```

```bash
# pakku ব্যবহার করা
pakku -S premid
```

```bash
# trizen ব্যবহার করা
trizen -S premid
```

```bash
# pacaur ব্যবহার করা
pacaur -S premid
```

```bash
# ... আশা করি তুমি বুঝতে পেরেছ
```

অথবা ম্যানুয়ালি [Arch User রিপোজিটরি](https://aur.archlinux.org/packages/premid) থেকে যদি তুমি জানো তুমি কী করছ।

<a name="archnotes"></a>

### অতিরিক্ত নোট

যদি তোমার ডিস্ট্রিবিউশন Pacman ব্যবহার করে, তাহলে তোমাকে প্রথমে একটি হেল্পার ইন্সটল করতে হবে। তোমার কাছে যদি একটিও না থাকে, Yay পরামর্শিত, রান করো:

```bash
git clone https://aur.archlinux.org/yay.git && cd yay && makepkg -si
```

```bash
yay -S premid
```

অন্যান্য AUR/Pacman হেল্পারগুলোও কাজ করে, যদিও প্রত্যেকটির কার্যকারিতা ভিন্ন তাই তুমি সমস্যার মুখোমুখি হতে পারো সেগুলো ব্যবহার করার সময়।