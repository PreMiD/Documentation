---
title: সমস্যা সমাধান
description: তোমার সমস্যা সমাধানের জন্য সবকিছু
published: true
date: 2021-02-08T21:30:58.603Z
tags:
editor: markdown
dateCreated: 2020-06-11T18:03:54.865Z
---

> নিশ্চিত করো যে তুমি এক্সটেনশনটি **এবং** অ্যাপ্লিকেশনটি ইন্সটল করেছ! 
> 
> {.is-warning}

এই পেজে আছে:
1. [সাধারণ সমস্যা সমাধান](https://docs.premid.app/troubleshooting#general)
2. [লিনাক্স এর সমস্যা সমাধান](https://docs.premid.app/troubleshooting#linux)
3. [ম্যাকওস এর সমস্যা সমাধান](https://docs.premid.app/troubleshooting#macos)

<a name="general"></a>

# সাধারণ সমস্যা সমাধান
> তুমি [এই](https://qkeleq10.github.io/PreMiD-Troubleshooting/) টুলটি ব্যবহার করতে পারো তোমার সমস্যা আরো সহজে শনাক্ত করার জন্যে। 
> 
> {.is-info}
### ওয়েবপেজটি রিলোড করো
তুমি তোমার কীবোর্ডের <kbd>CTRL+R</kbd>/<kbd>F5</kbd> (উইন্ডোজ) অথবা <kbd>CMD+R</kbd> (ম্যাকওস) দিতে পারো রিফ্রেশ বাটন খোঁজার বদলে।

### তুমি কি Discord অ্যাপটি ব্যবহার করছ?
Discord - এর ব্রাউজার ভার্সনে PreMiD কাজ করে **না**, তোমাকে অবশ্যই অ্যাপটা ডাউনলোড করতে হবে [এখানে](https://discord.com/download)।

### নিশ্চিত করো যে তুমি সেটিংসে Discord গেম এক্টিভিটি অন রেখেছ
**User Settings** > **Game Activity** ![gameactivity_edited.png](/gameactivity_edited.png)

### নিশ্চিত হও যে Discord এডমিনিস্ট্রেটরে রান হচ্ছে না
খুবই গুরুত্বপূর্ণ। Discord RPC কাজ করবে না যদি তুমি Discord এডমিনিস্ট্রেটরে রান করো।

### তুমি কি সেটিংসের সাথে একটি Presence ব্যবহার করছ?
অনেক Presences (`Twitch` এবং `SoundCloud` সহ) একটি এক্সটেনশন সমস্যায় প্রভাবিত। এই সমস্যাটির ফলে এক্সটেনশনটি সঠিকভাবে সেটিংস এর ডিফল্ট মান নিতে পারেনা।

এটা সমাধান করার জন্যে, যা করতে হবে সেটা হচ্ছে সবার উপরের সেটিংটি টগল করা: ![presencesettings.gif](/presencesettings.gif)

### তোমার ব্রাউজারটি রিস্টার্ট করো
<kbd>Alt</kbd>+<kbd>F4</kbd> (উইন্ডোজ) অথবা <kbd>CMD</kbd>+<kbd>Q</kbd> (ম্যাক ওএস) এও ভালো কাজ করে। (অবশ্য তোমাকে আবার তোমার ব্রাউজার স্টার্ট করতে হবে।)

### PreMiD (অ্যাপ্লিকেশন) রিস্টার্ট করো
![quit.png](/quit.png) তোমাকে পরে PreMiD রিস্টার্ট করতে হবে।

### Discord রিস্টার্ট করো
<kbd>CTRL+R</kbd> (উইন্ডোজ) অথবা <kbd>CMD+R</kbd> (ম্যাক ওএস) দাও তোমার কীবোর্ডে বা Discord ম্যানুয়ালি রিস্টার্ট করো।

### চেক করো তোমার কম্পিউটারে অ্যান্টিভাইরাস অথবা ফায়ারওয়াল চলছে কিনা
কখনও কখনও অ্যান্টিভাইরাস প্রোগ্রাম এবং ফায়ারওয়াল অ্যাপ্লিকেশনগুলোকে ব্লক করে যেগুলো সার্ভার তৈরি/হোস্ট করে অথবা শুধুমাত্র ইন্টারনেটে কানেক্ট হওয়ার চেষ্টা করে। আমরা একটি লোকাল সার্ভার ব্যবহার করছি আমাদের অ্যাপ্লিকেশন এবং এক্সটেনশন এর মাঝে ডাটা নেওয়া ও দেওয়ার জন্যে, তাই তুমি যদি অ্যাপ্লিকেশন এর ডাটা দেওয়ার ক্ষমতাকে ব্লক করো তাহলে তুমি সম্ভবত PreMiD ব্যবহার করতে পারবে না।

### তোমার অ্যাডনগুলো বন্ধ করো
তোমার সব অ্যাডনগুলো বন্ধ করো এবং দেখো এটি কাজ করে কিনা। যদি কাজ করে, তাহলে অ্যাডনগুলো ধাপে ধাপে অন করো এবং আমাদের বলো কোন অ্যাডনটি PreMiD - তে সমস্যা সৃষ্টি করেছে।

### তোমার কম্পিউটার রিস্টার্ট করো
আমি আশা করি তুমি জানো কীভাবে একটি কম্পিউটারকে রিস্টার্ট করতে হয়।

### PreMiD আবার ইন্সটল করো
কখনও কখনও ফাইলগুলোতে সমস্যা থাকতে পারে... ইন্সটলেশনের টিউটোরিয়ালগুলো পাওয়া যাবে [এখানে](/install)।

### ম্যানুয়ালি ডিলিট করা
উইন্ডোজ: ফাইল এক্সপ্লোরারে লেখ `%appdata%` এবং ডিলিট করো `PreMiD` ফোল্ডারটি। ম্যাক ওএস: `~/users/USER/~Library/Application Support/` এবং ডিলিট করো `PreMiD` ফোল্ডারটি।

### PreMiD - কে McAfee ভাইরাস হিসেবে শনাক্ত করেছে (উইন্ডোজ)
এটি McAfee থেকে একটি ফল্‌স পজিটিভ এবং আমরা এই সমস্যাটি তাদের কাছে রিপোর্ট করেছি, আপাতত তুমি PreMiD - কে বাদ দিতে পারো স্ক্যান করা হতে এই ধাপগুলো অনুসরণ করে:

> তুমি যদি এই ধাপগুলো নেওয়া সম্পর্কে নিশ্চিত না হও, নির্দ্বিধায় একটি টিকেট তৈরি করো [#support](https://discord.premid.app/) - এ এবং আমাদের একজন সাপোর্ট এজেন্ট তোমাকে সাহায্য করতে পারবে! 
> 
> {.is-warning}

1. McAfee অ্যাপ্লিকেশনটি ওপেন করো এবং উপরের ডানে সেটিংস আইকনে ক্লিক করো। <img src="https://i.imgur.com/rPLZn6c.png" width="500px" style="max-width:100%;" />
2. ক্লিক করো "Quarantined Items" (উপর থেকে দ্বিতীয়)।
3. এটাকে এক্সপ্যান্ড করো, এবং `>` আইকনটিকে ক্লিক করো "settings.dat" নামের একটি আইটেমের সামনে।
4. নিশ্চিত করো যে প্যাথটিতে যেন "AppData\Local\Temp\PreMiD" থাকে, যদি থাকে তাহলে এটিকে সিলেক্ট করো এবং ক্লিক করো "Restore". <img src="https://i.imgur.com/9nvHmiI.png" width="500px" style="max-width:100%;" />
5. রিস্টোর হওয়ার পরে তুমি "Quarantined Items" পপআপ বন্ধ করতে পারো, তারপর আবার উপরের ডানে সেটিংস আইকনে ক্লিক করো।
6. ক্লিক করো "Real-Time Scanning" (উপর থেকে তৃতীয়)।
7. এটাকে এক্সপ্যান্ড করো এবং ক্লিক করো "Add file".
8. ফাইল এক্সপ্লোরারের অ্যাড্রেস বারে টাইপ করো "%appdata%" এবং এন্টার চাপ দাও। <img src="https://i.imgur.com/2bchwLe.png" width="500px" style="max-width:100%;" />
9. "PreMiD" ফোল্ডারটি ওপেন করো এবং সিলেক্ট করো "PreMiD.exe" ফাইলটি এবং ওপেন ক্লিক করো। <img src="https://i.imgur.com/aHOyv3V.png" width="500px" style="max-width:100%;" />
10. McAfee এখন আমাদের ফাইলকে উপেক্ষা করবে, শুধু আমাদের অ্যাপ্লিকেশন রান করো এবং তুমি PreMiD চালাতে পারবে।

### PreMiD স্ট্যাটাস Discord - এ ঠিকমতো দেখাচ্ছে না!
চিন্তা করবে না। <kbd>CTRL+R</kbd> (উইন্ডোজ) অথবা <kbd>CMD+R</kbd> (ম্যাক ওএস) কীবাইন্ড দাও তোমার Discord উইন্ডোতে ফোকাস করা অবস্থায় এটাকে রিলোড করার জন্য।

<a name="linux"></a>

# লিনাক্স এর সমস্যা সমাধান
### Ubuntu/Debian ভিত্তিক ডিস্ট্রিবিউশনগুলো
তুমি যদি Snapcraft, RPC দিয়ে Discord ডাউনলোড করো তাহলে এটা কাজ করবে না। You have to uninstall the Snapcraft version by executing `sudo snap remove discord` on a terminal, download **[Discord's Linux build](https://discordapp.com/api/download?platform=linux)** (**[or Discord Canary](https://discordapp.com/api/canary/download?platform=linux)**), then navigating to the directory you downloaded Discord to (usually `$HOME/Downloads`), then installing the package using `sudo dpkg -i discord-*.deb`. If AppImage doesn't work, you should consider checking our other packages by **[this link](https://packagecloud.io/premid/linux)**.

### Arch Linux ভিত্তিক ডিস্ট্রিবিউশনগুলো
Arch Linux based distros should use AUR (Arch User Repository) package that is named <code>premid</code> or <code>premid-git</code> (<em x-id="3">WARNING: This repository builds premid from our source code.</em>). If you don't want to install an AUR manager (yay etc.), you can check out our AppImage that is downloadable from our <strong x-id="1"><a href="https://github.com/premid/linux/releases">Linux repository</a></strong>.
<em x-id="3">Warning: the package in the <strong x-id="1">AUR</strong> repository is not maintained by us (as PreMiD organization), but by other people.</em>

### পোর্ট বাইন্ডিং
You should know that <strong x-id="1">PreMiD</strong> binds itself to the port <strong x-id="1">3020</strong>. This is necessary for the Extension and the Application communicate. If <strong x-id="1">PreMiD</strong> shows you an error about this port, you should check if something is binded to the 3020 port by running <code>sudo lsof -i:3020</code> or <code>sudo netstat -tnlp | grep :3020</code> in your terminal. If some process is binded to it you should make sure to free the port and try running <code>PreMiD</code> again.

### PreMiD's AppImage doesn't launch at login
As we stated in our **Linux repository**, AppImage can't be launched at login. You can add it to autostart manually by doing these steps:
1. Make a file named <strong x-id="1">rc.local</strong> in the <code>/etc</code> directory.
2. Open this file in your favourite editor and paste given code with changing some things:
```bash
#!/bin/bash
# Required to run as /bin/bash (if you use zsh etc. you can change it.)

# Example: /home/PreMiD/PreMiD*.AppImage
<directory to appimage>/PreMiD*.AppImage

exit 0
```
3. Save file and chmod it as executable `sudo chmod a+x /etc/rc.local`.
4. Restart your PC and PreMiD AppImage should launch at login.

<a name="macos"></a>

# ম্যাকওস এর সমস্যা সমাধান
### "Error creating directory"
<img src="https://i.imgur.com/td92lf6.png" width="300px" style="max-width:100%;" />

তুমি যদি এই ত্রুটিটি পাও, এর মানে হচ্ছে যে তোমার অ্যাকাউন্ট এর এডমিনিস্ট্রেটর পারমিশন নেই। তোমাকে ম্যানুয়ালি একটি ফোল্ডার তৈরি করতে হবে এই ধাপগুলো অনুসরণ করে:
1. Finder ওপেন করো এবং **Applications** ফোল্ডার ওপেন করো।
2. ফাঁকা জায়গায় মাউসের ডান পাশের বাটনটি ক্লিক করো এবং ক্লিক করো **Create folder**.
3. এই ফোল্ডারটির নাম দাও `PreMiD` (খেয়াল রেখো বড় হাতের অক্ষরগুলো সম্পর্কে)।
4. ইন্সটলারটি আবার ওপেন করো।

# আমার সমস্যা সমাধান হয়নি
একটি টিকেট খোলো [#support](https://discord.premid.app/) - এ।