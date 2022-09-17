---
title: Řešení Problémů
description: Vše k vyřešení Tvého problému
published: true
date: 2021-12-20T14:27:18.034Z
tags:
editor: markdown
dateCreated: 2021-09-07T01:17:32.312Z
---

> Ujisti se, že máš nainstalováno rozšíření **a** aplikaci! 
> 
> {.is-warning}

Na této stránce nalezneš:
1. [Obecné Řešení Problémů](https://docs.premid.app/troubleshooting#general)
2. [Řešení Problémů na Linuxu](https://docs.premid.app/troubleshooting#linux)
3. [Řešení problémů na macOSP](https://docs.premid.app/troubleshooting#macos)

<a name="general"></a>

# Obecné Řešení Problémů
> You can use [this](https://qkeleq10.github.io/PreMiD-Troubleshooting/) tool to more easily identify your issue. 
> 
> {.is-info}
### Znovu načíst stránku
Namísto hledání tlačítka obnovení můžeš stisknout <kbd>CTRL+R</kbd>/<kbd>F5</kbd> (Windows) nebo <kbd>CMD+R</kbd> (MacOS) na Tvé klávesnici.

### Používáš desktopovou verzi aplikace Discord?
PreMiD **nefunguje** při používání prohlížečové verze Discordu, musíš si stáhnout desktopovou aplikaci [zde](https://discord.com/download).

### Ujistěte se, že jste povolili Discord herní aktivitu v nastavení
**Uživatelské Nastavení** > **Herní Aktivita**
<img src="https://i.imgur.com/9SfrrWm.png" width="500px" style="max-width:100%;" />

### Ujisti se, že Discord není spuštěn jako správce
Really important. Discord RPC will not work if you run Discord as an administrator.

### Používáš presenci s nastavením?
Many presences (including `Twitch` and `SoundCloud`) are affected by an extension issue. This issue causes the extension to not grab the default values of settings properly.

To solve this, all you have to do is toggle the topmost setting:
<img src="https://i.imgur.com/JtXxTzg.gif" width="500px" style="max-width:100%;" />

### Restartuj prohlížeč
<kbd>Alt</kbd>+<kbd>F4</kbd> (Windows) or <kbd>CMD</kbd>+<kbd>Q</kbd> (MacOS) does a good job too. (You have to start your browser again obviously.)

### Restartuj PreMiD (Aplikaci)
<img src="https://i.imgur.com/g3ShdnU.png" width="500px" style="max-width:100%;" />
You have to restart PreMiD afterwards.

### Znovu načti/restartuj Discord
Press <kbd>CTRL+R</kbd> (Windows) or <kbd>CMD+R</kbd> (MacOS) on your keyboard or restart Discord manually.

### Zkontrolujte, zda máš na svém počítači spuštěný antivirus nebo firewall
Sometimes antivirus programs and firewalls are blocking applications which are creating/hosting servers or just connecting to the internet. We are using a local server to receive and pass data between our app and extension, so if you block app's ability to pass data, you probably will not be able to use PreMiD.

### Zakázat doplňky
Disable all your addons and see if it works. If yes, try to enable your addons step-by-step and tell us which addon broke PreMiD.

### Restartování počítače
I hope you know how to restart a computer.

### Přeinstalování PreMiD
Sometimes there is something wrong with the files... Tutorials for the installation can be found [here](/install).

### Ruční odstranění
Windows: Write `%appdata%` on the file explorer and delete the `PreMiD` folder. MacOS: `~/users/USER/~Library/Application Support/` and delete the `PreMiD` folder.

### McAfee detekoval PreMiD jako virus (na Windows)
This is a false positive from McAfee and we have reported the issue to them, for now you can exclude PreMiD from the scan by doing the following steps:

> If you do not feel confident taking these steps, feel free to make a ticket in [#support](https://discord.premid.app/) and one of our Support Agents will be able to help you out! 
> 
> {.is-warning}

1. Otevřete aplikaci McAfee a klikněte na ikonu nastavení vpravo nahoře. <img src="https://i.imgur.com/rPLZn6c.png" width="500px" style="max-width:100%;" />
2. Klikněte na "Karantované položky" (druhé od shora).
3. Rozbalte a klikněte na `>` před položkou s názvem "settings.dat".
4. Ujistěte se, že cesta obsahuje "AppData\Local\Temp\PreMiD". Pokud je to tak, vyberete ji a stiskněte tlačítko Obnovit. <img src="https://i.imgur.com/9nvHmiI.png" width="500px" style="max-width:100%;" />
5. Po obnovení můžete zavřít vyskakovací okno "Karantované položky" a poté znovu stisknout ikonu nastavení v pravém horním rohu.
6. Klikněte na "Skenování v reálném čase" (třetí od shora).
7. Rozbalte a klepněte na tlačítko "Přidat soubor".
8. Type "%appdata%" in the address bar of the File Explorer and press Enter. <img src="https://i.imgur.com/2bchwLe.png" width="500px" style="max-width:100%;" />
9. Otevřete složku "PreMiD", vyberte soubor "PreMiD.exe" a klikněte na tlačítko Otevřít. <img src="https://i.imgur.com/aHOyv3V.png" width="500px" style="max-width:100%;" />
10. McAfee by nyní měl ignorovat náš soubor, stačí spustit naši aplikaci a měli byste být v pořádku.

### PreMiD status bugged on Discord
Don't worry. Press the <kbd>CTRL+R</kbd> (Windows) or <kbd>CMD+R</kbd> (MacOS) keybind while focused on your Discord window to reload it.

<a name="linux"></a>

# Řešení Problémů na Linuxu
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

# Řešení problémů na macOSP
### Error creating directory
<img src="https://i.imgur.com/td92lf6.png" width="300px" style="max-width:100%;" />

If you get this error, it means that your account doesn't have Administrator permissions and you need to create folder manually by doing these steps:
1. Open finder and open **Applications** folder.
2. Right-click on blank space and click **Create folder**.
3. To this folder assign `PreMiD` name (remember about upper-cased letters).
4. Open installer again.

# To můj problém nevyřešilo
Please create a new post in [#support](https://discord.com/channels/493130730549805057/1019726199494279248).
