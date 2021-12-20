---
title: Ngatasi masalah
description: Kabeh kanggo ngatasi masalah sampeyan
published: true
date: 2021-12-20T14:27:18.034Z
tags:
editor: markdown
dateCreated: 2021-09-07T01:17:32.312Z
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
Penting banget. Discord RPC ora bisa digunakake yen sampeyan mbukak Discord as administrator.

### Apa sampeyan nggunakake presence karo setelan?
Akeh presence (termasuk `Twitch` lan `SoundCloud`) terpengaruh karo masalah ekstensi. Masalah iki nyebabake ekstensi ora entuk default values setelan kanthi bener.

Kanggo ngatasi iki, sampeyan mung kudu ngaktifake pilihan setelan ndhuwur:
<img src="https://i.imgur.com/JtXxTzg.gif" width="500px" style="max-width:100%;" />

### Restart browsermu
<kbd>Alt</kbd>+<kbd>F4</kbd> (Windows) or <kbd>CMD</kbd>+<kbd>Q</kbd> (MacOS) does a good job too. (Sampeyan kudu mbukak browser maneh.)

### Restart PreMiD (Aplikasi)
<img src="https://i.imgur.com/wQA15xu.png" width="500px" style="max-width:100%;" />
Sampeyan kudu restart maneh PreMiD sawise iku.

### Reload/restart Discord
Pencet <kbd>CTRL+R</kbd> (Windows) utawa <kbd>CMD+R</kbd> (MacOS) ing keyboard utawa restart manual.

### Priksa manawa antivirus utawa firewall aktif ing komputermu
Kadang program antivirus lan firewall ngganggu program sing nggawe/hosting server utawa nyambung menyang internet. Kita nggunakake server lokal kanggo nampa lan ngliwati data ing antarane app lan ekstensi, dadi yen sampeyan blokir app sing lagi ngirim data, sampeyan ora isa nggunakake PreMiD.

### Pateni addon
Pateni kabeh addon lan periksa menawa bekerja. Yen bener, coba aktifake addon siji-siji lan critakake apa addon sing ngganggu PreMiD.

### Restart komputermu
Muga-muga sampeyan ngerti kepiye carane restart komputer.

### Instal ulang PreMiD
Kadhangkala ana kesalahan ing file... Tutorial kanggo instalasi isa didheleng [ing kene](/install).

### Penghapusan manual
Windows: Ketik `%appdata%` ing file explorer lan busek folder `PreMiD`. MacOS: `~/users/USER/~Library/Application Support/` lan busek folder `PreMiD`.

### McAfee ndeteksi PreMiD sebagai virus (Windows)
Iki minangka false positive palsu saka McAfee lan kita wis nglaporake masalah kasebut, saiki sampeyan bisa ngilangi PreMiD saka pindai kanthi nindakake perkara ing ngisor iki:

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

### PreMiD status bugged on Discord
Aja kuwatir. Pijet tombol <kbd>CTRL+R</kbd> (Windows) utawa <kbd>CMD+R</kbd> (MacOS) selagi jendela Discord mbukak kanggo memuat ulang.

<a name="linux"></a>

# Troubleshooting Linux
### Distro berbasis Ubuntu/Debian
Yen sampeyan download Discord liwat Snapcraft, RPC ora bakal bisa digunakake. Sampeyan kudu uninstall versi Snapcraft dengan menjalankan `sudo snap remove discord` ing terminal, unduh **[Discord Linux build](https://discordapp.com/api/download?platform=linux)** (**[utawa Discord Canary](https://discordapp.com/api/canary/download?platform=linux)**), banjur ngarah menyang direktori sing didownload (biasane `$HOME/Downloads`), banjur install paket gawe `sudo dpkg -i discord-*.deb`. Yen AppImage ora bisa digunakake, sampeyan bisa mriksa paket liyane ing **[link iki](https://packagecloud.io/premid/linux)**.

### Distro berbasis Arch Linux
Distros berbasis Arch Linux kudu nggunakake paket AUR (Arch User Repository) sing jenenge <code>premid</code> utawa <code>premid-git</code> (<em x-id="3"> AWAS: Repositori iki nggawe kode sumber asli kita. </em>). Yen sampeyan ora pengin nginstal manajer AUR (yay esp.), sampeyan bisa mriksa AppImage sing bisa diunduh saka <strong x-id="1"><a href="https://github.com/premid/linux/releases">Linux repository</a></strong>.
<em x-id="3">Pènginget: paket ing repositori <strong x-id="1">AUR</strong> ora dikelola karo kita (minangka organisasi PreMiD), nanging karo wong liya.</em>

### Port binding
Sampeyan kudu ngerti yen <strong x-id="1">PreMiD</strong> bakal mlebu ing port <strong x-id="1">3020</strong>. Iki dibutuhake supaya Ekstensi lan Aplikasi isa kominikasi. Yen <strong x-id="1">PreMiD</strong> ngasilake kesalahan tentang port kasebut, sampeyan kudu mriksa manawa ana sesuatu sing bakal mlebu ing port 3020 kanthi mbukak <code>sudo lsof -i:3020</code> utawa <code>sudo netstat -tnlp | grep: 3020 </code> ing terminal sampeyan. Yen proses kaiket ing port kasebut, priksa manawa port'e kosong lan coba jalanake <code>PreMiD</code> maneh.

### AppImage PreMiD ora mlaku nalika login
Kaya sing wis ditemtokake ing **Linux repository**, AppImage ora bisa mbukak nalika login. Sampeyan bisa nambah autostart kanthi nindakake langkah-langkah ing ngisor iki:
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

Yen sampeyan entuk kesalahan iki, tegese akun sampeyan ora duwe akses Administrator lan sampeyan kudu nggawe folder kanthi manual kanthi ngetutake langkah-langkah kasebut:
1. Bukak finder lan bukak folder **Applications**.
2. Klik-tengen ing bagian kosong lan klik **Create folder**.
3. Ing folder kasebut ketik jeneng `PreMiD` (perhatekno huruf kapital).
4. Bukak installer maneh.

# Masalahku durung mantun
Bukak tiket ing [#support](https://discord.premid.app/).
