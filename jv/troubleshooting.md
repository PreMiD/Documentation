---
title: Ngatasi masalah
description: Kabeh kanggo ngatasi masalah sampeyan
published: true
date: 2021-02-08T21:30:58.603Z
tags:
editor: markdown
dateCreated: 2020-06-11T18:03:54.865Z
---

> Priksa manawa sampeyan wis duwe ekstensi ** lan ** sing wis diinstal! 
> 
> {.is-warning}

Halaman iki memuat:
1. [Troubleshooting Umum](https://docs.premid.app/troubleshooting#general)
2. [Troubleshooting Linux](https://docs.premid.app/troubleshooting#linux)
3. [Troubleshooting MacOS](https://docs.premid.app/troubleshooting#macos)

<a name="general"></a>

# Troubleshooting Umum
> Sampeyan isa gunake alat [iki](https://qkeleq10.github.io/PreMiD-Troubleshooting/) supaya luwih penak ngidentifikasi masalahmu. 
> 
> {.is-info}
### Muat maneh halaman
Sampeyan ugo bisa mijet <kbd>CTRL+R</kbd>/<kbd>F5</kbd> (Windows) utawa <kbd>CMD+R</kbd> (MacOS) ing keyboard sak liyane tombol refresh.

### Apa sampeyan nggunakake aplikasi Discord?
PreMiD **ora** mlaku ing discord versi browser, sampeyan kudu download aplikasine [ing kene](https://discord.com/download).

### Priksa manawa sampeyan wis ngaktifake Activity Status ing setelan Discord
**User Settings** > **Activity Status**
<img src="https://i.imgur.com/9SfrrWm.png" width="500px" style="max-width:100%;" />

### Priksa menawa Discord ORA mlaku sebagai administrator
Really important. Discord RPC will not work if you run Discord as an administrator.

### Apa sampeyan nggunakake presence karo setelan?
Many presences (including `Twitch` and `SoundCloud`) are affected by an extension issue. This issue causes the extension to not grab the default values of settings properly.

To solve this, all you have to do is toggle the topmost setting:
<img src="https://i.imgur.com/JtXxTzg.gif" width="500px" style="max-width:100%;" />

### Restart browsermu
<kbd>Alt</kbd>+<kbd>F4</kbd> (Windows) or <kbd>CMD</kbd>+<kbd>Q</kbd> (MacOS) does a good job too. (You have to start your browser again obviously.)

### Restart PreMiD (Aplikasi)
<img src="https://i.imgur.com/wQA15xu.png" width="500px" style="max-width:100%;" />
You have to restart PreMiD afterwards.

### Reload/restart Discord
Press <kbd>CTRL+R</kbd> (Windows) or <kbd>CMD+R</kbd> (MacOS) on your keyboard or restart Discord manually.

### Priksa manawa antivirus utawa firewall aktif ing komputermu
Sometimes antivirus programs and firewalls are blocking applications which are creating/hosting servers or just connecting to the internet. We are using a local server to receive and pass data between our app and extension, so if you will block app's ability to pass data you probably will not be able to use PreMiD.

### Pateni addon
Disable all your addons and see if it works. If yes, try to enable your addons step-by-step and tell us which addon broke PreMiD.

### Restart komputermu
I hope you know how to restart a computer.

### Instal ulang PreMiD
Sometimes there is something wrong with the files... Tutorials for the installation can be found [here](/install).

### Penghapusan manual
Windows: Write `%appdata%` on the file explorer and delete the `PreMiD` folder. MacOS: `~/users/USER/~Library/Application Support/` and delete the `PreMiD` folder.

### McAfee ndeteksi PreMiD sebagai virus (Windows)
This is a false positive from McAfee and we have reported the issue to them, for now you can exclude PreMiD from the scan by doing the following steps:

> Yen sampeyan ora yakin ngetutake langkah-langkah kasebut, coba gawe tiket ing [ #support ](https://discord.premid.app/) lan salah sawijining Ejen Dhukungan bakal mbantu sampeyan! 
> 
> {.is-warning}

1. Bukak aplikasi McAfee lan klik lambang setelan ing sisih tengen ndhuwur. <img src="https://i.imgur.com/rPLZn6c.png" width="500px" style="max-width:100%;" />
2. Klik "Item Karantina" (Kapindho saka ndhuwur).
3. Ambakno, lan klik ikon `>` sadurunge item sing dijenengi "settings.dat".
4. Priksa manawa direktori "AppData\Local\Temp\PreMiD", yen bener pilih banjur pencet mulihake. <img src="https://i.imgur.com/9nvHmiI.png" width="500px" style="max-width:100%;" />
5. Sawise mari pemulihan, sampeyan bisa nutup "Quarantined Items", banjur pencet lambang setelan maneh ing sisih tengen ndhuwur.
6. Pijet "Real-Time Scanning" (Katelu saka ndhuwur).
7. Ngembangake lan klik "Tambah file".
8. Ketik "%appdata%" ing bilah alamat File Explorer lan Enter. <img src="https://i.imgur.com/2bchwLe.png" width="500px" style="max-width:100%;" />
9. Bukak folder "PreMiD" lan pilih file "PreMiD.exe" sakwise iku klik buka. <img src="https://i.imgur.com/aHOyv3V.png" width="500px" style="max-width:100%;" />
10. McAfee saiki wis ora nggatekake file kita, start aplikasi lan kudune wis kerja.

### Status PreMiD bermasalah ing Discord!
Don't worry. Press the <kbd>CTRL+R</kbd> (Windows) or <kbd>CMD+R</kbd> (MacOS) keybind while focused on your discord window to reload it.

<a name="linux"></a>

# Troubleshooting Linux
### Distro berbasis Ubuntu/Debian
If you have downloaded Discord through Snapcraft, RPC will not work. You have to uninstall the Snapcraft version by executing `sudo snap remove discord` on a terminal, download **[Discord's Linux build](https://discordapp.com/api/download?platform=linux)** (**[or Discord Canary](https://discordapp.com/api/canary/download?platform=linux)**), then navigating to the directory you downloaded Discord to (usually `$HOME/Downloads`), then installing the package using `sudo dpkg -i discord-*.deb`. If AppImage doesn't work, you should consider checking our other packages by **[this link](https://packagecloud.io/premid/linux)**.

### Distro berbasis Arch Linux
Arch Linux based distros should use AUR (Arch User Repository) package that is named <code>premid</code> or <code>premid-git</code> (<em x-id="3">WARNING: This repository builds premid from our source code.</em>). If you don't want to install an AUR manager (yay etc.), you can check out our AppImage that is downloadable from our <strong x-id="1"><a href="https://github.com/premid/linux/releases">Linux repository</a></strong>.
<em x-id="3">Warning: the package in the <strong x-id="1">AUR</strong> repository is not maintained by us (as PreMiD organization), but by other people.</em>

### Port binding
You should know that <strong x-id="1">PreMiD</strong> binds itself to the port <strong x-id="1">3020</strong>. This is necessary for the Extension and the Application communicate. If <strong x-id="1">PreMiD</strong> shows you an error about this port, you should check if something is binded to the 3020 port by running <code>sudo lsof -i:3020</code> or <code>sudo netstat -tnlp | grep :3020</code> in your terminal. If some process is binded to it you should make sure to free the port and try running <code>PreMiD</code> again.

### AppImage PreMiD ora mlaku nalika login
As we stated in our **Linux repository**, AppImage can't be launched at login. You can add it to autostart manually by doing these steps:
1. Gawe file sing jenenge <strong x-id="1">rc.local</strong> ing direktori <code>/etc</code>.
2. Bukak file nggunakake editor lan tempel kode sing diwenehi ganti sawetara perkara:
```bash
#!/bin/bash
# Dibutuhake kanggo ngelakokne /bin/bash (yen sampeyan nggunakake zsh etc. sampeyan bisa ngganti.)

# Conto: /home/PreMiD/PreMiD*.AppImage
<directory to appimage>/PreMiD*.AppImage

exit 0
```
3. Simpen file lan chmod minangka executable `sudo chmod a+x /etc/rc.local`.
4. Restart PCmu lan AppImage PreMiD bakal mbukak pas login.

<a name="macos"></a>

# Troubleshooting MacOS
### Error nggawe direktori
<img src="https://i.imgur.com/td92lf6.png" width="300px" style="max-width:100%;" />

If you get this error, it means that your account doesn't have Administrator permissions and you need to create folder manually by doing these steps:
1. Bukak finder lan bukak folder **Applications**.
2. Klik-tengen ing bagian kosong lan klik **Create folder**.
3. Ing folder kasebut ketik jeneng `PreMiD` (perhatekno huruf kapital).
4. Bukak installer maneh.

# Masalahku durung mantun
Please open a ticket in [#support](https://discord.premid.app/).
