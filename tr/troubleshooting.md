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
> [Bunu](https://qkeleq10.github.io/PreMiD-Troubleshooting/) kullanarak sorununuzu daha kolay tespit edebilirsiniz. 
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
Gerçekten önemli. Discord'u yönetici olarak çalıştırdığınız taktirde Discord RPC çalışmayacaktır.

### Bir servisi ayarlarla mı kullanıyorsunuz?
Çoğu presence (`Twitch` ve `SoundCloud` gibi) bir uzantı hatasından etkileniyor. Bu sorun uzantının varsayılan ayar değerlerini düzgün şekilde çekememesine sebep oluyor.

Bunu düzeltmek için, tüm yapmanız gereken şey en üstteki ayarı değiştirmek:
<img src="https://i.imgur.com/JtXxTzg.gif" width="500px" style="max-width:100%;" />

### Tarayıcınızı yeniden başlatın
<kbd>Alt</kbd>+<kbd>F4</kbd> (Windows) ya da <kbd>CMD</kbd>+<kbd>Q</kbd> (MacOS) da iyi bir iş çıkarıyor. (Tarayıcınızı tekrardan başlatmanız gerekiyor elbette.)

### PreMiD Uygulamasını Yeniden Başlatın
<img src="https://i.imgur.com/g3ShdnU.png" width="500px" style="max-width:100%;" />
Daha sonra PreMiD uygulamasını yeniden başlatmanız gerekli.

### Discord'u yeniden yükle/yeniden başlat
Klavyenizden <kbd>CTRL+R</kbd> (Windows) ya da <kbd>CMD+R</kbd> (MacOS)'ye basın yada Discord'u manuel olarak yeniden başlatın.

### Bilgisayarınızda çalışan bir antivirüs programı veya güvenlik duvarı olup olmadığını kontrol edin
Bazen antivirüs programları ve güvenlik duvarları, sunucu oluşturan/barındıran veya yalnızca Internet'e bağlanan uygulamaları engeller. Uygulamamız ve uzantımız arasında veri almak ve iletmek için yerel bir sunucu kullanıyoruz, bu nedenle uygulamanın veri aktarma özelliğini engellerseniz, muhtemelen PreMiD uygulamasını kullanamazsınız.

### Eklentilerinizi devre dışı bırakın
Bütün eklentilerinizi devre dışı bırakın ve düzelmiş mi diye kontrol edin. Eğer düzelmişse, adım adım bütün eklentilerinizi etkinleştirmeyi deneyin ve bize hangisinin PreMiD'i bozduğunu söyleyin.

### Bilgisayarınızı yeniden başlatın
Bir bilgisayarın nasıl yeniden başlatılacağını bildiğinizi umuyorum.

### PreMiD'i yeniden yükleyin
Bazen dosyalar ile ilgili bir sorun vardır... Kurulum ile ilgili öğreticiye [buradan](/install) ulaşılabilir.

### Manuel kaldırma
Windows: Dosya Gezginine `%appdata%` adresini yazın ve `PreMiD` klasörünü silin. MacOS: `~/users/USER/~Library/Application Support/` ve `PreMiD` klasörünü silin.

### McAfee PreMiD'i virüs olarak tespit etti (Windows)
Bu, McAfee'den bir yanlış alarmdır ve sorunu kendilerine bildirdik, şimdilik aşağıdaki adımları uygulayarak PreMiD'i taramanın dışında tutabilirsiniz:

> Eğer bu adımlarda sorun yaşıyorsanız, Discord sunucumuzdaki [#suppport](https://discord.premid.app/) kanalında bir destek talebi açıp, bir destek temsilcimizden yardım alabilirsiniz! 
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

### PreMiD durumu Discord'da yanlış görünüyor
Endişelenmeyin. Yeniden başlatmak için Discord pencerenizde iken <kbd>CTRL+R</kbd> (Windows) ya da <kbd>CMD+R</kbd> (MacOS)'ye kısayoluna basın.

<a name="linux"></a>

# Linux sorun giderme
### Ubuntu/Debian tabanlı dağıtımlar
Eğer Discord'u SnapCraft aracılığıyla indirdiyseniz RPC çalışmayacaktır. Terminalden `sudo snap remove discord` kodunu çalıştırarak Snapcraft versiyonunu silmeniz, **[Discord'un Linux versiyonunu](https://discordapp.com/api/download?platform=linux)** indirmeniz (**[ya da Discord Canary](https://discordapp.com/api/canary/download?platform=linux)**), sonrasında Discord'u indirdiğiniz dosya dizinine gitmeniz (genellikle `$HOME/Downloads`), sonra `sudo dpkg -i discord-*.deb` komudunu kullanarak paketi yüklemeniz gerekiyor. Eğer AppImage işe yaramazsa, **[bu bağlantı](https://packagecloud.io/premid/linux)** ile diğer paketlerimize bakmanızı öneririz.

### Arch Linux tabanlı dağıtımlar
Arch Linux tabanlı dağıtımlar, adı <code>premid</code> ya da <code>premid-git</code> adlı AUR (Arch User Repository) paketini kullanmalı (<em x-id="3">UYARI: Bu depo premidi bizim kaynak kodumuzdan derler.</em>). Eğer bir AUR yöneticisi (yay vb.) kurmak istemiyorsanız, <strong x-id="1"><a href="https://github.com/premid/linux/releases">Linux depomuzdan</a></strong> indirilebilir olan AppImage'ımıza bir göz gezdirebilirsiniz.
<em x-id="3">Uyarı: <strong x-id="1">AUR</strong> deposundaki paket bizim tarafımızdan (PreMiD organizasyonu olarak) değil, başkaları tarafından yönetiliyor.</em>

### Port ilişkilendirme
Şunu bilmelisiniz ki<strong x-id="1">PreMiD</strong> kendisini <strong x-id="1">3020</strong> portuna ilişkilendirir. Bu, Uzantı ve Uygulamanın iletişim kurması için gereklidir. Eğer <strong x-id="1">PreMiD</strong> size bu port hakkında bir hata gösterirse, <code>sudo lsof -i:3020</code> ya da<code>sudo netstat -tnlp | grep :3020</code> komudunu terminalinizde yürüterek 3020 portu ile bir şey ilişkilendirilmiş mi diye kontrol etmelisiniz. Eğer bu portla ilişkilendirilmiş bir işlem varsa dolu olan portu serbest bıraktığınızdan emin olun ve <code>PreMiD</code>'i tekrar çalıştırmayı deneyin.

### PreMiD AppImage ile kurulduğunda oturum açarken başlamıyor
**Linux depomuza** belirttiğimiz gibi, AppImage girişte başlatılamaz. Aşağıdaki adımları uygulayarak otomatik başlatmaya manuel olarak ekleyebilirsiniz:
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
