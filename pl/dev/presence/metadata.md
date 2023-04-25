---
title: Metadata.json
description: Zawiera podstawowe dane o Presence
published: true
date: 2021-12-20T14:27:18.034Z
tags:
editor: markdown
dateCreated: 2020-06-11T18:04:52.965Z
---

# Metadata.json

Jeśli chcesz opublikować swój status Presence w sklepie i załadować go przez rozszerzenie, powinieneś utworzyć plik `metadata.json` w folderze `dist`.

Przykład podanego profilu może być znaleziony poniżej.

```json
{
  "author": {
    "name": "USER",
    "id": "ID"
  },
  "contributors": [{
    "name": "USER",
    "id": "ID"
  }],
  "service": "SERVICE",
  "altnames": ["SERVICE"],
  "description": {
    "en": "DESCRIPTION"
  },
  "url": "URL",
  "regExp": "REGEXP",
  "iFrameRegExp": "REGEXP",
  "version": "VERSION",
  "logo": "URL",
  "thumbnail": "URL",
  "color": "#45A8FC",
  "tags": ["TAG1", "TAG2"],
  "category": "CATEGORY",
  "iframe": false,
  "settings": [
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

## Zrozumienie metadata.json

Ten przykład wygląda naprawdę dziwnie, prawda? Nie martw się, nie jest trudno zrozumieć, do czego służy każda zmienna.

<table>
  <thead>
    <tr>
      <th style="text-align:left">Zmienna</th>
      <th style="text-align:left">Opis</th>
      <th style="text-align:left">Typ</th>
      <th style="text-align:left">Opcjonalny</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>author</b></td>
      <td style="text-align:left">Powinien zawierać obiekt o <code>nazwie</code> i <code>id</code> współautora. User <code>id</code> can be copied from Discord by enabling developer
        mode and right-clicking on your profile. <code>Id</code> użytkownika można skopiować z Discorda włączając tryb programisty i klikając prawym przyciskiem myszy na swój profil.</td>
      <td style="text-align:left"><code>Object</code></td>
      <td style="text-align:left"><code>Nie</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>contributors</b></td>
      <td style="text-align:left">Powinien zawierać obiekt o <code>nazwie</code> i <code>id</code> współautora. <code>Id</code> użytkownika można skopiować z Discorda włączając tryb programisty i klikając prawym przyciskiem myszy na swój profil. <code>Id</code> użytkownika można skopiować z Discorda włączając tryb programisty i klikając prawym przyciskiem myszy na swój profil.</td>
      <td style="text-align:left"><code>Array&lt;Object&gt;</code></td>
      <td style="text-align:left"><code>Tak</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>service</b></td>
      <td style="text-align:left">Tytuł usługi wspieranej przez ten presence.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Nie</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>altnames</b></td>
      <td style="text-align:left">Służą do wyszukiwania presence używając alternatywnej nazwy.<br> 
      Ma być używany dla presence, które mają różne nazwy w różnych językach (np. Pokémon i 포켓몬스터).<br>
      Możesz tego użyć również dla presence posiadających znaki specjalne, więc nie musisz ich nawet wpisywać (np.: Pokémon i Pokemon).</td>
      <td style="text-align:left"><code>Array&lt;String&gt;</code></td>
      <td style="text-align:left"><code>Tak</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>description</b></td>
      <td style="text-align:left">Opis usługi <b>NOT</b> obecności. Twój opis musi zawierać kluczowe wartości wskazujące język oraz opis w tym konkretnym języku. Twórz opisy z językami <i>, które znasz</i>, nasi tłumacze wprowadzą zmiany do twojego pliku metadanych. Wyświetl kategorię języków Presence dla listy. </td>
      <td style="text-align:left"><code>Object</code></td>
      <td style="text-align:left"><code>Nie</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>url</b></td>
      <td style="text-align:left">URL usługi<br>
      <b>Przykład:</b><code>vk.com</code><br>
      <b>Podany URL musi być zgodny z adresem URL strony, bo będzie używany by wykryć czy to jest ta strona do której należy zainicjować skrypt. Może to być użyte jako tablica tylko wtedy, gdy istnieje więcej niż jeden adres URL.</b></td>
      <td style="text-align:left"><code>String, Array&lt;String&gt;</code></td>
      <td style="text-align:left"><code>Nie</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>regExp</b></td>
      <td style="text-align:left">Ciąg wyrażenia regularnego używany do dopasowywania adresów URL.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Tak</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>version</b></td>
      <td style="text-align:left">Wersja twojego presence.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Nie</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>logo</b></td>
      <td style="text-align:left">Link do loga serwisu.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Nie</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>thumbnail</b></td>
      <td style="text-align:left">Link do miniaturki presence.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Nie</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>color</b></td>
      <td style="text-align:left">Wartość <code>#HEX</code>. Zalecamy użycie podstawowego koloru usługi,
         którą obsługuje Twój presence.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Nie</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>category</b></td>
      <td style="text-align:left">Tablica z tagami, pomoże użytkownikom wyszukać Twoje presence na stronie.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Nie</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>tags</b></td>
      <td style="text-align:left">Ciąg używany do reprezentowania kategorii, pod którą znajduje się presence.</td>
      <td style="text-align:left"><code>String, Array&lt;String&gt;</code></td>
      <td style="text-align:left"><code>Nie</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>iframe</b></td>
      <td style="text-align:left">Określa, czy użyto <code>iFrames</code></td>
      <td style="text-align:left"><code>Boolean</code></td>
      <td style="text-align:left"><code>Tak</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>iFrameRegExp</b></td>
      <td style="text-align:left">Selektor wyrażenia regularnego, który wybiera iframes do wybrania.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Tak</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>readLogs</b></td>
      <td style="text-align:left">Określa, czy rozszerzenie powinno odczytywać logi.</td>
      <td style="text-align:left"><code>Boolean</code></td>
      <td style="text-align:left"><code>Tak</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>settings</b></td>
      <td style="text-align:left">Szereg ustawień, które użytkownik może zmienić</td>
      <td style="text-align:left"><code>Array&lt;Object&gt;</code></td>
      <td style="text-align:left"><code>Tak</code></td>
    </tr>
  </tbody>
</table>

## Wyrażenia regularne

Jeśli chcesz nauczyć się regularnych wyrażeń, oto kilka stron internetowych.

#### Nauka

• [Quick Starter Video](https://youtu.be/sXQxhojSdZM) • [RegexOne](https://regexone.com/) • [Regular Expressions Info](https://www.regular-expressions.info/tutorial.html)

#### Testowanie

• [Regexr](https://regexr.com/) • [Regex101](https://regex101.com/)

## Języki - Presence

PreMiD to usługa wielojęzyczna, co oznacza, że istnieje wiele języków, które łączą użytkowników na całym świecie. Pełna lista języków znajduje się w tym [punkcie końcowym API](https://api.premid.app/v2/langFile/list). By dostosować swój presence jeszcze bardziej możesz pozwolić użytkownikom na wybranie wyświetlanego języka. Przejdź do [`multiLanguage`](#multilanguage) po więcej. Zobacz [`multiLanguage`](#multilanguage), aby dowiedzieć się więcej.

## Ustawienia - Presence
Skonfiguruj ustawienia interaktywne, aby użytkownicy mogli dostosować swój status Presence!
```json
"settings": [
  {
    "id": "ID",
    "multiLanguage": true //See https://docs.premid.app/dev/presence/metadata#multilanguage
  },
  {
    "id": "ID",
    "title": "DISPLAY TITLE",
    "icon": "FONTAWESOME ICON", //Example "fas fa-info"
    "value": true // Wartość boolean stworzy to jako przełącznik włącz/wyłącz z obecną wartością z wartością dowolną
  },
  {
    "id": "ID",
    "if": {
      "ID": true //Jeżeli kolejne ustawienie równa się wartości (true/false/0/1/etc.) wtedy pokaż ten przycisk
    },
    "title": "DISPLAY TITLE",
    "icon": "FONTAWESOME ICON",
    "value": "\"%song%\" by %artist%", // Wkładanie wartości  spowoduje, że ustawienie zmieni się w wejściowe, gdzie będziesz mógł użyć dowolne wejście.
    "placeholder": "use %song% or %artist%" // Jeżeli wejściówka będzie pusta, będzie to  wyszarzone 
  },
  {
    "id": "ID",
    "title": "DISPLAY TITLE",
    "icon": "FONTAWESOME ICON",
    "value": 0, //Default value of the selector
    "values": ["1", "2", "etc."] // Zrobi ustawienie selektorem, gdzie ty wybierasz który chcesz
  }
]
```

### `multiLanguage`

#### Wprowadzenie

Ustawienie `multiLanguage` jest używane by pozwolić użytkownikom na manualny wybór języka w którym presence ma być wyświetlane. To wymaga użycie ciągów z naszego [API](https://api.premid.app/v2/langFile/presence/en),po informacje jak dodać więcej ciągów kliknij [tutaj](https://docs.premid.app/dev/presence/metadata#adding-new-strings).

#### Ustawienie

Ustawienie `multiLanguage` jest wyjątkowym przypadkiem, nie wymaga `tytułu` ani `ikonki` ani `wartości` lub `wartości` podobnie jak inne ustawienia, ale wymaga, żebyś ustawił wiele innych rzeczy!

Klucz `multiLanguage` może być ustawiony następująco:

`true` użyj tego, jeżeli tylko będziesz używać wartościpliku `general.json` i plik `<service>.json` [Localization Repository](https://github.com/PreMiD/Localization/tree/master/src/Presence). `string`: nazwa pliku nie wliczając rozszerzenia (.json) w <a>href="https://github.com/PreMiD/Localization/tree/master/src/Presence">Localization Repository</a> (nie wliczając pliku ` general `, od kiedy jest zawsze załadowany). Tylko języki, zarówno ` general ` i wprowadzonego pliku będą wyświetlane. `Array<String>`: if you are using more than one file inside the [Localization Repository](https://github.com/PreMiD/Localization/tree/master/src/Presence) Możesz specifykować wszystkie wartości w szyko (nie wliczając pliku ` general ` od kiedy jest zawsze załadowane). Tylko dowolne języki wszystkich plików będą wyświetlane.

#### Dodawanie nowych ciągów

Każdy `string` jest ` obiektem ` gdzie od nazwy zaczyna się nazwą usługi i wtedy tak nazwany stringName z kropką pomiędzy nimi.

##### Klonowanie projektu

1. Otwórz terminal i wpisz `git clone https://github.com/PreMiD/Localization`.
2. Wybierz folder.
3. Otwórz go w swoim edytorze kodu.

##### Tworzenie pliku

1. Przejdź do folderu `src`.
2. Idź do folderu `Presence`.
3. Utwórz plik o nazwie `<service>.json`. (Serwis jest **name** (to nie URL) w małych literkach serwisu którego chcesz wspierać.)

##### Dodawanie ciągów

Każdy `string` jest ` obiektem ` gdzie od nazwy zaczyna się nazwą usługi i wtedy tak nazwany stringName z kropką pomiędzy nimi.

StringName jest jednosłownym identyfikatorem wiadomości.

`Objekt` ma dwie właściwości; `wiadomość` i `opis`. `wiadomość` jest tekstem, który musi być przetłumaczony. `opis` jest opisem wiadomości który pomaga naszym tłumaczom zrozumieć co tłumaczą.

**Informacja:** Nie dodawaj żadnych duplikatów ciągów. (Wlicza to ciągi z pliku `general.json` ale nie z innych plików)

Wizualizacja pliku:

```json
{
  "<service>.<stringName>": {
    "message": "Text który musi zostać przetłumaczony.",
    "description": "To tłumaczy, czym jest wiadomość powyżej."
  },
  "<service>.<stringName>": {
    "message": "Text który musi zostać przetłumaczony."",
    "description": "To tłumaczy, czym jest wiadomość powyżej."
  }
}
```

Po pełnym utworzeniu pliku z ciągami, możesz utworzyć Pull Request w [Repozytorium Lokalizacji](https://github.com/PreMiD/Localization) w opisie ** musisz ** załączyć link do swojego Pull Request o zaktualizowanego Presenc po użyciu nowych ciągów z [Repozytorium Presence](https://github.com/PreMiD/Presences).

#### Domyślne przyciski
The keys you didn't have to set are automatically set to the following: `title`: "Language" **Note:** This is translated into their default language (browser language). `icon`: "fas fa-language" ([Preview](https://fontawesome.com/icons/language)) `value`: **Set to their browser language if it is available (100% translated), otherwise English.** `values`: **Set to the available languages (languages that have it 100% translated).**

**Informacja:** Nie można w żaden sposób takowych zmienić.

### Metody

Zwraca wartość ustawienia.
#### `getSetting(String)`
Ukrywa podane ustawienie.
```ts
const setting = await presence.getSetting("pdexID"); // Zamień pdexID z Id ustawienia
console.log(setting); // To zapisze log wartości ustawienia
```

#### `hideSetting(String)`
Pokazuje podane ustawienie (działa tylko, jeśli ustawienie było już ukryte).
```ts
presence.hideSetting("pdexID"); //Zamień pdexID na id ustawienia
```

#### `showSetting(String)`
Pokazuje podane ustawienie (działa tylko, jeśli ustawienie było już ukryte).
```ts
presence.showSetting("pdexID"); //Zamień pdexID na id ustawienia
```

## Kategorie - Presence

Tworząc swój Presence, musisz określić kategorię, do której należy. To jest skompilowana lista kategorii, których możesz użyć.

<table>
  <thead>
    <tr>
      <th style="text-align:left">Kategoria</th>
      <th style="text-align:left">Nazwa</th>
      <th style="text-align:left">Opis</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>anime</b></td>
      <td style="text-align:left"><b>Anime</b></td>
      <td style="text-align:left">Wszystko związane z anime, od forów po platformy streamingu wideo.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>games</b></td>
      <td style="text-align:left"><b>Gry</b></td>
      <td style="text-align:left">Każda strona internetowa, która ma treści związane z grami, takie jak <code>Kahoot</code> lub <code>Skribbl.io</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>music</b></td>
      <td style="text-align:left"><b>Muzyka</b></td>
      <td style="text-align:left">Są to strony internetowe oferujące treści związane z muzyką, czy to strumieniowe, czy pobierane.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>socials</b></td>
        <td style="text-align:left"><b>Media Społecznościowe</b></td>
      <td style="text-align:left">Strony internetowe wykorzystywane do tworzenia i udostępniania treści lub do udziału w innych formach sieci społecznościowych.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>videos</b></td>
        <td style="text-align:left"><b>Filmy i transmisje</b></td>
      <td style="text-align:left">Strony internetowe służące do dostarczania filmów i strumieni.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>other</b></td>
      <td style="text-align:left"><b>Inne</b></td>
      <td style="text-align:left">Każda z tych kategorii, które nie wchodzą w zakres określonych wyżej kategorii.</td>
    </tr>
  </tbody>
</table>

