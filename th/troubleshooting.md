---
title: การแก้ปัญหา
description: ทุกอย่างเพื่อใช้แก้ปัญหาของคุณ
published: true
date: 2021-09-18T14:08:01.002Z
tags:
editor: markdown
dateCreated: 2021-09-07T01:17:32.312Z
---

> ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้งส่วนขยาย ** และ ** แอปพลิเคชั่นแล้ว! 
> 
> {.is-warning}

รวมอยู่ในหน้านี้:
1. [การแก้ปัญหาทั่วไป](https://docs.premid.app/troubleshooting#general)
2. [การแก้ปัญหาบน Linux](https://docs.premid.app/troubleshooting#linux)
3. [การแก้ปัญหาบน MacOS](https://docs.premid.app/troubleshooting#macos)

<a name="general"></a>

# การแก้ปัญหาทั่วไป
> You can use [this](https://qkeleq10.github.io/PreMiD-Troubleshooting/) tool to more easily identify your issue. 
> 
> {.is-info}
### โหลดหน้านี้ใหม่
คุณสามารถกด <kbd>CTRL+R</kbd>/<kbd>F5</kbd> (Windows) หรือ <kbd>CMD+R</kbd> (MacOS) บนแป้นพิมพ์ของคุณเพื่อรีโหลดหน้าเว็บ

### คุณกำลังใช้แอพ Discord รึเปล่า?
PreMiD จะ**ไม่**ทํางานสําหรับ Brower Discord คุณต้องโหลดเเอพ Discord [ตรงนี้](https://discord.com/download)

### ตรวจสอบให้แน่ใจว่าคุณได้เปิด Activity Status ในการตั้งค่า Discord แล้ว
**ตั้งค่าบัญชีผู้ใช้** > **Activity Status**
<img src="https://i.imgur.com/9SfrrWm.png" width="500px" style="max-width:100%;" />

### ต้องแน่ใจว่า Discord ไม่ได้เปิดแบบ Administrator
Really important. Discord RPC will not work if you run Discord as an administrator.

### คุณได้ใช้การตั้งค่าของ Presence?
Many presences (including `Twitch` and `SoundCloud`) are affected by an extension issue. This issue causes the extension to not grab the default values of settings properly.

To solve this, all you have to do is toggle the topmost setting:
<img src="https://i.imgur.com/JtXxTzg.gif" width="500px" style="max-width:100%;" />

### รีสตาร์ทบราวเซอร์ของคุณ
<kbd>Alt</kbd>+<kbd>F4</kbd> (Windows) or <kbd>CMD</kbd>+<kbd>Q</kbd> (MacOS) does a good job too. (You have to start your browser again obviously.)

### รีสตาร์ท PreMiD (แอพพลิเคชั่น)
<img src="https://i.imgur.com/wQA15xu.png" width="500px" style="max-width:100%;" />
You have to restart PreMiD afterwards.

### รีโหลด/รีสตาร์ท ดิสคอร์ด
Press <kbd>CTRL+R</kbd> (Windows) or <kbd>CMD+R</kbd> (MacOS) on your keyboard or restart Discord manually.

### ตรวจสอบว่าคุณมีโปรแกรมป้องกันไวรัสหรือไฟร์วอลล์ทำงานบนคอมพิวเตอร์ของคุณหรือไม่ ?
Sometimes antivirus programs and firewalls are blocking applications which are creating/hosting servers or just connecting to the internet. We are using a local server to receive and pass data between our app and extension, so if you will block app's ability to pass data you probably will not be able to use PreMiD.

### ปิดการใช้งาน addons
Disable all your addons and see if it works. If yes, try to enable your addons step-by-step and tell us which addon broke PreMiD.

### รีสตาร์ทคอมพิวเตอร์ของคุณ
I hope you know how to restart a computer.

### ติดตั้ง PreMiD อีกครั้ง
Sometimes there is something wrong with the files... Tutorials for the installation can be found [here](/install).

### ลบข้อมูลด้วยตัวเอง
Windows: Write `%appdata%` on the file explorer and delete the `PreMiD` folder. MacOS: `~/users/USER/~Library/Application Support/` and delete the `PreMiD` folder.

### McAfee ตรวจจับ PreMiD เป็นไวรัส (Windows)
This is a false positive from McAfee and we have reported the issue to them, for now you can exclude PreMiD from the scan by doing the following steps:

> If you do not feel confident taking these steps, feel free to make a ticket in [#support](https://discord.premid.app/) and one of our Support Agents will be able to help you out! 
> 
> {.is-warning}

1. เปิดเเอพ McAfee เเละกดที่ไอคอนการตั้งค่าตรงขวาบน<img src="https://i.imgur.com/rPLZn6c.png" width="500px" style="max-width:100%;" />
2. คลิ๊ก Quarantined Items (อันที่ 2 นับจากบนสุด)
3. ขยายมัน, เเละกดไอคอน `>` ก่อนไฟล์ที่ชื่อว่า "settings.bat"
4. เเน่ใจว่าที่อยู่ของ PreMiD อยู่ที่  "AppData\Local\Temp\PreMiD", ถ้าใช้กดเลือกมันเเละกู้คืนกลับมา<img src="https://i.imgur.com/9nvHmiI.png" width="500px" style="max-width:100%;" />
5. หลังจากนั้นคุณสามารถปิด  "Quarantined Items" เเละกดไอคอนการตั้งค่าอีกครั้งตรงขวาบน
6. กด "Real-Time Scanning" (อันที่ 3 นับจากบนสุด)
7. กดขยายมันเเล้วเลือก "เพิ่มไฟล์"
8. Type "%appdata%" in the address bar of the File Explorer and press Enter. <img src="https://i.imgur.com/2bchwLe.png" width="500px" style="max-width:100%;" />
9. เปิด PreMiD โฟลเดอร์ เเละเลือกไฟล์ PreMiD.exe  เเละรันมัน<img src="https://i.imgur.com/aHOyv3V.png" width="500px" style="max-width:100%;" />
10. McAfee ควรละเว้นไฟล์ของเรา, รัน PreMiD เเละน่าจะปกติเเล้ว!

### สถานะ PreMiD เกิดบัคบน Discord!
Don't worry. Press the <kbd>CTRL+R</kbd> (Windows) or <kbd>CMD+R</kbd> (MacOS) keybind while focused on your discord window to reload it.

<a name="linux"></a>

# การแก้ปัญหาบน Linux
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

# การแก้ปัญหาบน MacOS
### Error creating directory
<img src="https://i.imgur.com/td92lf6.png" width="300px" style="max-width:100%;" />

If you get this error, it means that your account doesn't have Administrator permissions and you need to create folder manually by doing these steps:
1. เปิด Finder จากนั้นเปิดโฟลเดอร์ **Applications**
2. คลิกขวาบนพื้นที่ว่างจากนั้นคลิก **สร้างโฟลเดอร์**
3. To this folder assign `PreMiD` name (remember about upper-cased letters).
4. เปิดตัวติดตั้งอีกครั้ง

# นั่นไม่ได้แก้ปัญหาของฉัน
Please open a ticket in [#support](https://discord.premid.app/).
