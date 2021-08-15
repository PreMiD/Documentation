---
title: Fabhtcheartú
description: Gach rud chun d'fhadhb a réiteach
published: true
date: 2021-02-08T21:30:58.603Z
tags:
editor: markdown
dateCreated: 2020-06-11T18:03:54.865Z
---

> Déan cinnte go bhfuil an síneadh **agus** an feidhmchlár suiteáilte agat! 
> 
> {.is-warning}

San áireamh ar an leathanach seo:
1. [Fabhtcheartú ginearálta](https://docs.premid.app/troubleshooting#general)
2. [Fabhtcheartú Linux](https://docs.premid.app/troubleshooting#linux)
3. [Fabhtcheartú MacOS](https://docs.premid.app/troubleshooting#macos)

<a name="general"></a>

# Fabhtcheartú ginearálta
> Mura mbraitheann tú muiníneach as na céimeanna seo a ghlacadh, bíodh leisce ort ticéad a dhéanamh i [#support](https://discord.premid.app/) agus beidh duine dár nGníomhairí Tacaíochta in ann cabhrú leat! 
> 
> {.is-info}
### Athlódáil an leathanach
Is féidir leat <kbd>CTRL+R</kbd>/<kbd>F5</kbd> (Windows) nó <kbd>CMD+R</kbd> (MacOS) a bhrú ar do mhéarchlár freisin in ionad an cnaipe athnuachana a chuardach.

### An bhfuil an aip Discord á úsáid agat?
Ní oibríonn PreMiD **ní** ar leagan an bhrabhsálaí de Discord, ní mór duit an aip [a íoslódáil anseo](https://discord.com/download).

### Déan cinnte go bhfuil Gníomhaíocht Cluiche Discord cumasaithe agat i suíomhanna
**User Settings** > **Game Activity**
<img src="https://i.imgur.com/9SfrrWm.png" width="500px" style="max-width:100%;" />

### Bí cinnte nach bhfuil Discord ag rith NÍL mar riarthóir
Really important. Discord RPC will not work if you run Discord as an administrator.

### An bhfuil tú ag úsáid láithreacht le socruithe?
Many presences (including `Twitch` and `SoundCloud`) are affected by an extension issue. This issue causes the extension to not grab the default values of settings properly.

To solve this, all you have to do is toggle the topmost setting:
<img src="https://i.imgur.com/JtXxTzg.gif" width="500px" style="max-width:100%;" />

### Atosaigh do bhrabhsálaí
<kbd>Alt</kbd>+<kbd>F4</kbd> (Windows) or <kbd>CMD</kbd>+<kbd>Q</kbd> (MacOS) does a good job too. (You have to start your browser again obviously.)

### Atosaigh PreMiD (Feidhmchlár)
<img src="https://i.imgur.com/wQA15xu.png" width="500px" style="max-width:100%;" />
You have to restart PreMiD afterwards.

### Discord athlódáil/atosú
Press <kbd>CTRL+R</kbd> (Windows) or <kbd>CMD+R</kbd> (MacOS) on your keyboard or restart Discord manually.

### Seiceáil an bhfuil frithvíreas nó balla dóiteáin ag rith ar do ríomhaire
Sometimes antivirus programs and firewalls are blocking applications which are creating/hosting servers or just connecting to the internet. We are using a local server to receive and pass data between our app and extension, so if you will block app's ability to pass data you probably will not be able to use PreMiD.

### Díchumasaigh do síntí
Disable all your addons and see if it works. If yes, try to enable your addons step-by-step and tell us which addon broke PreMiD.

### Ag atosú do ríomhaire
I hope you know how to restart a computer.

### PreMiD a athshuiteáil
Sometimes there is something wrong with the files... Tutorials for the installation can be found [here](/install).

### Baint láimhe
Windows: Write `%appdata%` on the file explorer and delete the `PreMiD` folder. MacOS: `~/users/USER/~Library/Application Support/` and delete the `PreMiD` folder.

### Bhraith McAfee PreMiD mar víreas (Windows)
This is a false positive from McAfee and we have reported the issue to them, for now you can exclude PreMiD from the scan by doing the following steps:

> Mura mbraitheann tú muiníneach as na céimeanna seo a ghlacadh, bíodh leisce ort ticéad a dhéanamh i [#support](https://discord.premid.app/) agus beidh duine dár nGníomhairí Tacaíochta in ann cabhrú leat! 
> 
> {.is-warning}

1. Oscail feidhmchlár McAfee agus cliceáil deilbhín na socruithe ar thaobh na láimhe deise. <img src="https://i.imgur.com/rPLZn6c.png" width="500px" style="max-width:100%;" />
2. Cliceáil "Míreanna Coraintín" (An dara ceann ón mbarr).
3. Leathnaigh é, agus cliceáil an `>` deilbhín roimh earra leis an ainm "settings.dat" air.
4. Déan cinnte go bhfuil "AppData\Local\Temp\PreMiD" ar an gcosán, más ea, roghnaigh é agus brúigh athshlánú. <img src="https://i.imgur.com/9nvHmiI.png" width="500px" style="max-width:100%;" />
5. Tar éis é a athshlánú is féidir leat an aníos "Míreanna Coraintín" a dhúnadh, ansin brúigh deilbhín na socruithe arís ar thaobh na láimhe deise.
6. Cliceáil "Scanadh Fíor-ama" (An tríú ón mbarr).
7. Leathnaigh é agus cliceáil "Cuir comhad leis".
8. Clóscríobh "%appdata%" i mbarra URL an bhainisteora comhaid agus brúigh Iontráil. <img src="https://i.imgur.com/2bchwLe.png" width="500px" style="max-width:100%;" />
9. Oscail an fillteán "PreMiD" agus roghnaigh an comhad "PreMiD.exe" agus cliceáil oscailte. <img src="https://i.imgur.com/aHOyv3V.png" width="500px" style="max-width:100%;" />
10. Ba cheart do McAfee neamhaird a dhéanamh dár gcomhad anois, gan ach ár bhfeidhmchlár a lainseáil agus ba cheart go mbeifeá go maith chun dul.

### Stádas PreMiD bugged ar discord!
Don't worry. Press the <kbd>CTRL+R</kbd> (Windows) or <kbd>CMD+R</kbd> (MacOS) keybind while focused on your discord window to reload it.

<a name="linux"></a>

# Fabhtcheartú Linux
### Distros bunaithe ar Ubuntu/Debian
If you have downloaded Discord through Snapcraft, RPC will not work. You have to uninstall the Snapcraft version by executing `sudo snap remove discord` on a terminal, download **[Discord's Linux build](https://discordapp.com/api/download?platform=linux)** (**[or Discord Canary](https://discordapp.com/api/canary/download?platform=linux)**), then navigating to the directory you downloaded Discord to (usually `$HOME/Downloads`), then installing the package using `sudo dpkg -i discord-*.deb`. If AppImage doesn't work, you should consider checking our other packages by **[this link](https://packagecloud.io/premid/linux)**.

### Distros bunaithe ar Arch Linux
Arch Linux based distros should use AUR (Arch User Repository) package that is named <code>premid</code> or <code>premid-git</code> (<em x-id="3">WARNING: This repository builds premid from our source code.</em>). If you don't want to install an AUR manager (yay etc.), you can check out our AppImage that is downloadable from our <strong x-id="1"><a href="https://github.com/premid/linux/releases">Linux repository</a></strong>.
<em x-id="3">Warning: the package in the <strong x-id="1">AUR</strong> repository is not maintained by us (as PreMiD organization), but by other people.</em>

### Ceangal calafoirt
You should know that <strong x-id="1">PreMiD</strong> binds itself to the port <strong x-id="1">3020</strong>. This is necessary for the Extension and the Application communicate. If <strong x-id="1">PreMiD</strong> shows you an error about this port, you should check if something is binded to the 3020 port by running <code>sudo lsof -i:3020</code> or <code>sudo netstat -tnlp | grep :3020</code> in your terminal. If some process is binded to it you should make sure to free the port and try running <code>PreMiD</code> again.

### Ní sheoltar AppImage PreMiD ag logáil isteach
As we stated in our **Linux repository**, AppImage can't be launched at login. You can add it to autostart manually by doing these steps:
1. Déan comhad darb ainm <strong x-id="1">rc.local</strong> san <code>/etc</code> eolaire.
2. Oscail an comhad seo san eagarthóir is fearr leat agus greamaigh an cód tugtha le roinnt rudaí a athrú:
```bash
#! / bin / bash
# Iarrtar ort rith mar / bin / bash (má úsáideann tú zsh srl. is féidir leat é a athrú.)

# Sampla: /home/PreMiD/PreMiD*.AppImage
<directory to appimage>/PreMiD*.AppImage

exit 0
```
3. Sábháil comhad agus chmod é mar inrite `sudo chmod a+x /etc/rc.local`.
4. Atosaigh do ríomhaire agus ba chóir PreMiD AppImage a sheoladh ag logáil isteach.

<a name="macos"></a>

# Fabhtcheartú MacOS
### Earráid agus eolaire á chruthú
<img src="https://i.imgur.com/td92lf6.png" width="300px" style="max-width:100%;" />

If you get this error, it means that your account doesn't have Administrator permissions and you need to create folder manually by doing these steps:
1. Aimsitheoir oscailte agus fillteán **Applications ** oscailte.
2. Cliceáil ar dheis ar spás bán agus cliceáil **Create folder**.
3. Sann an t-ainm `PreMiD` don fhillteán seo (cuimhnigh faoi litreacha na gcásanna uachtair).
4. Suiteálaí oscailte arís.

# Níor réitigh sé sin mo fhadhb
Please open a ticket in [#support](https://discord.premid.app/).
