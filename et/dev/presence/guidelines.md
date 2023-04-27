---
title: Presence-i Juhised
description: Reeglid, mida kõik presence-i arendajad peavad järgima, et nende presence lisataks.
published: true
date: 2021-12-20T14:27:18.034Z
tags:
editor: markdown
dateCreated: 2021-09-07T01:44:53.883Z
---

<div align="center">
    <img src="https://github.com/PreMiD.png?size=2048" width="128px" style="max-width:100%;">
    <h3 style="font-size: 2rem; margin-bottom: 0">Presence-i Juhised</h3>
    <h4 style="margin-top: 0">3. redaktsioon</h4>
    <br />
</div>

# Juhised

Presence-i avaldamisel [Presence-ite repositooriumis](https://github.com/PreMiD/Presences/) nõuame, et järgiksite teatavaid suuniseid. Mõne jaoks võivad need ranged reeglid tunduda karmid. Nende reeglistike rakendamine hoiab meid ja kasutajaid probleemide tekkimisest.

# Loomine

Presence-i arendamise üldreeglid on järgmised:

- Presence-id **peavad** olema seotud valitud veebisaidiga.
- Ebaseaduslikele veebisaitidele **ei tohi ** teha Presence. (nt stressorid, uimastiturundus, lapsporno jne)
- Failistruktuur peab olema puhas ja haldatud, mitte sisaldama faile, mida pole täpsustatud. (nt vscode ja git kaustade, pildi- ja tekstifailide jms jaoks)
- Teil peab olema korralik failistruktuur, mustandid **pole **lubatud.
- Veebilehed Presence-itele, millel on (`.onion` tippdomeenid) või tasuta domeenid/hostid (nt `.TK` [kõik tasuta Freenomi domeenid], `.RF`, `GD` jne) **ei** ole lubatud, erandeid võib teha, kui esitatakse tõend, et domeeni eest on makstud.
- Presence-i domeen peab olema vähemalt 2 kuud vana.
- Presence-id, mis on suunatud brauseri siselehekülgedele (nagu Chrome Web Store, `chrome://`, `about:` leheküljed jne), **ei** ole lubatud, kuna need nõuavad kasutaja poolt eksperimentaalse lipu lubamist ja võivad potentsiaalselt põhjustada nende brauserite kahjustamist.
- Presence-id, mis toetavad ainult ühte alamdomeeni, **ei** ole lubatud, kuna need võivad tunduda teiste lehekülgede (näiteks kodulehe) jaoks katkised, erandeid võib teha poliitika- ja kontaktlehtede puhul (sisu, mida ei kasutata sageli) või saitide puhul, kus muu sisu ei ole seotud. (nt vikilehed)
- Veebiraadio Presence-id on lubatud ainult siis, kui raadiol on vähemalt 100 kuulajat nädalas ja 15 samaaegset kuulajat ning tal peavad olema muud funktsioonid kui lihtsalt albumi/laulu pealkirja näitamine jne.
- Presence-id ei tohi käivitada JS-koodi oma funktsiooniga, et saada muutujaid. Kui Firefoxil on probleeme sisseehitatud funktsiooniga `Presence` klassis, siis on teil lubatud teha oma funktsioon ja te peate sellest meile Pull Requesti kirjelduses rääkima.
- Madala kvaliteediga (või vähese kontekstiga) Presence-id **ei** ole lubatud (nt ainult logo ja teksti näitamine, kuid mitte selle muutmine).
- Selliste teenuste nagu Discord Bot/Server Lists Presence-id peavad järgima neid lisanõudeid:
  - Domeen peaks olema vähemalt **6 kuud** vana.
  - Unikaalsed külastajad päevas:
    - 6 kuud vanade domeenide puhul: **20 000 unikaalset külastajat päevas**.
    - Üle 12 kuu vanuste domeenide puhul: **45 000 unikaalset külastajat päevas**.
  - Veebisait ei tohi olla odavas domeenis, näiteks `.xyz`, `.club` ja nii edasi.
  - Veebileht ise peab olema väga hea kvaliteediga, kujundusega, jne.
- Presence-id peaksid kasutama [Üldised andmeid](https://api.premid.app/v2/langFile/presence/en) (stringid, mis algavad sõnaga "general."). Selle saate saavutada, kasutades `multiLanguage`-it koos antud stringidega. Kui teie Presences nõuab kohandatud stringi, siis ei tohiks te kasutada `multiLanguage` enne, kui Presence saab 1000 kasutajat. Näidise [leiate siit](https://docs.premid.app/dev/presence/class#getstringsobject).
- Kausta `dist`, faili `presence.ts`,faili `iframe.ts` ja `metadata.json` kaasamine on kohustuslik, nii et tulemus oleks järgmine skeem:

```bash
presence
├── dist
│   └── metadata.json
├── presence.ts
└── tsconfig.json
```

või kui kasutate faili `iframe.ts`:

```bash
presence
├── dist
│   └── metadata.json
├── presence.ts
├── iframe.ts
└── tsconfig.json
```

## [**metadata.json**](https://docs.premid.app/dev/presence/metadata)

> Meie presence-i arendajate mugavuse huvides oleme esitanud skeemi, mida saate kasutada oma `metaandmete` faili terviklikkuse kontrollimiseks. See on täiesti vabatahtlik ja ei ole läbivaatamise käigus nõutav.

> Väga soovitatav on korraldada oma `metaandmed`-faili allpool näidatud kujul ning teil peavad olema grammatiliselt korrektsed teenuste nimed, kirjeldused, sildid ja seadistusväljad. Kõik, mis ei ole korraldatud vastavalt spetsifikatsioonile, **ei** ole lubatud.

> Presence-i veebisaitidel, millel on Nsfw sisu **peab** olema `nsfw` silt ja logo/mõõdupilt **ei** tohi sisaldada sellist sisu.

Igal presence-il on kirjeldusfail nimega `metadata.json`, metaandmed on rangelt standarditud ja selle faili näide on allpool:

```json
{
  "$schema": "https://schemas.premid.app/metadata/1.7",
  "author": {
    "name": "KASUTAJA",
    "id": "ID"
  },
  "contributors": [
    {
      "name": "KASUTAJA",
      "id": "ID"
    }
  ],
  "service": "TEENUS",
  "altnames": ["TEENUS"],
  "description": {
    "en": "KIRJELDUS"
  },
  "url": "URL",
  "version": "VERSIOON",
  "logo": "URL",
  "thumbnail": "URL",
  "color": "#HEX000",
  "tags": ["TAG1", "TAG2"],
  "category": "KATEGOORIA",
  "regExp": "REGEXP",
  "iFrameRegExp": "REGEXP",
  "iframe": false,
  "readLogs": false,
  "settings": [
   {
      "id": "multiLanguage",
      "multiLanguage": true
    },
    {
      "id": "ID",
      "title": "KUVA PEALKIRI",
      "icon": "FONTAWESOME IKOON",
      "value": true
    },
    {
      "id": "ID",
      "if": {
        "ID": true
      },
      "title": "KUVA PEALKIRI",
      "icon": "FONTAWESOME IKOON",
      "value": "\"%song%\" by %artist%",
      "placeholder": "use %song% or %artist%"
    },
    {
      "id": "ID",
      "title": "KUVA PEALKIRI",
      "icon": "FONTAWESOME IKOON",
      "value": 0,
      "values": ["1", "2", "etc."]
    }
  ]
}
```

> Kui väli on [dokumentatsioonis](https://docs.premid.app/dev/presence/metadata) loetletud valikulisena või kui võtme kõrval on `*` ja teie presence kasutab selle jaoks vaikeväärtust, ärge lisage seda `metaandmed` faili. (näiteks presence ilma iframe'i toeta ei vaja `iframe` välja)

> Kõik `metaandmed` failis olevad pildid peavad olema majutatud aadressil `i.imgur.com`. Veebisaidil majutatud sisu kasutamine **ei** ole lubatud, kuna nad võivad tahtmatult muuta teekondi ja faile.

Allpool on loetletud väljad ja nende reeglid:

### **`$schema`**

- Skeemi _key_ alguses **peab** olema dollarimärk, see annab teie tekstiredaktorile märku, et soovite oma JSON-faili valideerida mudeli suhtes. _ Nagu varem öeldud, ei pea te skeemi lisama, kuid kui te seda lisate, peate sellega arvestama._

### **`author`**

- ID _väärtus_ **peab** olema teie Discord snowflake ID. Selle saate, kui lülitate sisse [arendajarežiimi](https://support.discord.com/hc/en-us/articles/206346498-Where-can-I-find-my-User-Server-Message-ID-). _Palun **ei** segi ajada seda teie appi ID-ga, mis on ainult teie Presence-i jaoks._

### **`*contributors`**

- **Ärge** lisage ennast kaastöötajaks ja ärge lisage kedagi teist kaastöötajaks, kui ta just ei ole aidanud Presence-it.

### **`service`**

- Teenuse nimi **peab** olema presence-i kataloogi nimi. Näiteks kui presence asub aadressil `/websites/Y/YouTube/`, peab teenuse nimi olema `YouTube`.
- Sa **ei saa** kasutada url-i teenuse nimena, välja arvatud juhul, kui veebisait kasutab url-i oma ametliku nimena. Kui nimi ei ole kirjeldav ja seda võib pidada ebamääraseks, on url kasutamine **nõutud**. (nt `YouTube` on lubatud, sest see on ametlik nimi ja kirjeldav, samas kui `youtube.com` ei ole. `Top` on mittekirjeldav nimi, nii et url `top.gg` kasutamine on **nõutud**)
- Kui teenusel on oma nime kohta mõned selgesõnalised brändireeglid, siis peaksite neid järgima.

### **`*altnames`**

- **Kasutage seda ainult** stsenaariumides, kus veebisait kannab mitut ametlikku nime (nt Pokémon ja 포켓몬스터). _Lühendatud_ versioonid teenuste nimedest lähevad `siltide` alla.

### **`description`**

- **Kõikidel** presence-itel **peab** olema ingliskeelne kirjeldus, sõltumata veebilehe eelistatud keelest.
- **Ärge** proovige kirjeldust ise tõlkida, kui te seda keelt ei oska, tõlkijad muudavad teie `metadata.json` ja muudavad vajaduse korral kirjeldusi.

### **`url`**

- Url ** peab** olema string, kui veebisait kasutab ainult ühte domeeni. Kui veebisait kasutab mitut, tehke sellest array ja täpsustage igaühele neist.
- **Ära** sisalda url-is protokolle (nt `http` või `https`) ja ära sisalda url-is päringuparameetreid (nt `www.google.com/search?gws_rd=ssl`, mis peaks olema `www.google.com`)

### **`version`**

- Veenduge alati, et versiooninumber järgib [semantilise versioonimise standardeid](https://semver.org), mis tähendab järgmist skeemi: `<MAJOR>.<MINOR>.<PATCH>`. Kõik muu nagu `1.0.0.0.1`, `1.0.0`, `1`, `1.0.0-BETA` või `1.0.0` muutmine `2.0.0` veaparanduse/väikese muudatuse puhul **ei** ole lubatud.
- Versioon **peab** alati algama `1.0.0`, kui ei ole öeldud teisiti, muud versioonid **ei** ole lubatud.

### **`logo`**

- Logo **peab** olema ruudukujuline, mille kuvasuhe on `1:1`.
- The image is **required** to have a resolution of `512x512` pixels. You can resize it using a tool like [imageresizer](https://imageresizer.com/).

### **`thumbnail`**

- Thumbnail **peaks** eelistatavalt olema [laiaulatuslik reklaamkaart](https://i.imgur.com/3QfIc5v.jpg) või [ekraanipilt](https://i.imgur.com/OAcBmwW.png), kui esimene ei ole **saadaval**.

### **`color`**

- Värv **peab** olema heksadekaalväärtus vahemikus `#000000` ja `#FFFFFFFF`.
- Värvi string **peab** olema eelistatud hash-sümboliga.

### **`tags`**

- **Kõikidel** presence-itel peab olema vähemalt _üks_ silt.
- Sildid **ei** tohi sisaldada tühikuid, kaldkriipsu, ühe- või kahekohalisi jutumärke, Unicode-märke ja need peavad alati olema väikse tähega.
- Sildid **selleks** peaksid eelistatavalt sisaldama alternatiivseid teenuste nimesid, et hõlbustada otsingut (nt kui Amazoni kohalolek oleks hõlmanud AWS-i tuge, oleks selle sildid nagu `amazon-web-services` ja `aws`)
- Te olete **kohustatud** lisama `NSFW` sildi, kui tegemist on NSFW veebilehega.

### **`category`**

- Kategooria **peab** olema üks järgmistest, mis on loetletud [dokumentatsioonis](https://docs.premid.app/dev/presence/metadata#presence-categories).
- Presence peab kasutama veebisaidi sisule vastavat kategooriat. (näiteks ärge kasutage `anime`, kui veebisait ei ole seotud anime'ga).

### **`*regExp`** <br /> **`*iFrameRegExp`**

- Regulaaravaldised **peavad** olema kehtivad. Palun testige oma väljendeid [dokumentatsioonis](https://docs.premid.app/dev/presence/metadata#testing) loetletud vahenditega.

### **`readLogs`**

- Peab olema `boolean` väärtus (nt `true` või `false`).
- Võimaldab teie Presence-i logid.

### **`warning`**

- Võimaldab hoiatussümboli, mis hoiatab kasutajat, et see presence vajab rohkem samme kui ainult presence-i lisamine.
- Näide selle metaandmete muutuja kasutamise kohta on `VLC`.

### **`settings`**

- Kui te otsustate teha vormingustringi (näiteks `%song% by %artist%`), siis peavad muutujad olema mõlemal pool protsentimärgiga ümbritsetud. Muutujad nagu `%var`, `var%` või `%%var%%%` ja kõik, mis jääb nende vahele, **ei** ole standardiseerimise huvides lubatud.
- Seadete nimi **ei** tohi olla suurtähtedega. Näiteks **ei** ole lubatud sellised nimed nagu `SHOW BROWSING STATUS`; aga sellised nimed nagu `Show Browsing Status` või `Show browsing status` on lubatud.
- Kui kasutate `multiLanguage` valikut, võib see olla järgmist tüüpi:
  - **Boolean** tüüpi, mis võimaldab ainult stringid [`general.json`](https://github.com/PreMiD/Localization/blob/master/src/Presence/general.json) lokaliseerimisrepostist või presence-i failist (nt kui presence-i nimi on YouTube, saab laiendus stringid ka `youtube.json`-st)
  - **String** tüüpi (nt `youtube`), mis määrab failide nimed, millest soovite saada stringid.
  - **Array<String>** tüüpi (nt `["youtube", "discord"]`), mis määrab failide nimed, millest soovite saada stringid.

## [**presence.ts**](https://docs.premid.app/dev/presence/class)

> Kirjutatud kood **peab** olema _hästi kirjutatud_ ja **peab** olema _loetav_ ning kõik stringid peavad olema grammatiliselt korrektsed (grammatilisi vigu veebilehtedel võib ignoreerida).

> Iga presence järgib ranget lintingu reeglistikku, mida kontrollitakse läbivaatamise käigus. Allpool on esitatud mõned soovitused. [TypeScript Plugin Recommendations for Strict Type Checking](https://github.com/typescript-eslint/typescript-eslint/tree/master/packages/eslint-plugin/docs/rules). [ESlint Recommendations](https://eslint.org/docs/rules). [Prettier](https://prettier.io/).

Siin on nimekiri reeglitest, mida peate oma `presence.ts` faili kirjutamisel järgima:

- **Alguses** deklareerige alati klassi `Presence` uus eksemplar enne mis tahes muud muutujat, et vältida harva esinevaid probleeme; see ei ole kavandatud nõue, seega võib selle tulevikus eemaldada.
- **Mitte kunagi** kasuta kohandatud funktsioone, kui [natiivsed variandid on saadaval](https://docs.premid.app/dev/presence#files-explained); see tagab, et parandused laiendustasandil kehtivad ka sinu presence-itele. Te võite vabalt kasutada mida iganes te vajate, kui te ei leia neid dokumentides loetletud.
- On **keelatud** kodeerida veebilehe presence-i, lisamata toetust selle põhikeelele (nt YouTube'i presence, mis on kodeeritud ainult portugali ja jaapani keele toetusega, kuid mitte inglise keele toetusega)
- Väljad `smallImageKey` ja `smallImageText` on mõeldud täiendava/sekundaarse konteksti pakkumiseks (näiteks `playing/paused` videosaitide puhul, `browsing` tavaliste saitide puhul ja muudel juhtudel), mitte Discord-profiilide või muu PreMiDiga mitteseotud asja reklaamimiseks.
- Teil **ei** ole lubatud juurdepääs `localStorage-ile`.
- Salvestatud andmete küpsistele juurdepääsul, palun kirjutage võtme ette `PMD_`.
- Saate teha HTTP/HTTPS päringuid ainult `premid.app` või presence-i veebisaidi API-le. Kui kasutate väliseid domeene, peate selgitama, miks see on vajalik. Ainus lubatud API, mille kaudu saab esitada päringu, on [`Fetch API`](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API).
- **Ärge** määrake presenceData objekti väljasid pärast selle deklareerimist määratlemata olekusse, kasutage selle asemel võtmesõna `delete`. (nt kasuta `delete data.startTimestamp` asemel `data.startTimestamp = undefined`)
- Sul on **ei** lubatud kirjutada presence, mis muudavad antud veebilehe funktsionaalsust. See hõlmab DOM-elementide lisamist, kustutamist või muutmist.
- Nuppe kasutavate presence-ite puhul tuleks järgida lisanõudeid:
  - Ümbersuunamised pealehele on keelatud.
  - Veebisaitide reklaamimine nende poolt on keelatud.
  - Nad ei saa kuvada teavet, mida te ei saanud mahutada teistesse väljadesse.
  - Otsene suunamine audio/video voogedastusele on keelatud.


## [**tsconfig.json**](https://docs.premid.app/dev/presence/tsconfig)

> **Ärge** kirjutage oma `tsconfig.json` faili, kasutage seda, mis on esitatud [dokumentatsioonis](https://docs.premid.app/dev/presence/tsconfig).

## Muudatused

> Sa **peab** muutma versiooni **metadata** eelmisest versioonist suuremaks, kui teed muudatusi kas **presence.ts**, **iframe.ts** või **metadata.json**.

Mõnes olukorras võivad presence-id käituda ootamatult või vajaksid mõningaid väiksemaid muudatusi, et parandada nende funktsionaalsust. Siin on nimekiri reeglitest, mida **peate</strong x> presence-i muutmisel järgima.</p>

- Kui presence-i autoriga ei ole üle kuu aja ühendust võetud, võite võtta ühendust ülevaatajaga, et vaadata, kas saate presence-it muuta.
- Kui te muudate presence-it ja muudate vähemalt **veerandi** presence-i koodibaasi, on teil lubatud lisada end kaastöötajaks. Lisateabe saamiseks võtke ühendust ülevaatajaga.
- Igaüks võib luua PR-e vigade parandamiseks. **Ära** muuda pilte, kui need ei ole vananenud ja on spetsifikatsioonides.

# Kontrollimine

> **Kõik** kauplusesse lisatud kood on litsentsitud `Mozilla Public License 2.0` alusel.

> Kui sul on vaja kellegagi ühendust võtta, kasuta palun meie ametlikku Discord-serverit. Kõigi retsensentide profiilil on roll `Reviewer`.

> Pidage meeles, et retsensendid töötavad vabatahtlikult ja haldavad lisaks sellele ka teisi repositooriume, mistõttu teie pull-päring võib saada läbi vaadatud alles tundide või isegi päevade pärast selle loomist.

> **Alati** enne oma tõmbetaotluse loomist veenduge, et on olemas ajakohane fork. See aitab piirata kontrollide valepositiivseid tulemusi.

Kõige tähtsam protsess presence-i arendamisel on teie presence-i poes avaldamine. Selleks tuleb teha [pull request](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/creating-a-pull-request) GitHubis `PreMiD/Presences` repositooriumis. Meie ülevaatajad kinnitavad, et teie presence vastab standarditele, ja toovad selle poodi.

<div>
  <h2 style="font-size: 2rem; margin-bottom: 0;">Presence-i ülevaatajad</h2>
  <a href="https://github.com/Bas950"><img src="https://github.com/Bas950.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
  <a href="https://github.com/EncryptedDev"><img src="https://github.com/EncryptedDev.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
</div>

## `Piirangud`

Korduvad rikkumised, nagu suuniste rikkumine, tõmbepäringute spämmimine, ähvardused või ebasobiv käitumine keelavad teil presence-ite loomise.

Selle stsenaariumi puhul toimuvad järgmised muudatused:

- Teie hallatavad presence-id kantakse üle PreMiDi boti või mõne teise kasutaja kätte (retsensendi otsus). Taotluse id iga presence-i jaoks luuakse uuesti uue omaniku nime all.
- Kõik teie probleemid ja tõmbepäringud (presence-i loomine, presence-isse panustamine jne), mis on loodud pärast keelustamist, suletakse kohe.
- Teie nime all loodud piletid, mis on seotud presence-i arendamisega, kustutatakse.

## `Ülevaatamine`

Mõned asjad, mida peaksite teadma pärast tõmbetaotluse avamist:

- Pull-päringu ühendamiseks on vaja 2 ülevaatajat.
- Kui tõmbetaotlus on 7 päeva mitteaktiivne, suletakse see kohe.
- Kõik kontrollid **peavad** olema läbitud, et ühendada.
- ⚠️ Sa **pead** esitama uued, muutmata ekraanipildid (sinu poolt tehtud), mis näitavad kõrvuti oma profiili ja veebilehe võrdlust, et tõestada, et sinu presence toimib. _Sulle on lubatud ekraanipilte vaatamisrõõmuks kokku kleepida_ See kehtib nii loomise kui ka muutmise kohta.
- ⚠️ Samuti on **vajalik** lisada ekraanipilte presence-i seadetest laienduses, kui need on esitatud. Üks näide on näha [siin](https://imgur.com/a/OD3sj5R).

## `Kontrollid`

![Näide kontrollide kohta](https://i.imgur.com/vF7QpBH.png)

Praegu läbib presence 3 eraldi kontrollietappi. Kõik need kontrollid aitavad hindajatel kindlaks teha, kas teie presence on kasutuselevõtuks sobiv.

- `DeepScan` on robot, mis kontrollib koodi kvaliteeti. Kui te saate kunagi vigu uute küsimuste kohta, olete **kohustatud** neid parandama. *Hoiatus: DeepScan ei anna alati vigu. Palun vaadake hoopis CodeFactori hoiatusi.*
- `CodeFactor` on robot, mis kontrollib koodi kvaliteeti. Kui te saate kunagi vigu uute küsimuste kohta, olete **kohustatud** neid parandama.
- `Schema Validation` skaneerib teie `metadata.json` faili vigade (nt puuduvad väljad, vigased väärtustüübid jne) suhtes. Kui te näete kunagi uusi probleeme, siis olete ka **kohustatud** neid parandada. Skeemivälja lisamine faili `metadata.json` võimaldab teie tekstiredaktoril (kui see on toetatud) näidata teile neid vigu arenduse ajal.

## `Lisareeglid`

- **Alati** veenduge, et alustate oma presence-i kõige sobivamas kaustas, kui selle nimi algab _mis tahes_ ladina tähega, siis see peab olema tähestikulise vaste all (nt `D/d ア ニ メ ス ト ア ` või `G/Google `). Kõik muud Unicode'i/ladina tähemärgid **peavad** asuma kausta `#` all (nt `#/巴哈姆特 `) ja numbrid `0-9` numbri kausta (nt `0-9/4anime`).

Pärast kõigi juhiste nõuetekohaste ülevaatuste ja kontrollide täitmist liidetakse teie presence kauplusega.

# Soovitused

Kui teil on meie juhiste kohta soovitusi, võtke meiega ühendust @ [PreMiD-i discordi serveris](https://discord.premid.app) ja me vaatame need üle!

# Kaasaaitamised

Juhiste `3. redaktsiooni` on kirjutatud ja sellele aitasid kaasa järgmised isikud:

<div>
<a href="https://github.com/PreMiD"><img src="https://github.com/PreMiD.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
</div>

Juhiste `2. redaktsiooni` on kirjutatud ja sellele aitasid kaasa järgmised isikud:

<div>
<a href="https://github.com/CobyPowers"><img src="https://github.com/CobyPowers.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
</div>

Juhiste `1. redaktsiooni` hooldasid järgmised isikud:

<div>
<a href="https://github.com/CobyPowers"><img src="https://github.com/CobyPowers.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
<a href="https://github.com/Bas950"><img src="https://github.com/Bas950.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
<a href="https://github.com/i1u5"><img src="https://github.com/i1u5.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
</div>
