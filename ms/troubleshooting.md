---
title: Selesaikan masalah
description: Segalanya untuk menyelesaikan masalah anda
published: true
date: 2021-02-08T21:30:58.603Z
tags:
editor: markdown
dateCreated: 2020-06-11T18:03:54.865Z
---

> Sila pastikan anda telah pasangkan kedua-dua sambungan **dan** aplikasi! 
> 
> {.is-warning}

Disertakan di halaman ini:
1. [Penyelesaian masalah umum](https://docs.premid.app/troubleshooting#general)
2. [Penyelesaian masalah di Linux](https://docs.premid.app/troubleshooting#linux)
3. [Penyelesaian masalah di MacOS](https://docs.premid.app/troubleshooting#macos)

<a name="general"></a>

# Penyelesaian masalah umum
> Anda boleh gunakan alatan [ini](https://qkeleq10.github.io/PreMiD-Troubleshooting/) untuk mengenal pasti isu anda dengan lebih mudah. 
> 
> {.is-info}
### Muat semula halaman
Anda boleh tekan <kbd>CTRL+R</kbd>/<kbd>F5</kbd> (Windows) atau <kbd>CMD+R</kbd> (MacOS) di papan kekunci anda juga di samping mencari butang muat semula.

### Adakah anda menggunakan aplikasi Discord?
PreMiD **tidak** berfungsi di Discord versi pelayar, anda mesti muat turun aplikasi [di sini](https://discord.com/download).

### Sila pastikan anda membolehkan Activity Status / Status Aktiviti dalam tetapan apl Discord anda
**User Settings / Tetapan Pengguna** > **Activity Status / Status Aktiviti**
<img src="https://i.imgur.com/9SfrrWm.png" width="500px" style="max-width:100%;" />

### Pastikan Discord dijalankan BUKAN sebagai pentadbir
Really important. Discord RPC will not work if you run Discord as an administrator.

### Adakah anda menggunakan Presence dengan tetapan?
Banyak Presence (termasuk `Twitch` dan `SoundCloud`) terkesan dengan masalah sambungan. Isu ini menyebabkan sambungan tidak mampu memperoleh nilai lalai tetapan dengan betul.

Untuk menyelesaikan isu ini, anda hanya perlu menogol tetapan teratas:
<img src="https://i.imgur.com/JtXxTzg.gif" width="500px" style="max-width:100%;" />

### Mula semula pelayar anda
<kbd>Alt</kbd>+<kbd>F4</kbd> (Windows) atau <kbd>CMD</kbd>+<kbd>Q</kbd> (MacOS) juga boleh lakukannya. (Sudah tentulah anda perlu mulakan semula pelayar anda.)

### Mulakan semula PreMiD (Aplikasi)
<img src="https://i.imgur.com/wQA15xu.png" width="500px" style="max-width:100%;" />
Anda perlu mulakan semula PreMiD selepas ini.

### Muat semula/mula semula Discord
Press <kbd>CTRL+R</kbd> (Windows) or <kbd>CMD+R</kbd> (MacOS) on your keyboard or restart Discord manually.

### Periksa jika anda mempunyai antivirus atau tembok api berjalan di komputer anda
Sometimes antivirus programs and firewalls are blocking applications which are creating/hosting servers or just connecting to the internet. We are using a local server to receive and pass data between our app and extension, so if you will block app's ability to pass data you probably will not be able to use PreMiD.

### Lumpuhkan sambungan anda
Disable all your addons and see if it works. If yes, try to enable your addons step-by-step and tell us which addon broke PreMiD.

### Memulakan semula komputer anda
I hope you know how to restart a computer.

### Memasang semula PreMiD
Sometimes there is something wrong with the files... Tutorials for the installation can be found [here](/install).

### Pembuangan manual
Windows: Write `%appdata%` on the file explorer and delete the `PreMiD` folder. MacOS: `~/users/USER/~Library/Application Support/` and delete the `PreMiD` folder.

### McAfee mengesan PreMiD sebagai virus (Windows)
Ini positif palsu daripada McAfee dan kami telah melaporkan isu ini kepada mereka, buat masa ini anda boleh kecualikan PreMiD daripada imbasan dengan langkah berikut:

> Jika anda rasa tidak yakin untuk melakukan langkah ini, silakan buat tiket dalam bahasa Inggeris di saluran [#support](https://discord.premid.app/) dan salah seorang Ejen Sokongan kami akan membantu anda! 
> 
> {.is-warning}

1. Buka aplikasi McAfee dan klik ikon tetapan di sebelah kanan atas. <img src="https://i.imgur.com/rPLZn6c.png" width="500px" style="max-width:100%;" />
2. Klik "Quarantined Items" / Item Dikuarantin (Kedua dari atas).
3. Kembangkannya, dan klik pada ikon `>` sebelum item dengan nama "settings.dat".
4. Pastikan laluan mengandungi "AppData\Local\Temp\PreMiD", jika ya pilih ia dan tekan Restore / Pulihkan. <img src="https://i.imgur.com/9nvHmiI.png" width="500px" style="max-width:100%;" />
5. Setelah ia dipulihkan anda boleh tutup tetingkap timbul "Quarantined Items" / Item Dikuarantin, kemudian tekan ikon tetapan lagi sekali di sebelah kanan atas.
6. Klik "Real-Time Scanning" / Imbasan Masa Nyata (Ketiga dari atas).
7. Kembangkannya dan pilih "Add file" / Tambah fail.
8. Taipkan "%appdata%" dalam bar alamat di File Explorer dan tekan Enter. <img src="https://i.imgur.com/2bchwLe.png" width="500px" style="max-width:100%;" />
9. Buka folder "PreMiD" dan pilih fail "PreMiD.exe" dan klik Open / Buka. <img src="https://i.imgur.com/aHOyv3V.png" width="500px" style="max-width:100%;" />
10. Sekarang McAfee patut abaikan fail kami, jadi lancarkan aplikasi kami dan anda boleh teruskan dari situ.

### Status PreMiD rosak di discord!
Don't worry. Press the <kbd>CTRL+R</kbd> (Windows) or <kbd>CMD+R</kbd> (MacOS) keybind while focused on your discord window to reload it.

<a name="linux"></a>

# Penyelesaian masalah di Linux
### Edaran berasaskan Ubuntu/Debian
If you have downloaded Discord through Snapcraft, RPC will not work. You have to uninstall the Snapcraft version by executing `sudo snap remove discord` on a terminal, download **[Discord's Linux build](https://discordapp.com/api/download?platform=linux)** (**[or Discord Canary](https://discordapp.com/api/canary/download?platform=linux)**), then navigating to the directory you downloaded Discord to (usually `$HOME/Downloads`), then installing the package using `sudo dpkg -i discord-*.deb`. Jika AppImage tidak berfungsi, anda patut pertimbangkan untuk menyemak pakej kami yang lain melalui **[pautan ini](https://packagecloud.io/premid/linux)**.

### Edaran berasaskan Arch Linux
Edaran berasaskan Arch Linux patut gunakan pakej AUR (Arch User Repository / Repositori Pengguna Arch) yang dinamakan <code>premid</code> atau <code>premid-git</code> (<em x-id="3">AMARAN: repositori ini membina premid terus dari kod sumber kami.</em>). Jika anda tidak ingin memasangkan pengurus AUR (seperti yay dll.), anda boleh dapatkan AppImage kami yang boleh dimuat turun daripada <strong x-id="1"><a href="https://github.com/premid/linux/releases">repositori Linux</a></strong> kami.
<em x-id="3">Amaran: pakej di repositori <strong x-id="1">AUR</strong> tidak disenggara oleh kami (sebagai organisasi PreMiD), tetapi oleh orang lain.</em>

### Ikatan port
Anda patut tahu <strong x-id="1">PreMiD</strong> mengikatkan dirinya di port nombor <strong x-id="1">3020</strong>. Perkara ini diperlukan untuk perhubungan di antara Sambungan dan Aplikasi. Jika <strong x-id="1">PreMiD</strong> menunjukkan ralat kepada anda mengenai port ini, anda patut periksa sama ada wujudnya benda lain yang diikatkan ke port 3020 dengan menjalankan <code>sudo lsof -i:3020</code> atau <code>sudo netstat -tnlp | grep :3020</code> dalam terminal anda. Jika ada proses yang diikatkan ke port tersebut, anda perlu bebaskan port tersebut dan jalankan <code>PreMiD</code> sekali lagi.

### AppImage PreMiD tidak dilancarkan ketika log masuk
As we stated in our **Linux repository**, AppImage can't be launched at login. You can add it to autostart manually by doing these steps:
1. Cipta fail bernama <strong x-id="1">rc.local</strong> dalam direktori <code>/etc</code>.
2. Buka fail ini dalam penyunting teks kegemaran anda dan tampalkan kod diberi dengan mengubah beberapa perkara:
```bash
#!/bin/bash
# Mesti dijalankan sebagai /bin/bash (jika anda gunakan zsh dll. anda boleh mengubahnya.)

# Contoh: /home/PreMiD/PreMiD*.AppImage
<direktori ke appimage>/PreMiD*.AppImage

exit 0
```
3. Simpan fail dan chmod ia sebagai boleh laku `sudo chmod a+x /etc/rc.local`.
4. Mulakan semula PC anda dan AppImage PreMiD patut dilancarkan ketika log masuk.

<a name="macos"></a>

# Penyelesaian masalah di MacOS
### Ralat mencipta direktori
<img src="https://i.imgur.com/td92lf6.png" width="300px" style="max-width:100%;" />

If you get this error, it means that your account doesn't have Administrator permissions and you need to create folder manually by doing these steps:
1. Buka finder dan buka folder **Applications**.
2. Klik-kanan di ruangan kosong dan klik **Cipta folder**.
3. Bagi folder ini berikannya nama `PreMiD` (pastikan yang mana perlu berhuruf besar).
4. Buka pemasang lagi sekali.

# Semua itu tidak selesaikan masalah saya
Please open a ticket in [#support](https://discord.premid.app/).
