---
title: Servis Kılavuzu
description: Her geliştiricinin, servisinin eklenebilmesi için takip etmeleri gereken kurallar.
published: true
date: 2021-10-18T16:38:44.932Z
tags: 
editor: markdown
dateCreated: 2021-09-07T02:00:04.145Z
---

<div align="center">
    <img src="https://github.com/PreMiD.png?size=2048" width="128px" style="max-width:100%;">
    <h3 style="font-size: 2rem; margin-bottom: 0">Servis Kılavuzu</h3>
    <h4 style="margin-top: 0">Revizyon 3</h4>
    <br />
</div>

# Yönergeler

[GitHub Depomuza](https://github.com/PreMiD/Presences/) İçerik paylaşırken, bir takım yönergelere uymanız gerekir. Bazıları için bu kurallar katı görünebilir. Ama bu kurallar aslında bizim ve kullanıcılarımız sorunlar yaşamasını önlemek için vardır.

# Oluşturma

Servis geliştirmenin genel kuralları aşağıdaki gibidir:

- Yaptığınız servisler, seçtiğiniz site ile alakalı olmak **zorundadır**.
- Yaptığınız servis **Kesinlikle**, herhangi bir illegal siteninki olmamalıdır. (örneğin, uyuşturucu satıcılığı, çocuk pornografisi vb.)
- Dosya yapısı temiz ve yönetilmeli, kullanılmayan dosyalar içermemelidir (örneğin, vscode ve git klasörleri, resim ve metin dosyaları, vb.)
- Uygun bir dosya yapısına sahip olmanız gerekir, taslaklar kabul **edilemez**.
- Servisler ( `.onion` ) bulunan internet siteleri ve bedava alan adları (örn, `.TK ` [tüm Freenom alan adları], `.RF` `.GD` gibi...) veya sağlayıcıları için bir servis **geliştiremezsiniz**, alan adı veya sağlayıcı için ödeme sağladıkları bilgiyi iletmeleri durumunda gerekli tolerans gösterilecektir.
- Servisin alan adı en az 2 aylık olmalıdır.
- Tarayıcılara yerleşik sayfalar için yapılan servislere izin verilmemektedir (örneğin, Chrome Web Mağazası, `chrome://`, `about:` sayfaları gibi). Bu sayfalara kod enjekte edebilmek gelişmiş bir ayar aktifleştirmeyi gerektirdiği ve tarayıcılara zarar verebileceğinden dolayı **yasaktır**.
- Yalnızca tek bir sayfa için desteğe sahip varlıklara izin **verilmeyecektir**, çünkü diğer sayfalar için bozuk görünebilirler (örneğin ana sayfa), politika ve iletişim sayfaları (sık kullanılmayan içerik) veya sitelerin diğer ilgisiz içerikleri. (ör. viki sayfaları)
- Çevrimiçi radyoların servislerinin eklenebilmesi için en az haftalık 100 ve aktif 15 dinleyicisi olmalıdır.
- Servislerin değişkenleri almak için kendi fonksiyonuyla JS kodu çalıştırmasına izin verilmez. If Firefox has issues with built-in function inside `Presence` class, you are allowed to do your own function and you need to tell us about it in Pull Request description.
- Low quality presences (or ones with little context) are **not** allowed (for e.g., only showing a logo and text but never changing it again).
- Discord Botları/Sunucu Listeleri için servis yaparken ekstra gereksinimler vardır:
  - Alan adı en az **6 aylık** olmalıdır.
  - Gün içinde farklı ziyaretçi sayısı:
    - 6 aylık alan adları için: **günde 20,000 farklı ziyaretçi**.
    - 12+ aylık alan adları için: **günde 45,000 farklı ziyaretçi**.
  - Site `.xyz`, `.club` gibi ucuz alan adlarında olamaz.
  - Site çok iyi bir kaliteye, tasarıma, vs. sahip olmalıdır.
- Presences should use [common details](https://api.premid.app/v2/langFile/presence/en) (strings starting with "general."). You can achieve this using `multiLanguage` with the provided strings. If your presence requires custom strings, then you shouldn't use `multiLanguage` until the presence gets 1000 users. You can find an example [here](https://docs.premid.app/dev/presence/class#getstringsobject).
- Including the `dist` folder, `presence.ts` file, `iframe.ts` file, and `metadata.json` file is mandatory so the result would be what is represented in the following schema:

```bash
presence
├── dist
│   └── metadata.json
├── presence.ts
└── tsconfig.json
```

veya eğer `iframe.ts` kullanıyorsanız:

```bash
presence
├── dist
│   └── metadata.json
├── presence.ts
├── iframe.ts
└── tsconfig.json
```

## [**metadata.json**](https://docs.premid.app/dev/presence/metadata)

> `metadata` dosyasınızın doğruluğunu kontrol ettirip geliştiricilere kolaylık sağlamak amacıyla sizlere bir şema sunuyoruz. Bu tamamen isteğe bağlıdır ve inceleme işlemi sırasında gerekli değildir.

> `metadata` dosyanızı burada gösterildiği şekilde organize etmeniz şiddetle tavsiye edilir. Bu dosyadaki servis isimleri, açıklamalar, etiketler ve ayarlar yazım kurallarına uygun olarak yazılmalıdır. Düzgün bir şekilde biçimlendirmemiş hiçbir şey kabul edilmeyecektir.

> Çıplaklık içeren sitelerin servisleri **mutlaka** `nsfw` etiketi içermelidir, ayrıca servisin resmi veya ekran görüntüsü bu içerikleri kesinlikle **barındırmamalıdır**.

Her servisin kendine ait açıklayıcı bir `metadata.json` dosyası vardır, bu dosya sistem tarafından okunarak ayarlar yapılır. Bu dosyanın bir örneği:

```json
{
  "$schema": "https://schemas.premid.app/metadata/1.5",
  "author": {
    "name": "USER",
    "id": "ID"
  },
  "contributors": [
    {
      "name": "USER",
      "id": "ID"
    }
  ],
  "service": "SERVICE",
  "altnames": ["SERVICE"],
  "description": {
    "en": "DESCRIPTION"
  },
  "url": "URL",
  "version": "VERSION",
  "logo": "URL",
  "thumbnail": "URL",
  "color": "#HEX000",
  "tags": ["TAG1", "TAG2"],
  "category": "CATEGORY",
  "regExp": "REGEXP",
  "iFrameRegExp": "REGEXP",
  "iframe": false,
  "readLogs": false,
  "settings": [
    {
      "id": "multiLanguage",
      "multiLanguage": true
    }
    {
      "id": "ID",
      "title": "DISPLAY TITLE",
      "icon": "FONTAWESOME ICON",
      "value": true
    },
    {
      "id": "ID",
      "if": {
        "ID": true
      },
      "title": "DISPLAY TITLE",
      "icon": "FONTAWESOME ICON",
      "value": "\"%song%\" by %artist%",
      "placeholder": "use %song% or %artist%"
    },
    {
      "id": "ID",
      "title": "DISPLAY TITLE",
      "icon": "FONTAWESOME ICON",
      "value": 0,
      "values": ["1", "2", "etc."]
    }
  ]
}
```

> If a field is listed as optional on the [documentation](https://docs.premid.app/dev/presence/metadata) or there is a `*` next to the key, and your presence uses the default value for it, do not include it in the `metadata` file. (örneğin, iframe kullanmayan servislerin `iframe` alanına sahip olmaması gerekir

> `metadata` dosyasında ki tüm görseller `i.imgur.com` da barındırılmak zorundadır. Sitenin kendisinde barındırılan resimlerin kullanımına **izin verilmemektedir**, çünkü bu resimler istemsiz de olsa bazen değişiklik gösterebilir.

Bazı alanlar ve alanların kuralları aşağıda belirtilmiştir.

### **`$schema`**

- Bu şema _anahtarı_, **mutlaka** başında dolar işareti barındırmalıdır. Bu işaret editörünüzün buradaki bağlantıyı kullanarak dosyayı doğrulamanızı sağlar. _Önceden de belirtildiği gibi, bir şema belirtmenize gerek olmasa da, belirttiğiniz takdirde bunu düşünmelisiniz._

### **`author`**

- Buradaki ID, Discord'daki kullanıcı ID'niz **olmalıdır**. ID'nizi öğrenmek için açmanız gerek geliştirici ayarlarını nasıl açacağınızı [buraya](https://support.discord.com/hc/en-us/articles/206346498-Where-can-I-find-my-User-Server-Message-ID-) tıklayarak öğrenebilirsiniz. _Lütfen bunu sadece servisiniz için kullanılacak olan uygulama ID'si ile **karıştırmayın**._

### **`*contributors`**

- Kendinizi bir katkı sağlayan kişi olarak eklemeyin, eğer servisi yapmanızda kimse yardımcı olmadıysa, bu alana kimseyi eklemeyin.

### **`service`**

- Servisin ismi, servisin içinde bulunduğu klasörle aynı isimde **olmalıdır**. Örneğin, eğer servisiniz `/website/Y/YouTube` yolunda bulunuyorsa, servisinizin ismi `YouTube` olmalıdır.
- Eğer site, adresini resmi ismi olarak kullanmıyorsa servis ismi olarak sitenin bağlantı adresini **kullanamazsınız**. Eğer isim tanımlayıcı değilse ve belirsiz sayılabilecek ise, bağlantı adresini kullanmak **gereklidir**. (örneğin, `youtube.com` kabul edilmez iken, `YouTube` kabul edilir çünkü bu resmi ve tanımlayıcı bir isimdir. `Top` tanımlayıcı bir isim olmadığından dolayı `top.gg` bağlantısını kullanmak **gereklidir**).
- Eğer servis, ismi konusunda özel kurallar gerektiriyorsa, onlara uyulmalıdır.

### **`*altnames`**

- Bunu **sadece** bir internet sitesinin resmi olarak birden fazla ismi olduğunda (örneğin, Pokémon ve 포켓몬스터) veya servis isminin içerisinde özel karekterlerin olduğu servislerde aramayı kolaylaştırmak için (örneğin, Pokémon ve Pokemon) kullanın. *Kısaltılmış* servis isimleri `tags` alanının altına yazılmalıdır.

### **`description`**

- **Tüm** servislerin, İngilizce açıklamaya sahip olması **zorunludur**, bu zorunluluk sitenin İngilizce destekleyip desteklememesiyle bağlantılı değildir.
- Bilmediğiniz bir dilde açıklama **eklemeyin**, çevirmenler, gerekli olduğu durumda sizin için sizin `metadata.json` dosyanıza gereken çevirileri ekleyecektir.

### **`url`**

- Adres, eğer internet sitesi tek bir alan adına sahipse string türünde olmalıdır. Eğer site birden fazla alan adı kullanıyorsa, bu veri, her birini belirttiğiniz bir array olmalıdır.
- Bu alanda HTTP protokollerini (örneğin, `http` veya `https`), parametreleri (örneğin,  `www.google.com/search?gws_rd=ssl` -bu değerin doğrusu `www.google.com` olacaktır) belirtmeyin.

### **`version`**

- Sürüm numaranızın her zaman [anlamsal sürümlendirme standartlarını](https://semver.org) takip ettiğine emin olun. Bu, sürüm isimlerinizi `<YENİ-ÖZELLİK>.<BÜYÜK-HATA-DÜZELTMESİ>.<KÜÇÜK-VE-METADATA-DÜZELTMELERİ>` şeklidir. Bunların dışında herhangi bir biçimlendirme (`1.0.0.1`, `1.0`, `1`, `1.0.0-BETA` vb.) ve ufak bir hata için sürüm numarasını `1.0.0`'dan `2.0.0`'a değiştirmeye izin verilmemektedir.
- Sürüm numarası ilk yayımda her zaman `1.0.0` olmalıdır, aksi belirtilmediği sürece bunu değiştirmek yasaktır.

### **`logo`**

- Logo, `1:1` en boy oranına sahip kare bir resim **olmalıdır**.
- Resim en az `512x512` piksel çözünürlüğünde olmalıdır. [waifu2x](http://waifu2x.udp.jp/) gibi araçlar kullanarak resminizi boyutlandırabilirsiniz.

### **`thumbnail`**

- Önizleme resmi (thumbnail), **tercihen** siteyi tanıtan bir afiş olmalıdır, bunun sağlanamadığı durumlarda [sitenin ekran görüntüsü](https://i.imgur.com/OAcBmwW.png) kullanılmalıdır.

### **`color`**

- Renk **mutlaka** hex değeri olmalıdır ve seçtiğiniz renk `#000000` ile `#FFFFFF` arasında olmalıdır.
- Bu alanın içine yazacağınız string, **mutlaka** hash işaretiyle (#) başlamalıdır.

### **`tags`**

- **Tüm** servisler en az _bir adet_ etikete sahip olmalıdır.
- Bu etiketlerde boşluk, taksim (/), tırnak işaretleri, unicode karakterleri gibi karakterler **bulundurmamalı** ve her zaman küçük harflerden oluşmalıdır.
- Etiketler, tercihen servis için alternatif isimler içermelidir. Bu sayede aramalarda çıkması daha kolaylaşır (örneğin, eğer YouTube servisi yapıyorsanız, etiketlerde `youtube` ve `video` etiketlerini belirtebilirsiniz)
- NSFW servisler için `NSFW` etiketi eklemeniz **gerekmektedir**.

### **`category`**

- The category **must** be one of the following listed on the [documentation](https://docs.premid.app/dev/presence/metadata#presence-categories).
- Servis, servisin sitesinin içeriğine uyan bir kategori kullanmalıdır. (örneğin, servisin sitesi anime ile alakalı değilse `anime` kullanamazsınız).

### **`*regExp`** <br /> **`*iFrameRegExp`**

- Regex verisi **mutlaka** geçerli olmalıdır. Please test your expressions with the tools listed on the [documentation](https://docs.premid.app/dev/presence/metadata#testing).

### **`readLogs`**

- Bir `boolean` değeri kullanmalıdır (örn. `true` ya da `false`).
- Servisiniz için kayıtları aktifleştirir.

### **`warning`**

- Sadece servisi eklemek yerine ek adımlar gerektiren servisler için bir uyarı işareti göstermeyi aktifleştirir.
- Bu seçeneği kullanan örnek bir servis: `VLC`

### **`settings`**

- Eğer bir format yazısı (örn. `%song% by %artist%`)eklemek istiyorsanız, bu değişkenleri yüzde işaretleri arasında yazmalısınız. `%var`, `var%` veya `%%var%%` gibi değişkenler bu işlemi standartlaştırmak adına yasaktır.
- Ayarların isimlerinin tamamı büyük harflerle **yazılmamalıdır**. Örneğin, `GÖZ ATMA BİLGİSİNİ GÖSTER` başlıklı ayara izin **verilmeyecektir**, fakat `Göz Atma Bilgisini Göster` veya `Göz atma bilgisini göster` başlıklarına izin verilecektir.
- Eğer `multiLanguage` ayarını kullanıyorsanız, bu ayarı şu türlerden biri olarak ayarlayabilirsiniz:
  - Sadece Localization deposundaki [`general.json`](https://github.com/PreMiD/Localization/blob/master/src/Presence/general.json) dosyası ve servis dosyasındaki çevirileri kullanmak için (örn. servisin ismi YouTube olduğunda eklenti otomatik olarak `youtube.json` dosyasını da alacaktır.)
  - Hangi dosyadaki çevirileri almak istediğinizi seçebileceğiniz **String** türü, (örn. `youtube`).
  - Hangi dosyalardaki çevirileri almak istediğinizi seçebileceğiniz **Array** türü, (örn. `["youtube", "discord"]`).

## [**presence.ts**](https://docs.premid.app/dev/presence/class)

> Kodunuz okunabilir ve anlaşılır **olmalıdır**, yazım hatalarına  dikkat etmeli ve kurallara uyulmalıdır. Sitede bulunan yazım hataları göz ardı edilebilir.

> Her servis, incelem sırasında kontrolden geçeceği sıkı tedbirlere tabi tutulur. Aşağıda birkaç öneri görülebilir. [TypeScript eklentisinin sıkı tip kontrolü için önerileri](https://github.com/typescript-eslint/typescript-eslint/tree/master/packages/eslint-plugin/docs/rules). [ESlint Önerileri](https://eslint.org/docs/rules). [Prettier](https://prettier.io/).

`presence.ts` dosyanızı yazarken izlemeniz gereken kuralların listesi:

- `Presence` sınıfının tanımını, nadir görülen hatalardan kurtulmak için, **her zaman** herhangi bir değişkenden önce belirtin; bu bir kural olmadığı için ileride bu listeden kaldırılabilir.
- [Eklentinin içerisinde bulunan fonksiyonlar](https://docs.premid.app/dev/presence#files-explained) ile yapabileceğiniz şeyi kendi fonksiyonlarınızı yazarak **yapmayın**; bu şekilde eklenti ile iletişimde sorun çekmezsiniz. Dokümanda görmediğiniz herhangi bir fonksiyonu kendiniz yazmakta özgürsünüz.
- Servislere, yapıldığı internet sitesinin ana dilinin eklenmemesi **yasaktır**, mesela YouTube'un Türkçe ve İspanyolca kodlanması ancak İngilizceyi desteklememesi gibi
- `smallImageKey` ve `smallImageText` alanları, ek/ikincil bilgiler koyabileceğiniz (oynatılıyor/durduruldu gibi) kısımlardır. Burada bir Discord hesabının reklamını yapamaz, PreMiD ile alakasız herhangi bir şey kullanamazsınız.
- `localStorage`'a erişmenize izin **verilmemektedir**.
- Çerezlerden bilgi alışverişi yaparken, çerezlerin başına her zaman `PMD_` ekini koyun.
- Sadece `premid.app` ve servisin sitesinin API'sine HTTP/HTTPS isteklerinde bulunabilirsiniz. Eğer farklı bir alan adına istek atıyorsanız, nedenini açıklamanız gerekir. API isteği yapmanın izin verilen tek yolu [`Fetch API`](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API) ile yapılan isteklerdir.
- presenceData object'inin içerisindeki kısımları ayarladıktan sonra undefined olarak **ayarlamayın**, bunun yerine `delete` yöntemini kullanın. (örneğin, `data.startTimestamp = undefined` yerine `delete data.startTimestamp` kullanın)
- Verilen bir sitenin işlevselliğini değiştirecek servisler yazmanıza izin **verilmez**. Bu DOM elementlerinin eklenmesi, silinmesi, ya da değiştirilmesini de kapsar.
- Presences that use buttons should follow extra requirements:
  - Ana sayfaya yönlendirmeler yasaktır.
  - Bu özelliği kullanarak site reklamları yapmak yasaktır.
  - Diğer bölümlerde ek bilgi göstermezken bunları ayarlamak mümkün değildir.
  - Direkt olarak ses/görüntü kaynağına yönlendirmek yasaktır.


## [**tsconfig.json**](https://docs.premid.app/dev/presence/tsconfig)

> Do **not** write your own `tsconfig.json` file, use what has been provided on [documentation](https://docs.premid.app/dev/presence/tsconfig).

## Yapılandırma

> **presence.ts**, **iframe.ts**  veya **metadata.json** dosyalarından herhangi birine değişiklik yaparken, **metadata** dosyanızda belirtilen sürüm numarasını, daha üst bir sayıya güncellemelisiniz.

Bazı durumlarda, servisler beklenmedik şekilde tepkiler verebileceği veya yazılan kodun daha iyi bir şekilde yazılabileceği durumlar olabilir. Aşağıdan **KESİNLİKLE** dikkat edilmesi gereken servis düzenleme kurallarını görebilirsiniz.

- Bir servisi baştan aşağıya yazmak ve yapımcısının adını değiştirme yetkisine sahip **değilsiniz**. Eğer servisin yapımcısı resmi sunucumuzdan yasaklanmış veya bir ay içerisinde herhangi bir değişiklik yapmadıysa, bir Gözden Geçiren ile iletişime geçip servis üzerinde değişiklik yapma talebinde bulunabilirsiniz.
- Eğer düzenleme yaptığınız servisin **çeyreğini** düzenlediyseniz, kendinizi o servise bir "katılımcı" olarak ekleyebilirsiniz. Bu konu hakkında daha detaylı bilgi alabilmek için bir inceleyici ile iletişime geçebilirsiniz.
- Herhangi biri hataları düzeltmek için düzeltme sağlayabilir; ancak gerekmeyen değişiklikleri yapmak için **yapmayın**. Geçerli değişiklikler arasında genel düzeltmeler (kod ve yazım hataları), eklemeler (açıklamalar ve etiketler), eksik dosyalar vb. yer alır. Resimler eğer geçerliliğini yitirmemiş veya kalitesi düşük değilse, değiştirmeyin.

# Onaylanma

> Katkıda bulunulan kodların **hepis** `Mozilla Public License 2.0` adı altında saklanacaktır.

> Eğer biriyle iletişime geçmek istiyorsanız, lütfen resmi Discord sunucumuzu kullanın. Tüm inceleyicilerin profilinde `Reviewer` rolü vardır.

> Lütfen inceleme ekibimizdeki üyelerin gönüllü olarak çalıştığını ve diğer işlerinin yanında bu işi yaptığını unutmayın, bu nedenle servis isteğiniz gönderildikten saatler, hatta belki günler sonra bile hâlâ onaylanma bekliyor olabilir.

> Bir pull request atmadan önce klon deponuzun güncel olduğuna **emin olun**. Bu, yanlış pozitiflerin denetlenmesini sınırlamaya yardımcı olacaktır.

Servis geliştirmenin en önemli aşamalarından biri servisinizi mağazaya ekletmektir. Bu, GitHub üzerinde bulunan `PreMiD/Presences` deposuna atacağınız bir [pull request](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/creating-a-pull-request) ile yapılır. Yorumcularımız, servisinin standartlara uygun olduğunu doğrulayacak ve mağazaya ekleyecektir.

<div>
  <h2 style="font-size: 2rem; margin-bottom: 0;">Servis İnceleyicileri</h2>

  <a href="https://github.com/Bas950"><img src="https://github.com/Bas950.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
  <a href="https://github.com/Slowlife01"><img src="https://github.com/Slowlife01.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
  <a href="https://github.com/EncryptedDev"><img src="https://github.com/EncryptedDev.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
  <br />
</div>

## `Kısıtlamalar`

Talimatları çiğneme, servis paylaşma işlemini durmadan tekrar etme, tehditler veya uygunsuz davranış gibi tekrarlayan aktivitelerde bulunmak sizi servis oluşturma sisteminden yasaklatacaktır.

Bu durumda, şu değişiklikler olur:

- Sizin yönetiminizde olan servisler PreMiD botuna veya (inceleyicinin kararına bağlı olarak) başka bir kullanıcıya devredilir. Tüm servisleriniz için oluşturulan uygulama ID'si yeni sahibinin adı altında tekrar oluşturulacak.
- Tüm hata bildirimleriniz ve servis paylaşımlarınız (servis oluşturma, başka bir servise katkıda bulunma vs.) kapatılacak ve geçersiz sayılacaktır.
- Sizin adınıza oluşturulmuş servis geliştiriciliği hakkındaki biletler silinecektir.

## `İnceleme`

Bir pull request atmadan önce bilmeniz gereken şeyler:

- Pull request'inizin onaylanması, ekipten 2 kişinin onayıyla gerçekleşir.
- Eğer bir pull request, 7 günden daha uzun bir süre boyunca inaktif olursa, otomatik olarak kapatılacaktır.
- Birleştirme için isteğinizin tüm isteklerden geçmesi **gereklidir**.
- ⚠️ İsteğinize, kendinizin çektiği, sitenin ve profilinizin yan yana gözüktüğü bir ekran görüntüsü ekleyerek servisinizin çalıştığını **kanıtlamalısınız**. Oluşturma ve düzenleme içinde de ekran görüntüleri belirtebilirsiniz.
- ⚠️ Eğer ayarlar özelliğini kullanıyorsanız, ayrıca buranın da bir ekran görüntüsünü atmanız **gereklidir**. [Buradan](https://imgur.com/a/OD3sj5R) bir örneğine ulaşabilirsiniz.

## `Kontroller`

![Örnek Kontroller](https://i.imgur.com/T8agbnB.png)

Şu anda, bir servis, 2 adet otomatik doğrulama aşamasından geçmektedir. Bu doğrulamalar, inceleme ekibimizin kodunuzun çalışmaya hazır olup olmadığını anlamasını kolaylaştırır.

- `Codacy` kod kalitesini kontrol eden bir otomattır. Hata almanız durumunda, aldığınız hatayı düzeltmekle **yükümlüsünüz**. *Warning: Codacy doesn't always give you errors. Lütfen bunun yerine CodeFactor uyarılarına bakın.*
- `CodeFactor` kod kalitesini kontrol eden bir otomattır. Hata almanız durumunda, aldığınız hatayı düzeltmekle **yükümlüsünüz**.
- `Schmea Validation` ise `metadata.json` dosyanızı tarayıp, hatalı veya eksik veriler olup olmadığını kontrol etmek için vardır. Eğer burada da bir hata ile karşılaşırsanız, o hatayı da **düzeltmelisiniz**. `metadata.json` dosyanıza bir şema değeri eklemek, kodlama sırasında (eğer destekliyorsa) editörünüzün size hatalarını belirtmesini sağlar.

## `Ek Kurallar`

- Servisiniz **her zaman** en uygun klasörde bulundurun. Servisinizin ismi bir Latin karakteriyle başlıyorsa, servisinizi o karaktere karşılık gereken klasörün içine koyun (örneğin, `D/dアニメストア` veya `G/Google`). Geriye kalan tüm unicode/Latin olmayan karakterler `#` klasörünün içine konulmalıdır (örneğin, `/#/巴哈姆特` gibi), numara ile başlayanlar ise `0-9` klasöründe olmalıdır (örneğin, `/0-9/4anime`).

Tüm yönergeleri uygun gözden geçirmeler ve kontrollerle karşıladıktan sonra, servisiniz mağazaya eklenecektir.

# Öneriler

Eğer kılavuzu geliştirebilmemiz için aklınızda bir öneri varsa, bize [PreMiD Discord sunucusundan](https://discord.premid.app) ulaşabilirsiniz.

# Katkılar

Kılavuzun `Revziyon 3` sürümü aşağıdaki şahıslar tarafından yazılmış ve katkıda bulunulmuştur:

<div>
<a href="https://github.com/ririxidev"><img src="https://github.com/ririxidev.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
</div>

Bu kılavuzun `Revizyon 2` sürümü aşağıdaki şahıslar tarafından hazırlanmıştır:

<div>
<a href="https://github.com/CobyPowers"><img src="https://github.com/CobyPowers.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
</div>

`Revizyon 1` ise aşağıdaki kişiler tarafından yönetilmiştir:

<div>
<a href="https://github.com/CobyPowers"><img src="https://github.com/CobyPowers.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
<a href="https://github.com/Bas950"><img src="https://github.com/Bas950.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
<a href="https://github.com/doomlerd"><img src="https://github.com/doomlerd.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
</div>
