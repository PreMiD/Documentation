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

> For the convenience of our presence developers, we have provided a schema which you can use to validate the integrity of your `metadata` file. See on täiesti vabatahtlik ja ei ole läbivaatamise käigus nõutav.

> Väga soovitatav on korraldada oma `metaandmed`-faili allpool näidatud kujul ning teil peavad olema grammatiliselt korrektsed teenuste nimed, kirjeldused, sildid ja seadistusväljad. Kõik, mis ei ole korraldatud vastavalt spetsifikatsioonile, **ei** ole lubatud.

> Presences of websites that have explicit content **must** have the `nsfw` tag, and the logo/thumbnail must **not** contain any of this content.

Each presence has a descriptor file called `metadata.json`, the metadata has a strict standard and an example of this file can be seem below:

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

> If a field is listed as optional on the [documentation](https://docs.premid.app/dev/presence/metadata) or there is a `*` next to the key, and your presence uses the default value for it, do not include it in the `metadata` file. (for e.g., a presence without iframe support would not need the `iframe` field.)

> Kõik `metaandmed` failis olevad pildid peavad olema majutatud aadressil `i.imgur.com`. Veebisaidil majutatud sisu kasutamine **ei** ole lubatud, kuna nad võivad tahtmatult muuta teekondi ja faile.

Allpool on loetletud väljad ja nende reeglid:

### **`$schema`**

- Skeemi _key_ alguses **peab** olema dollarimärk, see annab teie tekstiredaktorile märku, et soovite oma JSON-faili valideerida mudeli suhtes. _ Nagu varem öeldud, ei pea te skeemi lisama, kuid kui te seda lisate, peate sellega arvestama._

### **`author`**

- ID _väärtus_ **peab** olema teie Discord snowflake ID. Selle saate, kui lülitate sisse [arendajarežiimi](https://support.discord.com/hc/en-us/articles/206346498-Where-can-I-find-my-User-Server-Message-ID-). _Palun **ei** segi ajada seda teie appi ID-ga, mis on ainult teie Presence-i jaoks._

### **`*contributors`**

- **Ärge** lisage ennast kaastöötajaks ja ärge lisage kedagi teist kaastöötajaks, kui ta just ei ole aidanud Presence-it.

### **`service`**

- The service name **must** be the name of the presence directory. For example, if the presence is located at `/websites/Y/YouTube/`, the service name must be `YouTube`.
- Sa **ei saa** kasutada url-i teenuse nimena, välja arvatud juhul, kui veebisait kasutab url-i oma ametliku nimena. Kui nimi ei ole kirjeldav ja seda võib pidada ebamääraseks, on url kasutamine **nõutud**. (nt `YouTube` on lubatud, sest see on ametlik nimi ja kirjeldav, samas kui `youtube.com` ei ole. `Top` on mittekirjeldav nimi, nii et url `top.gg` kasutamine on **nõutud**)
- Kui teenusel on oma nime kohta mõned selgesõnalised brändireeglid, siis peaksite neid järgima.

### **`*altnames`**

- **Kasutage seda ainult** stsenaariumides, kus veebisait kannab mitut ametlikku nime (nt Pokémon ja 포켓몬스터). _Lühendatud_ versioonid teenuste nimedest lähevad `siltide` alla.

### **`description`**

- **All** presences are **required** to have an English description regardless of the website's prefered language.
- **Ärge** proovige kirjeldust ise tõlkida, kui te seda keelt ei oska, tõlkijad muudavad teie `metadata.json` ja muudavad vajaduse korral kirjeldusi.

### **`url`**

- Url ** peab** olema string, kui veebisait kasutab ainult ühte domeeni. Kui veebisait kasutab mitut, tehke sellest array ja täpsustage igaühele neist.
- **Ära** sisalda url-is protokolle (nt `http` või `https`) ja ära sisalda url-is päringuparameetreid (nt `www.google.com/search?gws_rd=ssl`, mis peaks olema `www.google.com`)

### **`version`**

- Veenduge alati, et versiooninumber järgib [semantilise versioonimise standardeid](https://semver.org), mis tähendab järgmist skeemi: `<MAJOR>.<MINOR>.<PATCH>`. Kõik muu nagu `1.0.0.0.1`, `1.0.0`, `1`, `1.0.0-BETA` või `1.0.0` muutmine `2.0.0` veaparanduse/väikese muudatuse puhul **ei** ole lubatud.
- Versioon **peab** alati algama `1.0.0`, kui ei ole öeldud teisiti, muud versioonid **ei** ole lubatud.

### **`logo`**

- Logo **peab** olema ruudukujuline, mille kuvasuhe on `1:1`.
- Pildi **vajalik** minimaalne resolutsioon `512x512` pikslit. Saate seda suurendada, kasutades sellist tööriista nagu [waifu2x](http://waifu2x.udp.jp/).

### **`thumbnail`**

- Thumbnail **peaks** eelistatavalt olema [laiaulatuslik reklaamkaart](https://i.imgur.com/3QfIc5v.jpg) või [ekraanipilt](https://i.imgur.com/OAcBmwW.png), kui esimene ei ole **saadaval**.

### **`color`**

- Värv **peab** olema heksadekaalväärtus vahemikus `#000000` ja `#FFFFFFFF`.
- Värvi string **peab** olema eelistatud hash-sümboliga.

### **`tags`**

- **All** presences are required to have at least _one_ tag.
- Sildid **ei** tohi sisaldada tühikuid, kaldkriipsu, ühe- või kahekohalisi jutumärke, Unicode-märke ja need peavad alati olema väikse tähega.
- Sildid **selleks** peaksid eelistatavalt sisaldama alternatiivseid teenuste nimesid, et hõlbustada otsingut (nt kui Amazoni kohalolek oleks hõlmanud AWS-i tuge, oleks selle sildid nagu `amazon-web-services` ja `aws`)
- Te olete **kohustatud** lisama `NSFW` sildi, kui tegemist on NSFW veebilehega.

### **`category`**

- Kategooria **peab** olema üks järgmistest, mis on loetletud [dokumentatsioonis](https://docs.premid.app/dev/presence/metadata#presence-categories).
- The presence must use a category that matches the content of the website. (for e.g., don't use `anime` when the website isn't related to anime).

### **`*regExp`** <br /> **`*iFrameRegExp`**

- Regular expressions **must** be valid. Please test your expressions with the tools listed on the [documentation](https://docs.premid.app/dev/presence/metadata#testing).

### **`readLogs`**

- Must be `boolean` value (e.g. `true` or `false`).
- Enables logs for your presence.

### **`warning`**

- Enables warning icon for prompting user that this presence needs more steps than only adding presence.
- Example of presence using this metadata variable is `VLC`.

### **`settings`**

- If you decide to make a format string (for e.g., `%song% by %artist%`), you must have the variables surrounded by a percent sign on either side. Variables like `%var`, `var%`, or `%%var%%` and anything in between are **not** permitted for the sake of standardization.
- The name of the settings must **not** be in all capital letters. For example, names such as `SHOW BROWSING STATUS` will **not** be permitted; however, names such as `Show Browsing Status` or `Show browsing status` are permitted.
- If you are using the `multiLanguage` option it can have the following types:
  - **Boolean** type which will only enable strings from [`general.json`](https://github.com/PreMiD/Localization/blob/master/src/Presence/general.json) from the Localization repo or from the presence file (e.g. when the name of the presence is YouTube, the extension will get strings from `youtube.json` too.)
  - **String** type (e.g. `youtube`) which will specify the name of the files that you want to get strings from.
  - **Array<String>** type (e.g. `["youtube", "discord"]`) which will specify the name of the files that you want to get strings from.

## [**presence.ts**](https://docs.premid.app/dev/presence/class)

> The code you write **must** be _well-written_ and **must** be _readable_ and all strings must be grammatically correct (grammar errors on websites can be ignored).

> Each presence follows a strict linting ruleset which will be checked during the review process. A couple of recommendations can be seen below. [TypeScript Plugin Recommendations for Strict Type Checking](https://github.com/typescript-eslint/typescript-eslint/tree/master/packages/eslint-plugin/docs/rules). [ESlint Recommendations](https://eslint.org/docs/rules). [Prettier](https://prettier.io/).

Here is a list of rules you must follow when writing your `presence.ts` file:

- **Always** declare a new instance of the `Presence` class before any other variable to avoid rare issues that may occur; this is not a requirement by design so it could be removed in the future.
- **Never** use custom functions when [native variants are available](https://docs.premid.app/dev/presence#files-explained); this makes sure fixes on the extension level also apply to your presences. You're free to use whatever you need if you do not find them listed in the docs.
- It is **forbidden** to code presences for a site without adding support to its primary language (for e.g., a YouTube presence coded with support only for Portueguese and Japanese, but not English itself.)
- The `smallImageKey` and `smallImageText` fields are intended to provide additional/secondary context (such as `playing/paused` for video sites, `browsing` for regular sites, and other cases) not to promote Discord profiles or anything unrelated to PreMiD.
- You are **not** allowed to access `localStorage`.
- When accessing cookies for stored data, please prefix the key with `PMD_`.
- You may only make HTTP/HTTPS requests to `premid.app` or the presence website API. If you are using external domains, you will be required to explain why it is necessary. Only allowed API to make request is [`Fetch API`](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API).
- Do **not** set fields in the presenceData object to undefined after it has been declared, use the `delete` keyword instead. (for e.g., use `delete data.startTimestamp` instead of `data.startTimestamp = undefined`)
- You are **not** allowed to write presences that change the functionality of a given website. This includes the addition, deletion, or modification of DOM elements.
- Presences that use buttons should follow extra requirements:
  - Redirects to main page are prohibited.
  - Promoting websites by them is prohibited.
  - They can't display information you couldn't fit in other fields.
  - Redirecting directly to audio/video stream is prohibited.


## [**tsconfig.json**](https://docs.premid.app/dev/presence/tsconfig)

> Do **not** write your own `tsconfig.json` file, use what has been provided on [documentation](https://docs.premid.app/dev/presence/tsconfig).

## Muudatused

> You **must** change the version in the **metadata** to be a higher value from the previous version when making changes to either the **presence.ts**, **iframe.ts** or **metadata.json**.

In some situations, presences may behave unexpectedly or could use some minor changes to improve their functionality. Here is a list of rules that you **must** follow while modifiying presences.

- If the presence author hasn't been contactable in over a month, you may contact a reviewer to see if you can modify the presence.
- If you make modifications to a presence and change at least a **quarter** of the presence's codebase, you are allowed to add yourself as a contributor. Contact a reviewer for more information about this subject.
- Anyone may create PRs to fix bugs. Do **not** change images if they are not outdated and are in specifications.

# Kontrollimine

> **All** code contributed to the store will be licensed under the `Mozilla Public License 2.0`.

> If you need to contact someone, please use our official Discord server. All reviewers will have the `Reviewer` role on their profile.

> Please keep in mind that the reviewers work voluntarily and manage other repositories in addition to this one, your pull request may not get reviewed until hours or even days after it has been created.

> **Always** have an up-to-date fork before creating your pull request. This will help limit false positives from the checks.

The most important process of presence development is getting your presence on the store. This is done by making a [pull request](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/creating-a-pull-request) on GitHub on the `PreMiD/Presences` repository. Our reviewers will confirm that your presence is up to standards and will push it onto the store.

<div>
  <h2 style="font-size: 2rem; margin-bottom: 0;">Presence-i ülevaatajad</h2>
  <a href="https://github.com/Bas950"><img src="https://github.com/Bas950.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
  <a href="https://github.com/EncryptedDev"><img src="https://github.com/EncryptedDev.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
</div>

## `Piirangud`

Repetitive offenses such as breaking guidelines, spamming pull requests, threats, or innapropriate behavior will get you banned from creating presences.

In this scenario, the following changes will occur:

- Presences under your management will be transferred to the PreMiD bot or another user (reviewer decision). The application id for each presence will be recreated under the new owner's name.
- All of your issues and pull requests (presence creation, presence contribution, etc) created following the ban will be prompty closed.
- Tickets created under your name regarding presence development will be deleted.

## `Ülevaatamine`

A few things you should know after opening a pull request:

- It takes 2 reviewers to merge a pull request.
- If a pull request is inactive for a period of 7 days, it will be promptly closed.
- All checks **must** be passed in order to merge.
- ⚠️ You **must** provide new, unaltered screenshots (taken by you) showing a side-by-side comparison of your profile and the website to prove that your presence works. _You are allowed to stitch screenshots together for viewing pleasure_ This applies for both creation and modification.
- ⚠️ You are also **required** to include screenshots of the presence settings in the extension if supplied. An example can be seen [here](https://imgur.com/a/OD3sj5R).

## `Kontrollid`

![Näide kontrollide kohta](https://i.imgur.com/vF7QpBH.png)

Currently, a presence goes through 3 separate stages of checks. All of these checks help the reviewers determine whether your presence is suitable for deployment.

- `DeepScan` is a bot that checks for code quality. If you ever receive errors for new issues, you are **required** to fix them. *Warning: DeepScan doesn't always give you errors. Please look at CodeFactor warnings instead.*
- `CodeFactor` is a bot that checks for code quality. If you ever receive errors for new issues, you are **required** to fix them.
- `Schema Validation` will scan your `metadata.json` file for any errors (for e.g., missing fields, invalid value types, etc.). If you ever see any new issues, you are also **required** to fix those. Adding a schema field to your `metadata.json` file will allow your text editor (if supported) to show you these errors during development.

## `Lisareeglid`

- **Alati** veenduge, et alustate oma presence-i kõige sobivamas kaustas, kui selle nimi algab _mis tahes_ ladina tähega, siis see peab olema tähestikulise vaste all (nt `D/d ア ニ メ ス ト ア ` või `G/Google `). Kõik muud Unicode'i/ladina tähemärgid **peavad** asuma kausta `#` all (nt `#/巴哈姆特 `) ja numbrid `0-9` numbri kausta (nt `0-9/4anime`).

After meeting all of the guidelines with the proper reviews and checks, your presence will be merged with the store.

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
