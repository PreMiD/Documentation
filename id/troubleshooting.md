---
title: Troubleshooting
description: Segalanya untuk menyelesaikan masalah kamu
published: true
date: 2021-02-08T21:30:58.603Z
tags:
editor: markdown
dateCreated: 2020-06-11T18:03:54.865Z
---

> Pastikan kamu sudah memasang ekstensi **dan** aplikasinya! 
> 
> {.is-warning}

Halaman ini meliputi:
1. [Troubleshooting Umum](https://docs.premid.app/troubleshooting#general)
2. [Troubleshooting Linux](https://docs.premid.app/troubleshooting#linux)
3. [Troubleshooting MacOS](https://docs.premid.app/troubleshooting#macos)

<a name="general"></a>

# Troubleshooting Umum
> Kamu bisa menggunakan alat [ini](https://qkeleq10.github.io/PreMiD-Troubleshooting/) agar lebih mudah mengidentifikasi permasalahanmu. 
> 
> {.is-info}
### Muat ulang halaman
Kamu juga bisa menekan <kbd>CTRL+R</kbd>/<kbd>F5</kbd> (Windows) atau <kbd>CMD+R</kbd> (MacOS) pada keyboard selain menekan tombol refresh.

### Apakah kamu menggunakan aplikasi Discord?
PreMiD **tidak** bekerja pada discord versi browser, kamu harus mengunduh aplikasinya [disini](https://discord.com/download).

### Pastikan kamu sudah mengaktifkan Status Activity pada pengaturan Discordmu
**User Settings** > **Activity Status**
<img src="https://i.imgur.com/9SfrrWm.png" width="500px" style="max-width:100%;" />

### Pastikan Discord TIDAK berjalan sebagai administrator
Sangat penting. Discord RPC tidak bisa bekerja jika kamu membuka Discord sebagai administrator.

### Apakah kamu menggunakan Presence dengan pengaturan?
Many presences (including `Twitch` and `SoundCloud`) are affected by an extension issue. This issue causes the extension to not grab the default values of settings properly.

To solve this, all you have to do is toggle the topmost setting:
<img src="https://i.imgur.com/JtXxTzg.gif" width="500px" style="max-width:100%;" />

### Mulai ulang browser
<kbd>Alt</kbd>+<kbd>F4</kbd> (Windows) atau <kbd>CMD</kbd>+<kbd>Q</kbd> (MacOS) juga bisa bekerja. (You have to start your browser again obviously.)

### Memulai ulang PreMiD (Aplikasi)
<img src="https://i.imgur.com/wQA15xu.png" width="500px" style="max-width:100%;" />
Kamu harus memulai ulang PreMiD setelah itu.

### Reload/mulai ulang Discord
Press <kbd>CTRL+R</kbd> (Windows) or <kbd>CMD+R</kbd> (MacOS) on your keyboard or restart Discord manually.

### Periksa jika antivirus atau firewall berjalan di komputermu
Sometimes antivirus programs and firewalls are blocking applications which are creating/hosting servers or just connecting to the internet. We are using a local server to receive and pass data between our app and extension, so if you will block app's ability to pass data you probably will not be able to use PreMiD.

### Nonaktifkan addon
Disable all your addons and see if it works. If yes, try to enable your addons step-by-step and tell us which addon broke PreMiD.

### Mulai ulang komputermu
I hope you know how to restart a computer.

### Instal ulang PreMiD
Sometimes there is something wrong with the files... Tutorials for the installation can be found [here](/install).

### Penghapusan manual
Windows: Write `%appdata%` on the file explorer and delete the `PreMiD` folder. MacOS: `~/users/USER/~Library/Application Support/` and delete the `PreMiD` folder.

### McAfee mendeteksi PreMiD sebagai virus (Windows)
This is a false positive from McAfee and we have reported the issue to them, for now you can exclude PreMiD from the scan by doing the following steps:

> Jika kamu tidak merasa percaya diri mengikuti langkah-langkah ini, silakan buat tiket di [#support](https://discord.premid.app/) dan salah satu Agen Bantuan akan membantumu! 
> 
> {.is-warning}

1. Buka aplikasi McAfee dan klik pada ikon pengaturan pada kanan atas. <img src="https://i.imgur.com/rPLZn6c.png" width="500px" style="max-width:100%;" />
2. Klik "Item Karantina" (Kedua dari atas).
3. Perluas, dan klik ikon `>` sebelum item bernama "settings.dat".
4. Pastikan direktorinya ""AppData\Local\Temp\PreMiD", jika benar pilih dan tekan pemulihan. <img src="https://i.imgur.com/9nvHmiI.png" width="500px" style="max-width:100%;" />
5. Setelah pemulihan kamu bisa menutup "Item Karantina", lalu tekan ikon pengaturan lagi di atas kanan.
6. Tekan "Pemindaian" (Ketiga dari atas).
7. Perluas dan klik "Tambahkan file".
8. Ketik "%appdata%" di bilah alamat File Explorer dan tekan Enter. <img src="https://i.imgur.com/2bchwLe.png" width="500px" style="max-width:100%;" />
9. Buka folder "PreMiD" dan pilih file "PreMiD.exe" lalu klik buka. <img src="https://i.imgur.com/aHOyv3V.png" width="500px" style="max-width:100%;" />
10. McAfee sekarang seharusnya sudah mengabaikan file kita, luncurkan saja aplikasi kita dan seharusnya baik-baik saja.

### Status PreMiD bermasalah di Discord!
Jangan khawatir. Press the <kbd>CTRL+R</kbd> (Windows) or <kbd>CMD+R</kbd> (MacOS) keybind while focused on your discord window to reload it.

<a name="linux"></a>

# Troubleshooting Linux
### Distro berbasis Ubuntu/Debian
If you have downloaded Discord through Snapcraft, RPC will not work. You have to uninstall the Snapcraft version by executing `sudo snap remove discord` on a terminal, download **[Discord's Linux build](https://discordapp.com/api/download?platform=linux)** (**[or Discord Canary](https://discordapp.com/api/canary/download?platform=linux)**), then navigating to the directory you downloaded Discord to (usually `$HOME/Downloads`), then installing the package using `sudo dpkg -i discord-*.deb`. Jika AppImage tidak bisa bekerja, kamu bisa memeriksa package lain kami di **[link ini](https://packagecloud.io/premid/linux)**.

### Distro berbasis Arch Linux
Arch Linux based distros should use AUR (Arch User Repository) package that is named <code>premid</code> or <code>premid-git</code> (<em x-id="3">WARNING: This repository builds premid from our source code.</em>). If you don't want to install an AUR manager (yay etc.), you can check out our AppImage that is downloadable from our <strong x-id="1"><a href="https://github.com/premid/linux/releases">Linux repository</a></strong>.
<em x-id="3">Warning: the package in the <strong x-id="1">AUR</strong> repository is not maintained by us (as PreMiD organization), but by other people.</em>

### Port binding
You should know that <strong x-id="1">PreMiD</strong> binds itself to the port <strong x-id="1">3020</strong>. This is necessary for the Extension and the Application communicate. If <strong x-id="1">PreMiD</strong> shows you an error about this port, you should check if something is binded to the 3020 port by running <code>sudo lsof -i:3020</code> or <code>sudo netstat -tnlp | grep :3020</code> in your terminal. If some process is binded to it you should make sure to free the port and try running <code>PreMiD</code> again.

### AppImage PreMiD tidak berjalan saat login
As we stated in our **Linux repository**, AppImage can't be launched at login. You can add it to autostart manually by doing these steps:
1. Buat file bernama <strong x-id="1">rc.local</strong> pada direktori <code>/etc</code>.
2. Buka file tersebut menggunakan editor yang kamu sukai dan tempel kode yang telah diberikan dengan mengubah beberapa hal:
```bash
#!/bin/bash
# Dibutuhkan untuk menjalankan /bin/bash (jika kamu menggunakan zsh etc. kamu dapat mengubahnya.)

# Contoh: /home/PreMiD/PreMiD*.AppImage
<directory to appimage>/PreMiD*.AppImage

exit 0
```
3. Simpan file dan chmod sebagai executable `sudo chmod a+x /etc/rc.local`.
4. Restart PCmu dan AppImage PreMiD akan berjalan saat login.

<a name="macos"></a>

# Troubleshooting MacOS
### Error membuat direktori
<img src="https://i.imgur.com/td92lf6.png" width="300px" style="max-width:100%;" />

If you get this error, it means that your account doesn't have Administrator permissions and you need to create folder manually by doing these steps:
1. Buka finder dan buka folder **Applications**.
2. Klik kanan pada bagian kosong dan klik **Create folder**.
3. Pada folder tersebut masukkan nama `PreMiD` (perhatikan huruf kapital).
4. Buka installer lagi.

# Masalahku belum terselesaikan
Please open a ticket in [#support](https://discord.premid.app/).
