---
title: Xử lý sự cố
description: Everything to solve your problem
published: true
date: 2021-09-18T14:08:01.002Z
tags:
editor: markdown
dateCreated: 2021-09-07T01:17:32.312Z
---

> Make sure you have the extension **and** the application installed! 
> 
> {.is-warning}

Included on this page:
1. [General troubleshooting](https://docs.premid.app/troubleshooting#general)
2. [Linux troubleshooting](https://docs.premid.app/troubleshooting#linux)
3. [MacOS troubleshooting](https://docs.premid.app/troubleshooting#macos)

<a name="general"></a>

# General troubleshooting
> You can use [this](https://qkeleq10.github.io/PreMiD-Troubleshooting/) tool to more easily identify your issue. 
> 
> {.is-info}
### Tải lại trang
Bạn có thể nhấn <kbd>CTRL+R</kbd>/<kbd>F5</kbd> (Windows) hoặc <kbd>CMD+R</kbd> (MacOS) trên bàn phím của bạn thay vì tìm kiếm nút tải lại.

### Are you using the Discord app?
PreMiD sẽ **không** hoạt động trên phiên bản trình duyệt web của Discord, vui lòng tải xuống phiên bản ứng dụng [tại đây](https://discord.com/download).

### Hãy chắc chắn là bạn đã cho phép Hoạt động trong game trong Discord trong cài đặt
**Cái đặt người dùng** > **Hoạt động trong game**
<img src="https://i.imgur.com/9SfrrWm.png" width="500px" style="max-width:100%;" />

### Hãy chắc chắn là Discord đang KHÔNG hoạt động ở chế độ administrator
Really important. Discord RPC will not work if you run Discord as an administrator.

### Are you using a presence with settings?
Many presences (including `Twitch` and `SoundCloud`) are affected by an extension issue. This issue causes the extension to not grab the default values of settings properly.

To solve this, all you have to do is toggle the topmost setting:
<img src="https://i.imgur.com/JtXxTzg.gif" width="500px" style="max-width:100%;" />

### Khởi động lại trình duyệt của bạn
<kbd>Alt</kbd>+<kbd>F4</kbd> (Windows) or <kbd>CMD</kbd>+<kbd>Q</kbd> (MacOS) does a good job too. (You have to start your browser again obviously.)

### Khởi động lại PreMiD (Ứng dụng)
<img src="https://i.imgur.com/wQA15xu.png" width="500px" style="max-width:100%;" />
You have to restart PreMiD afterwards.

### Tải lại/khởi động lại Discord
Press <kbd>CTRL+R</kbd> (Windows) or <kbd>CMD+R</kbd> (MacOS) on your keyboard or restart Discord manually.

### Check if you have antivirus or firewall running on your computer
Sometimes antivirus programs and firewalls are blocking applications which are creating/hosting servers or just connecting to the internet. We are using a local server to receive and pass data between our app and extension, so if you will block app's ability to pass data you probably will not be able to use PreMiD.

### Disable your addons
Disable all your addons and see if it works. If yes, try to enable your addons step-by-step and tell us which addon broke PreMiD.

### Khởi động lại máy tính của bạn
I hope you know how to restart a computer.

### Cài đặt lại PreMiD
Sometimes there is something wrong with the files... Tutorials for the installation can be found [here](/install).

### Gỡ cài đặt thủ công
Windows: Write `%appdata%` on the file explorer and delete the `PreMiD` folder. MacOS: `~/users/USER/~Library/Application Support/` and delete the `PreMiD` folder.

### McAfee phát hiện PreMiD là vi-rút (Windows)
This is a false positive from McAfee and we have reported the issue to them, for now you can exclude PreMiD from the scan by doing the following steps:

> If you do not feel confident taking these steps, feel free to make a ticket in [#support](https://discord.premid.app/) and one of our Support Agents will be able to help you out! 
> 
> {.is-warning}

1. Mở ứng dụng McAfee và bấm nút cài đặt ở trên cùng phía bên phải. <img src="https://i.imgur.com/rPLZn6c.png" width="500px" style="max-width:100%;" />
2. Chọn "Tệp tin cách ly" (Thứ hai từ trên đầu).
3. Mở rộng nó, và click vào nút `>` trước tệp tin với tên "settings.dat".
4. Hãy chắc chắn đường dẫn là "AppData\Local\Temp\PreMiD", sau đó chọn nó và bấm phục hồi. <img src="https://i.imgur.com/9nvHmiI.png" width="500px" style="max-width:100%;" />
5. Sau khi phục hồi xong bạn có thể đóng cửa sổ "Tệp tin cách ly", sau đó bấm vào nút cài đặt ở trên cùng bên phải một lần nữa.
6. Chọn "Quét thời gian thực" (Thứ ba từ trên đầu).
7. Mở rộng nó và bấm "Chọn tệp tin".
8. Type "%appdata%" in the address bar of the File Explorer and press Enter. <img src="https://i.imgur.com/2bchwLe.png" width="500px" style="max-width:100%;" />
9. Mở thư mục "PreMiD" và chọn tệp tin "PreMiD.exe" và bấm "mở". <img src="https://i.imgur.com/aHOyv3V.png" width="500px" style="max-width:100%;" />
10. McAfee sẽ bỏ qua tệp tin này, chỉ cần mở ứng dụng của chúng tôi là xong.

### PreMiD status bugged on Discord!
Don't worry. Press the <kbd>CTRL+R</kbd> (Windows) or <kbd>CMD+R</kbd> (MacOS) keybind while focused on your Discord window to reload it.

<a name="linux"></a>

# Linux troubleshooting
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

# MacOS troubleshooting
### Error creating directory
<img src="https://i.imgur.com/td92lf6.png" width="300px" style="max-width:100%;" />

If you get this error, it means that your account doesn't have Administrator permissions and you need to create folder manually by doing these steps:
1. Open finder and open **Applications** folder.
2. Right-click on blank space and click **Create folder**.
3. To this folder assign `PreMiD` name (remember about upper-cased letters).
4. Open installer again.

# Điều đó chưa giải được vấn đề của tôi
Please open a ticket in [#support](https://discord.premid.app/).
