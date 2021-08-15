---
title: Probleemoplossing
description: Alles om je probleem op te lossen
published: true
date: 2021-02-08T21:30:58.603Z
tags:
editor: markdown
dateCreated: 2020-06-11T18:03:54.865Z
---

> Zorg ervoor dat de extensie **en** de applicatie geïnstalleerd zijn! 
> 
> {.is-warning}

Deze pagina bevat:
1. [Algemene probleemoplossing](https://docs.premid.app/troubleshooting#general)
2. [Linux-probleemoplossing](https://docs.premid.app/troubleshooting#linux)
3. [MacOS-probleemoplossing](https://docs.premid.app/troubleshooting#macos)

<a name="general"></a>

# Algemene probleemoplossing
> Je kunt [dit](https://qkeleq10.github.io/PreMiD-Troubleshooting/) hulpmiddel gebruiken om je probleem gemakkelijker te identificeren. 
> 
> {.is-info}
### Pagina herladen
Je kunt ook op <kbd>CTRL+R</kbd>/<kbd>F5</kbd> (Windows) of <kbd>CMD+R</kbd> (MacOS) op het toetsenbord drukken in plaats van te zoeken naar de refresh knop.

### Gebruik je de Discord-app?
PreMiD werkt **niet** met de browserversie van Discord, je moet de app [hier](https://discord.com/download) downloaden.

### Zorg ervoor dat Activiteit Status is ingeschakeld in de Discord app instellingen
**Gebruikersinstellingen** > **Activiteit Status**
<img src="https://i.imgur.com/9SfrrWm.png" width="500px" style="max-width:100%;" />

### Zorg ervoor dat Discord NIET als administrator wordt uitgevoerd
Really important. Discord RPC will not work if you run Discord as an administrator.

### Gebruikt u een presence met instellingen?
Many presences (including `Twitch` and `SoundCloud`) are affected by an extension issue. This issue causes the extension to not grab the default values of settings properly.

To solve this, all you have to do is toggle the topmost setting:
<img src="https://i.imgur.com/JtXxTzg.gif" width="500px" style="max-width:100%;" />

### Herstart je browser
<kbd>Alt</kbd>+<kbd>F4</kbd> (Windows) or <kbd>CMD</kbd>+<kbd>Q</kbd> (MacOS) does a good job too. (You have to start your browser again obviously.)

### PreMiD herstarten (Applicatie)
<img src="https://i.imgur.com/wQA15xu.png" width="500px" style="max-width:100%;" />
You have to restart PreMiD afterwards.

### Discord herladen/herstarten
Press <kbd>CTRL+R</kbd> (Windows) or <kbd>CMD+R</kbd> (MacOS) on your keyboard or restart Discord manually.

### Controleer of u antivirus of firewall draait op je computer
Sometimes antivirus programs and firewalls are blocking applications which are creating/hosting servers or just connecting to the internet. We are using a local server to receive and pass data between our app and extension, so if you will block app's ability to pass data you probably will not be able to use PreMiD.

### Uw addons uitschakelen
Disable all your addons and see if it works. If yes, try to enable your addons step-by-step and tell us which addon broke PreMiD.

### Uw computer wordt opnieuw opstarten
I hope you know how to restart a computer.

### PreMiD opnieuw installeren
Sometimes there is something wrong with the files... Tutorials for the installation can be found [here](/install).

### Handmatige verwijdering
Windows: Write `%appdata%` on the file explorer and delete the `PreMiD` folder. MacOS: `~/users/USER/~Library/Application Support/` and delete the `PreMiD` folder.

### McAfee heeft PreMiD gedetecteerd als virus (Windows)
This is a false positive from McAfee and we have reported the issue to them, for now you can exclude PreMiD from the scan by doing the following steps:

> Als je niet het vertrouwen hebt om deze stappen uit te voeren, voel je dan vrij om een ticket te maken in [#support](https://discord.premid.app/) en een van onze ondersteuningsmedewerkers zal er zijn om je te helpen! 
> 
> {.is-warning}

1. Open de McAfee-applicatie en klik op het instellingen-icoon in de rechterbovenhoek. <img src="https://i.imgur.com/rPLZn6c.png" width="500px" style="max-width:100%;" />
2. Klik op "Quarantined Items" (Tweede van boven).
3. Breid het uit en klik op het `>` pictogram voor een item met de naam "settings.dat".
4. Zorg ervoor dat het pad "AppData\Local\Temp\PreMiD" bevat. Als dit zo is, selecteer deze dan en druk op Herstellen. <img src="https://i.imgur.com/9nvHmiI.png" width="500px" style="max-width:100%;" />
5. Nadat het is hersteld, kunt u de "Quarantined Items" pop-up sluiten, en vervolgens opnieuw op het instellingen icoon in de rechterbovenhoek drukken.
6. Klik op "Real-Time scanning" (Derde van bovenaan).
7. Breid het uit en klik op "Bestand toevoegen".
8. Typ "%appdata%" in de adresbalk van Verkenner en druk op Enter. <img src="https://i.imgur.com/2bchwLe.png" width="500px" style="max-width:100%;" />
9. Open de "PreMiD" map en selecteer het "PreMiD.exe" bestand en klik op openen. <img src="https://i.imgur.com/aHOyv3V.png" width="500px" style="max-width:100%;" />
10. McAfee zou nu ons bestand moeten negeren, lanceer gewoon onze applicatie en het zou nu gewoon moeten werken.

### PreMiD-status gebugd op discord!
Don't worry. Press the <kbd>CTRL+R</kbd> (Windows) or <kbd>CMD+R</kbd> (MacOS) keybind while focused on your discord window to reload it.

<a name="linux"></a>

# Linux-probleemoplossing
### Op Ubuntu/Debian gebaseerde distro's
If you have downloaded Discord through Snapcraft, RPC will not work. You have to uninstall the Snapcraft version by executing `sudo snap remove discord` on a terminal, download **[Discord's Linux build](https://discordapp.com/api/download?platform=linux)** (**[or Discord Canary](https://discordapp.com/api/canary/download?platform=linux)**), then navigating to the directory you downloaded Discord to (usually `$HOME/Downloads`), then installing the package using `sudo dpkg -i discord-*.deb`. If AppImage doesn't work, you should consider checking our other packages by **[this link](https://packagecloud.io/premid/linux)**.

### Op Arch Linux gebaseerde distro's
Arch Linux based distros should use AUR (Arch User Repository) package that is named <code>premid</code> or <code>premid-git</code> (<em x-id="3">WARNING: This repository builds premid from our source code.</em>). If you don't want to install an AUR manager (yay etc.), you can check out our AppImage that is downloadable from our <strong x-id="1"><a href="https://github.com/premid/linux/releases">Linux repository</a></strong>.
<em x-id="3">Warning: the package in the <strong x-id="1">AUR</strong> repository is not maintained by us (as PreMiD organization), but by other people.</em>

### Poort-binding
You should know that <strong x-id="1">PreMiD</strong> binds itself to the port <strong x-id="1">3020</strong>. This is necessary for the Extension and the Application communicate. If <strong x-id="1">PreMiD</strong> shows you an error about this port, you should check if something is binded to the 3020 port by running <code>sudo lsof -i:3020</code> or <code>sudo netstat -tnlp | grep :3020</code> in your terminal. If some process is binded to it you should make sure to free the port and try running <code>PreMiD</code> again.

### PreMiDs AppImage start niet bij het inloggen
As we stated in our **Linux repository**, AppImage can't be launched at login. You can add it to autostart manually by doing these steps:
1. Maak een bestand genaamd <strong x-id="1">rc.local</strong> in de <code>/etc</code> map.
2. Open dit bestand in je favoriete editor en plak de gegeven code en verander enkele dingen:
```bash
#!/bin/bash
# Vereist om uit te voeren als /bin/bash (als je zsh o.i.d. gebruikt kun je dit wijzigen.)

# Voorbeeld: /home/PreMiD/PreMiD*.AppImage
<directory to appimage>/PreMiD*.AppImage

exit 0
```
3. Sla bestand op en chmod het als executable `sudo chmod a+x /etc/rc.local`.
4. Herstart je PC en PreMiDs AppImage start bij het inloggen.

<a name="macos"></a>

# MacOS-probleemoplossing
### Fout bij aanmaken van map
<img src="https://i.imgur.com/td92lf6.png" width="300px" style="max-width:100%;" />

If you get this error, it means that your account doesn't have Administrator permissions and you need to create folder manually by doing these steps:
1. Open de finder en open de map **Applicaties**.
2. Rechtsklik op lege ruimte en klik op **Maak map**.
3. Geef de map de naam `PreMiD` (let op de hoofdletters).
4. Open het installatieprogramma opnieuw.

# Dat heeft mijn probleem niet opgelost
Please open a ticket in [#support](https://discord.premid.app/).
