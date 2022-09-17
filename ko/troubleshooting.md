---
title: 문제 해결
description: 문제를 해결하기 위한 모든 것
published: true
date: 2021-12-20T14:27:18.034Z
tags:
editor: markdown
dateCreated: 2021-09-07T01:17:32.312Z
---

> 익스텐션과 앱 **모두** 설치하셨는지 확인해주세요! 
> 
> {.is-warning}

이 페이지에 포함:
1. [일반적인 문제 해결](https://docs.premid.app/troubleshooting#general)
2. [Linux 문제 해결](https://docs.premid.app/troubleshooting#linux)
3. [MacOS 문제 해결](https://docs.premid.app/troubleshooting#macos)

<a name="general"></a>

# 일반적인 문제 해결
> You can use [this](https://qkeleq10.github.io/PreMiD-Troubleshooting/) tool to more easily identify your issue. 
> 
> {.is-info}
### 페이지 새로고침
새로고침 버튼을 누르는 대신 <kbd>CTRL+R</kbd>/<kbd>F5</kbd> (Windows) 나 <kbd>CMD+R</kbd> (macOS) 를 눌러보십시오.

### 디스코드 앱을 쓰고 계신가요?
PreMiD는 디스코드 브라우저 버전에선 작동하지 **않습니다**, [이 곳](https://discord.com/download)에서 앱을 설치 할 수 있습니다.

### 설정에서 Discord 게임 활동을 활성화했는지 확인하십시오.
**사용자 설정** > **게임 활동**
<img src="https://i.imgur.com/9SfrrWm.png" width="500px" style="max-width:100%;" />

### 디스코드를 관리자 권한으로 실행하지 마세요
Really important. Discord RPC will not work if you run Discord as an administrator.

### 프리센스 설정을 사용중이신가요?
Many presences (including `Twitch` and `SoundCloud`) are affected by an extension issue. This issue causes the extension to not grab the default values of settings properly.

To solve this, all you have to do is toggle the topmost setting:
<img src="https://i.imgur.com/JtXxTzg.gif" width="500px" style="max-width:100%;" />

### 브라우저 재시작
<kbd>Alt</kbd>+<kbd>F4</kbd> (Windows) or <kbd>CMD</kbd>+<kbd>Q</kbd> (MacOS) does a good job too. (You have to start your browser again obviously.)

### PreMid 프로그램 재시작
<img src="https://i.imgur.com/g3ShdnU.png" width="500px" style="max-width:100%;" />
You have to restart PreMiD afterwards.

### Discord 재시작
Press <kbd>CTRL+R</kbd> (Windows) or <kbd>CMD+R</kbd> (MacOS) on your keyboard or restart Discord manually.

### 안티바이러스 또는 방화벽을 확인해주세요.
Sometimes antivirus programs and firewalls are blocking applications which are creating/hosting servers or just connecting to the internet. We are using a local server to receive and pass data between our app and extension, so if you block app's ability to pass data, you probably will not be able to use PreMiD.

### 애드온 비활성화 하기
Disable all your addons and see if it works. If yes, try to enable your addons step-by-step and tell us which addon broke PreMiD.

### 컴퓨터 재시작
I hope you know how to restart a computer.

### PreMiD 재설치
Sometimes there is something wrong with the files... Tutorials for the installation can be found [here](/install).

### 수동 제거
Windows: Write `%appdata%` on the file explorer and delete the `PreMiD` folder. MacOS: `~/users/USER/~Library/Application Support/` and delete the `PreMiD` folder.

### McAfee 백신이 PreMiD를 바이러스로 오탐하는 경우 (윈도우)
This is a false positive from McAfee and we have reported the issue to them, for now you can exclude PreMiD from the scan by doing the following steps:

> If you do not feel confident taking these steps, feel free to make a ticket in [#support](https://discord.premid.app/) and one of our Support Agents will be able to help you out! 
> 
> {.is-warning}

1. McAfee 를 실행하고, 우측 상단에 있는 설정 아이콘을 클릭해주세요. <img src="https://i.imgur.com/rPLZn6c.png" width="500px" style="max-width:100%;" />
2. " 격리된 목록 " 을 클릭해주세요 ( 우측 상단에서 두번째)
3. 해당 파일을 확장하고, " settings.dat " 전에 있는 `>` 아이콘을 클릭해주세요.
4. Restore을 누르기 전, 경로에 "AppData\Local\Temp\PreMiD" 가 있는지 확인해주세요. 만약 있다면, settings.dat 을 선택하고 Restore 버튼을 누릅니다. <img src="https://i.imgur.com/9nvHmiI.png" width="500px" style="max-width:100%;" />
5. 복원후에 여러분은 " 격리된 목록 " 팝업을 종료하실수 있답니다, 그런 다음 우측 상단에 있는 설정 아이콘을 눌러주세요.
6. 위에서 세번째에 있는 " 실시간 스캔 " 을 클릭해주세요.
7. 확장하고 " 파일 추가 " 버튼을 눌러주세요.
8. Type "%appdata%" in the address bar of the File Explorer and press Enter. <img src="https://i.imgur.com/2bchwLe.png" width="500px" style="max-width:100%;" />
9. "PreMiD" 폴더를 열고, "PreMiD.exe" 파일을 더블클릭해서 열어주세요. <img src="https://i.imgur.com/aHOyv3V.png" width="500px" style="max-width:100%;" />
10. McAfee가 이제 저희 파일을 무시하게 될거에요. 저희의 앱을 다시 실행하면, 정상적으로 작동할거에요.

### PreMiD status bugged on Discord
Don't worry. Press the <kbd>CTRL+R</kbd> (Windows) or <kbd>CMD+R</kbd> (MacOS) keybind while focused on your Discord window to reload it.

<a name="linux"></a>

# Linux 문제 해결
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

# MacOS 문제 해결
### Error creating directory
<img src="https://i.imgur.com/td92lf6.png" width="300px" style="max-width:100%;" />

If you get this error, it means that your account doesn't have Administrator permissions and you need to create folder manually by doing these steps:
1. Open finder and open **Applications** folder.
2. Right-click on blank space and click **Create folder**.
3. To this folder assign `PreMiD` name (remember about upper-cased letters).
4. Open installer again.

# 이것들로는 제 문제가 해결되지 않았습니다
Please create a new post in \[#support\](https://discord.premid.app/](https://discord.com/channels/493130730549805057/1019726199494279248).
