---
title: Tõrkeparandus
description: Kõik teie probleemi lahendamiseks
published: true
date: 2021-02-08T21:30:58.603Z
tags:
editor: markdown
dateCreated: 2020-06-11T18:03:54.865Z
---

> Veenduge, et teil oleks installitud laiendus **ja** rakendus! 
> 
> {.is-warning}

Sellel leheküljel kaasatud:
1. [Üldine tõrkeotsing](https://docs.premid.app/troubleshooting#general)
2. [Linuxi tõrkeotsing](https://docs.premid.app/troubleshooting#linux)
3. [MacOS-i tõrkeotsing](https://docs.premid.app/troubleshooting#macos)

<a name="general"></a>

# Üldine tõrkeotsing
> Probleemi hõlpsamaks tuvastamiseks võite kasutada [seda](https://qkeleq10.github.io/PreMiD-Troubleshooting/) tööriista. 
> 
> {.is-info}
### Värskenda lehekülge
Värskendusnupu otsimise asemel võite klaviatuuril vajutada ka <kbd>CTRL + R</kbd>/<kbd>F5</kbd> (Windows) või <kbd>CMD + R</kbd> (MacOS).

### Kas kasutate Discordi rakendust?
PreMiD **ei** tööta Discordi brauseriversioonis, peate rakenduse alla laadima [siit](https://discord.com/download).

### Veenduge, et olete Discordi rakenduse seadetes lubanud Tegevuse Oleku
**Kasutaja seaded** > **Tegevuse Olek**
<img src="https://i.imgur.com/9SfrrWm.png" width="500px" style="max-width:100%;" />

### Veenduge, et Discord EI tööta administraatorina
Really important. Discord RPC will not work if you run Discord as an administrator.

### Kas kasutate presence-i, millel on seadmed?
Many presences (including `Twitch` and `SoundCloud`) are affected by an extension issue. This issue causes the extension to not grab the default values of settings properly.

To solve this, all you have to do is toggle the topmost setting:
<img src="https://i.imgur.com/JtXxTzg.gif" width="500px" style="max-width:100%;" />

### Taaskäivitage oma brauser
<kbd>Alt</kbd>+<kbd>F4</kbd> (Windows) or <kbd>CMD</kbd>+<kbd>Q</kbd> (MacOS) does a good job too. (You have to start your browser again obviously.)

### Taaskäivitage PreMiD (rakendus)
<img src="https://i.imgur.com/wQA15xu.png" width="500px" style="max-width:100%;" />
You have to restart PreMiD afterwards.

### Laadige/taaskäivitage Discord
Press <kbd>CTRL+R</kbd> (Windows) or <kbd>CMD+R</kbd> (MacOS) on your keyboard or restart Discord manually.

### Kontrollige, kas teie arvutis töötab viirusetõrje või tulemüür
Sometimes antivirus programs and firewalls are blocking applications which are creating/hosting servers or just connecting to the internet. We are using a local server to receive and pass data between our app and extension, so if you will block app's ability to pass data you probably will not be able to use PreMiD.

### Keelake oma lisad
Disable all your addons and see if it works. If yes, try to enable your addons step-by-step and tell us which addon broke PreMiD.

### Taaskäivitage arvuti
I hope you know how to restart a computer.

### PreMiD-i uuesti installimine
Sometimes there is something wrong with the files... Tutorials for the installation can be found [here](/install).

### Käsitsi eemaldamine
Windows: Write `%appdata%` on the file explorer and delete the `PreMiD` folder. MacOS: `~/users/USER/~Library/Application Support/` and delete the `PreMiD` folder.

### McAfee tuvastas PreMiD-i viirusena (Windows)
This is a false positive from McAfee and we have reported the issue to them, for now you can exclude PreMiD from the scan by doing the following steps:

> Kui te pole nende sammude tegemisel kindel, tehke pilet lehel [#support](https://discord.premid.app/) ja üks meie tugiagentidest saab teid aidata! 
> 
> {.is-warning}

1. Avage rakendus McAfee ja klõpsake paremas ülaosas seadete ikooni. <img src="https://i.imgur.com/rPLZn6c.png" width="500px" style="max-width:100%;" />
2. Klõpsake nuppu "Quarantined Items" (ülevalt teine).
3. Laiendage seda ja klõpsake ikooni nimega `>` üksuse "settings.dat" ees.
4. Veenduge, et tee sisaldab "AppData\Local\Temp\PreMiD", kui see on nii valitud vajutage taastada. <img src="https://i.imgur.com/9nvHmiI.png" width="500px" style="max-width:100%;" />
5. Pärast selle taastamist võite hüpikakna "Quarantined Items" sulgeda ja seejärel paremas ülanurgas uuesti seadete ikooni vajutada.
6. Klõpsake nuppu "Real-Time Scanning" (ülalt kolmas).
7. Laiendage seda ja klõpsake nuppu "Add file".
8. Sisestage File Exploreri aadressiribale "%appdata%" ja vajutage sisestusklahvi. <img src="https://i.imgur.com/2bchwLe.png" width="500px" style="max-width:100%;" />
9. Avage kaust "PreMiD", valige fail "PreMiD.exe" ja klõpsake nuppu Ava. <img src="https://i.imgur.com/aHOyv3V.png" width="500px" style="max-width:100%;" />
10. McAfee peaks nüüd meie faili ignoreerima, lihtsalt käivitage meie rakendus ja teil peaks olema korras.

### PreMiD-i olek on katki Discordis!
Don't worry. Press the <kbd>CTRL+R</kbd> (Windows) or <kbd>CMD+R</kbd> (MacOS) keybind while focused on your discord window to reload it.

<a name="linux"></a>

# Linuxi tõrkeotsing
### Ubuntu/Debiani põhised distrod
If you have downloaded Discord through Snapcraft, RPC will not work. You have to uninstall the Snapcraft version by executing `sudo snap remove discord` on a terminal, download **[Discord's Linux build](https://discordapp.com/api/download?platform=linux)** (**[or Discord Canary](https://discordapp.com/api/canary/download?platform=linux)**), then navigating to the directory you downloaded Discord to (usually `$HOME/Downloads`), then installing the package using `sudo dpkg -i discord-*.deb`. If AppImage doesn't work, you should consider checking our other packages by **[this link](https://packagecloud.io/premid/linux)**.

### Arch Linuxi põhised distrod
Arch Linux based distros should use AUR (Arch User Repository) package that is named <code>premid</code> or <code>premid-git</code> (<em x-id="3">WARNING: This repository builds premid from our source code.</em>). If you don't want to install an AUR manager (yay etc.), you can check out our AppImage that is downloadable from our <strong x-id="1"><a href="https://github.com/premid/linux/releases">Linux repository</a></strong>.
<em x-id="3">Warning: the package in the <strong x-id="1">AUR</strong> repository is not maintained by us (as PreMiD organization), but by other people.</em>

### Portide sidumine
You should know that <strong x-id="1">PreMiD</strong> binds itself to the port <strong x-id="1">3020</strong>. This is necessary for the Extension and the Application communicate. If <strong x-id="1">PreMiD</strong> shows you an error about this port, you should check if something is binded to the 3020 port by running <code>sudo lsof -i:3020</code> or <code>sudo netstat -tnlp | grep :3020</code> in your terminal. If some process is binded to it you should make sure to free the port and try running <code>PreMiD</code> again.

### PreMiD AppImage ei käivitu sisselogimisel
As we stated in our **Linux repository**, AppImage can't be launched at login. You can add it to autostart manually by doing these steps:
1. Tehke kataloogis <code>/etc</code> fail nimega <strong x-id="1">rc.local</strong>.
2. Avage see fail oma lemmikredaktoris ja kleepige antud kood, muutes mõningaid asju:
```bash
#! / bin / bash
# Nõutav käitamiseks failina /bin/bash (kui kasutate zsh jne. saate seda muuta.)

# Näide: /home/PreMiD/PreMiD*.AppImage
<directory to appimage>/PreMiD*.AppImage

exit 0
```
3. Salvestage fail ja chmod see käivitatava failina `sudo chmod a+x /etc/rc.local`.
4. Taaskäivitage arvuti ja PreMiD AppImage peaks käivituma sisselogimisel.

<a name="macos"></a>

# MacOS-i tõrkeotsing
### Viga kataloogi loomisel
<img src="https://i.imgur.com/td92lf6.png" width="300px" style="max-width:100%;" />

If you get this error, it means that your account doesn't have Administrator permissions and you need to create folder manually by doing these steps:
1. Avage leidja ja avage kaust **Rakendused**.
2. Paremklõpsake tühjal kohal ja klõpsake valikut **Loo kaust**.
3. Sellesse kausta määrake nimi `PreMiD` (pidage meeles suurtähti).
4. Avage installer uuesti.

# See pole minu probleemi lahendanud
Please open a ticket in [#support](https://discord.premid.app/).
