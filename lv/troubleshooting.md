---
title: Problēmu novēršana
description: Viss, lai atrisinātu jūsu problēmu
published: true
date: 2021-12-20T14:27:18.034Z
tags:
editor: markdown
dateCreated: 2021-09-07T01:17:32.312Z
---

> Pārliecinieties, vai esat uzstādījis paplašinājumu **un** aplikāciju!
>
> {.is-warning}

Iekļauts šajā lapā:
1. [Vispārīgu problēmu novēršana](https://docs.premid.app/troubleshooting#general)
2. [Linux problēmu novēršana](https://docs.premid.app/troubleshooting#linux)
3. [MacOS problēmu novēršana](https://docs.premid.app/troubleshooting#macos)

<a name="general"></a>

# Vispārīgu problēmu novēršana
> Jūs varat izmantot [šo](https://qkeleq10.github.io/PreMiD-Troubleshooting/) rīku, lai vieglāk identificētu jūsu problēmu.
>
> {.is-info}
### Pārlādējiet lapu
Jūs varat nospiest <kbd>CTRL+R</kbd>/<kbd>F5</kbd> (Windows) vai <kbd>CMD+R</kbd> (MacOS) uz tastatūras, nevis meklēt atsvaidzināšanas pogu.

### Vai jūs izmantojat lietotni Discord?
PreMiD **nedarbojas** uz Discord pārlūkprogrammas versijas, jums ir jāuzstāda lietotne [šeit](https://discord.com/download).

### Pārliecinieties, ka Aktivitātes Statuss ir iespējots Discord iestatījumos
**Lietotāja Iestatījumi** > **Aktivitātes Statuss**
<img src="https://i.imgur.com/9SfrrWm.png" width="500px" style="max-width:100%;" />

### Pārliecinieties, ka Discord NEIET, kā administrators
Really important. Discord RPC will not work if you run Discord as an administrator.

### Vai izmantojat presence ar iestatījumiem?
Many presences (including `Twitch` and `SoundCloud`) are affected by an extension issue. This issue causes the extension to not grab the default values of settings properly.

To solve this, all you have to do is toggle the topmost setting:
<img src="https://i.imgur.com/JtXxTzg.gif" width="500px" style="max-width:100%;" />

### Restartējiet savu pārlūkprogrammu
<kbd>Alt</kbd>+<kbd>F4</kbd> (Windows) vai <kbd>CMD</kbd>+<kbd>Q</kbd> (MacOS) strādā arī labi. (Jums, protams, arī jāpalaiž pārlūkprogrammu pa jaunu.)

### Restartējiet PreMiD (Lietotni)
<img src="https://i.imgur.com/wQA15xu.png" width="500px" style="max-width:100%;" />
You have to restart PreMiD afterwards.

### Pārlādējiet/restartējiet Discord
Press <kbd>CTRL+R</kbd> (Windows) or <kbd>CMD+R</kbd> (MacOS) on your keyboard or restart Discord manually.

### Pārbaudiet, vai datorā darbojas antivīruss vai ugunsmūris
Sometimes antivirus programs and firewalls are blocking applications which are creating/hosting servers or just connecting to the internet. We are using a local server to receive and pass data between our app and extension, so if you block app's ability to pass data, you probably will not be able to use PreMiD.

### Atspējojiet savus paplašinājumus
Disable all your addons and see if it works. If yes, try to enable your addons step-by-step and tell us which addon broke PreMiD.

### Restartējiet datoru
I hope you know how to restart a computer.

### Pārinstalējat PreMiD
Sometimes there is something wrong with the files... Tutorials for the installation can be found [here](/install).

### Manuālā noņemšana
Windows: Write `%appdata%` on the file explorer and delete the `PreMiD` folder. MacOS: `~/users/USER/~Library/Application Support/` and delete the `PreMiD` folder.

### McAfee atklāja PreMiD kā vīrusu (Windows)
This is a false positive from McAfee and we have reported the issue to them, for now you can exclude PreMiD from the scan by doing the following steps:

> Ja nejūtaties pārliecināts veicot šīs darbības, droši izveidojiet biļeti [#support](https://discord.premid.app/) un viens no mūsu Atbalsta Aģentiem varēs tev palīdzēt!
>
> {.is-warning}

1. Atveriet lietotni McAfee un augšējā labajā stūrī noklikšķiniet uz iestatījumu ikonas. <img src="https://i.imgur.com/rPLZn6c.png" width="500px" style="max-width:100%;" />
2. Spied uz "Karantīnā ievietotie vienumi" (Otrais no augšas).
3. Izvērsiet to un uzspiediet uz `>` ikonas pirms vienuma ar nosaukumu "settings.dat".
4. Pārliecinieties, vai ceļā ir iekļauts "AppData\Local\Temp\PreMiD", ja tā, atlasiet to un nospiediet atjaunot. <img src="https://i.imgur.com/9nvHmiI.png" width="500px" style="max-width:100%;" />
5. Pēc tā atjaunošanas varat aizvērt uznirstošo logu "Quarantined Items", pēc tam augšējā labajā stūrī vēlreiz nospiediet iestatījumu ikonu.
6. Uzspiediet uz "Real-Time Scanning" (trešais no augšas).
7. Izvērsiet to un uzspiediet uz "Add file".
8. Failu Pārvaldnieka adreses joslā ierakstiet "%appdata%" un nospiediet Enter. <img src="https://i.imgur.com/2bchwLe.png" width="500px" style="max-width:100%;" />
9. Atveriet "PreMiD" mapi un atlasiet "PreMiD.exe" failu un uzspiediet uz atvērt. <img src="https://i.imgur.com/aHOyv3V.png" width="500px" style="max-width:100%;" />
10. McAfee tagad vajadzētu ignorēt mūsu failu, vienkārši palaidiet mūsu lietotni un jums visam vajadzētu iet labi.

### PreMiD status bugged on Discord
Don't worry. Press the <kbd>CTRL+R</kbd> (Windows) or <kbd>CMD+R</kbd> (MacOS) keybind while focused on your Discord window to reload it.

<a name="linux"></a>

# Linux problēmu novēršana
### Ubuntu/Debian balstītas distribūcijas
If you have downloaded Discord through Snapcraft, RPC will not work. You have to uninstall the Snapcraft version by executing `sudo snap remove discord` on a terminal, download **[Discord's Linux build](https://discordapp.com/api/download?platform=linux)** (**[or Discord Canary](https://discordapp.com/api/canary/download?platform=linux)**), then navigating to the directory you downloaded Discord to (usually `$HOME/Downloads`), then installing the package using `sudo dpkg -i discord-*.deb`. If AppImage doesn't work, you should consider checking our other packages by **[this link](https://packagecloud.io/premid/linux)**.

### Arch Linux balstītas distribūcijas
Arch Linux based distros should use AUR (Arch User Repository) package that is named <code>premid</code> or <code>premid-git</code> (<em x-id="3">WARNING: This repository builds premid from our source code.</em>). If you don't want to install an AUR manager (yay etc.), you can check out our AppImage that is downloadable from our <strong x-id="1"><a href="https://github.com/premid/linux/releases">Linux repository</a></strong>.
<em x-id="3">Warning: the package in the <strong x-id="1">AUR</strong> repository is not maintained by us (as PreMiD organization), but by other people.</em>

### Portu saistīšana
You should know that <strong x-id="1">PreMiD</strong> binds itself to the port <strong x-id="1">3020</strong>. This is necessary for the Extension and the Application communicate. If <strong x-id="1">PreMiD</strong> shows you an error about this port, you should check if something is binded to the 3020 port by running <code>sudo lsof -i:3020</code> or <code>sudo netstat -tnlp | grep :3020</code> in your terminal. If some process is binded to it you should make sure to free the port and try running <code>PreMiD</code> again.

### PreMiD AppImage netiek palaists, pieslēdzoties
As we stated in our **Linux repository**, AppImage can't be launched at login. You can add it to autostart manually by doing these steps:
1. Izveidojiet failu <strong x-id="1">rc.local</strong> <code>/etc</code> direktorijā.
2. Atveriet šo failu iecienītākajā redaktorā un ielīmējiet norādīto kodu, mainot dažas lietas:
```bash
#!/bin/bash
# Nepieciešams, lai palaistu kā /bin/bash (ja izmantojat zsh utt. jūs to varat mainīt.)

# Piemērs: /home/PreMiD/PreMiD*.AppImage
<directory to appimage>/PreMiD*.AppImage

exit 0
```
3. Saglabājiet failu un chmod to kā izpildāmo failu `sudo chmod a+x /etc/rc.local`.
4. Restartējiet datoru un PreMiD AppImagine vajadzētu palaisties, pieslēdzoties.

<a name="macos"></a>

# MacOS problēmu novēršana
### Veidojot direktoriju, radās kļūda
<img src="https://i.imgur.com/td92lf6.png" width="300px" style="max-width:100%;" />

If you get this error, it means that your account doesn't have Administrator permissions and you need to create folder manually by doing these steps:
1. Atveriet meklētāju un atveriet **Applications** mapi.
2. Ar peles labo pogu uzspiediet uz tukšas vietas un uzspiediet uz **Create folder**.
3. Šai mapei piešķiriet `PreMiD` nosaukumu (atceries par lielajiem burtiem).
4. Atver uzstādītāju atkal.

# Tas neatrisināja manu problēmu
Please open a ticket in [#support](https://discord.premid.app/).
