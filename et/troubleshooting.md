---
title: Tõrkeparandus
description: Kõik teie probleemi lahendamiseks
published: true
date: 2021-12-20T14:27:18.034Z
tags:
editor: markdown
dateCreated: 2021-09-07T01:17:32.312Z
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
Väga oluline. Discordi RPC ei tööta, kui käivitate Discordi administraatorina.

### Kas kasutate presence-i, millel on seadmed?
Laienduse probleem mõjutab paljusid presence (sealhulgas `Twitch` ja `SoundCloud`). Selle probleemi tõttu ei haara laiendus sätete vaikeväärtusi korralikult.

Selle lahendamiseks peate vaid vahetama ülemise sätte:
<img src="https://i.imgur.com/JtXxTzg.gif" width="500px" style="max-width:100%;" />

### Taaskäivitage oma brauser
Ka <kbd>Alt</kbd>+<kbd>F4</kbd> (Windows) või <kbd>CMD</kbd>+<kbd>Q</kbd> (MacOS) teeb head tööd. (Peate oma brauseri ilmselgelt uuesti käivitama.)

### Taaskäivitage PreMiD (rakendus)
<img src="https://i.imgur.com/g3ShdnU.png" width="500px" style="max-width:100%;" />
Pärast peate PreMiDi taaskäivitama.

### Laadige/taaskäivitage Discord
Vajutage klaviatuuril <kbd>CTRL + R</kbd> (Windows) või <kbd>CMD + R</kbd> (MacOS) või taaskäivitage Discord käsitsi.

### Kontrollige, kas teie arvutis töötab viirusetõrje või tulemüür
Mõnikord blokeerivad viirusetõrjeprogrammid ja tulemüürid rakendusi, mis loovad/mõjutavad servereid või lihtsalt ühendavad internetiga. Paigaldamise õpetused leiate [siit](/install).

### Keelake oma lisad
Keelake kõik oma lisad ja vaadake, kas see töötab. Kui jah, proovige oma lisad samm-sammult lubada ja öelge meile, milline lisand PreMiD-i rikkus.

### Taaskäivitage arvuti
Loodan, et teate, kuidas arvutit taaskäivitada.

### PreMiD-i uuesti installimine
Mõnikord on failidega midagi valesti... Paigaldamise õpetused leiate [siit](/install).

### Käsitsi eemaldamine
Windows: Kirjutage failikeskkonda `%appdata%` ja kustutage kaust `PreMiD`. MacOS: `~/users/USER/~Library/Application Support/` ja kustutage kaust `PreMiD`.

### McAfee tuvastas PreMiD-i viirusena (Windows)
See on McAfee valepositiiv ja me oleme neile probleemist teatanud. Praegu saate PreMiDi skannimisest välja jätta, tehes järgmist:

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

### PreMiD status bugged on Discord
Ära muretse. Vajutage klahvikombinatsiooni <kbd>CTRL + R</kbd> (Windows) või <kbd>CMD + R</kbd> (MacOS), olles keskendunud Discordi aknale, selle uuesti laadimiseks.

<a name="linux"></a>

# Linuxi tõrkeotsing
### Ubuntu/Debiani põhised distrod
Kui olete Discordi alla laadinud Snapcrafti kaudu, ei tööta RPC. Peate Snapcrafti versiooni desinstallima, käivitades terminalis `sudo snap remove discord`, laadima alla **[Discordi Linuxi järk](https://discordapp.com/api/download?platform=linux) ** (**[või Discord Canary](https://discordapp.com/api/canary/download?platform=linux)**), seejärel navigeerige kataloogi, kuhu Discordi alla laadisite (tavaliselt `$HOME/Downloads`), seejärel installige pakett `sudo dpkg abil -i discord- *.deb`. Kui AppImage ei tööta, peaksite kaaluma meie teiste pakettide kontrollimist **[selle lingi abil](https://packagecloud.io/premid/linux)**.

### Arch Linuxi põhised distrod
Arch Linuxi põhised distrod peaksid kasutama AUR-paketti (Arch User Repository), mille nimi on <code>premid</code> või <code>premid-git</code> (<em x-id="3">HOIATUS: See hoidla ehitab premid-i meie lähtekoodist. </em>). Kui te ei soovi AUR-i haldurit installida (yay jne.), võite vaadata meie AppImage-i, mille saate alla laadida meie <strong x-id="1"><a href="https://github.com/premid/linux/releases">Linuxi hoidlast</a></strong>.
<em x-id="3">Hoiatus: <strong x-id="1">AUR</strong> hoidlas asuvat paketti ei hoolda me (PreMiD organisatsioonina), vaid teised inimesed.</em>

### Portide sidumine
Peaksite teadma, et <strong x-id="1">PreMiD</strong> seob end pordiga <strong x-id="1">3020</strong>. See on vajalik laienduse ja rakenduse suhtlemiseks. Kui <strong x-id="1">PreMiD</strong> kuvab selle pordi kohta vea, peaksite <code>sudo lsof -i:3020</code> või <code>sudo netstat -tnlp | grep :3020</code> käivitades kontrollima, kas teie terminalis on midagi seotud pordiga 3020. Kui mõni protsess on sellega seotud, peate kindlasti pordi vabastama ja proovima uuesti käivitada <code>PreMiD-i</code>.

### PreMiD AppImage ei käivitu sisselogimisel
Nagu me oma **Linuxi hoidlas** märkisime, ei saa AppImage-i sisselogimisel käivitada. Saate selle automaatse käivitamise alla käsitsi lisada, toimides järgmiselt:
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

Selle tõrke ilmnemisel tähendab see, et teie kontol pole administraatori õigusi ja peate kausta käsitsi looma, toimides järgmiselt:
1. Avage leidja ja avage kaust **Rakendused**.
2. Paremklõpsake tühjal kohal ja klõpsake valikut **Loo kaust**.
3. Sellesse kausta määrake nimi `PreMiD` (pidage meeles suurtähti).
4. Avage installer uuesti.

# See pole minu probleemi lahendanud
Please create a new post in [#support](https://discord.com/channels/493130730549805057/1019726199494279248).
