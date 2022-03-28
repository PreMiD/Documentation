---
title: اشکال‌زدایی
description: همه چیز برای برطرف کردن مشکل شما
published: true
date: 2021-12-20T14:27:18.034Z
tags:
editor: markdown
dateCreated: 2021-09-07T01:17:32.312Z
---

> مطمئن شوید که هردو افزونه **و** برنامه را نصب کرده باشید! 
> 
> {.is-warning}

موارد شامل شده در این صفحه:
1. [اشکال‌زدایی کلی](https://docs.premid.app/troubleshooting#general)
2. [اشکال‌زدایی لینوکس](https://docs.premid.app/troubleshooting#linux)
3. [اشکال‌زدایی MacOS](https://docs.premid.app/troubleshooting#macos)

<a name="general"></a>

# اشکال‌زدایی کلی
> شما می توانید از [این](https://qkeleq10.github.io/PreMiD-Troubleshooting/) ابزار برای راحت تر پیداکردن مشکلتان استفاده کنید. 
> 
> {.is-info}
### صفحه را مجددا بارگزاری کنید
شما می توانید به‌جای پیدا کردن دکمه بارگزاری مجدد در مرورگرخود، با فشردن <kbd>CTRL+R</kbd>/<kbd>F5</kbd> در (Windows) یا <kbd>CMD+R</kbd> در (MacOS) در صفحه کلیدتان نیز صفحه را مجدداً بارگزاری کنید.

### آیا از نرم‌افزار دیسکورد استفاده می کنید؟
PreMiD با نسخه های وب دیسکورد کار **نمی کند**، شما باید نرم‌افزار دیسکورد را از [اینجا](https://discord.com/download) دانلود کنید.

### مطمئن شوید که Activity Status را در تنظیمات دیسکورد فعال کرده باشید
**تنظیمات کاربر** > **Activity Status**
<img src="https://i.imgur.com/9SfrrWm.png" width="500px" style="max-width:100%;" />

### مطمئن شوید که دیسکورد روی حالت administrator اجرا نمی شود
بسیار بسیار مهم! RPC های دیسکورد روی حالت administrator اجرا نمی‌شوند.

### Are you using a presence with settings?
خیلی از Presence ها (از جمله `Twitch` و `SoundCloud`) تحت تاثیر مشکلات افزونه‌ای قرار میگیرند. این مشکل باعث می شود که افزونه نتواند مقادیر پیشفرض را برای تنظیمات به درستی به‌دست بیاورند.

برای حل این مشکل، تمام کاری که باید انجام دهید این است که دکمه تنظیمات را تغییر وضعیت دهید:
<img src="https://i.imgur.com/JtXxTzg.gif" width="500px" style="max-width:100%;" />

### مرورگر خود را دوباره باز کنید
<kbd>Alt</kbd>+<kbd>F4</kbd> در (Windows) یا <kbd>CMD</kbd>+<kbd>Q</kbd> در (MacOS) هم خوب عمل می کنند. (مشخصاً باید مرورگر خودتان را دوباره باز کنید.)

### باز کردن مجدد PreMiD (برنامه)
<img src="https://i.imgur.com/g3ShdnU.png" width="500px" style="max-width:100%;" />
بعد از آن شما باید PreMiD را ریستارت کنید.

### بارگزاری/اجرای مجدد دیسکورد
<kbd>CTRL+R</kbd> (در Windows) یا <kbd>CMD+R</kbd> (در MacOS) را روی صفحه کلید خود فشار دهید یا به طور دستی دیسکورد خود را مجددا باز نمایید.

### چک کنید که آیا ضدویروس یا دیوارآتش کامپیوتر شما در حال اجرا می باشند
بعضی مواقع برنامه های ضد ویروس یا دیوار آتش مانع اجرای برنامه هایی می شوند که درحال ساخت/میزبانی سرور هستند یا فقط درحال به اینترنت می باشند. ما از سرور محلی برای دریافت و انتقال اطلاعات بین برنامه و افزونه‌مان استفاده می کنیم، پس اگر شما دسترسی انتقال اطلاعات برنامه را مسدود کنید، احتمالا نمی توانید از PreMiD استفاده کنید.

### افزونه های خود را غیرفعال کنید
همه افزونه های خود را غیر فعال کنید و ببینید که این کار جواب می‌دهد یا نه. اگر بله، سعی کنید افزونه های خود را یکی یکی فعال کنید و امتحان کنید، و بعد به ما افزونه‌ای که باعث خرابی و اجرا نشدن PreMiD شده را به ما بگویید.

### کامپیوتر را دوباره راه‌اندازی کنید
امیدوارم بدونید که چطور میشه کامپیوتر رو ریستارت کرد.

### PreMiD را دوباره نصب کنید
بعضی مواقع مشکل از فایل ها می‌باشد... آموزش برای نصب را می توانید از [اینجا](/install) بیابید.

### حذف دستی
ویندوز: در نوار مرورگر فایل `%appdata%` را بنویسید و پوشه `PreMiD` را حذف کنید. MacOS: به آدرس `~/users/USER/~Library/Application Support/` رفته و بعد پوشه `PreMiD` را حذف کنید.

### McAfee برنامه PreMiD را به عنوان ویروس شناسایی کرده (Windows)
این یک تائید اشتباه از سوی McAfee است و ما این مشکل را به آن ها گزارش داده‌ایم، درحال حاضر شما می توانید PreMiD را از اسکن شدن مستثناء کنید با انجام مراحل زیر:

> اگر مطمئن نیستید که این مراحل را چگونه انجام دهید، می توانید یک تیکت در [#support](https://discord.premid.app/) ایجاد کنید و یکی از پشتیبانان در دسترس ما برای کمک به شما خواهد آمد! 
> 
> {.is-warning}

1. برنامه McAfee را باز کنید و روی آیکن تنظیمات در سمت راست بالا کلیک کنید. <img src="https://i.imgur.com/rPLZn6c.png" width="500px" style="max-width:100%;" />
2. روی "Quarantined Items" کلیک کنید (مورد دوم از بالا).
3. به طور گسترده بازش کنید، روی آیکن `>` قبل از آیتمی که نام "settings.dat" را دارد کلیک کنید.
4. مطمئن شوید که مسیر مشخص شده شامل "AppData\Local\Temp\PreMiD" می باشد، در این صورت روی آن کلیک کنید و restore را بزنید. <img src="https://i.imgur.com/9nvHmiI.png" width="500px" style="max-width:100%;" />
5. بعد از آنکه بازیابی انجام شد می توانید پنجره "Quarantined Items" را ببندید و دوباره روی آیکن تنظیمات بالا سمت راست صفحه کلیک کنید.
6. روی "Real-Time Scanning" کلیک کنید (مورد سوم از بالا).
7. به حالت گسترده بازش کنید و روی "Add file" بزنید.
8. در نوار آدرس مدیریت فایل "%appdata%" را وارد کنید و Enter صفحه کلید را بزنید. <img src="https://i.imgur.com/2bchwLe.png" width="500px" style="max-width:100%;" />
9. پوشه "PreMiD" را باز کنید و فایل "PreMiD.exe" را انتخاب کنید و روی باز کردن بزنید. <img src="https://i.imgur.com/aHOyv3V.png" width="500px" style="max-width:100%;" />
10. از الان به بعد McAfee دیگر نباید کاری به فایل هایمان داشته باشد، برنامه را دوباره باز کنید و از این به بعد همه چیز باید خوب پیش برود.

### وضعیت PreMiD در دیسکورد باگ خورده!
نگران نباشید. Press the <kbd>CTRL+R</kbd> (Windows) or <kbd>CMD+R</kbd> (MacOS) keybind while focused on your Discord window to reload it.

<a name="linux"></a>

# اشکال‌زدایی لینوکس
### Ubuntu/Debian based distros
If you have downloaded Discord through Snapcraft, RPC will not work. You have to uninstall the Snapcraft version by executing `sudo snap remove discord` on a terminal, download **[Discord's Linux build](https://discordapp.com/api/download?platform=linux)** (**[or Discord Canary](https://discordapp.com/api/canary/download?platform=linux)**), then navigating to the directory you downloaded Discord to (usually `$HOME/Downloads`), then installing the package using `sudo dpkg -i discord-*.deb`. If AppImage doesn't work, you should consider checking our other packages by **[this link](https://packagecloud.io/premid/linux)**.

### Arch Linux based distros
Arch Linux based distros should use AUR (Arch User Repository) package that is named <code>premid</code> or <code>premid-git</code> (<em x-id="3">WARNING: This repository builds premid from our source code.</em>). If you don't want to install an AUR manager (yay etc.), you can check out our AppImage that is downloadable from our <strong x-id="1"><a href="https://github.com/premid/linux/releases">Linux repository</a></strong>.
<em x-id="3">Warning: the package in the <strong x-id="1">AUR</strong> repository is not maintained by us (as PreMiD organization), but by other people.</em>

### Port binding
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

# اشکال‌زدایی MacOS
### Error creating directory
<img src="https://i.imgur.com/td92lf6.png" width="300px" style="max-width:100%;" />

If you get this error, it means that your account doesn't have Administrator permissions and you need to create folder manually by doing these steps:
1. Open finder and open **Applications** folder.
2. Right-click on blank space and click **Create folder**.
3. To this folder assign `PreMiD` name (remember about upper-cased letters).
4. Open installer again.

# That has not solved my problem
Please open a ticket in [#support](https://discord.premid.app/).
