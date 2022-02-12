---
title: Sorun Giderme
description: Karşılaştığınız hatayı çözebilmek için her şey
published: true
date: 2021-12-20T14:27:18.034Z
tags:
editor: markdown
dateCreated: 2021-09-07T01:17:32.312Z
---

> Uzantıyı **ve** uygulamanın yüklü olduğundan emin olun! 
> 
> {.is-warning}

Bu sayfanın içerikleri:
1. [Genel sorun giderme](https://docs.premid.app/troubleshooting#general)
2. [Linux sorun giderme](https://docs.premid.app/troubleshooting#linux)
3. [MacOS sorun giderme](https://docs.premid.app/troubleshooting#macos)

<a name="general"></a>

# Genel sorun giderme
> You can use [this](https://qkeleq10.github.io/PreMiD-Troubleshooting/) tool to more easily identify your issue. 
> 
> {.is-info}
### Sayfayı yenileyin
Windows'daysanız <kbd>CTRL+R</kbd>/<kbd>F5</kbd>, Mac üzerindeyseniz ise <kbd>CMD+R</kbd> tuşlarını kullanarak sayfayı yenileyebilirsiniz.

### Discord uygulamasını kullandığınıza emin misiniz?
PreMiD, Discord'un tarayıcı sürümünde **çalışamaz**, bu yüzden [buradan](https://discord.com/download) uygulamayı indirmelisiniz.

### Ayarlardaki Oyun Etkinliği'nin açık olduğuna emin olun
**Kullanıcı Ayarları** > **Oyun Etkinliği**
<img src="https://i.imgur.com/9SfrrWm.png" width="500px" style="max-width:100%;" />

### Discord'un yönetici olarak çalışmadığından emin olun
Really important. Discord RPC will not work if you run Discord as an administrator.

### Bir servisi ayarlarla mı kullanıyorsunuz?
Many presences (including `Twitch` and `SoundCloud`) are affected by an extension issue. This issue causes the extension to not grab the default values of settings properly.

To solve this, all you have to do is toggle the topmost setting:
<img src="https://i.imgur.com/JtXxTzg.gif" width="500px" style="max-width:100%;" />

### Tarayıcınızı yeniden başlatın
<kbd>Alt</kbd>+<kbd>F4</kbd> (Windows) or <kbd>CMD</kbd>+<kbd>Q</kbd> (MacOS) does a good job too. (You have to start your browser again obviously.)

### PreMiD Uygulamasını Yeniden Başlatın
<img src="https://i.imgur.com/g3ShdnU.png" width="500px" style="max-width:100%;" />
You have to restart PreMiD afterwards.

### Discord'u yeniden başlatın
Press <kbd>CTRL+R</kbd> (Windows) or <kbd>CMD+R</kbd> (MacOS) on your keyboard or restart Discord manually.

### Bilgisayarınızda çalışan bir antivirüs programı veya güvenlik duvarı olup olmadığını kontrol edin
Sometimes antivirus programs and firewalls are blocking applications which are creating/hosting servers or just connecting to the internet. We are using a local server to receive and pass data between our app and extension, so if you block app's ability to pass data, you probably will not be able to use PreMiD.

### Eklentilerinizi devre dışı bırakın
Disable all your addons and see if it works. If yes, try to enable your addons step-by-step and tell us which addon broke PreMiD.

### Bilgisayarınızı yeniden başlatın
I hope you know how to restart a computer.

### PreMiD'i yeniden yükleyin
Sometimes there is something wrong with the files... Tutorials for the installation can be found [here](/install).

### Manuel kaldırma
Windows: Dosya Gezginine `%appdata%` adresini yazın ve `PreMiD` klasörünü silin. MacOS: `~/users/USER/~Library/Application Support/` and delete the `PreMiD` folder.

### McAfee PreMiD'i virüs olarak tespit etti (Windows)
This is a false positive from McAfee and we have reported the issue to them, for now you can exclude PreMiD from the scan by doing the following steps:

> If you do not feel confident taking these steps, feel free to make a ticket in [#support](https://discord.premid.app/) and one of our Support Agents will be able to help you out! 
> 
> {.is-warning}

1. McAfee uygulamasını açın ve sağ üst taraftaki ayarlar simgesini tıklayın. <img src="https://i.imgur.com/rPLZn6c.png" width="500px" style="max-width:100%;" />
2. "Karantinaya Alınan Öğeler"e tıklayın (üstten ikinci seçenek).
3. Geniletin, ve "settings.dat" isimli bir elemandan önceki `>` işaretine tıklayın.
4. Dosya yolunun "AppData\Local\Temp\PreMiD"  içerdiğine emin olun, bulduktan sonra geri yükle tuşuna basın. <img src="https://i.imgur.com/9nvHmiI.png" width="500px" style="max-width:100%;" />
5. Geri yüklendikten sonra "Karantinaya Alınmış Öğeler" penceresini kapatabilir ve sağ üstteki ayarlar simgesine tekrar basabilirsiniz.
6. "Gerçek Zamanlı Tarama"ya tıklayın (üstten üçüncü seçenek).
7. Genişletin ve "Dosya ekle"ye tıklayın.
8. Dosya Gezgini adres çubuğuna "%appdata%" yazın ve Enter tuşuna basın. <img src="https://i.imgur.com/2bchwLe.png" width="500px" style="max-width:100%;" />
9. "PreMiD" klasörünü açın ve "PreMiD.exe" dosyasını seçin ve aç'a tıklayın. <img src="https://i.imgur.com/aHOyv3V.png" width="500px" style="max-width:100%;" />
10. McAfee şimdi dosyamızı göz ardı etmeli, uygulamayı çalıştırın ve kullanmaya başlayın.

### PreMiD status bugged on Discord
Endişelenmeyin. Press the <kbd>CTRL+R</kbd> (Windows) or <kbd>CMD+R</kbd> (MacOS) keybind while focused on your Discord window to reload it.

<a name="linux"></a>

# Linux sorun giderme
### Ubuntu/Debian tabanlı dağıtımlar
If you have downloaded Discord through Snapcraft, RPC will not work. You have to uninstall the Snapcraft version by executing `sudo snap remove discord` on a terminal, download **[Discord's Linux build](https://discordapp.com/api/download?platform=linux)** (**[or Discord Canary](https://discordapp.com/api/canary/download?platform=linux)**), then navigating to the directory you downloaded Discord to (usually `$HOME/Downloads`), then installing the package using `sudo dpkg -i discord-*.deb`. If AppImage doesn't work, you should consider checking our other packages by **[this link](https://packagecloud.io/premid/linux)**.

### Arch Linux Tabanlı Dağıtımlar
Arch Linux based distros should use AUR (Arch User Repository) package that is named <code>premid</code> or <code>premid-git</code> (<em x-id="3">WARNING: This repository builds premid from our source code.</em>). If you don't want to install an AUR manager (yay etc.), you can check out our AppImage that is downloadable from our <strong x-id="1"><a href="https://github.com/premid/linux/releases">Linux repository</a></strong>.
<em x-id="3">Warning: the package in the <strong x-id="1">AUR</strong> repository is not maintained by us (as PreMiD organization), but by other people.</em>

### Port ilişkilendirme
You should know that <strong x-id="1">PreMiD</strong> binds itself to the port <strong x-id="1">3020</strong>. Bu, Uzantı ve Uygulamanın iletişim kurması için gereklidir. If <strong x-id="1">PreMiD</strong> shows you an error about this port, you should check if something is binded to the 3020 port by running <code>sudo lsof -i:3020</code> or <code>sudo netstat -tnlp | grep :3020</code> in your terminal. If some process is binded to it you should make sure to free the port and try running <code>PreMiD</code> again.

### PreMiD AppImage ile kurulduğunda oturum açarken başlamıyor
As we stated in our **Linux repository**, AppImage can't be launched at login. Aşağıdaki adımları uygulayarak otomatik başlatmaya manuel olarak ekleyebilirsiniz:
1. <code>/etc</code> klasöründe <strong x-id="1">rc.local</strong> adında bir dosya oluşturun.
2. Bu dosyayı istediğiniz düzenleyici ile açıp bazı değişiklikler yaparak aşağıdaki kodu yapıştırın:
```bash
#!/bin/bash
# /bin/bash olarak çalıştırmak için gereklidir (eğer zsh vb. kullanıyorsanız değiştirebilirsiniz.)

# Örnek: /home/PreMiD/PreMiD*.AppImage
<appimage klasörü>/PreMiD*.AppImage

exit 0
```
3. Dosyayı kaydedin ve chmod ile çalıştırma izni verin `sudo chmod a+x /etc/rc.local`.
4. Bilgisayarınızı yeniden başlattığınızda PreMiD AppImage giriş yaptığınızda otomatik başlar.

<a name="macos"></a>

# MacOS sorun giderme
### Klasör oluşturmada hata
<img src="https://i.imgur.com/td92lf6.png" width="300px" style="max-width:100%;" />

Eğer bu hatayı alıyorsanız, hesabınızın Yönetici izinlerine sahip olmadığını ve şu adımları uygulayarak manuel bir şekilde klasör oluşturmanızın gerektiği anlamına gelir:
1. Finder'ı açın ve **Uygulamalar** klasörünü bulun.
2. Boş bir yere sağ tıklayın be **Klasör oluştur**'a tıklayın.
3. Bu klasöre `PreMiD` adını verin (küçük büyük harfe dikkat edin).
4. Yükleyiciyi yeniden başlatın.

# Bunların hiçbiri sorununuzu çözmediyse
Lütfen [#support](https://discord.premid.app/) kanalından bir destek talebi açın.
