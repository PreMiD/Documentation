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

### নিশ্চিত করো যে তুমি সেটিংসে Discord অ্যাক্টিভিটি স্ট্যাটাস অন রেখেছ
**User Settings** > **Activity Status**
<img src="https://i.imgur.com/9SfrrWm.png" width="500px" style="max-width:100%;" />

### নিশ্চিত হও যে Discord এডমিনিস্ট্রেটরে রান হচ্ছে না
Really important. Discord RPC will not work if you run Discord as an administrator.

### তুমি কি সেটিংসের সাথে একটি Presence ব্যবহার করছ?
Many presences (including `Twitch` and `SoundCloud`) are affected by an extension issue. This issue causes the extension to not grab the default values of settings properly.

To solve this, all you have to do is toggle the topmost setting:
<img src="https://i.imgur.com/JtXxTzg.gif" width="500px" style="max-width:100%;" />

### তোমার ব্রাউজারটি রিস্টার্ট করো
<kbd>Alt</kbd>+<kbd>F4</kbd> (Windows) or <kbd>CMD</kbd>+<kbd>Q</kbd> (MacOS) does a good job too. (You have to start your browser again obviously.)

### PreMiD (অ্যাপ্লিকেশন) রিস্টার্ট করো
<img src="https://i.imgur.com/wQA15xu.png" width="500px" style="max-width:100%;" />
You have to restart PreMiD afterwards.

### Discord রিস্টার্ট করো
Press <kbd>CTRL+R</kbd> (Windows) or <kbd>CMD+R</kbd> (MacOS) on your keyboard or restart Discord manually.

### চেক করো তোমার কম্পিউটারে অ্যান্টিভাইরাস অথবা ফায়ারওয়াল চলছে কিনা
Sometimes antivirus programs and firewalls are blocking applications which are creating/hosting servers or just connecting to the internet. We are using a local server to receive and pass data between our app and extension, so if you will block app's ability to pass data you probably will not be able to use PreMiD.

### তোমার অ্যাডনগুলো বন্ধ করো
Disable all your addons and see if it works. If yes, try to enable your addons step-by-step and tell us which addon broke PreMiD.

### তোমার কম্পিউটার রিস্টার্ট করো
I hope you know how to restart a computer.

### PreMiD আবার ইন্সটল করো
Sometimes there is something wrong with the files... Tutorials for the installation can be found [here](/install).

### ম্যানুয়ালি ডিলিট করা
Windows: Write `%appdata%` on the file explorer and delete the `PreMiD` folder. MacOS: `~/users/USER/~Library/Application Support/` and delete the `PreMiD` folder.

### PreMiD - কে McAfee ভাইরাস হিসেবে শনাক্ত করেছে (উইন্ডোজ)
This is a false positive from McAfee and we have reported the issue to them, for now you can exclude PreMiD from the scan by doing the following steps:

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
Don't worry. Press the <kbd>CTRL+R</kbd> (Windows) or <kbd>CMD+R</kbd> (MacOS) keybind while focused on your discord window to reload it.

<a name="linux"></a>

# লিনাক্স এর সমস্যা সমাধান
### Ubuntu/Debian ভিত্তিক ডিস্ট্রিবিউশনগুলো
If you have downloaded Discord through Snapcraft, RPC will not work. You have to uninstall the Snapcraft version by executing `sudo snap remove discord` on a terminal, download **[Discord's Linux build](https://discordapp.com/api/download?platform=linux)** (**[or Discord Canary](https://discordapp.com/api/canary/download?platform=linux)**), then navigating to the directory you downloaded Discord to (usually `$HOME/Downloads`), then installing the package using `sudo dpkg -i discord-*.deb`. If AppImage doesn't work, you should consider checking our other packages by **[this link](https://packagecloud.io/premid/linux)**.

### Arch Linux ভিত্তিক ডিস্ট্রিবিউশনগুলো
Arch Linux based distros should use AUR (Arch User Repository) package that is named <code>premid</code> or <code>premid-git</code> (<em x-id="3">WARNING: This repository builds premid from our source code.</em>). If you don't want to install an AUR manager (yay etc.), you can check out our AppImage that is downloadable from our <strong x-id="1"><a href="https://github.com/premid/linux/releases">Linux repository</a></strong>.
<em x-id="3">Warning: the package in the <strong x-id="1">AUR</strong> repository is not maintained by us (as PreMiD organization), but by other people.</em>

### পোর্ট বাইন্ডিং
You should know that <strong x-id="1">PreMiD</strong> binds itself to the port <strong x-id="1">3020</strong>. This is necessary for the Extension and the Application communicate. If <strong x-id="1">PreMiD</strong> shows you an error about this port, you should check if something is binded to the 3020 port by running <code>sudo lsof -i:3020</code> or <code>sudo netstat -tnlp | grep :3020</code> in your terminal. If some process is binded to it you should make sure to free the port and try running <code>PreMiD</code> again.

### PreMiD - এর AppImage চালু হয় না লগইনের সময়
As we stated in our **Linux repository**, AppImage can't be launched at login. You can add it to autostart manually by doing these steps:
1. <strong x-id="1">rc.local</strong> নামের একটি ফাইল তৈরি করো <code>/etc</code> ডিরেক্টরিতে।
2. এই ফাইলটি ওপেন করো তোমার প্রিয় এডিটরে এবং নিচের কোডটি পেস্ট করো কিছু জিনিস পরিবর্তন করে:
```bash
#!/bin/bash
# প্রয়োজন /bin/bash হিসেবে রান করার জন্য (যদি তুমি zsh ইত্যাদি ব্যবহার করো তুমি এটিকে চেঞ্জ করতে পারো।)

# উদাহরণ: /home/PreMiD/PreMiD*.AppImage
<directory to appimage>/PreMiD*.AppImage

exit 0
```
3. ফাইলটিকে সেভ করো এবং এটিকে chmod করো এক্সিকিউটেবল হিসেবে `sudo chmod a+x /etc/rc.local`.
4. তোমার PC - টিকে রিস্টার্ট করো এবং PreMiD AppImage চালু হবে লগইনের সময়।

<a name="macos"></a>

# ম্যাকওস এর সমস্যা সমাধান
### "Error creating directory"
<img src="https://i.imgur.com/td92lf6.png" width="300px" style="max-width:100%;" />

If you get this error, it means that your account doesn't have Administrator permissions and you need to create folder manually by doing these steps:
1. Finder ওপেন করো এবং **Applications** ফোল্ডার ওপেন করো।
2. ফাঁকা জায়গায় মাউসের ডান পাশের বাটনটি ক্লিক করো এবং ক্লিক করো **Create folder**.
3. এই ফোল্ডারটির নাম দাও `PreMiD` (খেয়াল রেখো বড় হাতের অক্ষরগুলো সম্পর্কে)।
4. ইন্সটলারটি আবার ওপেন করো।

# আমার সমস্যা সমাধান হয়নি
Please open a ticket in [#support](https://discord.premid.app/).
