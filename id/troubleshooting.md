---
title: Troubleshooting
description: Segalanya untuk menyelesaikan masalah kamu
published: true
date: 2021-09-19T01:53:00.599Z
tags: 
editor: markdown
dateCreated: 2021-09-19T01:17:41.835Z
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
Banyak presence (termasuk `Twitch` dan `SoundCloud`) terpengaruh oleh masalah ekstensi. Masalah ini menyebabkan ekstensi tidak mendapat value default dari setting dengan benar.

Untuk memecahkan ini, kamu hanya butuh untuk menyalakan pilihan pengaturan paling atas:
<img src="https://i.imgur.com/JtXxTzg.gif" width="500px" style="max-width:100%;" />

### Mulai ulang browser
<kbd>Alt</kbd>+<kbd>F4</kbd> (Windows) atau <kbd>CMD</kbd>+<kbd>Q</kbd> (MacOS) juga bisa bekerja. (Kamu harus membuka kembali browsermu.)

### Memulai ulang PreMiD (Aplikasi)
<img src="https://i.imgur.com/wQA15xu.png" width="500px" style="max-width:100%;" />
Kamu harus memulai ulang PreMiD setelah itu.

### Reload/mulai ulang Discord
Tekan <kbd>CTRL+R</kbd> (Windows) atau <kbd>CMD+R</kbd> (MacOS) di keyboard kamu atau mulai ulang Discord dengan cara manual.

### Periksa jika antivirus atau firewall berjalan di komputermu
Kadang program antivirus dan firewall juga memblokir akses aplikasi dalam pembuatan server atau hanya terhubung ke internet. Kita menggunakan server lokal untuk menerima dan meneruskan data antara aplikasi dan ekstensi kita, jadi jika kamu akan memblokir ability aplikasi untuk meneruskan data, kamu mungkin tidak akan bisa menggunakan PreMiD.

### Nonaktifkan addon
Matikan semua addon dan lihat apakah bekerja. Jika iya, coba untuk menyalakan addon sesuai step satu persatu dan beri tahu kami addon mana yang merusak PreMiD.

### Mulai ulang komputermu
Kami harap kamu paham bagimana cara untuk memulai ulang komputer.

### Instal ulang PreMiD
Kadang juga terjadi sesuatu yang salah dengan file nya... Tutorial untuk penginstalan bisa kamu lihat di [sini](/install).

### Penghapusan manual
Windows: Ketik `%appdata%` di file explorer dan hapus folder `PreMiD`. MacOS: `~/users/USER/~Library/Application Support/` dan hapus folder `PreMiD`.

### McAfee mendeteksi PreMiD sebagai virus (Windows)
Ini adalah pendeteksian palsu dari McAfee dan kami telah melaporkan masalah ini kepada mereka, untuk saat ini kamu dapat menghapus PreMiD dari pengecekan dengan melakukan langkah-langkah berikut:

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
Jangan khawatir. Tekan tombol <kbd>CTRL+R</kbd> (Windows) atau <kbd>CMD+R</kbd> (MacOS) saat berada di Discord kamu untuk memuat ulang.

<a name="linux"></a>

# Troubleshooting Linux
### Distro berbasis Ubuntu/Debian
Jika kamu mengunduh Discord melalui Snapcraft, RPC tidak bisa bekerja. Kamu harus menghapus instalan versi Snapcraft dengan menggunakan `sudo snap remove discord` di terminal, download **[Discord Linux build](https://discordapp.com/api/download?platform=linux)** (**[ataupun Discord Canary](https://discordapp.com/api/canary/download?platform=linux)**), lalu navigasikan ke direktori tempat kamu mengunduh Discord (biasanya `$HOME/Downloads`), lalu instal paket menggunakan `sudo dpkg -i discord-*.deb`. Jika AppImage tidak bisa bekerja, kamu bisa memeriksa package lain kami di **[link ini](https://packagecloud.io/premid/linux)**.

### Distro berbasis Arch Linux
Distro berbasis Arch Linux sebaiknya menggunakan paket AUR (Arch User Repository) yang bernama <code>premid</code> atau <code>premid-git</code> (<em x-id="3"> PERINGATAN: Repository ini membangun premid dari kode sumber kami.</em>). Jika kamu tidak ingin memasang AUR manager (yay dll.), kamu dapat memeriksa AppImage kami yang dapat diunduh dari <strong x-id="1"><a href="https://github.com/premid/linux/releases">Linux repository</a></strong> kami.
<em x-id="3">Peringatan: paket pada repository <strong x-id="1">AUR</strong> tidak dikelola oleh kami (sebagai organisasi PreMiD), tapi oleh orang lain.</em>

### Port binding
Kamu harus tahu bahwa <strong x-id="1">PreMiD</strong> terikat pada port <strong x-id="1">3020</strong>. Ini dibutuhkan agar Ekstensi dan Aplikasi dapat berkomunikasi. Jika <strong x-id="1">PreMiD</strong> menampilkan error tentang port tersebut, kamu sebaiknya memeriksa jika ada sesuatu yang terikat pada port 3020 dengan menjalankan <code>sudo lsof -i:3020</code> atau <code>sudo netstat -tnlp | grep :3020</code> pada terminalmu. Jika suatu proses terikat pada port tersebut kamu harus memastikan port tersebut kosong dan coba menjalankan <code>PreMiD</code> lagi.

### AppImage PreMiD tidak berjalan saat login
Seperti yang telah kami tetapkan pada **Linux repository**, AppImage tidak bisa dijalankan saat login. Kamu dapat menambahkan autostart dengan melakukan langkah berikut:
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

Jika kamu mendapatkan error ini, itu berarti akunmu tidak memiliki akses Administrator dan kamu harus membuat folder secara manual dengan mengikuti langkah berikut:
1. Buka finder dan buka folder **Applications**.
2. Klik kanan pada bagian kosong dan klik **Create folder**.
3. Pada folder tersebut masukkan nama `PreMiD` (perhatikan huruf kapital).
4. Buka installer lagi.

# Masalahku belum terselesaikan
Harap membuka tiket pada [#support](https://discord.premid.app/).
