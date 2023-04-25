---
title: Wytyczne dotyczące presence
description: Reguły, których muszą przestrzegać wszyscy twórcy Presence, aby ich Presence zostały zaakceptowane.
published: true
date: 2021-12-20T14:27:18.034Z
tags:
editor: markdown
dateCreated: 2021-09-07T01:44:53.883Z
---

<div align="center">
    <img src="https://github.com/PreMiD.png?size=2048" width="128px" style="max-width:100%;">
    <h3 style="font-size: 2rem; margin-bottom: 0">Wytyczne dotyczące presence</h3>
    <h4 style="margin-top: 0">Wersja 3</h4>
    <br />
</div>

# Wytyczne

Podczas publikowania Presences do [naszego repozytorium GitHub](https://github.com/PreMiD/Presences), wymagamy od Ciebie przestrzegania zbioru wytycznych. Dla niektórych te ścisłe zasady mogą wydawać się surowe. Jednak wdrożenie tych zestawów reguł powstrzyma nas i użytkowników od problemów.

# Tworzenie

Ogólne zasady rozwijania statusów są następujące:

- Statusy **muszą** być powiązane z wybraną witryną.
- Statusy **nie mogą** być tworzone dla nielegalnych stron internetowych. (np. stresory, handel narkotykami, dziecięca pornografia, itp.)
- Struktura plików musi być czysta i uporządkowana, nie powinna zawierać plików, które nie są wymagane. (np. foldery vscode i git, pliki graficzne i tekstowe itp.)
- Musisz mieć odpowiednią strukturę plików, wersje robocze **są niedozwolone**.
- Statusy dla stron z ((`.onion` TLD)) lub stron z darmowymi domenami/hostami (np. `.TK` [wszystkie bezpłatne domeny Freenom], `.RF`, `.GD`, itp.) są **niedozwolone**, można zrobić wyjątek, jeśli zostanie przedstawiony dowód, że zapłacono za domenę.
- Domena musi mieć conajmniej 2 miesiące.
- Status kierowane na wewnętrzne strony przeglądarki (takie jak Chrome Web Store, `chrome://`, strony `about:`, itp.) **są niedozwolone**, ponieważ wymagają włączenia eksperymentalnej flagi po stronie użytkowników i mogą potencjalnie spowodować uszkodzenie ich przeglądarki.
- Statusy wspierające tylko jedną sub-domenę **są niedozwolone** ponieważ mogą nie działać na innych stronach (takich jak strona główna), wyjątek mogą stanowić strony kontaktowe lub z polityką prywatności (czyli takie które nie są często używae) lub strony gdzie inna zawartość jest niezwiązana z sub-domeną. (np. strony wiki)
- Obecności dla radia internetowego są dozwolone tylko wtedy, gdy radio ma co najmniej 100 słuchaczy tygodniowych i 15 na raz i musi mieć jakieś funkcje inne niż tylko pokazywanie albumu/tytułu piosenki, etc.
- Statusy nie mają prawa by uruchamiać kod JS z ich własną funkcją by uzyskiwać zmienne. Jeżeli Firefox ma problemy z wbudowaną funkcją wewnątrz klasy `Presence`, możesz napisać swoją własną funckję i musisz poinformawać nam o tym w opisie w Pull Request.
- Presence słabej jakości (albo z małą ilością danych) **nie** są dozwolone. (np. pokazywanie logo i nazwy strony i nigdy nie zmienianie danych).
- Presence dla serwisów typu Lista botów/serwerów muszą spełniać kilka dodatkowych wymagań:
  - Domena musi mieć conajmniej **6** miesięcy.
  - Unikalni użytkownicy dziennie:
    - Dla 6+ miesięcznych domen: **20,000 unikalnych użytkowników dziennie**.
    - Dla 12+ miesięcznych domen: **45,000 unikalnych użytkowników dziennie**.
  - Strona nie może być na taniej domenie takiej jak `.xyz`, `.club`, i tak dalej.
  - Strona musi mieć bardzo dobra jakość, wygląd, itp.
- Prezentacje powinny używać [wspólnych szczegółów](https://api.premid.app/v2/langFile/presence/en) (ciągi zaczynające się od "general."). Możesz to osiągnąć używając `multiLanguage` z podantymi tekstami. Jeżeli Twój presence wymaga niestandardowych ciągów, nie powinieneń używać `multiLanguage`, dopóki presence nie będzie używane przez 1000 użytkowników. Zobacz przykład [tutaj](https://docs.premid.app/dev/presence/class#getstringsobject).
- Załączenie folderu `dist`, pliku `presence.ts`, pliku `iframe.ts` i pliku `metadata.json` jest obowiązkowe w taki sposób aby struktura plików naśladowała poniższy schemat:

```bash
presence
├── dist
│   └── metadata.json
├── presence.ts
└── tsconfig.json
```

lub jeżeli używasz pliku `iframe.ts`:

```bash
presence
├── dist
│   └── metadata.json
├── presence.ts
├── iframe.ts
└── tsconfig.json
```

## [**metadata.json**](https://docs.premid.app/dev/presence/metadata)

> Dla wygody naszych twórców presence dostarczyliśmy schemat, którego możesz użyć do weryfikacji integralności pliku `metadata`. Jest to całkowicie opcjonalne i nie jest wymagane w procesie weryfikacji.

> Zalecane jest zorganizowanie pliku `metadata` w formacie przedstawionym poniżej, musi on także zawierać gramatycnie poprawne nazwy serwisów, opisy, tagi i pola ustawień. Wszystkie pliki które nie śledzą schematu **nie** są dozwolone.

> Presences stron internetowych z treściami nieodpowiednimi dla dzieci **muszą** mieć tag `nsfw`, a logo/miniaturka **nie** może zawierać żadnej z tych treści.

Każdy presence posiada plik metadanych nazwany `metadata.json`, ten plik ma ścisły schemat. Jego przykład można znaleźć poniżej:

```json
{
  "$schema": "https://schemas.premid.app/metadata/1.7",
  "author": {
    "name": "NAZWA UŻYTKOWNIKA",
    "id": "DISCORD ID UŻYTKOWNIKA"
  },
  "contributors": [
    {
      "name": "NAZWA UŻYTKOWNIKA",
      "id": "DISCORD ID UŻYTKOWNIKA"
    }
  ],
  "service": "NAZWA USŁUGI",
  "altnames": ["INNA NAZWA USŁUGI"],
  "description": {
    "pl": "OPIS"
  },
  "url": "URL",
  "version": "WERSJA",
  "logo": "LINK DO LOGO",
  "thumbnail": "LINK DO MINIATURKI",
  "color": "#HEX000",
  "tags": ["TAG1", "TAG2"],
  "category": "KATEGORIA",
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
      "title": "WYŚWIETL TYTUŁ",
      "icon": "NIESAMOWITA IKONA",
      "value": true
    },
    {
      "id": "ID",
      "if": {
        "ID": true
      },
      "title": "WYŚWIETL TYTUŁ",
      "icon": "NIESAMOWITA IKONA",
      "value": "\"%song%\" stworzona przez %artist%",
      "placeholder": "użyj %song% lub %artist%"
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

> Jeśli pole jest wymienione jako opcjonalne w [dokumentacji](https://docs.premid.app/dev/presence/metadata) lub jest `*` obok klucza, a Twoja obecność używa dla niej wartości domyślnej, nie włączaj jej do pliku `. metadanych`. (np. statusy bez wsparcia dla iframe nie potrzebują pola `iframe`)

> Wszystkie obrazy w pliku `metadata`, muszą być hostowane na `i.imgur.com`. Używanie treści hostowanych na stronie **nie** jest dozwolone, ponieważ ścieżki i pliki mogą ulec zmianie.

Lista pól i ich zasad znajduje się poniżej:

### **`$schema`**

- Schemat _key_ **musi** zawierać znak dolara na jego początku, to zasygnalizuje twój edytor tekstowy, że chcesz zweryfikować plik JSON przeciwko modelowi. _Jak stwierdzono wcześniej, nie musisz zawierać schematu, ale jeśli go włączysz, musisz to uwzględnić._

### **`author`**

- _Wartość_ ID **musi** być twoim Discord ID. Możesz go uzyskać poprzez włączenie [trybu dewelopera](https://support.discord.com/hc/en-us/articles/206346498-Where-can-I-find-my-User-Server-Message-ID-). _Proszę **nie** mylić tego z ID aplikacji, która jest tylko dla Twojego presence._

### **`*contributors`**

- **Nie** dodawaj siebie jako współtwórcy, ani nie dodawaj kogoś innego, dopóki nie pomógł w presence.

### **`service`**

- Nazwa usługi **musi** być nazwą katalogu presence. Dla przykładu, jeśli presence jest w folderze `/websites/Y/YouTube`, w service musisz napisać `YouTube`.
- **Nie możesz** używać adresu serwisu jako nazwy, chyba że serwis używa URL jako nazwę. Jeśli nazwa nie jest opisowa i może zostać uznana za niejasną, **należy** użyć adresu URL. (np. `YouTube` jest dozwolony, ponieważ jest to oficjalna nazwa i opis, a `youtube.com` już nie jest. `Top` nie jest opisową nazwą, więc użycie URL strony `top.gg` jest **wymagane**.)
- Jeśli usługa ma zasady używania ich nazwy, powinieneś ich przestrzegać.

### **`*altnames`**

- Użyj tego **tylko wtedy**, gdy strona ma kilka oficjalnych nazw (np. Pokémon i 포켓몬스터). *Skrócono* wersje nazw naszych usług pod `tagami`.

### **`description`**

- **Wszystkie** presence **muszą** mieć angielski opis bez względu na preferowany język na stronie.
- **Nie próbuj** samodzielnie tłumaczyć opisu, chyba że znasz dany język, tłumacze zmodyfikują twój plik `metadata.json` i zmienią opisy jeśli będzie to potrzebne.

### **`url`**

- URL **musi** być stringiem jeśli strona używa tylko jednej domeny. Jeśli strona używa kilku domen, stwórz array z każdą domeną.
- **Nie** dodawaj protokołów do URL (np. `http` lub `https`) oraz nie dodawaj żadnych parametrów zapytania (np. `www.google.com/search?gws_rd=ssl`, gdzie powinno być `www.google.com`)

### **`version`**

- Zawsze upewnij się, że numer wersji spełnia [semantyczne standardy wersjonowania](https://semver.org), co przekłada się na następujący schemat: `<NEW-FEATURE>.<HUGE-BUGFIX>.<SMALL-BUGFIX-OR-METADATA-CHANGES>`. Wersje takie jak `1.0.0.1`, `1.0`, `1`, `1.0.0-BETA` lub zmiana `1.0.0` na `2.0.0` przy naprawieniu buga/małej zmianie jest **niedozwolone**.
- Wersja **musi** zawsze zaczynać się od `1.0.0`, inne wersje **nie** będą dozwolone.

### **`logo`**

- Logo **musi** być kwadratowym obrazem o proporcjach `1: 1`.
- Obraz **musi** mieć minimalną rozdzielczość `512x512` pikseli. Możesz zmienić rozmiar obrazu za pomocą narzędzia takiego jak [waifu2x](http://waifu2x.udp.jp/).

### **`thumbnail`**

- Miniaturka **powinna** być najlepiej [szeroką kartą promocyjną](https://i.imgur.com/3QfIc5v.jpg) lub [zrzutem ekranu](https://i.imgur.com/OAcBmwW.png), jeśli ta pierwsza **nie jest** dostępna.

### **`color`**

- Kolor **musi** być wartością szesnastkową pomiędzy `#000000` i `#FFFFFF`.
- Ciąg z kolorem **musi** być poprzedzony symbolem kratki.

### **`tags`**

- **Wszystkie** statusy muszą mieć przynajmniej _jeden_ tag.
- Tagi **Nie** mogą zawierać spacji, ukośników, pojedynczych/podwójnych cudzysłowów, znaków Unicode i powinny zawsze być pisane z małej litery.
- Tagi **powinny** zawierać alternatywne nazwy usług, aby ułatwić wyszukiwanie (np. jeśli obecność Amazon obejmowała obsługę AWS, miałaby swoje tagi, takie jak `amazon-web-services` i `aws`)
- Jesteś **zobowiązany** do dodania tagu `NSFW`, jeżeli presence jest dla strony NSFW</strong>.

### **`category`**

- Kategoria **musi** być jedną z następujących kategorii wymienionych w [dokumentacji](https://docs.premid.app/dev/presence/metadata#presence-categories).
- Presence musi używać kategorii, która pasuje do zawartości witryny. (np. nie używaj `anime`, gdy strona nie jest powiązana z anime).

### **`*regExp`** <br /> **`*iFrameRegExp`**

- Wyrażenia regularne **muszą** być prawidłowe. Proszę przetestować swoje wyrażenia za pomocą narzędzi wymienionych w [dokumentacji](https://docs.premid.app/en/dev/presence/metadata#testing).

### **`readLogs`**

- Musi być `wartości logicznej` (np. `true` lub `false`).
- Włącza logi twojego presence.

### **`warning`**

- Włącza ikonę ostrzeżenia, aby zapytać użytkownika, że ta obecność wymaga więcej kroków niż tylko dodawanie obecności.
- Przykładem obecności tej zmiennej metadanych jest `VLC`.

### **`settings`**

- Jeśli zdecydujesz się utworzyć ciąg formatu (np. `%song% by %artist%`), musisz mieć zmienne otoczone znakiem procentowym po obu stronach. Takie zmienne, jak `%var`, `var%`, lub `%%var%%` i wszystko pomiędzy **nie** są dozwolone ze względu na standaryzację.
- Nazwa ustawień nie może **** zawierać wszystkich wielkich liter. Na przykład nazwy takie jak `POKAŻ STATUS BROWSING` **nie** będą dozwolone; jednakże nazwy takie jak `Pokaż status przeglądania` lub `Pokaż status przeglądania` są dozwolone.
- Jeśli używasz opcji `wielojęzyczna`, może mieć następujące typy:
  - **typ logiczny**, który włączy tylko ciągi od [`ogólnie. syn`](https://github.com/PreMiD/Localization/blob/master/src/Presence/general.json) z repozytorium lokalizacji lub z pliku obecności (e.. kiedy nazwą obecności jest YouTube, rozszerzenie otrzyma również ciągi od `youtube.json`)
  - **String** type (np. `youtube`), który określi nazwę plików, z których chcesz pobrać ciągi.
  - **Array<String>** typ (np. `["youtube", "discord"]`) określający nazwę plików, z których chcesz pobrać ciągi.

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

## Modification

> You **must** change the version in the **metadata** to be a higher value from the previous version when making changes to either the **presence.ts**, **iframe.ts** or **metadata.json**.

In some situations, presences may behave unexpectedly or could use some minor changes to improve their functionality. Here is a list of rules that you **must** follow while modifiying presences.

- If the presence author hasn't been contactable in over a month, you may contact a reviewer to see if you can modify the presence.
- If you make modifications to a presence and change at least a **quarter** of the presence's codebase, you are allowed to add yourself as a contributor. Contact a reviewer for more information about this subject.
- Anyone may create PRs to fix bugs. Do **not** change images if they are not outdated and are in specifications.

# Verification

> **Wszystkie** kody dodane do sklepu będą licencjonowane jako `Mozilla Public License 2.0`.

> Jeśli chcesz się z kimś skontaktować, użyj naszego oficjalnego serwera Discord. All reviewers will have the `Reviewer` role on their profile.

> Please keep in mind that the reviewers work voluntarily and manage other repositories in addition to this one, your pull request may not get reviewed until hours or even days after it has been created.

> **Zawsze** miej aktualny "fork" przed utworzeniem "Pull Request". This will help limit false positives from the checks.

The most important process of presence development is getting your presence on the store. This is done by making a [pull request](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/creating-a-pull-request) on GitHub on the `PreMiD/Presences` repository. Our reviewers will confirm that your presence is up to standards and will push it onto the store.

<div>
  <h2 style="font-size: 2rem; margin-bottom: 0;">Presence Reviewers</h2>
  <a href="https://github.com/Bas950"><img src="https://github.com/Bas950.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
  <a href="https://github.com/EncryptedDev"><img src="https://github.com/EncryptedDev.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
</div>

## `Restrictions`

Repetitive offenses such as breaking guidelines, spamming pull requests, threats, or innapropriate behavior will get you banned from creating presences.

In this scenario, the following changes will occur:

- Presences under your management will be transferred to the PreMiD bot or another user (reviewer decision). The application id for each presence will be recreated under the new owner's name.
- All of your issues and pull requests (presence creation, presence contribution, etc) created following the ban will be prompty closed.
- Tickets created under your name regarding presence development will be deleted.

## `Przegląd i recenzja`

Kilka rzeczy, które powinieneś wiedzieć po otwarciu pull request:

- It takes 2 reviewers to merge a pull request.
- If a pull request is inactive for a period of 7 days, it will be promptly closed.
- All checks **must** be passed in order to merge.
- ⚠️ You **must** provide new, unaltered screenshots (taken by you) showing a side-by-side comparison of your profile and the website to prove that your presence works. _You are allowed to stitch screenshots together for viewing pleasure_ This applies for both creation and modification.
- ⚠️ You are also **required** to include screenshots of the presence settings in the extension if supplied. An example can be seen [here](https://imgur.com/a/OD3sj5R).

## `Checks`

![Testy](https://i.imgur.com/vF7QpBH.png)

Currently, a presence goes through 3 separate stages of checks. All of these checks help the reviewers determine whether your presence is suitable for deployment.

- `DeepScan` is a bot that checks for code quality. If you ever receive errors for new issues, you are **required** to fix them. *Warning: DeepScan doesn't always give you errors. Please look at CodeFactor warnings instead.*
- `CodeFactor` is a bot that checks for code quality. If you ever receive errors for new issues, you are **required** to fix them.
- `Schema Validation` will scan your `metadata.json` file for any errors (for e.g., missing fields, invalid value types, etc.). If you ever see any new issues, you are also **required** to fix those. Adding a schema field to your `metadata.json` file will allow your text editor (if supported) to show you these errors during development.

## `Additional Rules`

- **Always** make sure to start your presence in the most appropriate folder, if its name starts with _any_ Latin letter then it must be under its alphabetical match (for e.g., `D/dアニメストア` or `G/Google`). Any other Unicode/non-Latin characters **must** be under the `#` folder (for e.g., `#/巴哈姆特`) and numbers under the `0-9` folder (for e.g., `0-9/4anime`).

After meeting all of the guidelines with the proper reviews and checks, your presence will be merged with the store.

# Weryfikacja

Jeśli masz jakieś sugestie dotyczące naszych wytycznych, powinieneś skontaktować się z nami @ [Serwer Discorda PreMiD](https://discord.premid.app) a my je sprawdzimy!

# Wkład

`3 Rewizja` wytycznych została stworzona przez następujące osoby:

<div>
<a href="https://github.com/PreMiD"><img src="https://github.com/PreMiD.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
</div>

`2 Rewizja` wytycznych została stworzona przez następujące osoby:

<div>
<a href="https://github.com/CobyPowers"><img src="https://github.com/CobyPowers.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
</div>

`1 Rewizja` była stworzona przez następujące osoby:

<div>
<a href="https://github.com/CobyPowers"><img src="https://github.com/CobyPowers.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
<a href="https://github.com/Bas950"><img src="https://github.com/Bas950.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
<a href="https://github.com/i1u5"><img src="https://github.com/i1u5.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
</div>
